# lab-notebook
gen711 lab notebook

Friday April 21
conda activate genomics
# going into genomics

git clone "repository link"
# puts the repository in as a directory

cp /tmp/gen711_project_data/fastp-single.sh ~/fastp-single.sh

chmod +x ~/fastp-single.sh

./fastp-single.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-2 trimmed_fastqs
./fastp-single.sh 150 /tmp/gen711_project_data/FMT_3/fmt-tutorial-demux-1 trimmed_fastqs

~/fastp.sh <1.poly-g length> <1.path to fastq directory>  <3.path to your output directory>
