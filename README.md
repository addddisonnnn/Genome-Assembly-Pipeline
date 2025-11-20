# Genome Assembly Project & Pipeline
Through this Genome Assembly Project, a pipeline was created to assemble a bacterial genome and assess and analyze the result of this assembly.

Here lies the result of establishing a nextflow pipeline capable of assembling the genome of a bacteria as well as analyzing the consequences and output of said assembly.

## Methods

The bacterial genome of Alteromonas mecleodii was assembled through a pipeline and analyzed.

This pipeline started off with getting the reads and quality control. Long and short reads were acquired and initial quality control was performed using FastQC v0.12.1 (on default parameters) [1] was run on the short reads. Filtlong v0.3.0 (minimum length at 500 and 90% kept) [2] was run on the long reads for quality control. Flye v2.9.6 (on parameters set to correct nanopore reads) [3] was run on the filtered long reads for assembly.

After assembly, create an index of the assembly, align the short reads to the assembly, and sort and index the alignments with Bowtie2 v2.5.4 [4] and samtools v1.22.1 (on default parameters) [5]. Using the alignments, short-read polish with Pilon v1.24 (with default parameters) [6].

Annotate the polished assembly with Prokka v1.14.6 (on default parameters) [7]. Run BUSCO v6.0.0 (set to the alteromonas_odb12 lineage) [8] on the polished assembly to evaluate completeness. After downloading the canoical reference genome from NCBI RefSeq assembly (GCF_000172635.2) with NCBI-datasets-cli tool v18.6.0 (on default parameters) [9], run QUAST v5.3.0 (on default parameters) [10] twice comparing the final assembly with the reference genome as well as the unpolished assembly.

## References

1. Andrews, S. (2010). FastQC: A Quality Control Tool for High Throughput Sequence Data [Online]. Available online at: http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
2. Wick, R. (2017). Filtlong (Version 0.3.0) [Computer software]. GitHub. https://github.com/rrwick/Filtlong.
3. Kolmogorov, M., Yuan, J., Lin, Y., & Pevzner, P. A. (2019). Assembly of long, error-prone reads using repeat graphs. Nature Biotechnology, 37(5), 540–546. doi:10.1038/s41587-019-0072-8
4. Langmead, B., & Salzberg, S. L. (2012). Fast gapped-read alignment with Bowtie 2. Nature methods, 9(4), 357–359. https://doi.org/10.1038/nmeth.1923
5. Danecek, P., Bonfield, J. K., Liddle, J., Marshall, J., Ohan, V., Pollard, M. O., Whitwham, A., Keane, T., McCarthy, S. A., Davies, R. M., & Li, H. (2021). Twelve years of SAMtools and BCFtools. GigaScience, 10(2), giab008. https://doi.org/10.1093/gigascience/giab008
6. Walker BJ, Abeel T, Shea T, Priest M, Abouelliel A, Sakthikumar S, et al. (2014) Pilon: An Integrated Tool for Comprehensive Microbial Variant Detection and Genome Assembly Improvement. PLoS ONE 9(11): e112963. https://doi.org/10.1371/journal.pone.0112963
7. Seemann T. (2014). Prokka: rapid prokaryotic genome annotation. Bioinformatics (Oxford, England), 30(14), 2068–2069. https://doi.org/10.1093/bioinformatics/btu153
8. Seppey, M., Manni, M., & Zdobnov, E. M. (2019). BUSCO: Assessing Genome Assembly and Annotation Completeness. Methods in molecular biology (Clifton, N.J.), 1962, 227–245. https://doi.org/10.1007/978-1-4939-9173-0_14
9. O’Leary, N. A., Cox, E., Holmes, J. B., Anderson, W. R., Falk, R., Hem, V., Tsuchiya, M. T. N., Schuler, G. D., Zhang, X., Torcivia, J., Ketter, A., Breen, L., Cothran, J., Bajwa, H., Tinne, J., Meric, P. A., Hlavina, W., & Schneider, V. A. (2024). Exploring and retrieving sequence and metadata for species across the tree of life with NCBI Datasets. Scientific Data, 11(1), 732. https://doi.org/10.1038/s41597-024-03571-y
10. Gurevich, A., Saveliev, V., Vyahhi, N., & Tesler, G. (2013). QUAST: quality assessment tool for genome assemblies. Bioinformatics (Oxford, England), 29(8), 1072–1075. https://doi.org/10.1093/bioinformatics/btt086
