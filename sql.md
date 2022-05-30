**unix timestamp to date**
```
select CAST(to_timestamp(create_ts / 1000) AS date)
select to_char(to_timestamp(create_ts / 1000), 'yyyy-mm-dd')
```

**now**
```
select to_char(now(), 'yyyy-mm-dd')
```
**now java timestamp**
```
select CAST (EXTRACT (epoch from current_timestamp) AS bigint) * 1000 as now;
```

**json**
```
where action ->> 'canonCode' = 'incggzz8wnkn5'
```
