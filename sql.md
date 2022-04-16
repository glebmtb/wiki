**unix timestamp to date**
```
select CAST(to_timestamp(create_ts / 1000) AS date)
select to_char(to_timestamp(create_ts / 1000), 'yyyy-mm-dd')
```

**now**
```
select to_char(now(), 'yyyy-mm-dd')
```

