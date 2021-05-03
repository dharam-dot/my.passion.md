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
  <summary> Output of script </summary>
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
