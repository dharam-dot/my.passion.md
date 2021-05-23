<h2 align="center">Task-4</h2>

<details>
  <summary> Summary of Task </summary>
  <ul>
    <br>
    <li> Create a testScript to analyse reliability of the Evaluation script .</li>
  </ul>
</details>

<details>
<summary> INDEX </summary>
  <ul>
    <br>
    <li> Test cases</li>
    <li> Implementation </li>
    <li> Conclusion  </li>
  </ul>
  </details>
  
<details>
  <summary> Test Cases </summary>
  
|S.NO|Test Cases|Test Case Description|Expected Result|Test Status|
|:----:|:-----:|:-----:|:-----:|:-----:|
|1|**Published Url** |Spread sheet link published by using publish to web option from file of spreadsheet and select the .csv format |Url should be published|**PASS** |
|2|**The path of commands  is declared in Variable** |I declared the path of commands in variables in the configuration file which i used in the script file. |Path of command should be declare in the variable |**PASS**|
|3|**Google spread sheet downloaded in CSV format** |I used wget with -q option with url of the google spread sheet to download in csv format -q option is used for silently downloaded <br/> I used this $WGET $WGETOPT1 $MYURL01 and $MYURL02 the value of these variable extracting from the configuration file |Google spreadsheet in csv format should be downloaded |**PASS** |
|4|**Rename downloaded files**|Renamed  files by using mv command  <br/> I used this $MV $OLDFILENAME1 $NEWFILENAME1  the value of these variable extract from the configuration file |Files should be renamed|**PASS** |
|5 |**DISPLAY THE OUTPUT using configuration file** | I used the source of configuration file in the script and run the script  <br/> I used  this to extract the required column (awk -F "," '{print "Name :",$name1, "\n", "Sum :",$average1* z "\n", "Average :",$average1, "\n"}') |Script should be run and display the output |**PASS** |
|6 |**Adding the column in the spreadsheet** |Add the column in the spreadsheet and gives the word to all students |Output should be updated |**PASS** |
|7 |**Adding the row in the spreadsheet** |Add the row in the spreadsheet and gives the word in all the columns |Output should be updated |**PASS** |
|8 |**Compair test script** |Using diff command comapred the both file and got result|Script should be run and display the output |**pass** |
  
</details>


<details>
  <summary> Implementation </summary>
  
In this script, first of all I copied the spreadsheet link to csv link through web publish option. After that I downloaded the link to the spreadsheet with the wget command and rename the download file with the mv command. Then I got the required output from awk command. after that i used diff command in my test script and compare the both files and got the required output.
  
 </details>
 
 <details>
  <summary> Configuration file </summary>
  
  #This is the main configuration file of script

#============================================================

#Variable declaration of command path which used in script

#wget command is a Linux command line utility that helps us to download the files from the web.

  WGET=/usr/bin/wget

  #echo command in linux is used to display line of text/stringon terminal.

  ECHO=/usr/bin/echo

  #mv command renames a file or folder and moves a group of files to a different directory

  MV=/usr/bin/mv

  #cat command allows us to create single or multiple files, view contain of file, concatenate files and redirect output in terminal or files.

  CAT=/usr/bin:/cat

  #awk command searches files for text containing a pattern. When a line or text matches, awk performs a specific action on that line/text.

  AWK=/usr/bin/awk

  #tail commandprint the last N number of data of the given input.

  TAIL=/usr/bin/tail

  #tr is a command for translating or deleting characters.

  TR=/usr/bin/tr

  #The grep command in unix or linux system is used to print the lines that match a given pattern.

  GREP=/usr/bin/grep

  #wc Command in Linux Count Number of Lines, Words, and Character.

  WC=/usr/bin/wc

  #pwd command prints the path of the working directory

  PWD=/usr/bin/pwdi

  #cp command is used to copy files or group of files or directory.

  CP=/usr/bin/cp

  #date command is used to display the system date and time.

  DATE=/usr/bin/date

  #=/usr/bin/

  DIFF=/usr/bin/diff

  #====================================================================================================================================================

  #wget command option

  #The download output is not visible so -q is used

  WGETOPT1=-q

  #====================================================================================================================================================

  #tr command option

  #-cd option used for delete the character.

  TROPT1=-cd

  #===================================================================================================================================================

  #wc command option

  #-c is used ko count the character

  WCOPT1=-c

  #===================================================================================================================================================

  #grep command option

  #-i option used for displays both uppercase and lowercase results.

  GREPOPT1=-i

  #===================================================================================================================================================

  #awk command option

  #-F used for the input field separator.

  AWKOPT1=-F

  #===================================================================================================================================================

  #here url used to download the spreadsheet in the format CSV

  #Below url01 for download the spreadsheet 1

  MYURL01=https://docs.google.com/spreadsheets/d/e/2PACX-1vS9pmOTPTCVI3XdmGtzetXIm9YVD2cnLDXAkBviswsYAifm9d9dq_iKfPFaHOMpL9oxtSJBh-u9R5CW/pub?output=csv


  #====================================================================================================================================================

  #Below url02 for download the spreadsheet 2

  MYURL02=https://docs.google.com/spreadsheets/d/e/2PACX-1vSEjogtwoNCCLzmjLHSegdJXH-icphTYJfzpAGC7WYOBPqgkwXNgcC3HQGpfU4tP-Jf8KUTVOHBloX6/pub?output=csv

  #=====================================================================================================================================================

  #Rename the downloaded file 1

  #OLDFILENAME1=/home/pradeep/Task-3/datafile/pub?output=csv

  OLDFILENAME1=/home/pradeep/mytask2/pub?output=csv

  #NEWFILENAME1=/home/pradeep/Task-3/datafile/sheet1.csv

  NEWFILENAME1=/home/pradeep/mytask2/sheet1.csv

  #=====================================================================================================================================================

  #Rename the downloaded file 2

  OLDFILENAME2=/home/pradeep/mytask2/pub?output=csv

  NEWFILENAME2=/home/pradeep/mytask2/sheet2.csv

  #====================================================================================================================================================

  #Column of spreadsheet

  AVGCOLUMN=Average

  avgcolumn=average

  #namecolumn=name

  #=================================================================================================================================================

  #Extra column

  NAMECOL=Name

  INTERNCOL=Intern

  SUMCOL=Sum

  AVGCOL=Avg

  #==================================================================================================================================================

  #log file of script

  log=/home/pradeep/mytask2/mytask2.log

  #==================================================================================================================================================

  #directory for datafile

  DATADIR=/home/pradeep/mytask2/datafile24

  DATADIR1=/home/pradeep/mytask2/datafile24/output20.txt

  DATADIR2=/home/pradeep/mytask2/datafile24/output21.txt

  #==================================================================================================================================================

  OLD_DATA_FILE_PATH1=/home/pradeep/mytask1/datafile23/output11.txt

  OLD_DATA_FILE_PATH2=/home/pradeep/mytask1/datafile23/output12.txt

  NEW_DATA_FILE_PATH1=/home/pradeep/mytask2/datafile24/output20.txt

  NEW_DATA_FILE_PATH2=/home/pradeep/mytask2/datafile24/output21.txt


#==================================================================================================================================================

  
  </details>
 
 <details>
  <summary> Conclusion </summary>
  
  I would like to share my experience while doing this work. The given script is doing its job correctly.
  
  </details>
