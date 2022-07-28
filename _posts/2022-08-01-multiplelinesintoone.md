---
title: How to convert many lines to one line?
layout: post
published: true
tag: cli
---


From [here](https://stackoverflow.com/questions/15758814/turning-multiple-lines-into-one-comma-separated-line)

```
murphy@eva02:~/B/data_4.5/ridl/RIDL-metrics/csvFiles/Standard awk -F "," '{print $2}' head21lossstandardcopy.csv 
atominfo
A-30-CYS-SG
A-115-CYS-SG
A-94-CYS-SG
C-4-CL-CL
A-80-CYS-SG
A-81-SER-N
S-106-HOH-O
A-8-LEU-CD2
A-9-ALA-O
A-61-ARG-N
A-65-ASN-O
A-76-CYS-SG
A-129-LEU-C
A-27-ASN-CG
A-74-ASN-C
A-47-THR-OG1
A-25-LEU-N
A-13-LYS-NZ
A-129-LEU-O
murphy@eva02:~/B/data_4.5/ridl/RIDL-metrics/csvFiles/Standard awk -F "," '{print $2}' head21lossstandardcopy.csv | xargs
atominfo A-30-CYS-SG A-115-CYS-SG A-94-CYS-SG C-4-CL-CL A-80-CYS-SG A-81-SER-N S-106-HOH-O A-8-LEU-CD2 A-9-ALA-O A-61-ARG-N A-65-ASN-O A-76-CYS-SG A-129-LEU-C A-27-ASN-CG A-74-ASN-C A-47-THR-OG1 A-25-LEU-N A-13-LYS-NZ A-129-LEU-O
```
