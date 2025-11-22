@startuml

entity "User" as User {
  *id : UUID <<PK>>
  --
  email : string <<UNIQUE>>
  passwordHash : string
  createdAt : datetime
  updatedAt : datetime
}

entity "Task" as Task {
  *id : UUID <<PK>>
  --
  userId : UUID <<FK>>
  title : string
  description : string
  isCompleted : boolean
  createdAt : datetime
  updatedAt : datetime
  --
  userId : INDEX
  isCompleted : INDEX
}

entity "Tag" as Tag {
  *id : UUID <<PK>>
  --
  userId : UUID <<FK>>
  name : string <<UNIQUE (per user)>>
  createdAt : datetime
  updatedAt : datetime
  --
  userId : INDEX
  name : INDEX
}

entity "TaskTag" as TaskTag {
  *taskId : UUID <<FK>>
  *tagId  : UUID <<FK>>
  --
  (taskId, tagId) : COMPOSITE PK
}

User ||--o{ Task : owns
User ||--o{ Tag : creates
Task ||--o{ TaskTag : ""
Tag ||--o{ TaskTag : ""

@enduml
