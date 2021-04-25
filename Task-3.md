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
  
| **SR-No.** | **TEST CASE** | **COMMAND** | **TEST OUTCOME** | **EXPECTED OUTCOME** | **STATUS** | **REMARKS** |
| --- | --- | --- | --- | --- | --- | ---- |  
| **1** | Spreadsheet link convert in CSV format | No Command | Using Publish to the web option got the Spreadsheet link in CSV format | After using Publish to the web option in Spreadsheet succesully got the link of Spreadsheet in csv format  | **Passed** | Testing has been passed |
| **2** | Spreadsheet Downoad | wget -q url of Spreadsheet | Using wget command  Spreadsheet successfully  download in csv format. | After using wget command Spreadsheet succefully download in csv format.  | **Passed** | Testing has been passed |
| **3** | Rename the download file | mv "pub?output=csv" output1.csv | Using mv command  downloaded file successfully  rename. | After using mv command  downloaded file succefully rename.  | **Passed** | Testing has been passed |
| **4** | Get the output in NAME,AVRAGE and SUM | AWK command | Using awk command got the result in te form in NAME, AVERAGE and SUM | after Using awk command successfully  got the result in te form in NAME, AVERAGE and SUM |  **Passed** | Testing has been passed |
| **5** |After add any column in Spreadsheet  | No command | Using insert option added the any column in spreadsheet got the update result and added column is showing in csv file.| After Using insert option added the any column in spreadsheet got the update result and added column is showing in csv file.|  **Passed** | Testing has been passed |
| **6** |After add any ROW in Spreadsheet  | No command | Using insert option added the any ROW in spreadsheet got the update result and added ROW is showing in csv file.| After Using insert option added the any ROW in spreadsheet got the update result and added ROW is showing in csv file.|  **Passed** | Testing has been passed |
  
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
