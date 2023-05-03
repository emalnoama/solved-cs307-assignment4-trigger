Download Link: https://assignmentchef.com/product/solved-cs307-assignment4-trigger
<br>
Each resident in mainland China has a unique 18-digit identity card number.  When you play online game like Honor of Kings, you need to enter your ID and name when you register. The game decides how many hours user can play the game each game. However, some teenagers may enter fake ID number trying to cheat the system so he/ she can play the game all day long. Suppose you are the database administrator of Honor of Kings, you are required to write a trigger to prevent illegal ID number insert to the game database.

<ol start="2">

 <li><strong>How does the China ID Card Citizen Identity Number </strong> <strong>work?</strong></li>

</ol>

The first 6 digits is the address code which refers to a specific administrative division. It indicates where the resident was born.  GB/T 2260 (a national standard) defines  address codes for all administrative divisions in China.  We also provide you a table <sub>district</sub> which can help you check whether the address code in the ID number is valid or not.

The 7-14 digits is the birthday of the resident. The format is <sub>YYYYMMDD </sub>. For example,  if you was born  in August 17th,  1926. The code for birthday is <sub>19260817 </sub>.  In this assignment, we assume all residents were born on or after January 1th, 1900.

The 15-17 digits is the order number. Odd number indicates the resident is male. Even number indicates the resident is female. For example, <sub>007</sub> means the resident is male, while <sub>666</sub> means the resident is female.

The last digit is the checksum.

Here is the algorithm for checksum (ISO 7064:1983.MOD 11-2).

<ol start="3">

 <li><strong> What you need to do? </strong></li>

</ol>

Given the database which contains two tables <sub>district</sub> and <sub>people</sub> ,you need to write a trigger and a function. The trigger is triggered before the data is inserted into table <sub>people </sub>. The function for trigger check whether the ID number is valid or not.

The format of insertion statement is shown as follow.




If the ID number is not valid. The function should throw the exception and stop the insertion.

If the ID number is valid. The new inserted row need the value of <sub>birthday</sub>  and <sub>address</sub> which are according to the ID number.

The format of <sub>address</sub> : [province],[city],[district]

If any of province, city or district doesn’t exists, you can ignore it.

The format of <sub>birthday </sub>: substring(ID, 7, 8)




Several successful test cases:

insert into people (id, name) values (‘110101200402232714’, ‘name1’); insert into people (id, name) values (‘440303210005112718’, ‘name2’); insert into people (id, name) values (‘440300199003162929’, ‘name3’); insert into people (id, name) values (‘540000199905203221’, ‘name3’); Result:




You can try the function: string_agg


