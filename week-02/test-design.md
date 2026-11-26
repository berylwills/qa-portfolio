# Week 2: Test Design
Date: 15th Nov 2026 |Browser: Chrome on Macbook. 

## 1. The Internet: [Input page](https://the-internet.herokuapp.com/inputs.). 

### What the page tells me
This is a simple one-page site that displays a header, "Inputs", and shows an empty input field which is labelled as 'Number'. There are no instructions on the page, and no buttons.

### What the page tells me
  - The page doesn't say what minimum number is acceptable.
  - The page doesn't say what maximum number is acceptable.
  - The page doesn't say a rule about decimals, zero, or negative values

### My assumptions 
  - I will assume that the field accepts ONLY whole numbers from between 1 and 50. Any other values will be rejected. This includes negative values, zero and numbers above 50
  - I will also assume that decimals will be rejected.

### Partitions (based on my assumptions)

|PARTITION|TEST VALUES|VALID/INVALID|ACTUAL RESULTS
|---|---|---|---|
|Valid values (1-50)|1, 4, 25|Valid|Values accepted in field|
|Below Min value|0, -1, -5|Invalid|Values accepted in field|
|Above Max value|51, 97, 105|Invalid|Values accepted in field|
|Empty field|Blank|Invalid|N/A|
|Non-Numbers|*, $, #|Invalid|Values rejected in field|
|Letters/Text|red, Naomi|Invalid|Values rejected in field. Except 'e'|
|Decimals|5.3, 7.8|Invalid|Values accepted in field|
|Very long Numbers|637463223364|Invalid|Values accepted in field|

'e' means raised to the power of a number. The field accepts 'e'. (3e45, 2e3, etc)

### Boundary Values (based on my assumptions)

|2 BOUNDARY VALUE|VALID/INVALID|3BOUNDARY VALUE|VALID/INVALID|
|---|---|---|---|
|0|Invalid|0|Invalid|
|1|Valid|1|Valid|
|-|-|2|Valid|Valid|
|50|Valid|49|Valid|
|51|Invalid|50|Valid|
|-|-|51|Invalid|

2 Boundary values and 3 Boundary values, based on the accepted 1-50 values


## 2. Sauce Demo checkout form 
Website: [Sauce Demo](https://www.saucedemo.com/) <br>
Login cred: Username 'standard_user', Password 'secret sauce' <br>
Log in, add product to cart, go to cart, and click checkout <br>
This page displays a checkout form with three empty fields requesting for the user's first name, last name, and zip/postal code. There's also a 'cancel' button and a 'checkout' button. <br>
There are no specific requirements for validation

### First name (partitions, boundaries, why) 
Assumptions:
- First name is required
- Min length is 3 characters
- Max length is 30 characters
- Only Letters, hyphens and apostrophes are allowed
- Numbers, symbols, and underscores are invalid

PARTITIONS **(Based on assumptions)**
|Partition|Test data|Expected Results|Why|
|---|---|---|---|
|Empty||invalid|First name is required|
|Normal value|Naomi|Valid|Basic name|
|Very short|Na|Invalid|Below the min length|
|Very long|"45 characters"|Invalid|Above max length|
|Only Spaces|"   "|Invalid|Spaces alone is not a valid name|
|numbers in name|Naomi456|Invalid|Numbers are not allowed|
|Symbols|*&%@|Invalid|Symbols alone are not allowed|
|Hyphenated name|Jack-Sparrow|Valid|Hyphens are accepted|
|Apostrophe|D'Angelo|Valid|Hyphens are accepted|

Boundary Values **(Based on assumptions)**

|Boundary|Value|Expected results|
|---|---|---|
|Below Min|2 characters|Invalid|
|Minimum|3 characters|Valid|
|Just above min|4 characters|Valid|
|Just below max|29 characters|Valid|
|Maximum|30 characters|Valid|
Above max|31 characters|Invalid|

### Last name (partitions, boundaries, why) 
Assumptions:
- Last name is required
- Min length is 3 characters
- Max length is 30 characters
- Only Letters, hyphens and apostrophes are allowed
- Numbers, symbols, and underscores are invalid

PARTITIONS **(Based on assumptions)**
|Partition|Test data|Expected Results|Why|
|---|---|---|---|
|Empty||invalid|First name is required|
|Normal value|Paul|Valid|Basic name|
|Very short|Na|Invalid|Below the min length|
|Very long|"45 characters"|Invalid|Above max length|
|Only Spaces|"   "|Invalid|Spaces alone is not a valid name|
|numbers in name|Paul456|Invalid|Numbers are not allowed|
|Symbols|*&%@|Invalid|Symbols alone are not allowed|
|Hyphenated name|Jack-Sparrow|Valid|Hyphens are accepted|
|Apostrophe|D'Angelo|Valid|Hyphens are accepted|

Boundary Values **(Based on assumptions)**
|Boundary|Value|Expected results|
|---|---|---|
|Below Min|2 characters|Invalid|
|Minimum|3 characters|Valid|
|Just above min|4 characters|Valid|
|Just below max|29 characters|Valid|
|Maximum|30 characters|Valid|
|Above max|31 characters|Invalid|

### Postal code (partitions, boundaries, why) 
Assumptions:
- Postal code is required
- Min length is 4 characters
- Max length is 10 characters
- Only Letters and Numbers are allowed
- Special characters are invalid
  
PARTITIONS  **(Based on assumptions)**

|Partition|Test data|Expected Results|Why|
|---|---|---|---|
|Empty||Invalid|Postal code is required|
|Normal numeric code|100001|Valid|A normal 6 digit postal code (for Lagos)|
|Very short|101|Invalid|Below min length|
|Very long|12345678901|Invalid|Above max length|
|Only Spaces|"   "|Invalid|Not a postal code|
|Letters only|GTSJRBC|Valid|Letters are allowed|
|Symbols Only|*%#&@|Invalid|Symbols are not allowed|
|Symbols and numbers|6979&%3|Invalid|Special characters not allowed|

 Boundary Values **(Based on assumptions)**
|Boundary|Value|Expected results|
|---|---|---|
|Below Min|3 characters|Invalid|
|Minimum|4 characters|Valid|
|Just above min|5 characters|Valid|
|Just below max|9 characters|Valid|
|Maximum|10 characters|Valid|
Above max|11 characters|Invalid|



### Tests I ran and what I observed 
Valid data <br>
- First Name: Jane
- Last Name: Doe
- Postal Code: 100001

|Test ID| First Name|Last Name|Postal Code|Expected Results|Actual Results|Pass/Fail|
|---|---|---|---|---|---|---|
|TC01|Jane|Doe|100001|'Checkout: Overview' page is displayed|'Checkout: Overview' page is displayed|Pass|
|TC02||Doe|100001|Remain on information page, Error: First Name is required)|Remain on information page, Error: First Name is required|Pass|
|TC03|Jane||100001|Remain on information page, Error: Last Name is required|Remain on information page, Error: Last Name is required)|Pass|
|TC04|Jane|Doe||Remain on information page, Error: Postal Code is required|Remain on information page, Error: Postal Code is required|Pass|
|TC05|A|Doe|100001|Remain on information page, Error: First name is too short|'Checkout: Overview' page is displayed|Fail|
|TC06|Jane|A|100001|Remain on information page, Error: Last name is too short|'Checkout: Overview' page is displayed|Fail|
|TC07|TIDTEVDDVDSERWQHDIYDGSDDJHSBDSJD|Doe|100001|Remain on information page, Error: First name is too long|'Checkout: Overview' page is displayed|Fail|
|TC08|Jane|TIDTEVDDVDSERWQHDIYDGSDDJHSBDSJD|100001|Remain on information page, Error: Last name is too long|'Checkout: Overview' page is displayed|Fail|
|TC09|Spaces only ("   ")|Doe|100001|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC10|Jane|Spaces only ("   ")|100001|Remain on information page Error:,|'Checkout: Overview' page is displayed|Fail|
|TC11|4332556|Doe|100001|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC12|Jane|4332556|100001|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC13|@$%#@|Doe|100001|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC14|Jane|@$%#@|100001|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC15|Jane|Doe|121|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC16|Jane|Doe|12345678901|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC17|Jane|Doe|RDGWFG|'Checkout: Overview' page is displayed|'Checkout: Overview' page is displayed|Pass|
|TC18|Jane|Doe|@$%#@|Remain on information page, Error:|'Checkout: Overview' page is displayed|Fail|
|TC19|Jack-Sparrow|Anne-Mary|100001|'Checkout: Overview' page is displayed|'Checkout: Overview' page is displayed|Pass|
|TC20|D'Angelo|O'Neil|100001|'Checkout: Overview' page is displayed|'Checkout: Overview' page is displayed|Pass|

**Fail:** meant that I remained on the checkout form page with the error displayed.  <br>
**Pass:** meant that I was directed to the Checkout:Overview page which shows the details of the product(s) Qty and Description, Payment Information, Shipping Information and Total Price. There's also a "Cancel" button to cancel the order, and a Finish button that directs you to a Thank you page.

### Questions
- Why did the checkout form accept every input value?
- Why did the checkout form accept only spaces in the field?
- Why did the checkout form only flag empty fields? Is that intended??

## 3. Sauce Demo login decision table 

### Conditions and actions 
Conditions:
- C1: Is the username valid? (One of the usernames the page lists.)
- C2: Is the password correct?
- C3: Is the user locked out? (The locked_out_user account.)
Actions:
- A1: Login successful, Go to Products page
- A2: Login Fails, display error message "Password is incorrect"
- A3: Login Fails, display error message "User is locked out"

### Full table, then simplified table (with why) 

||R1|R2|R3|R4|R5|R6|R7|R8|
|---|---|---|---|---|---|---|---|---|
|Is the username valid?|T|T|T|T|F|F|F|F|
|Is the password correct?|T|T|F|F|T|T|F|F|
|Is the user locked out?|T|F|T|F|T|F|T|F|
|Go to Products page||X|||N/A||N/A||
|Display error message "Password is incorrect"|X||X|X|N/A|X|N/A|X|
|display error message "User is locked out"|X||||||||

A username cannot be invalid and locked out. It is an impossible combination  Since the username must be valid for login to be possible, the columns will be merged.

**Simplified Table**

||R1|R2|R3|R4|
|---|---|---|---|---|
|Is the password correct?|T|T|F|F|
|Is the user locked out?|T|F|T|F|
|Go to Products page||X|||
|Display error message "Password is incorrect"|||X|X|
|display error message "User is locked out"|X||||

### Test data and observed results 

|Username|Password|Expected response|Actual Response|
|---|---|---|---|
|standard_user|secret_sauce|Login successful|*Login successful, it moved to Products page*|
|standard_user|wrong_password|Login Failed: "Invalid username/password"|Epic sadface: Username and password do not match any user in this service|
|locked_out_user|secret_sauce|Login rejected:"User is locked out"|Epic sadface: Sorry, this user has been locked out.
|locked_out_user|wrong_password|Login Failed: "Invalid username/password"|Epic sadface: Username and password do not match any user in this service
|invalid_user|secret_sauce|Login rejected:"User does not exist"|Epic sadface: Username and password do not match any user in this service
|invalid_user|wrong_password|Login rejected:"User does not exist"|Epic sadface: Username and password do not match any user in this service

### Bonus tests (empty fields, capitals, spaces)

|Test Case|Username|Password|Response/results|
|---|---|---|---|
|Empty Username|(blank)|secret_sauce|Epic sadface: Username is required|
|Empty Password|standard_user|(blank)|Epic sadface: Password is required|
|Both fields empty|(blank)|(blank)|Epic sadface: Username is required|
|Username in capital letters|STANDARD_USER|secret_sauce|Epic sadface: Username and password do not match any user in this service|
|Leading space|" standard_user"|secret_sauce|Epic sadface: Username and password do not match any user in this service|


## 4. What I learned 
Quality Assurance is a responsibility that requires careful observation of the software, testing every possible input to ensure that it is optimal for the users. Usage of Conditions, Partitions, and Boundary values helps with proper test case planning for a better testing experience.



