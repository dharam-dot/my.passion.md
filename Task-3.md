<h2 align="center">Task-3</h2>

<details>
  <summary> Summary of Task </summary>
  <ul>
    <br>
    <li> Write a script in Shell.</li>
    <li> This script has been used to download 2 google sheets. </li>
    <li> Both of those Google sheets will have the formate csv file. </li>
    <li> Only the name, Average and Sum columns and their values should be printed. </li>
  </ul>
</details>

<details>
<summary> INDEX </summary>
  <ul>
    <br>
    <li> Test cases</li>
    <li> Implementation </li>
    <li> Script </li>
    <li> Output of script </li>
    <li> Conclusion  </li>
    <li> download files links </li>
  </ul>
  </details>

<details>
  <summary> Test Cases </summary>
  
|S.NO|Test Cases|Test Case Description|Expected Result|Test Status|Output|
|:----:|:-----:|:-----:|:-----:|:-----:|:----:|
|1|**Published Url** |Spread sheet link published by using publish to web option from file of spreadsheet and select the .csv format |Url should be published|**PASS** |![Webpublish](https://user-images.githubusercontent.com/82143335/116895216-94476480-ac50-11eb-9466-18a10936a60e.PNG)|
|2|**Declaring the path of commands in variable** |I declared the path of commands in variables in the configuration file which i used in the script  |Path of command should be declare in the variable |**PASS**|![variables](https://user-images.githubusercontent.com/82143335/116895709-1cc60500-ac51-11eb-8d94-fbb9faf237a5.PNG)|
|3|**DOWNLOADING THE GOOGLE SPREAD SHEETS IN CSV FORMAT** |I used wget with -q option with url of the google spread sheet to download in csv format -q option is used for silently downloaded <br/> I used this $WGET $option $URL1 and $URL2 the value of these variable extracting from the configuration file |Google spreadsheet in csv format should be downloaded |**PASS** |![download spreadsheet](https://user-images.githubusercontent.com/82143335/116896072-7cbcab80-ac51-11eb-9828-6bb1f0caf055.PNG)|
|4|**RENAME THE DOWNLOADED FILE**|Renamed  files which was downloading through 3 test case to sheet1.csv and sheet2.csv by using mv command  <br/> Iused this $MV $OLDFILE $NEWFILE the value of these variable extract from the configuration file |Files should be renamed|**PASS** |--|
|5 |**RENAME THE DOWNLOADED FILE** |Renamed  files which was downloading through 3 test case to sheet1.csv and sheet2.csv by using mv command  <br/> Iused this $MV $OLDFILE $NEWFILE the value of these variable extract from the configuration file |Files should be renamed|**PASS** |--|
|6 |**DISPLAY THE OUTPUT using configuration file** | I used the source of configuration file in the script and run the script  <br/> I used  this to extract the required column (awk -F "," '{print "Name :",$name1, "\n", "Sum :",$average1* "\n", "Average :",$average1, "\n"}') |Script should be run and display the output |**PASS** |![outpu2](https://user-images.githubusercontent.com/82143335/116898853-872c7480-ac54-11eb-92b5-81bcc2a41a1c.PNG)|
|7 |**Adding the column in the spreadsheet** |Add the column in the spreadsheet and gives the word to all students |Output should be updated |**PASS** | |
|8 |**Adding the row in the spreadsheet** |Add the row in the spreadsheet and gives the word in all the columns |Output should be updated |**PASS** | |
|9 |**Redirect the output** |Redirect the output of both sheet in a file  using this **> & >>** |Output should be redirect in the file |**PASS** | |
|10 |**log file** |when script run all logs genrate in log file |log should be genrated successfully in log file |**pass** |![log](https://user-images.githubusercontent.com/82143335/116899357-12a60580-ac55-11eb-822a-faa3d25cfff6.PNG)|

  
  </details>
  
  <details>
  <summary> Implementation </summary>
  
In this script, first of all I copied the spreadsheet link to csv link through web publish option.
After that I downloaded the link to the spreadsheet with the wget command and rename the download file with the mv command.
Then I got the required output from awk command.
  
  </details>
  
  <details>
  <summary> Script </summary>
  </details>
  
  <details>
  <summary> Configuration File </summary>
  
 #This is the main configuration file of script

#====================================================================================================================================================

#Variable declaration of command path which used in script

#wget command is a Linux command line utility that helps us to download the files from the web.

WGET=/usr/bin/wget

#echo command in linux is used to display line of text/stringon terminal.

ECHO=/usr/bin/echo

#mv command renames a file or folder and moves a group of files to a different directory

MV=/usr/bin/mv

#cat command allows us to create single or multiple files, view contain of file, concatenate files and redirect output in terminal or files.

CAT=/usr/bin/cat

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

PWD=/usr/bin/pwd

#cp command is used to copy files or group of files or directory.

CP=/usr/bin/cp

#date command is used to display the system date and time.

DATE=/usr/bin/date

#=/usr/bin/

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

OLDFILENAME1=/home/pradeep/task/pub?output=csv

NEWFILENAME1=/home/pradeep/task/sheet1.csv

#=====================================================================================================================================================

#Rename the downloaded file 2

OLDFILENAME2=/home/pradeep/task/pub?output=csv

NEWFILENAME2=/home/pradeep/task/sheet2.csv

#====================================================================================================================================================

#Column of spreadsheet

#SRNCOLUMN=SrNo

#INTERCOL=Intern Name

#COLUMN3=Punctuality

#COLUMN4=Time management

#COLUMN5=Attendance

#COLUMN6=Communication

#COLUMN7=Requirement analysis

#COLUMN8=Self Learning

#COLUMN9=Grammatical error

#COLUMN10=Creativity

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

log=/home/pradeep/task/script.log

#==================================================================================================================================================

#directory for datafile

DATADIR=/home/pradeep/task/datafile

OUTPUTFIR=/home/pradeep/task/datafile/output.txt

#==================================================================================================================================================

  </details>
  
  <details>
  <summary> Log file </summary>
   
Mon May  3 17:08:08 IST 2021 [wget command] download the csv file using wget command /usr/bin/wget -q https://docs.google.com/spreadsheets/d/e/2PACX-1vS9pmOTPTCVI3XdmGtzetXIm9YVD2cnLDXAkBviswsYAifm9d9dq_iKfPFaHOMpL9oxtSJBh-u9R5CW/pub?output=csv

Mon May  3 21:09:12 IST 2021 [wget command] download the csv file using wget command /usr/bin/wget -q https://docs.google.com/spreadsheets/d/e/2PACX-
1vS9pmOTPTCVI3XdmGtzetXIm9YVD2cnLDXAkBviswsYAifm9d9dq_iKfPFaHOMpL9oxtSJBh-u9R5CW/pub?output=csv

Mon May  3 21:09:12 IST 2021 [mv command] It rename the downloaded file using mv command /usr/bin/mv /home/pradeep/task/pub?output=csv /home/pradeep/task/sheet1.csv

Mon May  3 21:09:12 IST 2021 [count commas] count the no of commas before the Intern name 1

Mon May  3 21:09:12 IST 2021 [add 1 in the previous result of commas] 1

Mon May  3 21:09:12 IST 2021  [total commas for extract the Intern name column ] 2

Mon May  3 21:09:12 IST 2021 [count commas] count the no of commas before the Average 10

Mon May  3 21:09:12 IST 2021 [add 1 in the total no of commas before average column to get the exact average column] 1

Mon May  3 21:09:12 IST 2021 [commas for extract the average column] 11

Mon May  3 21:09:12 IST 2021 [output for sheet 1] successfully print sheet1 the required output

Mon May  3 21:09:17 IST 2021 [wget command] download the csv file using wget command /usr/bin/wget -q https://docs.google.com/spreadsheets/d/e/2PACX-1vSEjogtwoNCCLzmjLHSegdJXH-icphTYJfzpAGC7WYOBPqgkwXNgcC3HQGpfU4tP-Jf8KUTVOHBloX6/pub?output=csv

Mon May  3 21:09:17 IST 2021 [mv command] download sheet2 csv file using mv command /usr/bin/mv /home/pradeep/task/pub?output=csv /home/pradeep/task/sheet2.csv

Mon May  3 21:09:17 IST 2021 [count comma for intername] count the no of commas before the Intern name 1

Mon May  3 21:09:17 IST 2021 [add 1 in the total no of commas before Intern name column to get the exact Intern name column] 1

Mon May  3 21:09:17 IST 2021  [total commas for intername] download sheet2 csv file using this command 2

Mon May  3 21:09:17 IST 2021 [count commas] count the no of commas before the Average 10

Mon May  3 21:09:17 IST 2021 [add 1 for Average] download sheet2 csv file using this command 1

Mon May  3 21:09:17 IST 2021 [commas for extract the average column] 11

Mon May  3 21:09:17 IST 2021 [output for sheet 2] successfully print sheet2 the required output
  
  </details>
  
  <details>
  <summary> Conclusion </summary>
  
  I would like to share my experience while doing this work. The given script is doing its job correctly.
  
  </details>
  
  <details>
  <summary> Download files Links </summary>
  
#### Download the google sheet in csv format for evaluation of self and others on the basis of previous performance.
- [Link for download csv file 1](https://docs.google.com/spreadsheets/d/e/2PACX-1vS9pmOTPTCVI3XdmGtzetXIm9YVD2cnLDXAkBviswsYAifm9d9dq_iKfPFaHOMpL9oxtSJBh-u9R5CW/pub?output=csv)

#### Download the google sheet in  csv format for evaluation of self and others on the basis of task1
- [Link for download csv file 2](https://docs.google.com/spreadsheets/d/e/2PACX-1vSEjogtwoNCCLzmjLHSegdJXH-icphTYJfzpAGC7WYOBPqgkwXNgcC3HQGpfU4tP-Jf8KUTVOHBloX6/pub?output=csv)

  </details>

```
     Thank You
```
