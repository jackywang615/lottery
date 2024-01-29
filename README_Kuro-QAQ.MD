# Edit by Kuro-QAQ
### 1. 修复中奖人员重复问题：
原因是在点击重新抽奖时，本轮中奖人员并未放回抽奖池。当奖品数等于人员数，又使用了重新抽奖功能时，最终池子里人员不足就会开启第二轮人员池，导致有人没中奖，有人多次中奖。
### 2. 修复有人不中奖问题：
举个例子：奖品数90，人数88，一次抽取5个，最后一轮只剩下3个人，进入判断小于一次抽取数并重开人员池，导致这3个人被跳过。改为当剩余人数小于设定的一轮抽奖数时，只抽剩余人员数的奖，剩下的可以继续再抽，并修复修改功能后各种情况下的页面左侧数量显示问题。
### 3. 修改部分：
```
/product/src/lottery/index.js

# 增加 LastLeftUsers 属性
basicData

# 修改剩余人员不足时的处理逻辑
lottery()

# 修改计算逻辑
changePrize()

# 增加对 LastLeftUsers 和 leftUsers 的操作
switch (target) {
  case "lottery":
    ...
    break;
  case "reLottery":
    ...
    break; 
}

```

详情见/product/src/lottery/index.js
