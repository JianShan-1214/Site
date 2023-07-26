---
title: "C++ 教學(三) 運算"
date: 2020-03-02T23:38:59+08:00
slug: "cpp-3"
---
---
C++提供了許多運算方法，稱之為運算式，而運算式則是由運算子與運算元所構成的，以大家最熟悉的算術運算為例，運算子就是加減乘除，運算元則是我們所宣告的變數或常數，當然除了算術運算常見的還有關係運算'邏輯運算等，下面會一一解釋。

---
## 算術運算

算術運算基本上就是我們數學上的四則運算，包含加 `+`、減 ``-`` 、乘 ``*`` 、除 ``/`` 還有一個比較特別的取餘數 ``%``，當然她也遵守數學上的先乘除後加減，必要的時候也可以用括號來執行優先運算，取餘的優先度則跟乘除一樣。

#### 範例:
```cpp=
#include <iostream>
using namespace std;

int main(){
    int a,b,c;
    cin>>a>>b>>c;
    cout<<a+b<<endl;
    cout<<a-b<<endl;
    cout<<a*b<<endl;
    cout<<a/b<<endl;
    cout<<a%b<<endl;
    cout<<(a+b)*c<<endl;
    cout<<a+b*c<<endl;
    return 0;
}
```
把它放到 [ideone](https://ideone.com/) 上看看
>![](https://i.imgur.com/Z8jlfSB.png)

是不是很簡單啊，但有個小細節一定要注意，那就是變數的型態，什麼是變數的型態呢，還記的上一章我們講得宣告變數嗎，裡面有說到不同的變數型態所存的東西是不一樣的，就像上面我們是用`int`宣告變數，所以不管怎樣計算出來都一定只會有整數，這就是為什麼`cout<<a/b;`時出來的是`1`不是`1.3333`，那如果我今天希望它計算出小數點呢，有很多不同的方法，最簡單的就是在宣告的時候就用浮點數也就是`double`跟`flaot`，另一個則是叫強制型別轉換是個很方便的東西，它的寫法是這樣:
```cpp
型別(變數);
```
通常會用在運算時直接改變型別，下面兩種不同的寫法結果都一樣，就看各位喜歡哪一種了，我個人是建議新手都用第一種比較好，第二種在某些特殊情況下再使用。

>![](https://i.imgur.com/QdVZLD1.png)


>![](https://i.imgur.com/XNkKEJJ.png)

除了正常我們數學上常用的寫法外，在C++裡有還有許多懶人的寫法，~~因為工程師通常都很懶~~，能少打就少打，所以這邊我們來介紹兩個常見的縮寫

### (一)
```cpp
變數 += 變數;//以加為範例
```
他等於我們平常寫的`變數 = 變數 + 變數;`，通常用在迴圈算總和的時候，加也可以換成其他的算數運算子。

#### 範例:
```cpp
#include <iostream>

using namespace std;

int main(){
    int a=1;
    cout<<(a+=a);
    return 0;
}
```
![](https://i.imgur.com/LrRPoG5.png)


### (二)
```cpp
變數++;
```
或
```cpp
++變數;
```
在C++裡面，`++`就是加一的意思，當然也有`--`就是減一，但`＋+`放在前面或後面有不一樣的意思喔，一個是先做`++變數;`、一個是後做`變數++;`，不懂嗎，沒關係我們直接看例子。

#### 範例1:
```cpp
#include <iostream>

using namespace std;

int main(){
    int a=0;
    cout<<(a++)<<endl;
    cout<<a<<endl;
    return 0;
}
```
![](https://i.imgur.com/pTVQKfk.png)

#### 範例2:
```cpp
#include <iostream>

using namespace std;

int main(){
    int a=0;
    cout<<(++a)<<endl;
    cout<<a<<endl;
    return 0;
}
```
![](https://i.imgur.com/rXNFfZ8.png)

有看出差別嗎，簡單來說，範例1就是先做`cout<<a;`才做`a++;`，範例2則是先做`++a;`才做`cout<<a;`，這樣都懂了嗎。

---

## 關係運算

關係運算就是我們常見的大於`>`、小於`<`、不大於`＜=`、不小於`>=`、等於`==`跟不等於`!=`，關係運算的結果就是回傳`1`或`0`，也就是`true`或`false`，因為在 C++ 中所有非`0`的數都被視為`true`。
#### 範例:
```cpp=
#include <iostream>
using namespace std;

int main(){
    int a=4;
    int b=3;
    cout<<"a>b  "<<(a>b)<<endl;
    cout<<"a<b  "<<(a<b)<<endl;
    cout<<"a>=b  "<<(a>=b)<<endl;
    cout<<"a<=b  "<<(a<=b)<<endl;
    cout<<"a==b  "<<(a==b)<<endl;
    cout<<"a!=b  "<<(a!=b)<<endl;
    return 0;
}
```
一樣丟上去看看 [ideone](https://ideone.com/)
>![](https://i.imgur.com/IEzKZDe.png)

那就有人好奇啦，我們前面在宣告變數時用的等於明明就是長這樣`=`，為什麼在關係運算裡面會長這樣`==`呢，其實`=`這個才是我們數學上常用的等於，而`=`這個則是另外一個意思，通常我們是翻譯為賦予，你要賦予變數一個值，所以我們的寫法才會是`c = a + b;`，不是寫成數學上的`a + b = c`，這個很重要一定要記住`=`跟`==`是不一樣的，很多人會搞混，要搞清楚在寫`if...else`條件判斷的時候才不會不知道自己哪裡錯。

---
## 邏輯運算

在邏輯上我們有"且(and)"`&&`、"或(or)"`||`跟"相反(not)"`!`，他們的邏輯判斷如下

|  `&&`    |   `1`    |   `0`    |
| -------- | -------- | -------- |
| `1`      | `true`   | `false`  |
| `0`      | `false`  | `false`  |

|  `||`    |   `1`    |   `0`    |
| -------- | -------- | -------- |
| `1`      | `true`   | `true`   |
| `0`      | `true`   | `false`  |

`!`就是結果都相反

在 [ideone](https://ideone.com/) 上實作:
![](https://i.imgur.com/NZ6nU6h.png)
![](https://i.imgur.com/6QytZdt.png)

是不是很簡單啊，就跟平常的邏輯一樣，在之後的`if...else`條件判斷或迴圈都會用到，還有什麼不懂可以留言給我喔。

---
**這章結束囉，當然C++還有很多其他的運算子以後有機會還會說到，下一章會開始講條件判斷**