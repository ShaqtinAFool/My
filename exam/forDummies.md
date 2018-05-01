<!-- MarkdownTOC -->

- OSI
- IEEE 標準
- 通訊協定
	- 應用層
	- 傳輸層
	- 網路層
	- 資料連結層
- 駭客

<!-- /MarkdownTOC -->

---

# OSI
1. 應用層
	- 定義應用程式如何進入應用層的溝通介面，將資料接收或傳送給應用程式，最終展示給使用者。
1. 展現層
	- 將應用層的資料格式轉換(或者是重新編碼)成為網路的標準格式，包括資料的加解密，然後再由傳輸層...等的協定來進行處理。
1. 會議層
	- 確定網路服務建立連線的確認。
	- 定義了兩個位址的連線通道之連接與掛斷，確定網路服務建立連線的確認。此外，亦可建立應用程式之對談、提供其他加強型服務如網路管理、簽到簽退、對談之控制等等。
1. 傳輸層
	- 這層定義了發送端與接收端的連線技術(如 TCP, UDP 技術)。
	- 同時包括該技術的封包格式，資料封包傳送、流程控制、傳輸過程的偵測檢查與復原重新傳送...等等，以確保各個資料封包可以正確無誤的到達目的端。
1. 網路層
	- 封包能否到達目的地的路由 (route) 概念了！
	- 決定資料的路徑選擇和轉寄，將網路表頭加至資料包，以形成封包。
	- 定義電腦之間的連線建立、終止與維持、資料封包的傳輸路徑選擇等等。
1. 資料鏈結層
	- 偏軟體部分: 由邏輯連結層(logical link control, LLC)所控制，主要在多工處理來自網路層的**封包**資料並轉成 MAC 的格式，負責的工作包括訊息交換、流量控制、壅塞問題的處理等等。
	- 偏硬體部分: 主要負責的是 MAC，我們稱這個資料包裹為 MAC **訊框**， MAC 是網路媒體所能處理的主要資料包裹，這也是最終被實體層編碼成位元串的資料。MAC 必須要經由通訊協定來取得媒體的使用權， 目前最常使用的則是 IEEE 802.3 的乙太網路協定。詳細的 MAC 與乙太網路請參考下節說明。
1. 實體層
	- 在區域網路上傳送資料框，它負責管理電腦通訊裝置和網路媒體之間的互通(0、1)。
	- 包括了針腳、電壓、線纜規範、集線器、中繼器、網卡、主機介面卡等。

---

# IEEE 標準
- IEEE 802.3: 規定了包括實體層的連線、電子訊號和介質存取層協定的內容。
- IEEE 802.4
- IEEE 802.5
- IEEE 802.11
- IEEE 802.15
- IEEE 802.22

---

# 通訊協定
## 應用層
- HTTP，超文本傳輸協定(**H**yper**T**ext **T**ransfer **P**rotocol): 超文字傳輸通訊協定是一種通訊協定，用於在全球資訊網上載輸或傳遞資訊。它是一項專利的開放式 Internet 通訊協定，其目的在於提供一種發行和接收 HTML 網頁的方法。
- HTTPS，超文字傳輸安全協定(**H**yper**T**ext **T**ransfer **P**rotocol **S**ecure): HTTPS 開發的主要目的，是提供對網站伺服器的身分認證，保護交換資料的隱私與完整性。

- BGP，邊界閘道器協定(**B**order **G**ateway **P**rotocol): 通過維護 IP 路由表或『字首』表來實現自治系統之間的可達性，屬於向量路由協定。

- DHCP，動態主機設定協定(**D**ynamic **H**ost **C**onfiguration **P**rotocol): 用於內部網路或網路服務供應商自動分配 IP 位址給用戶。
- DCCP，數據擁塞控制協議(Datagram Congestion Control Protocol): 一個可以進行擁塞控制的非可靠傳輸協議，並同時提供多種擁塞控制機制，在通信開始時由用戶進行協商選擇。

- FTP，檔案傳輸協定(**F**ile **T**ransfer **P**rotocol): 進行檔案傳輸的一套標準協議，使用客戶/伺服器模式。

- IGMP，網路群組管理協定(**I**nternet **G**roup **M**anagement **P**rotocol): 用於管理網路協定多播組成員的一種通訊協定，IP主機和相鄰的路由器利用IGMP來建立多播組的組成員
- IMAP，網際網路資訊存取協定(**I**nternet **M**essage **A**ccess **P**rotocol): 本地郵件用戶端存取遠端伺服器上的郵件。
	- POP，郵局協議(Post Office **P**rotocol): 用戶端遠端(離線)管理在伺服器上的電子郵件。

- LDAP，輕型目錄存取協定(Lightweight Directory Access Protocol): 透過IP協定提供存取控制和維護分散式資訊的目錄資訊。

- NCP，網絡控制協議(Network Control **P**rotocol)
- NTP，網路時間協定(Network Time **P**rotocol): 在資料網路潛伏時間可變的電腦系統之間通過封包交換進行時鐘同步的一個網路協定。
- NNTP，網路新聞傳輸協定(Network News Transport Protocol): 用於閱讀和張貼新聞文章到 Usenet 上的 Internet 的應用協定。

- PPP，點對點協定(Point-to-Point **P**rotocol): 在兩節點間建立直接的連線，並可以提供連線認證、傳輸加密以及壓縮。

- RIP，路由信息協議(**R**outing **I**nformation **P**rotocol): 
- RTP，即時傳輸協定(Real-time Transport **P**rotocol): 
- RTSP，即時串流協定(Real Time Streaming **P**rotocol): 專為娛樂和通訊系統的使用，以控制串流媒體伺服器。

- SIP，對話啟動協定(Session Initiation Protocol): 用於建立、修改和終止包括影片、語音、即時通訊、線上遊戲和虛擬現實...等多種多媒體元素在內的互動式用戶對談。
- SMTP，簡單郵件傳輸協定(Simple Mail Transfer Protocol): 

- TCP，傳輸控制協定(Transmission Control **P**rotocol): 一種連接導向的、可靠的傳輸層協定。
- TLS，傳輸層安全性協定(Transport Layer Security): 採用主從式架構模型，用於在兩個應用程式間透過網路建立起安全的連線，防止在交換資料時受到竊聽及篡改。
- TFTP，簡單檔案傳輸協定(Trivial File Transfer **P**rotocol)
- Telnet: 使用虛擬終端機的形式，提供雙向、以文字字串為主的命令列介面互動功能。

- UDP，用戶資料報協定(User Datagram **P**rotocol): 提供資料的不可靠傳遞。

- XMPP，可延伸訊息與存在協定(Extensible Messaging and Presence Protocol): 一種以XML為基礎的開放式即時通訊協定。

## 傳輸層


## 網路層
- IP，網際網路協定(Internet **P**rotocol): 用於封包交換資料的一種網路協定。
- ICMP，網際網路控制訊息協定(**I**nternet **C**ontrol **M**essage **P**rotocol): 用於 TCP/IP 網路中傳送控制訊息，提供可能發生在通訊環境中的各種問題反饋。

- IPSec

## 資料連結層
- ARP，位址解析協定(**A**ddress **R**esolution **P**rotocol): 通過解析網路層位址來找尋資料鏈結層位址的一個協定。
- RARP，反向位址解析協定(**R**everse **A**ddress **R**esolution **P**rotocol): 通過解析尋資料鏈結層位址來找網路層位址的一個協定。
- NDP
- L2TP
- DSL
- ISDN
- FDDI
- PPP

---

# 駭客
