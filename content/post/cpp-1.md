---
title: "C++ 教學(一) 基本介紹 & Hello World"
date: 2020-03-02T23:24:45+08:00
slug: "cpp-1"
tags: ["C++"]
---

## 介紹
![](https://i.imgur.com/Rvvd058.png)
<br>
C++ 是一種被廣泛使用的電腦程式設計語言，**比雅尼·斯特勞斯特魯普**博士在**貝爾實驗室**工作期間在20世紀80年代發明並實現了C++，作為C語言的增強版，C++ 引入了更多的特性，包括：複合型別（參照類型等）、const限定符和constexpr常數表達式、型別處理運算子（型別別名及auto和decltype等多種型別指示符）、C++ 標準庫（IO庫與多種容器類）與疊代器、動態記憶體與智慧型指標、函式重載、物件導向程式設計。

以上引自 [wikipedia](https://zh.wikipedia.org/wiki/C%2B%2B)

C++ 雖然是一門古老的語言，易讀性也比不過其他的腳本語言，可至今仍有大量的工程師在使用，這也是各大比賽中最常出現的語言。如 [APCS](hhttps://apcs.csie.ntnu.edu.tw/)、[ITSA](https://sites.google.com/site/itsancku/home) 等，所以對想讀資訊的同學，是非常值得深入學習的語言。

**2020 TIOBE 程式語言排行**
>![](https://i.imgur.com/Lujgujx.png)

<br>

---

## 編譯環境
<br>

這邊我們選用線上編譯器--- [ideone](https://ideone.com/)，方便又快速。
>![](https://i.imgur.com/F0TDGzA.png)
  **↑** 左下角記得選C++，如果要自訂輸入請點![](https://i.imgur.com/mKORutu.png)

<br>

寫好了就按下![](https://i.imgur.com/eOrd2sD.png)就會看到結果了
>![](https://i.imgur.com/9s3947l.png)


---

## 第一個程式-- Hello World
<br>

這個程式常為初學者的第一個程式

```c++
#include <iostream>

using namespace std;

int main(){
    cout<<"Hello World";
    return 0;
}
```

<br>

首先看這兩行:

```c++
#include <iostream>

using namespace std;
```

```#include```就是引入的意思，引入標頭檔```iostream```(input / output stream的縮寫)，很多新手會問什麼是標頭檔，標頭檔就像字典一樣，告訴電腦這個字是什麼意思，假如今天給你一個英文單字Apple，但你沒學過英文所以不知道是什麼意思，但我再給你一本字典讓你去查，你就會知道這個字叫蘋果，標頭檔就像那個字典，讓電腦知道你要他幹什麼。

<br>

```using namespace std;```這段話就是在告訴電腦我今天要用的東西在```std```(標準函數庫)這個空間裡面，就像字典厚厚一本同一個字有可能有不同的意思，所以我們告訴電腦我們要的東西在```std```這個範圍裡面，就不容易搞錯我們的意思了。

<br> 

再來看到主函式```main```:
```c++
int main(){
    ...
    return 0;
}
```
這是 C++ 程式中，程式的進入點，就是告訴電腦要從這裡開始執行，整個函式用大誇號包起來，前面的```int```表示函式結束時會回傳整數(Integer)，最後一行```return 0;```，也就是程式結束回傳```0```，通常回傳```0```表示程式正常結束，當然也可以回傳其他數字讓其他程式做進一步的處理，而在標準 C++ 中沒有指定```return```，```main```預設也會回傳```0```。

<br>

接下來看```main```中的程式碼:
```c++
cout<<"Hello World";
```
C++中每行都要用```;```表示結束，```cout```是表示輸出，而```<<```是輸出的運算子，更詳細的觀念會在後面介紹，簡單來說```cout<<"Hello World";```就是把```Hello World```輸出在銀幕上。
<br>

在編譯器看到就會長這樣
![](https://i.imgur.com/64uwANu.png)

---
**這章就先到這邊，下一章會開始介紹基本的輸出輸入。**
