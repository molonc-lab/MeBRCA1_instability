# MeBRCA1_instability

**BRCA1 promoter methylation analysis**

This repository contains a streamlined processing pipeline for nanopore sequencing data, used to extract relevant methylation and structural variant information at the *BRCA1* locus.

---

## System Requirements

Developed and tested on CentOS Linux 7 (Core) with:

- R/4.2.0, R/3.6.2, R/3.5.1, R/3.4.1
- Python/3.9.13, Python/3.9.6
- bedtools/2.29.0
- VEP/102
- Bismark/0.19.1

Dependencies for Python and R are listed below.

---

## R Dependencies

**R/4.3.1**

<details>
<summary>Click to expand full package list</summary>

- ggforce
- GenomicAlignments
- GenomicRanges
- Rsamtools
- data.table
- signal
- ComplexHeatmap
- ggplot2
- tidyverse
- purrr
- scales
- ggrepel
- vroom
- matrixStats
- circlize
- dplyr
- patchwork
- stats
- ggbeeswarm
- edgeR
- Gviz
- ggridges
- BSgenome.Hsapiens.UCSC.hg38
- glue
- rstatix
- ggpubr
- drc
- emmeans
- FactoMineR
- factoextra

</details>

Full session package versions:

```
other attached packages:
 [1] emmeans_1.10.4                    factoextra_1.0.7                  FactoMineR_2.11                   drc_3.0-1
 [5] BSgenome.Hsapiens.UCSC.hg38_1.4.5 BSgenome_1.70.2                   rtracklayer_1.62.0                BiocIO_1.12.0
 [9] glue_1.7.0                        rstatix_0.7.2                     ggridges_0.5.6                    Gviz_1.46.1
[13] edgeR_4.0.16                      limma_3.58.1                      ggbeeswarm_0.7.2                  GenomicAlignments_1.38.2
[17] Rsamtools_2.18.0                  Biostrings_2.70.3                 XVector_0.42.0                    SummarizedExperiment_1.32.0
[21] Biobase_2.62.0                    MatrixGenerics_1.14.0             GenomicRanges_1.54.1              GenomeInfoDb_1.38.8
[25] IRanges_2.36.0                    S4Vectors_0.40.2                  BiocGenerics_0.48.1               ggforce_0.4.2
[29] MASS_7.3-60.0.1                   VennDiagram_1.7.3                 futile.logger_1.4.3               ggtranscript_1.0.0
[33] patchwork_1.3.0                   tidyfast_0.4.0                    circlize_0.4.16                   scattermore_1.2
[37] ggpubr_0.6.0                      corrplot_0.94                     matrixStats_1.4.1                 vroom_1.6.5
[41] ggrepel_0.9.6                     scales_1.3.0                      lubridate_1.9.3                   forcats_1.0.0
[45] stringr_1.5.1                     dplyr_1.1.4                       purrr_1.0.2                       readr_2.1.5
[49] tidyr_1.3.1                       tibble_3.2.1                      tidyverse_2.0.0                   ggplot2_3.5.1
[53] ComplexHeatmap_2.18.0             data.table_1.17.0
```

---

## Required Data

For supporting data from public datasets and publications, please refer to the **Methods** and **Data Availability** sections of the associated manuscript.

---

## Final Directory Structure

```
.
├── data
│   └── Sample
│       └── POD5
└── output
    └── Sample
        ├── clair3
        ├── clairs_to
        ├── coverage
        ├── Me
        ├── QC
        ├── savana
        ├── severus
        └── SV
```

---

## Running the Pipeline

Steps to generate the processed data required for downstream plotting:

1. Acquire all raw and supporting data needed.
2. Run [`0_master.pbs`](.) to trigger all relevant PBS jobs.
3. For **global breakpoint–methylation comparison**, run `0_master` from the `meth_sv` folder.
4. For **CUT&RUN**, run the scripts under `cut_and_run`.
5. For **HRDetect**, run [`HRDetect_lr.Rmd`](https://github.com/molonc-lab/MeBRCA1_instability/blob/main/HRDetect/HRDetect_lr.Rmd) (in the `HRDetect` folder) **after** the main nanopore scripts have completed.

