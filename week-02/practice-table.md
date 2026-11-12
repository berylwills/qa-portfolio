# Decision Tables
“A bank app allows a transfer if the PIN is correct and the balance is enough. If
the PIN is wrong, it shows ‘Wrong PIN’. If the PIN is right but the balance isn’t enough, it shows ‘Not
enough money’.”

||R1|R2|R3|R4|
|---|---|---|---|---|
|Is the PIN correct?|T|T|F|F|
|Is the balance enough?|T|F|T|F|
|Allow Transfer|X||||
|Wrong PIN|||X|X|
|Not enough money||X|||

## Merged Conditions *(assuming the PIN is correct)*

||R1|R2|
|---|---|---|
|Is the balance enough?|T|F|
|Allow Transfer|X||
|Not enough money||X|

## Add "accountfrozen" condition.

||R1|R2|R3|R4|R5|R6|R7|R8
|---|---|---|---|---|---|---|---|---|
|Is the PIN correct?|T|T|T|T|F|F|F|F|
|Is the balance enough?|T|T|F|F|T|T|F|F|
|Is the account frozen|T|F|T|F|T|F|T|F|
|Allow Transfer||X|||||||
|Wrong PIN|||||X|X|X|X|
|Not enough money|||X|X|||||
|Account Frozen|X||X||X||X||

## Merged Conditions with accountfrozen condition *(assuming the PIN is correct)*

||R1|R2|R3|R4|
|---|---|---|---|---|
|Is the balance enough?|T|T|F|F|
|Is the account frozen|T|F|T|F|
|Allow Transfer||X|||
|Not enough money|||X|X|
|Account Frozen|X||X||

## Questions
- If the account is frozen and the PIN is wrong, which message appears first?
- If the balance is not enough and acccount is frozen, which message appears first?
