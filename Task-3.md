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
    <li> Configuration File </li>
    <li> Log file </li>
    <li> Conclusion  </li>
    <li> download files links </li>
  </ul>
  </details>

<details>
  <summary> Test Cases </summary>
  
|S.NO|Test Cases|Test Case Description|Expected Result|Test Status|Output|
|:----:|:-----:|:-----:|:-----:|:-----:|:----:|
|1|**Published Url** |Spread sheet link published by using publish to web option from file of spreadsheet and select the .csv format |Url should be published|**PASS** |![Webpublish](https://user-images.githubusercontent.com/82143335/116895216-94476480-ac50-11eb-9466-18a10936a60e.PNG)|
|2|**The path of commands  is declared in Variable** |I declared the path of commands in variables in the configuration file which i used in the script file. |Path of command should be declare in the variable |**PASS**|![variables](https://user-images.githubusercontent.com/82143335/116895709-1cc60500-ac51-11eb-8d94-fbb9faf237a5.PNG)|
|3|**Google spread sheet downloaded in CSV format** |I used wget with -q option with url of the google spread sheet to download in csv format -q option is used for silently downloaded <br/> I used this $WGET $WGETOPT1 $MYURL01 and $MYURL02 the value of these variable extracting from the configuration file |Google spreadsheet in csv format should be downloaded |**PASS** |![download spreadsheet](https://user-images.githubusercontent.com/82143335/116896072-7cbcab80-ac51-11eb-9828-6bb1f0caf055.PNG)|
|4|**Rename downloaded file**|Renamed  files by using mv command  <br/> I used this $MV $OLDFILENAME1 $NEWFILENAME1  the value of these variable extract from the configuration file |Files should be renamed|**PASS** |--|
|5 |**Rename downloaded file** |Renamed  files by using mv command  <br/> I used this $MV $OLDFILENAME2 $NEWFILENAME2 the value of these variable extract from the configuration file |Files should be renamed|**PASS** |--|
|6 |**DISPLAY THE OUTPUT using configuration file** | I used the source of configuration file in the script and run the script  <br/> I used  this to extract the required column (awk -F "," '{print "Name :",$name1, "\n", "Sum :",$average1* "\n", "Average :",$average1, "\n"}') |Script should be run and display the output |**PASS** |![outpu2](https://user-images.githubusercontent.com/82143335/116898853-872c7480-ac54-11eb-92b5-81bcc2a41a1c.PNG)|
|7 |**Adding the column in the spreadsheet** |Add the column in the spreadsheet and gives the word to all students |Output should be updated |**PASS** | |
|8 |**Adding the row in the spreadsheet** |Add the row in the spreadsheet and gives the word in all the columns |Output should be updated |**PASS** | |
|9 |**log file** |when script run all logs genrate in log file |log should be genrated successfully in log file |**pass** |![log](https://user-images.githubusercontent.com/82143335/116899357-12a60580-ac55-11eb-822a-faa3d25cfff6.PNG)|

  
  </details>
  
  <details>
  <summary> Implementation </summary>
  
In this script, first of all I copied the spreadsheet link to csv link through web publish option.
After that I downloaded the link to the spreadsheet with the wget command and rename the download file with the mv command.
Then I got the required output from awk command.
  
  </details>
  
  <details>
  <summary> Script </summary>

#!/bin/bash

PWD=`/usr/bin/pwd`

#Here we given the path of configuration file using source command

source /home/pradeep/task/scriptconfig.conf

#if condition is true then print error in sheet otherwise go to the else.

if [ $MYURL01 = $0 ]

then

$ECHO "This error for sheet1"

else

$ECHO "==================First sheet output==================="

#Here wget command is used to download spreadsheet 1 with the help of url

$WGET $WGETOPT1 $MYURL01

$ECHO "$(date) [wget command] download the csv file using wget command $WGET $WGETOPT1 $MYURL01" >> "$log"  #Collect logs in log file

#Here mv command is used to rename the file

$MV $OLDFILENAME1 $NEWFILENAME1

$CP $NEWFILENAME1 $DATADIR

$ECHO "$(date) [mv command] It rename the downloaded file using mv command $MV $OLDFILENAME1 $NEWFILENAME1" >> "$log"  #Collect logs in log file

#Here the exact column  Intern Name is found.

#Here $CAT is used to show the contents of a file.

#GREP is used to find the row with a specific name.

#-i is used to find letters whether the letter is in upercase or in lowercase.

#Here tr command is used to translate and delete characters.

#Here wc -c command is used to count commas.

#The below command  shows the total number of commas.

COUNT1=$($CAT $NEWFILENAME1 | $GREP $GREPOPT1 $NAMECOL | $AWK -F "$INTERNCOL" '{print $1}'|$TR $TROPT1 , | $WC $WCOPT1)

$ECHO "$(date) [count commas] count the no of commas before the Intern name $COUNT1" >> "$log"  #Collect logs in log file

#ADD1 is used to add 1 to the total number of commas.

ADD1=1

$ECHO "$(date) [add 1 in the previous result of commas] $ADD1" >> "$log"  #Collect logs in log file

#PLUS1 is used to get the exact column no.

PLUS1=$((COUNT1+ADD1))

$ECHO "$(date)  [total commas for extract the Intern name column ] $PLUS1" >> "$log"  #Collect logs in log file

$ECHO "Afetr adding 1 total commas before Intern Name column $PLUS1"

#Here the exact column Average is found.

#Here $CAT is used to show the contents of a file.

#GREP is used to find the row with a specific name.

#-i is used to find letters whether the letter is in upercase or in lowercase.

#Here tr command is used to translate and delete characters.

#Here wc -c command is used to count commas.

#The below command shows the total number of commas.

COUNT2=$($CAT $NEWFILENAME1 | $GREP $GREPOPT1 $avgcolumn | $AWK $AWKOPT1 "$AVGCOLUMN" '{print $1}'|$TR $TROPT1 , | $WC $WCOPT1)

$ECHO "$(date) [count commas] count the no of commas before the Average $COUNT2" >> "$log"  #Collect logs in log file

#ADD2 is used to add 1 to the total number of commas.

ADD2=1

$ECHO "$(date) [add 1 in the total no of commas before average column to get the exact average column] $ADD2" >> "$log"  #Collect logs in log file

#PLUS2 is used to get the exact column no.

PLUS2=$((COUNT2+ADD2))

$ECHO "$(date) [commas for extract the average column] $PLUS2" >> "$log"  #Collect logs in log file

$ECHO "After adding 1 total commas before Average column $PLUS2"

###########################

$ECHO "Without adding 1 total commas before Intern Name $COUNT1"

$ECHO "Without adding 1 total commas before Average $COUNT2"

AUTOMUL=$((COUNT2-COUNT1))

$ECHO "diffrence of Intern name and Average$AUTOMUL"

VAL1=1

ACTVAL=$((AUTOMUL-VAL1))

$ECHO "pls multiply by this numbere=$ACTVAL"

###########################

#========================================================================================================================#

#Here $ cat is used to show the contents of a file.

#$TAIL -n + 4 is used to not show the beginning 4 line of the file.

#$AWK is used to extract the required column and print the Name Sum and Average.

#Extracting value from average1 $ PLUS1

#extracting value from name1 $ PLUS2

#Extracting value from x $ value1

$CAT $NEWFILENAME1 | $TAIL -n+4 | awk -F "," '{print "Name : ",$name1, "\n", "Sum : ",$average1*z, "\n", "Avg : ",$average1, "\n"}' name1=$PLUS1 average1=$PLUS2 z=$ACTVAL
$ECHO "$(date) [output for sheet 1] successfully print sheet1 the required output" >> "$log"  #Collect logs in log file

fi

###############################################################################################################################################################

##############################################################################################################################################################

if [ $MYURL02 = $0 ]

then

$ECHO "This error for sheet2"

else

$ECHO "==================Second sheet output==================="

#Here wget command is used to download spreadsheet 1 with the help of url

$WGET $WGETOPT1 $MYURL02

$ECHO "$(date) [wget command] download the csv file using wget command $WGET $WGETOPT1 $MYURL02" >> "$log" #Collect logs in log file

#Here mv command is used to rename the file

$MV $OLDFILENAME2 $NEWFILENAME2

$CP $NEWFILENAME2 $DATADIR

$ECHO "$(date) [mv command] download sheet2 csv file using mv command $MV $OLDFILENAME2 $NEWFILENAME2" >> "$log"  #Collect logs in log file

#Here the exact column  Intern Name is found.

#Here $CAT is used to show the contents of a file.

#GREP is used to find the row with a specific name.

#-i is used to find letters whether the letter is in upercase or in lowercase.

#Here tr command is used to translate and delete characters.

#Here wc -c command is used to count commas.

#The below command shows the total number of commas.

COUNT11=$($CAT $NEWFILENAME2 | $GREP $GREPOPT1 $NAMECOL | $AWK $AWKOPT1 "Intern Name" '{print $1}'|$TR $TROPT1 , | $WC $WCOPT1)

$ECHO "$(date) [count comma for intername] count the no of commas before the Intern name $COUNT11" >> "$log"  #Collect logs in log file

#ADD11 is used to add 1 to the total number of commas.

ADD11=1

$ECHO "$(date) [add 1 in the total no of commas before Intern name column to get the exact Intern name column] $ADD11" >> "$log"

#PLUS11 is used to get the exact column no.

PLUS11=$((COUNT11+ADD11))

$ECHO "$(date)  [total commas for intername] download sheet2 csv file using this command $PLUS11" >> "$log"  #Collect logs in log file

$ECHO "Afetr adding 1 total commas before Intern Name column $PLUS11"

#Here the exact column Average is found.

#Here $CAT is used to show the contents of a file.

#GREP is used to find the row with a specific name.

#-i is used to find letters whether the letter is in upercase or in lowercase.

#Here tr command is used to translate and delete characters.

#Here wc -c command is used to count commas.

#The below commands shows the total number of commas.

COUNT22=$($CAT $NEWFILENAME2 | $GREP $GREPOPT1 $avgcolumn | $AWK $AWKOPT1 "$AVGCOLUMN" '{print $1}'|$TR $TROPT1 , | $WC $WCOPT1)

$ECHO "$(date) [count commas] count the no of commas before the Average $COUNT22" >> "$log"  #Collect logs in log file

#ADD22 is used to add 1 to the total number of commas.

ADD22=1

$ECHO "$(date) [add 1 for Average] download sheet2 csv file using this command $ADD22" >> "$log"  #Collect logs in log file

#PLUS22 is used to get the exact column no.

PLUS22=$((COUNT22+ADD22))

$ECHO "$(date) [commas for extract the average column] $PLUS22" >> "$log"  #Collect logs in log file

$ECHO "After adding 1 total commas before Average column $PLUS22"

#========================================================================================================================#

$ECHO "Without adding 1 total commas before Intern Name $COUNT11"

$ECHO "Without adding 1 total commas before Average $COUNT22"

AUTOMUL1=$((COUNT22-COUNT11))

$ECHO "diffrence of Intern name and Average$AUTOMUL1"

VAL2=1

ACTVAL1=$((AUTOMUL1-VAL2))

$ECHO "pls multiply by this numbere=$ACTVAL1"

#========================================================================================================================#

#Here $ cat is used to show the contents of a file.

#$TAIL -n + 4 is used to not show the beginning 4 line of the file.

#$AWK is used to extract the required column and print the Name Sum and Average.

#Extracting value from average1 $ PLUS11

#extracting value from name1 $ PLUS22

#Extracting value from x $ value2

$CAT $NEWFILENAME2 | $TAIL -n+4 | awk -F "," '{print "Name : ",$name1, "\n", "SUM : ",$average1*s, "\n", "Avg : ",$average1, "\n"}' name1=$PLUS11 average1=$PLUS22 s=$ACTVAL1

$ECHO "$(date) [output for sheet 2] successfully print sheet2 the required output" >> "$log"  #Collect logs in log file

fi
    
  </details>
  
  <details>
  <summary> Configuration File </summary>
  
 #This is the main configuration file of script

#=======================================================================================

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

#===================================================================================

#wget command option

#The download output is not visible so -q is used

WGETOPT1=-q

#===================================================================================

#tr command option

#-cd option used for delete the character.

TROPT1=-cd

#====================================================================================

#wc command option

#-c is used ko count the character

WCOPT1=-c

#====================================================================================

#grep command option

#-i option used for displays both uppercase and lowercase results.

GREPOPT1=-i

#====================================================================================

#awk command option

#-F used for the input field separator.

AWKOPT1=-F

#=====================================================================================

#here url used to download the spreadsheet in the format CSV

#Below url01 for download the spreadsheet 1

MYURL01=https://docs.google.com/spreadsheets/d/e/2PACX-1vS9pmOTPTCVI3XdmGtzetXIm9YVD2cnLDXAkBviswsYAifm9d9dq_iKfPFaHOMpL9oxtSJBh-u9R5CW/pub?output=csv

#=====================================================================================

#Below url02 for download the spreadsheet 2

MYURL02=https://docs.google.com/spreadsheets/d/e/2PACX-1vSEjogtwoNCCLzmjLHSegdJXH-icphTYJfzpAGC7WYOBPqgkwXNgcC3HQGpfU4tP-Jf8KUTVOHBloX6/pub?output=csv

#======================================================================================

#Rename the downloaded file 1

OLDFILENAME1=/home/pradeep/task/pub?output=csv

NEWFILENAME1=/home/pradeep/task/sheet1.csv

#======================================================================================

#Rename the downloaded file 2

OLDFILENAME2=/home/pradeep/task/pub?output=csv

NEWFILENAME2=/home/pradeep/task/sheet2.csv

#======================================================================================

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

#=====================================================================================

#Extra column

NAMECOL=Name

INTERNCOL=Intern

SUMCOL=Sum

AVGCOL=Avg

#====================================================================================

#log file of script

log=/home/pradeep/task/script.log

#====================================================================================

#directory for datafile

DATADIR=/home/pradeep/task/datafile

#====================================================================================

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
