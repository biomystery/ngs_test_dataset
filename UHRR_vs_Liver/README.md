```shell
# download R1
awk -v FS=',' '(NR>1){print $2}' SampleSheet.csv |while read l; do echo $l; wget $l;done 
# download R2 
awk -v FS=',' '(NR>1){print $2}' SampleSheet.csv |while read l; do echo $l; wget ${l/R1/R2};done 

# install seqtk
conda install -c bioconda seqtk

# random sample 
awk -v FS=',' '(NR>1){var=$2;idx = split(var, parts, "/");print "seqtk sample -s100 "parts[idx]" 100000 |gzip -nc>"$1"_R1.fastq.gz"}' SampleSheet.csv |bash 

awk -v FS=',' '(NR>1){var=$2;idx = split(var, parts, "/");print "seqtk sample -s100 "parts[idx]" 100000 |gzip -nc>"$1"_R1.fastq.gz"}' SampleSheet.csv | sed 's/_R1/_R2/g' |bash 

seqtk sample -s100 mRNA-UHRR-1_S9_L001_R2_001.fastq.gz 10|gzip -nc > tmp.gz
```


https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver1_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver1_R2.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver2_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver2_R2.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver3_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/Liver3_R2.fastq.gz

https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR1_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR1_R2.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR2_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR2_R2.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR3_R1.fastq.gz
https://raw.githubusercontent.com/biomystery/ngs_test_dataset/master/UHRR_vs_Liver/UHRR3_R2.fastq.gz
