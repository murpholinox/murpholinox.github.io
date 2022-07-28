---
layout: post
title: How to do a complete cross-validation with pairef?
published: true
tag: Pairef
---

1. Get the `*.mtz` **sans** `R_free` flags. 
2. Then do ```phenix.reflection_file_converter --generate_r_free_flags --r_free_flags_fraction=0.05 --r_free_flags_max_free=99999 --r_free_flags_format=ccp4 output_file_name.mtz --label="IMEAN,SIGIMEAN" --mtz=nocut_rfreeflagswithprfc.mtz```
3. Finally do ```cctbx.python -m pairef --XYZIN PDBFILE --HKLIN nocut_rfreeflagswithprfc.mtz -u XDS_ASCII.HKL -i 1.3 -r 1.25,1.20,1.15,1.10,1.05 -P --complete```