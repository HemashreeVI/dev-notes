# awk for columns

awk splits each line into fields `$1, $2, ...` (whitespace by default).

```bash
awk '{print $1}' access.log                     # first column (IP)
awk -F, '{print $2}' data.csv                   # comma-separated
awk '$9 == 500' access.log                      # rows where status is 500
awk '{sum += $3} END {print sum}' sizes.txt      # total of column 3
awk '{c[$1]++} END {for (ip in c) print c[ip], ip}' access.log | sort -rn | head
# ^ top IPs by request count
awk 'NR > 1' data.csv                           # skip header line
```

`NR` = line number, `NF` = number of fields, `$NF` = last field.
