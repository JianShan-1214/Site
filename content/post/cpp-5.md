---
title: "C++ 教學(五) 迴圈"
date: 2020-03-02T23:39:04+08:00
slug: "cpp-5"
---

---

當你要做同一件事做好幾次時候該怎麼呢，雖然複製貼上很方便但這樣就會很醜，所以這時候就是迴圈上場的時候啦，迴圈是程式中很重要的一環，它可以幫我們節省大量的code，在C++ 中提供三種迴圈寫法 `for` 、 `while` 跟 `do...while`，接下來我們將一一介紹。

---

## for迴圈

`for`是常用於有固定次數的迴圈，當中包含三個參數，初始值、判斷式及控制式，中間則是用 `;` 隔開，一樣要特別注意因為迴圈還不是一個完整的指令，所以後面不用加 `;` ，到敘述句的時候再加。

#### 寫法:
```cpp
for(初始值;判斷式;控制式){
    敘述句;
}
```

是不是很簡單啊，我們直接來看個範例，我們要輸出1到10要怎麼做呢。

### 範例:
```cpp
#include <iostream>

using namespace std;

int main(){
    for(int i=1;i<=10;i++)
        cout<<i<<endl;
    return 0;
}
```
我們一樣用 [ideone](https://ideone.com/) 來實作看看。
>![](https://i.imgur.com/MVImT2P.png)

---

## while迴圈

  `while`常用於不固定次數的迴圈，是根據判斷式來決定是否結束，那他跟`for`一樣並不是一個完整的指令，所以要等到敘述句時再加`;`。
### 寫法:
```cpp
while(判斷式){
    敘述句;
}
```

因為次數不固定，所以我們給他一個條件來表示結束吧。

### 範例:
```cpp
#include <iostream>

using namespace std;

int main(){
    int sum=0,i=1;
    while(i<100){
        sum+=i;
        i++;
    }
    cout<<sum<<endl;
    return 0;
}
```
一樣到 [ideone](https://ideone.com/) 上測試。
>![](https://i.imgur.com/EurOeWw.png)


---

## do...while迴圈

  `do...while`比較特殊也比較少用到，他的概念跟`while`很像，但是他會先執行然後才判斷，但有一點要特別注意，前面兩個是迴圈使不用加`;`的，但使用`do..while`結束時一定要記得加`;`，這很重要一定要記住。
  
### 寫法:
```cpp
do{
    敘述句;
    敘述句;
}while(判斷式);
```
那我們一樣用剛剛`while`的範例吧。

### 範例:
```cpp
#include <iostream>

using namespace std;

int main(){
    int sum=0,i=1;
    do{
        sum+=i;
        i++;
    }while(i<100);
    cout<<sum<<endl;
    return 0;
}
```

 [ideone](https://ideone.com/)
>![](https://i.imgur.com/sXmYAg7.png)

發現其實兩個程式跑出來的結果是一樣的，所以`do...while`同樣也可以做到`while`能做的事，但還是要特別注意兩個跑的方式還是不太一樣的。

---
**迴圈就到這邊結束啦，接下來就要進入比較進階的部分，有任何問題也歡迎下面留言**
