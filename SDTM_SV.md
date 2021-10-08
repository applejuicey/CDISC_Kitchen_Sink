# SDTM.SV Kitchen Sink
---
## Genernal Idea on How to Generate SDTM.SV
1. 取出rawdata中所有dtc变量，包括该条记录对应的visit（访视名称）（TODO: 哪些dtc变量不要？）
2. 根据每条记录的visit，将所有记录分为计划内访视和计划外访视两个数据集，其后分别进行处理
### 单独处理计划内访视
3. 根据visit从SDTM.TV里面获取visitnum, visitdy两个变量
4. 按照受试者-visitnum-dtc变量升序排序，每个受试者的每个visitnum的第一个dtc变量为svstdtc、最后一个dtc变量为svendtc
### 单独处理计划外访视
5. 按照受试者-visit-dtc变量升序排序，每个受试者的每个visit的第一个dtc变量为svstdtc、最后一个dtc变量为svendtc
### 合并计划内访视与计划外访视，整体处理
6. 按照受试者-svstdtc变量升序排序，计划外访视的visitnum为其上一条记录的visitnum + 0.1，其visit为'Unscheduled Visit ' + visitnum拼接
7. 根据usubjid从SDTM.DM中获取rfstdtc，以此计算svstdy, svendy
