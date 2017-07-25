# NanoPlot
Plotting tool for Oxford Nanopore sequencing data and alignments.  
In addition to various plots also a NanoStats file is created summarizing key features of the dataset.

![Example plot](https://github.com/wdecoster/NanoPlot/blob/master/examples/scaled_Log_Downsampled_LengthvsQualityScatterPlot_kde.png)

The example plot above shows a bivariate plot comparing log transformed read length with average basecall Phred quality score. More examples can be found in the [gallery on my blog 'Gigabase Or Gigabyte'.](https://gigabaseorgigabyte.wordpress.com/2017/06/01/example-gallery-of-nanoplot/)

This script performs data extraction from Oxford Nanopore sequencing data in the following formats:
- fastq files  
(can be bgzip, bzip2 or gzip compressed)  
- fastq files generated by albacore or MinKNOW containing additional information  
(can be bgzip, bzip2 or gzip compressed)  
- sorted bam files  
- sequencing_summary.txt output table generated by albacore

### Installation

`pip install NanoPlot`  

Upgrade to a newer version using:  
`pip install NanoPlot --upgrade`

The script is written for python3 but also seems to work for python2.7.

### USAGE:
```

NanoPlot [-h] [-v] [-t THREADS] [--maxlength MAXLENGTH]
        [--drop_outliers] [--downsample DOWNSAMPLE] [--loglength]
        [--alength] [-o OUTDIR] [-p PREFIX]
        (--fastq FASTQ | --fastq_rich FASTQ_RICH | --summary SUMMARY | --bam BAM)


Required input argument is (exact) one of these:
    --fastq FASTQ           Data presented is in fastq format exported from fast5
                            files by e.g. poretools.
    --fastq_rich FASTQ_rich Data presented is in fastq format generated by
                            Albacore or MinKNOW with additional information concerning
                            channel and time.
    --bam BAM               Data presented as a sorted bam file.
    --summary SUMMARY       Data is a summary file generated by albacore.
Each of these options can take one or multiple files e.g.
--summary summary1.txt summary2.txt summary3.txt
--bam bam1.txt bam2.txt


Arguments for optional filtering:
    --readtype              Specify read type to extract from summary file
                            Options: 1D (default), 2D
    --maxlength MAXLENGTH   Drop reads longer than length N.
    --downsample DOWNSAMPLE Reduce dataset to N reads by random sampling.
    --drop_outliers         Drop outlier reads with extreme long length.
    --loglength             Logarithmic scaling of lengths in plots.
    --alength               Use aligned read lengths rather than sequenced length (bam mode).


Optional output arguments:
    -o, --outdir OUTDIR     Specify directory in which output has to be created.
    -p, --prefix PREFIX     Specify a prefix to be used for the output files.
    -c, --color COLOR       Specify a color for the plots
                            must be a valid matplotlib color (see color_options.txt)
                            default: green
    -f, --format FORMAT     Specify the output format for the plots,
                            options are: eps, jpg, pdf, png, ps, svg
                            default: png
    --plots PLOTS           Specify which type of bivariate plots have to be made
                            options are: hex, kde, dot (multiple can be specified together)
                            default: all


General arguments:
    -h, --help              show this help message and exit
    -v, --version           Print version and exit.
    -t, --threads THREADS   Max number of threads to be used by the script
```






## Companion scripts
- [NanoFilt](https://github.com/wdecoster/nanofilt): filtering and trimming of reads
- [NanoStat](https://github.com/wdecoster/nanostat): statistic summary report of reads or alignments
