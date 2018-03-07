```mermaid
gantt
	dateFormat  YYYY-MM-DD
	title График готовности функционала
	Cогласование				:active, ct, 2018-03-15, 1w
	section 14 вебсервисов
	Ярфит    			        :crit, active, yar14, after ct, 14w
	ArealIdea           		:crit, active, after ct, 2w
	Тестирование       			:crit, after yar14, 7d
	section 1 вебсервис
	ЯрФИТ	            		:crit, active, yar, after ct, 7w
	ArealIdea            		:crit, active, after ct, 7w
	Тестирование       			:crit, after yar, 7d
```
