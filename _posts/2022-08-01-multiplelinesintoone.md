---
layout: post
title: How to convert many lines to one line?
published: true
tag: command line
---

How to convert many lines to one, from [here](https://stackoverflow.com/questions/15758814/turning-multiple-lines-into-one-comma-separated-line).

```bash
cat file.txt 
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
awk -F "-" '{print $2}' file.txt | xargs
30 115 94 4 80 81 106 8 9 61 65 76 129 27 74 47 25 13 129
# or we can use `tr`
awk -F "-" '{print $2}' prueba.txt | tr '\n' ' ' 
30 115 94 4 80 81 106 8 9 61 65 76 129 27 74 47 25 13 129
```
