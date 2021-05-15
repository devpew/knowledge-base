# PostgreSQL Backup & Restore



### Для того чтобы сделать бэкап 

```
pg_dump -U postgres -d fin -t funds > 1.sql
```

### Чтобы восстановить таблицу из бэкапа

```
psql -U postgres fin < investpercent
```

