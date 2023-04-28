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

~/fastp.sh <1.poly-g length> <1.path to fastq directory>  <3.path to your output directory>   --type "SampleData[PairedEndSequencesWithQuality]"  \
   --input-format CasavaOneEightSingleLanePerSampleDirFmt \
   --input-path <path to your output directory of trimmed fastqs> \
   --output-path <path to an output directory>/<a name for the output files>

April 28
qiime tools import --type "SampleData[SequencesWithQuality]" --input- format CasavaOneEightSingleLanePerSampleDirFmt --input-path trimmed_fastqs --output-path combined_fastqs

qiime cutadapt trim-single --i-demultiplexed-sequences combined_fastqs.qza --p-front TACGTATGGTGCA --p-discard-untrimmed --p-match-adapter-wildcards --verbose --o-trimmed-sequences with_primer

qiime demux summarize --i-data with_primer.qza --o-visualization third_folder

qiime dada2 denoise-single --i-demultiplexed-seqs combined_fastqs.qza --p-trunc-len 150 --p-trim-left 13 --p-n-threads 4 --o-denoising-stats denoising-stats.qza --o-table feature_table.qza --o-representative-sequences rep-seqs.qza

qiime metadata tabulate --m-input-file denoising-stats.qza --o-visualization denoising-stats.qzv

qiime feature-table tabulate-seqs --i-data rep-seqs.qza --o-visualization rep-seqs.qzv

qiime feature-table merge-seqs --i-data taxonomy/rep-seqs.qza
# this didn't work since we have both sets in the same folder we are following the commands for the other dataset

git hub
cp file poop_project
