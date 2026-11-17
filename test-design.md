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

|PARTITION|VALUES|EXPECTED RESULTS|ACTUAL RESULTS
|---|---|---|---|
|Valid values (1-50)|1, 4, 25|Accepted|Values accepted in field|
|Below Min value|0, -1, -5|Rejected|Values accepted in field|
|Above Max value|51, 97, 105|Rejected|Values accepted in field|
|Empty field|Blank|Rejected|N/A|
|Non-Numbers|*, $, #|Rejected|Values rejected in field|
|Letters/Text|red, Naomi|Rejected|Values rejected in field. Except 'e'|
|Decimals|5.3, 7.8|Rejected|Values accepted in field|
|Very long Numbers|637463223364|Rejected|Values accepted in field|

'e' means raised to the power of a number. The field accepts 'e'. (3e45, 2e3, etc)

## Boundary Values

|2 BOUNDARY VALUE|EXPECTED RESULTS|ACTUAL RESULTS|3BOUNDARY VALUE|EXPECTED RESULTS|ACTUAL RESULTS|
|---|---|---|---|---|---|
|0|Rejected|Accepted|0|Rejected|Accepted|
|1|Accepted|Accepted|1|Accepted|Accepted|
|-|-|-|2|Accepted|Accepted|
|50|Accepted|Accepted|49|Accepted|Accepted|
|51|Rejected|Accepted|50|Accepted|Accepted|
|-|-|-|51|Rejected|Accepted|





