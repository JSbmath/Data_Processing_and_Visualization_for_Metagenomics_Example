All sequences were downloaded from NCBI. Upon downloading, it was noticed that there were single-end read sequences (e.g., ERR210598.fastq.gz), paired-end read sequences (e.g., SRR5383391_1.fastq.gz and SRR5383391_2.fastq.gz), and sequences with both.
Therefore, it was decided to remove the single-end part in the sequences where both were found, in order to reduce space.
In this context:

Single-end reads refer to sequencing reads obtained from only one end of the DNA fragments.
Paired-end reads refer to sequencing reads obtained from both ends of the DNA fragments, resulting in two files (usually denoted with _1 and _2).

The decision to remove the single-end reads from sequences that contained both single-end and paired-end reads was made to save storage space, as the paired-end reads provide more information and are generally preferred for analysis.

For this purpose, three programs created in Bash were used:

* separador.sh
* salvar_lista.sh
* checar_no_guion.sh

The separador.sh script separates files into two folders: archivos_guion for files with "_1" or "_2" before the extension, and archivos_no_guion for the remaining files.
The salvar_lista.sh script creates a list of unique file names without extensions and "_1" or "_2" endings from the files in the archivos_guion folder and saves them in lista.txt.

The checar_no_guion.sh script checks the files in the archivos_no_guion folder against the list in lista.txt. If a file name is not found in the list, it is moved to the archivos_guion folder.

These scripts work together to separate and organize the sequence files based on their naming conventions, ensuring that paired-end read files are grouped together in the archivos_guion folder, while single-end read files are placed in the archivos_no_guion folder. The lista.txt file keeps track of the unique file names for reference.