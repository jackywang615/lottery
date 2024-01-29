# Edit by Kuro-QAQ
### 1. Fixed the issue of duplicate winners：
The reason is that when clicking on the redraw, the winners of this round are not put back into the lottery pool. When the number of prizes is equal to the number of people, and the re-lottery function is used, the second round of personnel pool will be opened when there are not enough people in the pool, resulting in someone not winning the lottery and someone winning the lottery multiple times.
### 2. Fixed an issue where someone didn't win the lottery：
For example: the number of prizes is 90, the number of people is 88, 5 are drawn at a time, and there are only 3 people left in the final round, and the judgment is less than the number of draws and the pool of people is reopened, causing these 3 people to be skipped. We changed that When the number of remaining people is less than the set number of lottery rounds, only the remaining number of people will be drawn, and the rest can continue to be drawn, and we also did some change that the numbers on the left side of the page will be displayed correctly after zhese changes.
### 3. Change part：
```
/product/src/lottery/index.js

# Add the LastLeftUsers property
basicData

# Modify the processing logic when the remaining staff is insufficient
lottery()

# Modify the calculation logic
changePrize()

# Added operations for LastLeftUsers and leftUsers
switch (target) {
  case "lottery":
    ...
    break;
  case "reLottery":
    ...
    break; 
}

```

For details, see: /product/src/lottery/index.js
