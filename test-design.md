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

2 Boundary values and 3 Boundary values, based on the accepted 1-50


## 2. Sauce Demo checkout form 
Website: [Sauce Demo](https://www.saucedemo.com/) <br>
Login cred: Username 'standard_user', Password 'secret sauce' <br>
Log in, add product to cart, go to cart, and click checkout <br>
This page displays a checkout form with three empty fields requesting for the user's first name, last name, and zip/postal code. There's also a 'cancel' button and a 'checkout' button.

### First name (partitions, boundaries, why) 


### Last name (partitions, boundaries, why) 
### Postal code (partitions, boundaries, why) 
### Tests I ran and what I observed ### Questions





