Download Link: https://assignmentchef.com/product/solved-ee312-project-4-crm-system-for-a-hypothetical-small-company
<br>
<strong>: </strong>In this project you will write an inventory and customer relationship management (CRM) system for a hypothetical small company, <em>Ellie’s Baby Emporium</em>.  Your program will use the String abstract data type from class.




<strong>GRADING: </strong>you will be graded on producing the output precisely as documented.  That includes all punctuation, capitalization, spacing, spelling errors, etc.  You will also be graded on your program’s avoidance of memory leaks.




<strong>Summary of the task:</strong>  When main.cpp is run, it reads input commands from a text file with a specified format, i.e., a series of one-word commands and arguments for each command. The required read function is provided to you.  As each command is read from the input file, it is parsed (code provided), and then each command is executed (your code).  The command processing functions (and helper functions) that you write must interact with a database (which is represented as an array of structs) that is provided to you, but must be modified and read by you in your code.




<strong>Input: </strong>Your system will read input from a file. The file contains a sequence of commands. Each command begins with one of four keywords. The remainder of the command depends upon the keyword.

<ul>

 <li><strong>Inventory </strong>&lt;<em>type&gt; </em># – This command is used to record a new shipment from the factory into the store’s inventory. To read this command you must read from the file the type of item received (Bottles, Diapers, or Rattles) and the number of items in this shipment. You should then increase the store’s inventory by that amount. For example: “Inventory Bottles 50” means that 50 bottles should be added to the store’s inventory.</li>

 <li><strong>Purchase </strong><em>&lt;name&gt; &lt;type&gt; </em># – This command is used to record a purchase by a customer. Each customer is known by their first name (it’s a very friendly company), so <em>&lt;name&gt; </em>will be a <em>one-word</em> string for the customer’s name. The</li>

</ul>

<em>&lt;type&gt; </em>is once again Bottles, Diapers, or Rattles and is used to indicate what type of item this customer purchased. Finally, the last part of the command is the number of items purchased. For example, “Purchase Frank Diapers 100” means that the customer

“Frank” has purchased 100 Diapers.

<ul>

 <li><strong>Summarize </strong>– This command requests that a summary be printed of the store’s activity.</li>

 <li><strong>Quit </strong>– This command terminates the input.</li>

</ul>

To get you started, <em>main.cpp </em>includes source code for reading the keyword at the start of each command and “understanding” the keyword. What <em>main.cpp </em>will do is invoke one of three functions depending upon what the keyword is.

<ul>

 <li><em>processInventory() </em>– This function should read the item type and quantity from the input file and update the store’s inventory of the indicated item type.</li>

 <li><em>processPurchase() </em>– This function should read the customer’s name, the item type and the quantity. The function should look up the customer in the customer database</li>

</ul>

(creating a new customer record if this is a 1<sup>st</sup>-time customer) and increment the number of items purchased by this customer in their customer record. For example, if the customer record indicates that “Frank” had previously purchased 10 diapers and the current command indicates that “Frank” is purchasing 20 diapers, then the customer record should be set to indicate that 30 diapers have been purchased by Frank. Note that each customer should have their own customer record (so that Ellie can keep track of who her best customers are and offer incentives like coupons and things).

<ul>

 <li><em>processSummarize() </em>– This command should print out a summary. The summary should first display the number of Bottles, Rattles, and Diapers remaining in inventory at the time of the <strong>Summarize </strong> Next, the summary should display how many different customers have come to the store for purchases. Finally, the summary should report which customer purchased the most diapers (and how many diapers), who purchased the most bottles (and how many) and who purchased the most rattles (and how many). If a certain item has not been purchased by anybody, then the summary should indicate that.</li>

</ul>

You are provided with three input files. At the end of each file (after the <strong>Quit </strong>command) is a transcript of what the output should be from the <strong>Summary </strong>command. Please format your output exactly as shown in the file.




<strong>Error Handling: </strong>Note of course, that it is <strong>not</strong> possible to sell someone 50 bottles if there are only 20 in the inventory. If an error occurs when a purchase is attempted and the amount exceeds the amount currently in inventory, your <em>processPurchase </em>routine should print an error message, “Sorry &lt;name&gt;, we only have %d <em>&lt;type&gt;</em>” (see the test files for the exact format the error message should take.)  In this case, you should not update either the inventory or the customer record (and you should not add any new customers to the database unless they actually buy something).




<strong>Your Mission: </strong>Edit the file Project4.cpp to complete this project. To read from the input file, you may use two functions <em>readNum </em>and <em>readString</em>. Both of these functions are inside <em>main.cpp </em>and you should not change these functions in any way. You should only call <em>readNum </em>when the next parcel of input in the input file is a number (you can always know what’s coming because the commands are formatted in a specific order). When the next parcel in the input file is a string (like the customer’s name, or the type of item purchased), use <em>readString</em>.  Be sure to use <em>StringDestroy </em>appropriately to avoid memory leaks.




The <em>Customer </em>struct is defined in <em>Invent.h</em>. You should use this struct to keep track of all the customers. For this project we’ll assume that there will be a maximum of 1000 customers, so an array of 1000 <em>Customer </em>structs will be adequate, and most of the elements of the array will never actually be used. Each time you read a customer’s name, you should search through this array to find a matching customer. Obviously, if there have only been three customers so far, you should only search the first three entries in the array to find a match. Use the comparison function from the String abstract data type (StringIsEqualTo) to check to see if two Strings are the same. Note: you are required to use the Customer struct as defined in Invent.h AND you are required to use the String ADT example provided in String.h/String.cpp. PLEASE take a

look at String.h!  For this project you will need to call at least StringDestroy and

StringIsEqualTo. The code in main.cpp illustrates how these functions can be used.




<strong><em>Your program must produce exactly the same output as specified in the test files, including the same punctuation, capitalization, spacing and typographical errors (if any) present in those files. In addition, your program should produce the correct corresponding output for any other test file that we might create (with the equivalent formatting, punctuation, capitalization, typos, etc.).</em></strong>

<strong><em> </em></strong>

<strong>Testing: </strong>We’ve supplied three test files. Please note that all three test files use “Summarize” as the last command in the file.  Please do not assume that Summarize has to be the last command in a file, or that Summarize can appear only once. Any command can appear any number of times in any order.  You might want to write your own test files (as always).  You can edit the files using any text editor.




The test files provided with this project are VERY weak. They are intended merely to help you understand what your program is supposed to do (generally speaking). They are not intended to help you detect errors in your program.  Feel free to share test cases and their outputs on Piazza/Canvas with the whole class. If the only testing you do is with the tests we provide to you … well, good luck, you’ll need it.




<table width="0">

 <tbody>

  <tr>

   <td width="193"><strong>Provided File</strong></td>

   <td width="409"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="193">CRM.pdf</td>

   <td width="409">This document containing the description.</td>

  </tr>

  <tr>

   <td width="193">Invent.h</td>

   <td width="409">Inventory data structure’s interface.</td>

  </tr>

  <tr>

   <td rowspan="2" width="193">MyString.cpp MyString.h</td>

   <td width="409">A String ADT with added functionality.</td>

  </tr>

  <tr>

   <td width="409"></td>

  </tr>

  <tr>

   <td width="193"><strong>Project4.cpp </strong></td>

   <td width="409"><strong>The file that you will submit to the graders.</strong></td>

  </tr>

  <tr>

   <td width="193">main.cpp</td>

   <td width="409">Contains main, and starter code to read the input files, parse their contents, and call the functions that you write in Project3.cpp.</td>

  </tr>

  <tr>

   <td width="193">test1.txt test2.txt test3.txt</td>

   <td width="409">Sample input files.</td>

  </tr>

  <tr>

   <td width="193">Makefile</td>

   <td width="409">Used for testing on kamek</td>

  </tr>

 </tbody>

</table>


