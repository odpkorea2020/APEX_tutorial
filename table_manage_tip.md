### # How to log log-in user activities by a table trigger in APEX application

1. for inserting

```
CREATE OR REPLACE EDITIONABLE TRIGGER  "unique trigger name" 
  before insert on "table name"               
  for each row  
begin   
  if :NEW."column name" is null then 
    select sysdate into :NEW."column name" from sys.dual; 
  end if; 
end;

/
ALTER TRIGGER  "unique trigger name" ENABLE
/
```

2. for updating

```
CREATE OR REPLACE EDITIONABLE TRIGGER  "unique trigger name" 
  before update on "table name"               
  for each row  
begin   
  select sysdate into :NEW."column name" from sys.dual; 
end;

/
ALTER TRIGGER  "unique trigger name" ENABLE
```

### # How to log inserted, or updated date & time by a table trigger in APEX application


1. inserting (v('APP_USER') is a log-in user name)

```
CREATE OR REPLACE EDITIONABLE TRIGGER  "unique trigger name" 
  before insert on "table name"               
  for each row  
begin   
  if :NEW."column name" is null then 
    select v('APP_USER') into :NEW."column name" from sys.dual; 
  end if; 
end;

/
ALTER TRIGGER  "unique trigger name" ENABLE
/
```

2. updating (v('APP_USER') is a log-in user name)

```
CREATE OR REPLACE EDITIONABLE TRIGGER  "unique trigger name" 
  before update on "table name"               
  for each row  
begin   
  select v('APP_USER') into :NEW."column name" from sys.dual; 
end;

/
ALTER TRIGGER  "unique trigger name" ENABLE
```

