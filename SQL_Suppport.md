```SQL
SELECT * FROM information_schema.tables WHERE table_schema = 'qihanoa';
#table_name, COLUMN_NAME, COLUMN_TYPE, IS_NULLABLE, COLUMN_KEY, COLUMN_COMMENT
SELECT * FROM information_schema.columns WHERE table_schema = 'qihanoa' AND table_name = 'customerservices';
```
```SQL
show create table customerservices;
select TABLE_NAME,COLUMN_NAME,REFERENCED_TABLE_NAME,REFERENCED_COLUMN_NAME from information_schema.KEY_COLUMN_USAGE where TABLE_NAME = 'customerservices' and CONSTRAINT_NAME != 'PRIMARY';
```
#用于查询表关系
```SQL
SELECT col.table_name, col.COLUMN_NAME, col.COLUMN_TYPE, col.IS_NULLABLE, col.COLUMN_KEY,
  (select REFERENCED_TABLE_NAME from information_schema.KEY_COLUMN_USAGE kcu where kcu.TABLE_NAME = col.table_name and kcu.COLUMN_NAME=col.COLUMN_NAME and kcu.CONSTRAINT_NAME != 'PRIMARY') as REFERENCED_TABLE_NAME,
  (SELECT TABLE_COMMENT FROM information_schema.tables tb WHERE tb.table_schema = col.table_schema and tb.TABLE_NAME = col.table_name) as TABLE_COMMENT, col.COLUMN_COMMENT
FROM information_schema.columns col WHERE col.table_schema = 'qihanoa' ;
```
