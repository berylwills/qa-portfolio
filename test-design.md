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

|Test ID| First Name|Last Name|Postal Code|Response|
|---|---|---|---|---|
|TC01|Jane|Doe|100001||
|TC02||Doe|100001|
|TC03|Jane||100001|
|TC04|Jane|Doe||
|TC05||Doe||
|TC06|Jane|||
|TC07||Doe||
|TC08|Jane|||
### Questions





