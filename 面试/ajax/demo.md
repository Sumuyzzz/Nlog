```dataview 
table time-played, length, rating from "games" sort rating desc 
```


```dataviewjs 
dv.taskList(dv.pages().file.tasks.where(t => !t.completed)); 
```