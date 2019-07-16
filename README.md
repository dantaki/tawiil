# tawiil
Calculate Read Length from a BAM file
--------------------------------------

## Usage

```
  O                                         o                                              
  O                                         o
ooOooo                          .     .     o
  O                                         o
  o      .oOoO     o     O      O     O     o 
  O      O   o     O  o  o      o     o     O 
  o      o   O     o  O  O      O     O     o 
  `oO    `OoO'o    `Oo'oO'      o     o     O'

            calculate read length
----------------------------------------------
Version:    0.0.1
Author:     Danny Antaki <dantaki at ucsd dot edu>

About:      Calculate read length from a BAM file
Usage:      tawiil [-h] <-i BAM> [options]

Required arguments:
    -i    FILE        bam file

Options:
    -n    INT         number of reads to process per scaffold [1000000]
    -r    STR         scaffolds, comma separated [1..22,X,Y]
    -p    INT         starting position on scaffold for analysis [5000000]
    -o    FILE        output file [bam-file_tawiil_read_length.txt]

    -h                print this message and exit

```

## Installation

Download the `tawiil` file and make it executable

`chmod +x tawiil` 

### Requirements

* python 3+
* pysam

* BAM file with `.bai` index

------------------

## Notes

Reads skipped if they have one of the following characteristics

* flagged as a duplicate
* flagged as a QC fail
* is unmapped
* mate is unmapped
* Mapping quality is 0
* is NOT in proper pair

tawiil analyzes read lengths from the 5Mb position of the chromosome, this is to avoid analyzing reads with problematic mappings to repetitive sequence or near assymbly gaps 

tawiil only considers the first 1,000,000 reads on each scaffold by default 

