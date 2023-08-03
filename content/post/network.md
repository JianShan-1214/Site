---
title: "網路概論"
date: 2022-08-01T01:21:00+08:00
slug: "networking-introduction"
tags: ["雜學"]
keywords: ["網路","networking"]
---

## 什麼是網路

![](https://i.imgur.com/TcGKwXW.png)

1. 通訊連接 (communication links)
    *  使用者 (client) / 主機端 (server)
    *  無線/有線
 
2. 網路核心 
    * Packet Switches (封包交換)
    > 網路的交換是將東西切成一個一個小小的區塊(稱為封包)來進行傳輸


3. 網路構成組件
    * Routers (路由器)
        * 閘道(GateWay)：電腦連上網際網路要先連上 Router 閘道可以說是 Router 和電腦連接的 IP
    * Switches (交換器) 

## ISP(Internet Service Providers)
> 網路服務供應商

 ![](https://i.imgur.com/3cejadC.png)


## 通訊協定(protocol)
>定義封包格式與交換方式

![](https://i.imgur.com/PRJrtgq.png)

1. DNS 將 URL 轉換成實際的 IP，Browser 將 IP 包成一個 Request 送出去。
1. Request 透過 Internet 傳送到 Server 。
1. 收到 Request 的 Server 會跑去 Data center 撈取資料。
1. 將撈取到的資料透過 Internet Response 回去。
1. Browser 解析資料並印於 Browser 上。

### Internet Protocol Stack
![](https://i.imgur.com/5TDeZg5.png)

* 應用層 Application：HTTP、HTTPS、FTP、DNS…
* 傳輸層 Transport：TCP、UDP
* 網路層 Internet：IPv4、IPv6
* 網路訪問層 Network Access：乙太網路、WiFi

![](https://i.imgur.com/gaHiRLf.png)


### IP Address
在這個協定裡面有一個 IP Address ，就是我們在網路上的網址，別人可以從這個地址訪問到你的電腦。有分為以下幾種類型：

* 固定 IP：不會變、固定的 IP，基本上公司企業及伺服器都是使用固定 IP，這樣才能確保使用者可以連上伺服器。
* 浮動 IP：在每次連上網的時候 IP 位置都會不一樣，普通的使用者跟家用電腦大部分都是浮動 IP。
* 虛擬 IP：僅能使用於內部網路（或者說是區域網路內），外網是連不上的。
:::info
通常 192.168 或 10.0 開頭的，都是虛擬 IP。
localhost 就是 127.0.0.1 這是特殊的 IP 代表自己的電腦。
:::
#### IP 是如何計算的 (待補)
![](https://i.imgur.com/TtuTvQd.png)

### DNS(Domain Name System)
* 將「域名（Domain）」就是「網址」轉換成實際的 IP
* 就像是電話簿一樣，上面會記載著每個人的電話是多少，你只需要拿著名字去問就可以找到電話


### HTTP(HyperText Transfer Protocol) / HTTPS(HyperText Transfer Protocol Secure)
* 超文本傳輸協定
* 由於 HTTP 一直都有安全性的問題，因此 HTTPS 就是基於 HTTP 並利用 SSL/TLS 將資訊加密封包的另一種更安全的協定。

#### HTTP 狀態碼 Status Code
> 以表示網頁伺服器響應狀態的3位數字代碼
* 1XX ─ 1 開頭的狀態碼：你等等 （client 端需要做一些處理）。
* 2XX ─ 2 開頭的狀態碼：成功。
    * 200 OK 就是完全順利成功
    * 204 No Content 就是成功但沒有回傳任何訊息（使用 delete 時）。
* 3XX ─ 3 開頭的狀態碼：去其他地方（重新導向）。
    * 301 Moved Permanently ：就是這個網域永久的被移到其他位置，下次再度使用 get 時，會直接導向另一個網域。
    * 302 Found（Moved Temporarily）：是暫時被移到其他位置，下次使用 get 時，一樣會導到此網域。
    * 304 Not Modified：東西跟之前長一樣，可以從快取拿就好。
* 4XX ─ 4 開頭的狀態碼：你慘了（client 端錯誤）。
    * 400 Bad Request：請求語法錯誤、或資源太大…等等。
    * 401 Unauthorized：未認證，可能需要登入。
    * 403 Forbidden：沒有權限。
    * 404 Not Found：找不到資源。
    * 408 Request Timeout : 請求超時。可再隨時提交一次請求且無須修改。
* 5XX ─ 5 開頭的狀態碼：我慘了（server 端錯誤）。
    * 500 Internal Server Error：通用的伺服器出錯。（搶票時常見）
    * 503 Service Unavailable：伺服器暫時無法處理。

### UDP(User Datagram Protocol)
* 不保證資料移動傳到對方，重視即時性和傳送速度
* 例如：串流媒體、即時多人遊戲，網路電話。

### TCP(Transmission Control Protocol)

* 大部分的網路協定都是建立在 TCP 上面，因為是比較「可靠」的方式。
* TCP 三次握手（Three-way handshake）
![](https://i.imgur.com/bqPxMr4.png)

三次握手如果用傳紙條比喻的話大概會是這樣
小明：安安，在嗎？
小美：在阿，你好。
小明：收到，太好了！

![](https://i.imgur.com/p3mxfPZ.png)


## Port
* 連接埠、端口
* 簡單來說 IP 是電腦的地址 Port 就是軟體的地址，為了區分並接收同個電腦（ IP 位址 ）的不同服務，IP 就像寄信時候的地址而 Port 就是上面的收件人告訴你要給這個家的誰。

## API(Application Programming Interface)
API 是應用程式介面，它定義了應用程式之間如何互相通訊。API 允許不同的軟體產品互相交流，使得每一個軟體不必擔心如何實現其他軟體的功能。

在網路中，API 最常被用在客戶端和伺服器之間的溝通。客戶端可以透過 API 向伺服器請求特定的資料或功能，而伺服器則會回應這些請求。

APIs 在網路程式設計中最常被使用的方式是透過 HTTP 方法，這些方法包括 GET、POST、PUT、和 DELETE，這四種方法分別代表讀取(Read)、建立(Create)、更新(Update)、和刪除(Delete)資料的操作，也被稱為 CRUD。

### HTTP Method

1. `GET` - Read：這個方法用來獲取資訊。例如：`GET /user/{id}` 這個 API 的用途是獲取 id 為 `{id}` 的使用者的資訊。

2. `POST` - Create：這個方法用來創建新的資訊。例如：`POST /user` 這個 API 的用途是創建一個新的使用者，並將新使用者的資訊作為請求的內容。

3. `PUT` - Update：這個方法用來更新已存在的資訊。例如：`PUT /user` 這個 API 的用途是更新一個已存在的使用者，並將要更新的使用者資訊作為請求的內容。

4. `DELETE` - Delete：這個方法用來刪除已存在的資訊。例如：`DELETE /user/{id}` 這個 API 的用途是刪除 id 為 `{id}` 的使用者。

注意：上述的 `{id}` 是一個變數，代表使用者的唯一識別碼。

這些 HTTP 方法讓我們可以從客戶端進行 CRUD 操作，並與伺服器進行資料交換。透過這種方式，我們可以輕鬆地建立、讀取、更新和刪除伺服器上的資料，而不需要直接訪問伺服器的資料庫。