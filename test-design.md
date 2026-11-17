Date: 15th Nov 2026. <br>
Browser: Chrome on Macbook. <br>
Site: [Input page](https://the-internet.herokuapp.com/inputs.). <br>
This is a simple one-page site that displays a header, "Inputs", and shows an empty input field which is labelled as 'Number'. There are no instructions on the page, and no buttons.  <br>

  ## Observations
  - The page doesn't say what minimum number is acceptable.
  - The page doesn't say what maximum number is acceptable.
  - The page doesn't say a rule about decimals, zero, or negative values

  ## Assumptions 
  - I will assume that the field accepts ONLY whole numbers from between 1 and 50. Any other values will be rejected. This includes negative values, zero and numbers above 50
  - I will also assume that decimals will be rejected.

## Partitions

|PARTITION|VALUES|EXPECTED RESULTS|
|---|---|---|
|Valid values (1-50)|1, 4, 25|Accepted|
|Below Min value|0, -1, -5|Rejected|
|Above Max value|51, 97, 105|Rejected|
|Empty field|Blank|Rejected|
|Non-Numbers|*, $, #|Rejected|
|Letters/Text|red, Naomi|Rejected|
|Decimals|5.3, 7.8|Rejected|
|Very long Numbers|637463223364|Rejected|

## Boundary Values

|BOUNDARY VALUE|VALUES|EXPECTED RESULTS|
|---|---|---|

