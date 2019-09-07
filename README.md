# Ubuntu Basic Commands for Biologist

## What is Ubuntu?

Ubuntu is a free complete Linux operating system, which is available with professional  and community support. The Ubuntu community is built on the ideas “that software should be available free of charge, that software tools should be usable by people in their local language and despite any disabilities, and that people should have the freedom to customize and alter their software in whatever way they see fit”. 
---


### Ubuntu Graphical User Interface Overview
<img src="images/ubuntu.jpg"

---


## Interacting with Linux via terminal window

* In Linux machine user can communicate via commands which is  typed  in the terminal window
The commands are interpreted by a program referred to as shell which is  an interface between Linux and the user. We will be using the shell called bash during this whole exercise.

* Typically, each command is typed in one line and executed by hitting the Enter key on the keyboard.

A commands deal with operation on files ( i.e. creating, editing, copying, writing) and execution of processes, its status monitoring or termination of executed process e.g.,
Request information (e.g., list user’s files- ls command)
Launch a simple task (e.g., rename a file-mv command)
Start an application (e.g., Firefox web browser, BWA aligner, IGV viewer, ...)
Stop an application



How to open terminal in Linux

    1. Use the ‘Dashboard’ search tool (the little magnifying glass in the top left of the menu bar) to find, and then launch, Ubuntu Terminal application:




You should now see something that looks like the following (any text that appears inside your terminal window will look different):





Your first Linux command

#To see the current location of your working directory, we need to use the “pwd” command.

• Command: $ pwd
• Output:   home/ajay



#To see what files are in our home directory, we need to use the “ls” command.

•  Command :$ ls  
•  Output:
		Application 
		Shortcuts  
		Documents   
		Library  
		Desktop                 
		Downloads  
		

#Changing location of file in Linux system

We are in the home directory on the computer but we want to to work on a folder present in the Desktop of your computer. To change directories in Linux, we use the “cd” command:

•  $ cd  /home/ajay/Desktop/Learn_linux ( This command will take you to the desire location where you want to work)

• $ ls
	Applications    
	Code        
	Data        
	Documentation  
	
	
$ pwd
home/ajay/Learn_linux

    • Move upward in the Linux file system

Frequently, you will find that you want to go ‘upwards’ one level in the directory hierarchy. Two dots “ ..”are used in Linux to refer to the parent directory of wherever you are. 

$ cd  /home/ajay/Learn_linux ( This command will take you to the desire location where you want to work)

$ ls
Applications    
Code           
Documentation  
$ pwd
home/ajay/Desktop/Learn_linux
$ cd ..
$ pwd
/home/ajay/Desktop
If you wanted to navigate up two levels in the file system in one go? It’s very simple, just use two sets of the ..operator, separated by a forward slash:
$ cd  /home/ajay/Desktop/Learn_linux
$ pwd
/home/ajay/Desktop/Learn_linux $ cd ../..  
$ pwd
/ajay 
    • Creating new folder 
If we want to make a new directory (e.g. to store some work related data), we can use the
mkdir command:
$ mkdir Data
$ ls

Applications    
Code        
Data        
Documentation  
$ cd  Data
$ pwd
//home/ajay/Desktop/Learn_linux/Data
    • Creating a new file
The Unix command “touch” will let us create a new, empty file. 
$ touch genes.txt  
$ touch genes.fasta
$ ls
genes.txt   genes.fasta
    • Moving files from location to another location
Now, let’s assume that we want to  these files move  (genes.txt and genes.fasta) to a new directory (‘Temp’). We will do this using the Linux “mv” (move) command:
$ mkdir Temp  
$ mv genes.txt Temp/  
$ mv genes.fasta Temp/  
$ ls
Temp genes.txt genes.fasta
$ ls Temp/  
genes.txt genes.fasta 
For the mv command, we always have to specify a source file (or directory) that we want to move, and then specify a target location. 
If we had wanted to we could have moved both files in one go by typing any of the following commands:
$ mv *.txt Temp/  
$ mv *t Temp/  
$ mv *ea* Temp/

    • Renaming of files 
Now, let’s assume that you want to rename file name genes.txt to genome.fasta, for this command “mv” used.
$ pwd
/home/ajay/Desktop/Learn_linux/Data/Temp
$ ls Temp/  
genes.txt genes.fasta 
$mv genes.txt genome.fasta
$ls 
genome.fasta genes.fasta

Source and target are important concepts for Linux commands, in the earlier example, the destination for the mv command was a directory name (Temp) and later a file (genes.txt).

 So we moved a file from its source location to a target location and rename a file. The single mv command can be used to moving a file from one location to another and changing the file name at the same time.

E.g. let’s make a new file and move it whilst renaming it at the same time:

$ touch dna.fasta  
$ ls
Temp  dna.fasta
$ mv dna.fasta Temp/mydna.fasta

$ ls Temp/  
dna.fasta genome.fasta genes.fasta 


    • Deleting directory or file in Linux (The most dangerous Linux command)

For removing a directory command “rmdir” is used 

$ mkdir ecoli
$ ls
Temp ecoli
$ rm ecoli
$ ls
Temp

But rmdir won’t remove directories if they contain any files.

$ mkdir ecoli
$cd ecoli
$ touch file1
$ ls
file1
$cd ../
$ rmdir ecoli/
rmdir: failed to remove ‘ecoli/’: Directory not empty


to delete this file we have to first remove the files we have created in (/home/ajay/Desktop/Learn_linux/Data/Temp/ecoli)? 

In order to do this, we will have to use the rm (remove) command.

Misuse of the rm command can lead to destruction or needless death of your computer system which is irrepaiiable.

If you delete something with rm, you will not get it back! It does not go into the trash or recycle can, it is permanently removed. It is possible a user with root permission can unknowingly delete everything in their home directory (all directories and subdirectories) with rm,  which leads to operating system death.  Hence this particular command will be used with high precaution.

$ pwd
/home/ajay/Desktop/Learn_linux/Data/Temp/
$ Temp ecoli
$ cd Temp
$ls 
dna.fasta genome.fasta genes.fasta 
$ rm -i dna.fasta
remove dna.fasta? y
$ rm -i genome.fasta  
remove heaven.txt? y

We could have simplified this step by using a wild-card (e.g. rm -i *.fasta), this will remove all file with .fasta extension in one go and saves time

    • View  contents of a file

So far we have covered listing the contents of directories and moving/copying/deleting either files and/or directories. Now we will cover how you can look in to  files and see its content for this “less” (view content of file but no edit) command is used.

Let’s take a look at a file of Arabidopsis thaliana protein sequences:

$ less Data/Arabidopsis/At_proteins.fasta

>ATCG00500.1 pacid=19637947 transcript=ATCG00500.1 locus=ATCG00500 ID=ATCG00500.1.TAIR10 annot-version=TAIR10
MEKSWFNFMFSKGELEYRGELSKAMDSFAPGEKTTISQDRFIYDMDKNFYGWDERSSYSSSYSNNVDLLVSSKDIRNFIS
DDTFFVRDSNKNSYSIFFDKKKKIFEIDNDFSDLEKFFYSYCSSSYLNNRSKGDNDLHYDPYIKDTKYNCTNHINSCIDS
YFRSYICIDNNFLIDSNNFNESYIYNFICSESGKIRESKNYKIRTNRNRSNLISSKDFDITQNYNQLWIQCDNCYGLMYK
KVKMNVCEQCGHYLKMSSSERIELSIDPGTWNPMDEDMVSADPIKFHSKEEPYKNRIDSAQKTTGLTDAVQTGTGQLNGI
PVALGVMDFRFMGGSMGSVVGEKITRLIEYATNQCLPLILVCSSGGARMQEGSLSLMQMAKISSVLCDYQSSKKLFYISI
LTSPTTGGVTASFGMLGDIIIAEPYAYIAFAGKRVIEQTLKKAVPEGSQAAESLLRKGLLDAIVPRNLLKGVLSELFQLH
AFFPLNTN*
>ATCG00510.1 pacid=19637948 transcript=ATCG00510.1 locus=ATCG00510 ID=ATCG00510.1.TAIR10 annot-version=TAIR10
MTTFNNLPSIFVPLVGLVFPAIAMASLFLHIQKNKIF*
>ATCG00280.1 pacid=19637949 transcript=ATCG00280.1 locus=ATCG00280 ID=ATCG00280.1.TAIR10 annot-version=TAIR10
MKTLYSLRRFYHVETLFNGTLALAGRDQETTGFAWWAGNARLINLSGKLLGAHVAHAGLIVFWAGAMNLFEVAHFVPEKP
MYEQGLILLPHLATLGWGVGPGGEVIDTFPYFVSGVLHLISSAVLGFGGIYHALLGPETLEESFPFFGYVWKDRNKMTTI
LGIHLILLGVGAFLLVFKALYFGGVYDTWAPGGGDVRKITNLTLSPSVIFGYLLKSPFGGEGWIVSVDDLEDIIGGHVWL
GSICIFGGIWHILTKPFAWARRALVWSGEAYLSYSLAALSVCGFIACCFVWFNNTAYPSEFYGPTGPEASQAQAFTFLVR
DQRLGANVGSAQGPTGLGKYLMRSPTGEVIFGGETMRFWDLRAPWLEPLRGPNGLDLSRLKKDIQPWQERRSAEYMTHAP
LGSLNSVGGVATEINAVNYVSPRSWLSTSHFVLGFFLFVGHLWHAGRARAAAAGFEKGIDRDFEPVLSMTPLN*
>ATCG00890.1 pacid=19637950 transcript=ATCG00890.1 locus=ATCG00890 ID=ATCG00890.1.TAIR10 annot-version=TAIR10
MAITEFLLFILTATLGGMFLCGANDLITIFVAPECFSLCSYLLSGYTKKDIRSNEATMKYLLMGGASSSILVHGFSWLYG
Athaliana_167_TAIR10.protein.fa


When you are using less, you can bring up a page of help commands by pressing h, scroll forward a page by pressing space, or go forward or backwards one line at a time by pressing j or k. To exit less, press q (for quit). The less program also does about a million other useful things (including text searching).

To exit from this command press “Esc” key on the keyboard


    • Edit files using CMD and GUI text editor

You can used command base text editor to edit a file in the linux, the best and widely used command prompt based text editor is vi or vim text editor default in Linux operating system.

It little difficult to learn the editor command hence now these days many graphical user interpose (GUI) text editor (Gedit, Geany) is present which is very hand and does not required and command to remember it’s just like your familiar “notepad” text editor widely used by windows user.

But the GUI text editor is higly powerful as compare to notepad as they are capable of opening huge fastq file which are generally of heavy file size in GB.


    • Vies contents of a very large file Heads and tails

You can view contents of a verly large file (.fastq) via head and tail command, here the head command display the content start from beginning of file. Command tail display the content at the end of file.

$ head Athaliana_167_TAIR10.protein.fa 
>ATCG00500.1 pacid=19637947 transcript=ATCG00500.1 locus=ATCG00500 ID=ATCG00500.1.TAIR10 annot-version=TAIR10
MEKSWFNFMFSKGELEYRGELSKAMDSFAPGEKTTISQDRFIYDMDKNFYGWDERSSYSSSYSNNVDLLVSSKDIRNFIS
DDTFFVRDSNKNSYSIFFDKKKKIFEIDNDFSDLEKFFYSYCSSSYLNNRSKGDNDLHYDPYIKDTKYNCTNHINSCIDS
YFRSYICIDNNFLIDSNNFNESYIYNFICSESGKIRESKNYKIRTNRNRSNLISSKDFDITQNYNQLWIQCDNCYGLMYK
KVKMNVCEQCGHYLKMSSSERIELSIDPGTWNPMDEDMVSADPIKFHSKEEPYKNRIDSAQKTTGLTDAVQTGTGQLNGI
PVALGVMDFRFMGGSMGSVVGEKITRLIEYATNQCLPLILVCSSGGARMQEGSLSLMQMAKISSVLCDYQSSKKLFYISI
LTSPTTGGVTASFGMLGDIIIAEPYAYIAFAGKRVIEQTLKKAVPEGSQAAESLLRKGLLDAIVPRNLLKGVLSELFQLH
AFFPLNTN*
>ATCG00510.1 pacid=19637948 transcript=ATCG00510.1 locus=ATCG00510 ID=ATCG00510.1.TAIR10 annot-version=TAIR10
MTTFNNLPSIFVPLVGLVFPAIAMASLFLHIQKNKIF*

$ tail Athaliana_167_TAIR10.protein.fa 
HNHEGEDEREKKLDDGVVTWFWVKNESNARVSYKEVVVKNGAETLAAIQAMNVNDYDLWITGRREGINPKILEGLSTWSE
DHQLGVIGDTVAGSVFASEGSVLVVQQQVRNQMGGDGFLNGKFDYKKLVSPWSHSHN*
>AT5G46874.1 pacid=19673331 transcript=AT5G46874.1 locus=AT5G46874 ID=AT5G46874.1.TAIR10 annot-version=TAIR10
MKILAFFIFVLLIFSCSSSMIMGVHYHEYRCHDWVDCAIWCKQWVPQPKCINRVCDCKPKSLPTNEEVPQSAYSSNSNY*
>AT5G47240.1 pacid=19673332 transcript=AT5G47240.1 locus=AT5G47240 ID=AT5G47240.1.TAIR10 annot-version=TAIR10
MDSVSLSEVTVIKGTTHLGFMHSFRQPFCGVKISPKFYLSKVDGPKAISSSSNTKSQFVYGGGSIAATSDSGYKMNGVNL
KSRTLMSSAVKERSLLDAYDDEYGGVIVDHGKLPSNPYAFASMLRASLSDWRRKGKKGVWLKLPVEQSELVPIAIKEGFE
YHHAEKGYVMLTYWIPEEEPSMLPANASHQVGVGGFVLNQHKEVLVVQEKYCAPSITGLWKLPTGFINESEEIFSGAVRE
VKEETGVDTEFSEVIAFRHAHNVAFEKSDLFFICMLRPLSDKIIIDALEIKAAKWMPLAEFVEQPMIRGDKMFKRVIEIC
EARLSHRYCGLSPHRLVSTFDGKPSSLYYNVVDDDHDPSHSNCSTEFYR*


    • Change content of file in upper of lower cases in one go.

$ head -n 2 chr1.fasta

>Chr1 dumped from ADB: Mar/14/08 12:28; last updated: 2007-12-20  
CCCTAAACCCTAAACCCTAAACCCTAAACCTCTGAATCCTTAATCCCTAAATCCCTAAATCTTTAAATCCTACATCCAT

We have seen that these sequence files contain upper-case characters. What if we wanted to turn them into lower-case characters (required by another bioinformatics program will only work if they are lower-case)?

 The Linux  command “tr” will be used  (short for transliterate) does just this, it takes one range of characters that you specify and changes them into another range of characters:

$ head -n 2 chr1.fasta

>Chr1 dumped from ADB: Mar/14/08 12:28; last updated: 2007-12-20  
CCCTAAACCCTAAACCCTAAACCCTAAACCTCTGAATCCTTAATCCCTAAATCCCTAAATCTTTAAATCCTACATCCAT

$ head chr1.fasta | tr 'A-Z' 'a-z' 
>chr1 dumped from adb: mar/14/08 12:28; last updated: 2007-12-20  
Ccctaaaccctaaaccctaaaccctaaacctctgaatccttaatccctaaatccctaaatctttaaatcctacatccat


    • .Download file from internet using command

File transfer: from the web to Linux

Use “wget” command on the workstation (if you know the URL of the file)
•
Example 1: simple URL
wget ftp://ftp.ncbi.nih.gov/blast/matrices/BLOSUM100
(will download the file BLOSUM100 from the NCBI FTP site and deposit it in the current directory under the name BLOSUM100)

--2017-11-27 12:50:03--  ftp://ftp.ncbi.nih.gov/blast/matrices/BLOSUM100
           => ‘BLOSUM100’
Resolving ftp.ncbi.nih.gov (ftp.ncbi.nih.gov)... 130.14.250.12, 2607:f220:41e:250::7
Connecting to ftp.ncbi.nih.gov (ftp.ncbi.nih.gov)|130.14.250.12|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /blast/matrices ... done.
==> SIZE BLOSUM100 ... 2174
==> PASV ... done.    ==> RETR BLOSUM100 ... done.
Length: 2174 (2.1K) (unauthoritative)

100%[===================================================================================================================================================================>] 2,174       --.-K/s   in 0s      

2017-11-27 12:50:07 (127 MB/s) - ‘BLOSUM100’ saved [2174]


Downloading can be best done using graphical GUI  The SSH File Transfer Protocol (SFTP) client software which can offer several function of pausing, resuming or multiple file download in one go.

Some SFTP clients for Ubuntu:
        ◦ FileZilla, fireftp,  Kasablanca,



Installation of software using terminal


    • How to Install BLAST+ version 2.6.0 (Step-by-Step) Ubuntu/Fedora/CentOS

*Step 1: Create a new directory name ncbi-blast+

$ mkdir ncbi-blast+

*Step 2: Enter in to created directory

$ cd ncbi-blast+

#For Fedora/ CentOS/ Ubuntu operating system


*Step 3: Download the software from NCBI-FTP site

$ wget -N ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.6.0/ncbi-blast-2.6.0+-1.x86_64.rpm

*Step 4: To Install (Fedora/ CentOS operating system)

$ sudo yum install ncbi-blast-2.6.0+-1.x86_64.rpm -nogpgcheck

 To Install ( Ubuntu operating system)

$ sudo alien -i ncbi-blast-2.6.0+-1.x86_64.rpm 

*Step 5:  To check for successful installation

$ blastn -h

Output: USAGE
blastn [-h] [-help] [-import_search_strategy filename]
[-export_search_strategy filename] [-task task_name] [-db database_name]
[-dbsize num_letters] [-gilist filename] [-seqidlist filename]
[-negative_gilist filename] [-entrez_query entrez_query]
[-db_soft_mask filtering_algorithm] [-db_hard_mask filtering_algorithm]
[-subject subject_input_file] [-subject_loc range] [-query input_file]
[-out output_file] [-evalue evalue] [-word_size int_value]
[-gapopen open_penalty] [-gapextend extend_penalty]
[-perc_identity float_value] [-qcov_hsp_perc float_value]
[-max_hsps int_value] [-xdrop_ungap float_value] [-xdrop_gap float_value]
[-xdrop_gap_final float_value] [-searchsp int_value]
[-sum_stats bool_value] [-penalty penalty] [-reward reward] [-no_greedy]
[-min_raw_gapped_score int_value] [-template_type type]
[-template_length int_value] [-dust DUST_options]
[-filtering_db filtering_database]
[-window_masker_taxid window_masker_taxid]
[-window_masker_db window_masker_db] [-soft_masking soft_masking]
[-ungapped] [-culling_limit int_value] [-best_hit_overhang float_value]
[-best_hit_score_edge float_value] [-window_size int_value]
[-off_diagonal_range int_value] [-use_index boolean] [-index_name string]
[-lcase_masking] [-query_loc range] [-strand strand] [-parse_deflines]
[-outfmt format] [-show_gis] [-num_descriptions int_value]
[-num_alignments int_value] [-line_length line_length] [-html]
[-max_target_seqs num_sequences] [-num_threads int_value] [-remote]
[-version]

**NCBI-BLAST+ version 2.6.0   is successfully installed on your system, now you can perform sequence similarity search locally with your customized database and queries.

    • Running applications example: local BLAST search

Prepare input

Create your local scratch directory (if not yet done) and a sub-directory blast_test
where this exercise will be run
$mkdir blast_test
$cd blast_test

Copy file with query sequences to the exercise directory:
cp /shared_data/Linux_workshop/seq_tst.fa 
.
Copy Swissprot BLAST database (we’ll make a separate directory for it)
mkdir databases
cp /shared_data/Linux_workshop/databases/swissprot* ./databases

 Verify that the files have been copied (use ls command)
Running applications example: BLAST
run the program

Very general syntax for launching applications:
In our specific case:
blastall -p blastx -b 1 -d ./databases/swissprot -i seq_tst.fa >& run.log

 Options used:
-p: type of search (blastx: compare 6-frame translations of DNA to AA sequences)
-b: number of database sequences to show alignments for
-d: path to database files
-i: input file (with query sequences in fasta format)
 For full set of options, run
blastall | more

 Documents   
Library  
Desktop                 
Downloads  

    • Changing location of file in Linux system
We are in the home directory on the computer but we want to to work on a folder present in the Desktop of your computer. To change directories in Linux, we use the “cd” command:

$ cd  /home/ajay/Desktop/Learn_linux ( This command will take you to the desire location where you want to work)

$ ls
Applications    
Code        
Data        
Documentation  
$ pwd
home/ajay/Learn_linux

    • Move upward in the Linux file system

Frequently, you will find that you want to go ‘upwards’ one level in the directory hierarchy. Two dots “ ..”are used in Linux to refer to the parent directory of wherever you are. 

$ cd  /home/ajay/Learn_linux ( This command will take you to the desire location where you want to work)

$ ls
Applications    
Code           
Documentation  
$ pwd
home/ajay/Desktop/Learn_linux
$ cd ..
$ pwd
/home/ajay/Desktop
If you wanted to navigate up two levels in the file system in one go? It’s very simple, just use two sets of the ..operator, separated by a forward slash:
$ cd  /home/ajay/Desktop/Learn_linux
$ pwd
/home/ajay/Desktop/Learn_linux $ cd ../..  
$ pwd
/ajay 
    • Creating new folder 
If we want to make a new directory (e.g. to store some work related data), we can use the
mkdir command:
$ mkdir Data
$ ls

Applications    
Code        
Data        
Documentation  
$ cd  Data
$ pwd
//home/ajay/Desktop/Learn_linux/Data
    • Creating a new file
The Unix command “touch” will let us create a new, empty file. 
$ touch genes.txt  
$ touch genes.fasta
$ ls
genes.txt   genes.fasta
    • Moving files from location to another location
Now, let’s assume that we want to  these files move  (genes.txt and genes.fasta) to a new directory (‘Temp’). We will do this using the Linux “mv” (move) command:
$ mkdir Temp  
$ mv genes.txt Temp/  
$ mv genes.fasta Temp/  
$ ls
Temp genes.txt genes.fasta
$ ls Temp/  
genes.txt genes.fasta 
For the mv command, we always have to specify a source file (or directory) that we want to move, and then specify a target location. 
If we had wanted to we could have moved both files in one go by typing any of the following commands:
$ mv *.txt Temp/  
$ mv *t Temp/  
$ mv *ea* Temp/

    • Renaming of files 
Now, let’s assume that you want to rename file name genes.txt to genome.fasta, for this command “mv” used.
$ pwd
/home/ajay/Desktop/Learn_linux/Data/Temp
$ ls Temp/  
genes.txt genes.fasta 
$mv genes.txt genome.fasta
$ls 
genome.fasta genes.fasta

Source and target are important concepts for Linux commands, in the earlier example, the destination for the mv command was a directory name (Temp) and later a file (genes.txt).

 So we moved a file from its source location to a target location and rename a file. The single mv command can be used to moving a file from one location to another and changing the file name at the same time.

E.g. let’s make a new file and move it whilst renaming it at the same time:

$ touch dna.fasta  
$ ls
Temp  dna.fasta
$ mv dna.fasta Temp/mydna.fasta

$ ls Temp/  
dna.fasta genome.fasta genes.fasta 


    • Deleting directory or file in Linux (The most dangerous Linux command)

For removing a directory command “rmdir” is used 

$ mkdir ecoli
$ ls
Temp ecoli
$ rm ecoli
$ ls
Temp

But rmdir won’t remove directories if they contain any files.

$ mkdir ecoli
$cd ecoli
$ touch file1
$ ls
file1
$cd ../
$ rmdir ecoli/
rmdir: failed to remove ‘ecoli/’: Directory not empty


to delete this file we have to first remove the files we have created in (/home/ajay/Desktop/Learn_linux/Data/Temp/ecoli)? 

In order to do this, we will have to use the rm (remove) command.

Misuse of the rm command can lead to destruction or needless death of your computer system which is irrepaiiable.

If you delete something with rm, you will not get it back! It does not go into the trash or recycle can, it is permanently removed. It is possible a user with root permission can unknowingly delete everything in their home directory (all directories and subdirectories) with rm,  which leads to operating system death.  Hence this particular command will be used with high precaution.

$ pwd
/home/ajay/Desktop/Learn_linux/Data/Temp/
$ Temp ecoli
$ cd Temp
$ls 
dna.fasta genome.fasta genes.fasta 
$ rm -i dna.fasta
remove dna.fasta? y
$ rm -i genome.fasta  
remove heaven.txt? y

We could have simplified this step by using a wild-card (e.g. rm -i *.fasta), this will remove all file with .fasta extension in one go and saves time

    • View  contents of a file

So far we have covered listing the contents of directories and moving/copying/deleting either files and/or directories. Now we will cover how you can look in to  files and see its content for this “less” (view content of file but no edit) command is used.

Let’s take a look at a file of Arabidopsis thaliana protein sequences:

$ less Data/Arabidopsis/At_proteins.fasta

>ATCG00500.1 pacid=19637947 transcript=ATCG00500.1 locus=ATCG00500 ID=ATCG00500.1.TAIR10 annot-version=TAIR10
MEKSWFNFMFSKGELEYRGELSKAMDSFAPGEKTTISQDRFIYDMDKNFYGWDERSSYSSSYSNNVDLLVSSKDIRNFIS
DDTFFVRDSNKNSYSIFFDKKKKIFEIDNDFSDLEKFFYSYCSSSYLNNRSKGDNDLHYDPYIKDTKYNCTNHINSCIDS
YFRSYICIDNNFLIDSNNFNESYIYNFICSESGKIRESKNYKIRTNRNRSNLISSKDFDITQNYNQLWIQCDNCYGLMYK
KVKMNVCEQCGHYLKMSSSERIELSIDPGTWNPMDEDMVSADPIKFHSKEEPYKNRIDSAQKTTGLTDAVQTGTGQLNGI
PVALGVMDFRFMGGSMGSVVGEKITRLIEYATNQCLPLILVCSSGGARMQEGSLSLMQMAKISSVLCDYQSSKKLFYISI
LTSPTTGGVTASFGMLGDIIIAEPYAYIAFAGKRVIEQTLKKAVPEGSQAAESLLRKGLLDAIVPRNLLKGVLSELFQLH
AFFPLNTN*
>ATCG00510.1 pacid=19637948 transcript=ATCG00510.1 locus=ATCG00510 ID=ATCG00510.1.TAIR10 annot-version=TAIR10
MTTFNNLPSIFVPLVGLVFPAIAMASLFLHIQKNKIF*
>ATCG00280.1 pacid=19637949 transcript=ATCG00280.1 locus=ATCG00280 ID=ATCG00280.1.TAIR10 annot-version=TAIR10
MKTLYSLRRFYHVETLFNGTLALAGRDQETTGFAWWAGNARLINLSGKLLGAHVAHAGLIVFWAGAMNLFEVAHFVPEKP
MYEQGLILLPHLATLGWGVGPGGEVIDTFPYFVSGVLHLISSAVLGFGGIYHALLGPETLEESFPFFGYVWKDRNKMTTI
LGIHLILLGVGAFLLVFKALYFGGVYDTWAPGGGDVRKITNLTLSPSVIFGYLLKSPFGGEGWIVSVDDLEDIIGGHVWL
GSICIFGGIWHILTKPFAWARRALVWSGEAYLSYSLAALSVCGFIACCFVWFNNTAYPSEFYGPTGPEASQAQAFTFLVR
DQRLGANVGSAQGPTGLGKYLMRSPTGEVIFGGETMRFWDLRAPWLEPLRGPNGLDLSRLKKDIQPWQERRSAEYMTHAP
LGSLNSVGGVATEINAVNYVSPRSWLSTSHFVLGFFLFVGHLWHAGRARAAAAGFEKGIDRDFEPVLSMTPLN*
>ATCG00890.1 pacid=19637950 transcript=ATCG00890.1 locus=ATCG00890 ID=ATCG00890.1.TAIR10 annot-version=TAIR10
MAITEFLLFILTATLGGMFLCGANDLITIFVAPECFSLCSYLLSGYTKKDIRSNEATMKYLLMGGASSSILVHGFSWLYG
Athaliana_167_TAIR10.protein.fa


When you are using less, you can bring up a page of help commands by pressing h, scroll forward a page by pressing space, or go forward or backwards one line at a time by pressing j or k. To exit less, press q (for quit). The less program also does about a million other useful things (including text searching).

To exit from this command press “Esc” key on the keyboard


    • Edit files using CMD and GUI text editor

You can used command base text editor to edit a file in the linux, the best and widely used command prompt based text editor is vi or vim text editor default in Linux operating system.

It little difficult to learn the editor command hence now these days many graphical user interpose (GUI) text editor (Gedit, Geany) is present which is very hand and does not required and command to remember it’s just like your familiar “notepad” text editor widely used by windows user.

But the GUI text editor is higly powerful as compare to notepad as they are capable of opening huge fastq file which are generally of heavy file size in GB.


    • Vies contents of a very large file Heads and tails

You can view contents of a verly large file (.fastq) via head and tail command, here the head command display the content start from beginning of file. Command tail display the content at the end of file.

$ head Athaliana_167_TAIR10.protein.fa 
>ATCG00500.1 pacid=19637947 transcript=ATCG00500.1 locus=ATCG00500 ID=ATCG00500.1.TAIR10 annot-version=TAIR10
MEKSWFNFMFSKGELEYRGELSKAMDSFAPGEKTTISQDRFIYDMDKNFYGWDERSSYSSSYSNNVDLLVSSKDIRNFIS
DDTFFVRDSNKNSYSIFFDKKKKIFEIDNDFSDLEKFFYSYCSSSYLNNRSKGDNDLHYDPYIKDTKYNCTNHINSCIDS
YFRSYICIDNNFLIDSNNFNESYIYNFICSESGKIRESKNYKIRTNRNRSNLISSKDFDITQNYNQLWIQCDNCYGLMYK
KVKMNVCEQCGHYLKMSSSERIELSIDPGTWNPMDEDMVSADPIKFHSKEEPYKNRIDSAQKTTGLTDAVQTGTGQLNGI
PVALGVMDFRFMGGSMGSVVGEKITRLIEYATNQCLPLILVCSSGGARMQEGSLSLMQMAKISSVLCDYQSSKKLFYISI
LTSPTTGGVTASFGMLGDIIIAEPYAYIAFAGKRVIEQTLKKAVPEGSQAAESLLRKGLLDAIVPRNLLKGVLSELFQLH
AFFPLNTN*
>ATCG00510.1 pacid=19637948 transcript=ATCG00510.1 locus=ATCG00510 ID=ATCG00510.1.TAIR10 annot-version=TAIR10
MTTFNNLPSIFVPLVGLVFPAIAMASLFLHIQKNKIF*

$ tail Athaliana_167_TAIR10.protein.fa 
HNHEGEDEREKKLDDGVVTWFWVKNESNARVSYKEVVVKNGAETLAAIQAMNVNDYDLWITGRREGINPKILEGLSTWSE
DHQLGVIGDTVAGSVFASEGSVLVVQQQVRNQMGGDGFLNGKFDYKKLVSPWSHSHN*
>AT5G46874.1 pacid=19673331 transcript=AT5G46874.1 locus=AT5G46874 ID=AT5G46874.1.TAIR10 annot-version=TAIR10
MKILAFFIFVLLIFSCSSSMIMGVHYHEYRCHDWVDCAIWCKQWVPQPKCINRVCDCKPKSLPTNEEVPQSAYSSNSNY*
>AT5G47240.1 pacid=19673332 transcript=AT5G47240.1 locus=AT5G47240 ID=AT5G47240.1.TAIR10 annot-version=TAIR10
MDSVSLSEVTVIKGTTHLGFMHSFRQPFCGVKISPKFYLSKVDGPKAISSSSNTKSQFVYGGGSIAATSDSGYKMNGVNL
KSRTLMSSAVKERSLLDAYDDEYGGVIVDHGKLPSNPYAFASMLRASLSDWRRKGKKGVWLKLPVEQSELVPIAIKEGFE
YHHAEKGYVMLTYWIPEEEPSMLPANASHQVGVGGFVLNQHKEVLVVQEKYCAPSITGLWKLPTGFINESEEIFSGAVRE
VKEETGVDTEFSEVIAFRHAHNVAFEKSDLFFICMLRPLSDKIIIDALEIKAAKWMPLAEFVEQPMIRGDKMFKRVIEIC
EARLSHRYCGLSPHRLVSTFDGKPSSLYYNVVDDDHDPSHSNCSTEFYR*


    • Change content of file in upper of lower cases in one go.

$ head -n 2 chr1.fasta

>Chr1 dumped from ADB: Mar/14/08 12:28; last updated: 2007-12-20  
CCCTAAACCCTAAACCCTAAACCCTAAACCTCTGAATCCTTAATCCCTAAATCCCTAAATCTTTAAATCCTACATCCAT

We have seen that these sequence files contain upper-case characters. What if we wanted to turn them into lower-case characters (required by another bioinformatics program will only work if they are lower-case)?

 The Linux  command “tr” will be used  (short for transliterate) does just this, it takes one range of characters that you specify and changes them into another range of characters:

$ head -n 2 chr1.fasta

>Chr1 dumped from ADB: Mar/14/08 12:28; last updated: 2007-12-20  
CCCTAAACCCTAAACCCTAAACCCTAAACCTCTGAATCCTTAATCCCTAAATCCCTAAATCTTTAAATCCTACATCCAT

$ head chr1.fasta | tr 'A-Z' 'a-z' 
>chr1 dumped from adb: mar/14/08 12:28; last updated: 2007-12-20  
Ccctaaaccctaaaccctaaaccctaaacctctgaatccttaatccctaaatccctaaatctttaaatcctacatccat


    • .Download file from internet using command

File transfer: from the web to Linux

Use “wget” command on the workstation (if you know the URL of the file)
•
Example 1: simple URL
wget ftp://ftp.ncbi.nih.gov/blast/matrices/BLOSUM100
(will download the file BLOSUM100 from the NCBI FTP site and deposit it in the current directory under the name BLOSUM100)

--2017-11-27 12:50:03--  ftp://ftp.ncbi.nih.gov/blast/matrices/BLOSUM100
           => ‘BLOSUM100’
Resolving ftp.ncbi.nih.gov (ftp.ncbi.nih.gov)... 130.14.250.12, 2607:f220:41e:250::7
Connecting to ftp.ncbi.nih.gov (ftp.ncbi.nih.gov)|130.14.250.12|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /blast/matrices ... done.
==> SIZE BLOSUM100 ... 2174
==> PASV ... done.    ==> RETR BLOSUM100 ... done.
Length: 2174 (2.1K) (unauthoritative)

100%[===================================================================================================================================================================>] 2,174       --.-K/s   in 0s      

2017-11-27 12:50:07 (127 MB/s) - ‘BLOSUM100’ saved [2174]


Downloading can be best done using graphical GUI  The SSH File Transfer Protocol (SFTP) client software which can offer several function of pausing, resuming or multiple file download in one go.

Some SFTP clients for Ubuntu:
        ◦ FileZilla, fireftp,  Kasablanca,



Installation of software using terminal


    • How to Install BLAST+ version 2.6.0 (Step-by-Step) Ubuntu/Fedora/CentOS

*Step 1: Create a new directory name ncbi-blast+

$ mkdir ncbi-blast+

*Step 2: Enter in to created directory

$ cd ncbi-blast+

#For Fedora/ CentOS/ Ubuntu operating system


*Step 3: Download the software from NCBI-FTP site

$ wget -N ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.6.0/ncbi-blast-2.6.0+-1.x86_64.rpm

*Step 4: To Install (Fedora/ CentOS operating system)

$ sudo yum install ncbi-blast-2.6.0+-1.x86_64.rpm -nogpgcheck

 To Install ( Ubuntu operating system)

$ sudo alien -i ncbi-blast-2.6.0+-1.x86_64.rpm 

*Step 5:  To check for successful installation

$ blastn -h

Output: USAGE
blastn [-h] [-help] [-import_search_strategy filename]
[-export_search_strategy filename] [-task task_name] [-db database_name]
[-dbsize num_letters] [-gilist filename] [-seqidlist filename]
[-negative_gilist filename] [-entrez_query entrez_query]
[-db_soft_mask filtering_algorithm] [-db_hard_mask filtering_algorithm]
[-subject subject_input_file] [-subject_loc range] [-query input_file]
[-out output_file] [-evalue evalue] [-word_size int_value]
[-gapopen open_penalty] [-gapextend extend_penalty]
[-perc_identity float_value] [-qcov_hsp_perc float_value]
[-max_hsps int_value] [-xdrop_ungap float_value] [-xdrop_gap float_value]
[-xdrop_gap_final float_value] [-searchsp int_value]
[-sum_stats bool_value] [-penalty penalty] [-reward reward] [-no_greedy]
[-min_raw_gapped_score int_value] [-template_type type]
[-template_length int_value] [-dust DUST_options]
[-filtering_db filtering_database]
[-window_masker_taxid window_masker_taxid]
[-window_masker_db window_masker_db] [-soft_masking soft_masking]
[-ungapped] [-culling_limit int_value] [-best_hit_overhang float_value]
[-best_hit_score_edge float_value] [-window_size int_value]
[-off_diagonal_range int_value] [-use_index boolean] [-index_name string]
[-lcase_masking] [-query_loc range] [-strand strand] [-parse_deflines]
[-outfmt format] [-show_gis] [-num_descriptions int_value]
[-num_alignments int_value] [-line_length line_length] [-html]
[-max_target_seqs num_sequences] [-num_threads int_value] [-remote]
[-version]

**NCBI-BLAST+ version 2.6.0   is successfully installed on your system, now you can perform sequence similarity search locally with your customized database and queries.

    • Running applications example: local BLAST search

Prepare input

Create your local scratch directory (if not yet done) and a sub-directory blast_test
where this exercise will be run
$mkdir blast_test
$cd blast_test

Copy file with query sequences to the exercise directory:
cp /shared_data/Linux_workshop/seq_tst.fa 
.
Copy Swissprot BLAST database (we’ll make a separate directory for it)
mkdir databases
cp /shared_data/Linux_workshop/databases/swissprot* ./databases

 Verify that the files have been copied (use ls command)
Running applications example: BLAST
run the program

Very general syntax for launching applications:
In our specific case:
blastall -p blastx -b 1 -d ./databases/swissprot -i seq_tst.fa >& run.log

 Options used:
-p: type of search (blastx: compare 6-frame translations of DNA to AA sequences)
-b: number of database sequences to show alignments for
-d: path to database files
-i: input file (with query sequences in fasta format)
 For full set of options, run
blastall | more
