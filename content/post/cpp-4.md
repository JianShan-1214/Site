---
title: "C++ 教學(四) 條件敘述句"
date: 2020-03-02T23:39:02+08:00
slug: "cpp-4"
---

---

條件敘述句是我們在程式中做判斷時會用到的句型，通常用來比較兩個以上的資料來做判斷，今天我們會介紹兩種在C++中常見的判斷敘述`if...else`跟`switch`。

---

## if...else判斷式

`if...else`是程式語言中非常常見的，大部分的程式語言都有這個語法，而他也很好理解翻成中文就是`假如...否則`。
#### 寫法:
```cpp
if (條件) {
    敘述句;
}
else {
    敘述句;
}
```
但有個小地方要特別注意，因為在寫判斷式時還不算一句完整的指令，所以還不用加`;`，要到寫敘述句的時候再加，這要特別注意。

那假如我們今天的判斷不只兩個要到三個四個呢，這時候就會用到`if..else`的另一個寫法`else if`，可以同時加入不同條件做判斷。

#### 寫法:
```cpp
if (條件){
    敘述句;
}
else if (條件){
    敘述句;
}
else{
    敘述句;
}
```
* 小技巧: 當敘述句只有一句的時候，可以不需要大括號。

接下來我們來試著寫個成績判斷的範例程式。

#### 範例:

```cpp
#include <iostream>
using namespace std;

int main(){
    int score;
    cin>>score;
    if(score>=60)
        cout<<"及格"<<endl;
    else
        cout<<"不及格"<<endl;
    return 0;
}
```

一樣放到 [ideone](https://ideone.com/) 上看看
>![](https://i.imgur.com/FAsxSdP.png)


那假如今天我們要將分數分級的話該怎麼辦呢，所以現在我們就來寫多個判斷的程式吧，把分數分成`A` `B` `C` `D` `E`五組吧。

```cpp
#include <iostream>

using namespace std;

int main(){
    int score;
    cin>>score;
    if(score>=90)
        cout<<"A";
    else if(score<90 && score>=80)
        cout<<"B";
    else if(score<80 && score>=70)
        cout<<"C";
    else if(score<70 && score>=60)
        cout<<"D";
    else
        cout<<"E";
    return 0;
}
```

在 [ideone](https://ideone.com/)檢查有沒有錯
>![](https://i.imgur.com/DMBZHt9.png)

那如果今天出現了不正常的分數該怎麼辦呢，是不是只要在前面多一個判斷就好了呢，現在先不要往下滑試著自己寫寫看吧。
.
.
.
.
.
.
.
.
.
.
.
.
```cpp
//答案僅供參考，只要能達成目的的都是正確答案
#include <iostrea>

using namespace std;

int main(){
    int score;
    cin>>score;
    if(score>=0 && score<=100){
        if(score>=60)
            cout<<"及格";
        else
            cout<<"不及格";
    }
    else
        cout<<"請輸入有效分數";
    return 0;
}
```

---

## switch...case判斷式

`switch..case`常見於一個變數需要大量的判斷，想想看一直用`else if`是不是很煩阿，這時候就是`switch`上場的時候了，不過他的寫法與前面教得有點不一樣，要特別注意。

#### 用法:
```cpp
switch(變數){
    case 符合的數字或字元:
        敘述句;
        break;
    case 符合的數字或字元:
        敘述句;
        break;
        .
        .
        .
    default:
        敘述句;
}
```
`switch`的判斷是這樣，會去比對變數與`case`是否一樣，如果一樣就執行下面的敘述句然後`break`跳出判斷，這個`break`非常重要，如果你沒有加他就會繼續判斷下去，直到遇到`default`並執行敘述句，因為`default`就是在你以上都不符合的時候才會執行，所以一定要記住加`break`。

#### 範例:
```cpp
#include <iostream>

using namespace std;

int main(){
    char score;
    cin>>score;
    switch(score){
        case 'A':
            cout<<"90分";
            break;
        case 'B':
            cout<<"80分";
            break;
        case 'C':
            cout<<"70分";
            break;
        case 'D':
            cout<<"60分";
            break;
        default:
            cout<<"不及格";
    }
    return 0;
}
```

到 [ideone](https://ideone.com/) 看看吧
>![](https://i.imgur.com/93BtkLX.png)



那假如我們今天要判斷的是一個範圍該怎麼辦呢，所以`switch`還有另一種寫法，要特別注意，他數字的範圍是包含於頭尾兩個數字。

#### 用法：
```cpp
switch(變數){
    case 數字 ... 數字:
        敘述句;
        break;
        .
        .
        .
    default:
        敘述句;
}
```

那我們就用前面的範例換成`switch...case`寫寫看吧。

```cpp
#include <iostream>

using namespace std;

int main(){
    int score;
    cin>>score;
    switch(score){
        case 90 ... 100:
            cout<<"A";
            break;
        case 80 ... 89:
            cout<<"B";
            break;
        case 70 ... 79:
            cout<<"C";
            break;
        case 60 ... 69:
            cout<<"D";
            break;
        case 0 ... 59:
            cout<<"F";
            break;
        default:
            cout<<"請輸入有效數字";
    }
    return 0;
}
```

[ideone](https://ideone.com/)
>![](https://i.imgur.com/QZ2MUqy.png)
>![](https://i.imgur.com/7emaI2n.png)

---
**那這章就到這邊啦，有任何問題歡迎下面留言指教，下一章我們會開始教迴圈的使用**
