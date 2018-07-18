### 快速生成表常量

```
SELECT CONCAT('const COL_',UPPER(column_name),' = ''',column_name,''';') FROM information_schema.`COLUMNS` 
WHERE table_schema = 'ccs_workflow' AND  table_name = 'workflow_instance';

SELECT CONCAT('self::COL_',UPPER(column_name),',     //',column_name) FROM information_schema.`COLUMNS` WHERE table_schema = 'ccs_workflow' AND  table_name = 'workflow_instance'
```