# Changing schema name
```sql
-- get id of schema
-- to perform this you will have to login as sysdba
select user#,NAME from SYS.user$ WHERE NAME='TEST';

-- modify name
UPDATE USER$ SET NAME='NEW_SCHEMA_NAME' WHERE USER#=93;
commit;

-- modify system scn
ALTER SYSTEM CHECKPOINT;

-- refresh shared pool
ALTER SYSTEM FLUSH SHARED_POOL;

-- modify the new schema's password
ALTER USER new_schema  IDENTIFIED BY new_pass;

```

#### Links
[[Oracle]]
#### Tags

#### References
[How to change schema name?](https://stackoverflow.com/questions/18730850/how-to-change-schema-name)
