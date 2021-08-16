#### replaceAll
- 정규식이나 반복문 없이 전체 변경 가능

#### Logical assignment operators
```
  let a = 1;
  if (a) {
    a = 2
  }

//new
  let a = 1;
  a &&= 2;
```
#### Numeric separators 
```
const money = 1000000000;
const money = 1_000_000_000;
```