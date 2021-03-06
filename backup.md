```plantuml
@startuml
title Approximate Backup Scheme
skinparam arrowThickness 2
actor "User" as user

rectangle #WhiteSmoke {

  queue RabbitMQ as q
  package "frontend package" as package_front #SeaShell {
    frame api
  }

  package "Backup service package" as package_b #PowderBlue {
    component "Backup runner" as brunner
    note bottom of brunner
      May be more
      than one service
    end note
    component "Backup service" as bservice
  }

  package "DB service package" as package_db #Ivory {
    database "\nDatabase\n" as db
    component "Credentials service" as cred_service
    component "Cron service" as cron_service
    component "Write service" as wservice
  }
}


user -d--> api #IndianRed: Add\nbackup\njob

cron_service <-- db #Purple: Get jobs\n by schedule
cron_service -r-> q #DarkGreen: Put\njobs

cred_service <- q #SteelBlue: Get job\nwithout\ncredentials
cred_service <--- db #Purple: Get credentials
cred_service -> q #DarkGreen: Put job\nwith\ncredentials

api -> q #DarkGreen: Put backup job\nwithout credentials
q -d-> brunner #SteelBlue
brunner -> q #DarkGreen: Backup\nfinished

brunner --> bservice #Navy: Run backup
brunner <- bservice #Navy: Backup\nfinished
q -> wservice #SteelBlue: Get\nbackup\ninfo
wservice -u-> db #Purple: Put\nbackup\ninfo

@enduml

```