## 🔍 Detection Queries



### Brute Force Detection

```sql

FROM soc_logs

| WHERE message LIKE "*4625*"

```



### Successful Login

```sql

FROM soc_logs

| WHERE message LIKE "*4624*"

```



### Suspicious Process Execution

```sql

FROM soc_logs

| WHERE message LIKE "*4688*"

```



### Correlation (Same IP)

```sql

FROM soc_logs

| STATS count BY source_ip

| SORT count DESC

```

These queries were used to detect brute-force attempts, successful authentication, and suspicious post-login activity
