```bash
yc compute filesystem list
```

Result:

```text
+----------------------+-------------------+------------+-------------------+--------+-------------+
|          ID          |        NAME       |    SIZE    |       ZONE        | STATUS | DESCRIPTION |
+----------------------+-------------------+------------+-------------------+--------+-------------+
| epdtcr9blled******** | first-filesystem  | 1073741824 | {{ region-id }}-a | READY  |             |
| epd3f4gv8bs4******** | second-filesystem | 1073741824 | {{ region-id }}-a | READY  |             |
+----------------------+-------------------+------------+-------------------+--------+-------------+
```