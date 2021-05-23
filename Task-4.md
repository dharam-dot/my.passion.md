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
  <summary> Conclusion </summary>
  
  I would like to share my experience while doing this work. The given script is doing its job correctly.
  
  </details>
