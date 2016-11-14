# Computer_Network
-	[OSI](https://github.com/cjkjackee/Computer_Network#osi) 
-	[Five Layer](https://github.com/cjkjackee/Computer_Network#five-layer)
-	[信號](https://github.com/cjkjackee/Computer_Network#信號)
-	[Multiplexing](https://github.com/cjkjackee/Computer_Network#multiplexing)
-	[Spread Spectrum](https://github.com/cjkjackee/Computer_Network#multiplexing)
-	[transmission media](https://github.com/cjkjackee/Computer_Network#transmission-media)
-	[LAN](https://github.com/cjkjackee/Computer_Network#lan)
-	[ethernet LAN](https://github.com/cjkjackee/Computer_Network#ethernet-lan)
-	[supplementary：security](https://github.com/cjkjackee/Computer_Network#supplementarysecurity)

# OSI
1.	physical Layer
2.	Data link layer
	*	功用：除錯
3.	Network layer
	*	功用：routing，flow control
	*	就算是頻寬無限大還是需要進行flow control 防止不正當的使用者

4.	Transport Layer
	*	功能：provide reliable link，重組信息
	*	爲什麼data link layer 已經進行錯誤重傳了，這層還要進行一次？
		因爲可能是router crash，或wire壞掉。

5.	Session Layer（實用中沒有用到）
	*	功能：連接的權限，連接路徑
	*	大多數時間不需要建立路徑（網絡是以packet solution的方式），所以就直接不需要

6.	Presentation Layer (實用中沒有用到)
	*	功能：加密，壓縮，轉換編碼;
	*	因爲不是很重要（理由同上一層），所以就直接不做
7. 	application Layer

# Five Layer

+	Network Access Layer
	*	因爲有不同的標準（第二層一下），但因爲第三層有相同的協定（IP）所以可以溝通
+	Internet Layer
	*	可以做routing的就是router
	*	router不需要到第四層以上
+	Transport Layer
	*	reliable end to end transfer

# 信號
+	analog-類比信號
	*	信號是連續的
+	digital-數位信號
	*	信號是離散的

analog的傳輸方式
+	ASK
	*	傳輸距離太遠，信號會減弱。
+	FSK
+	PSK

# Multiplexing
+	frequency-division multiplexing (FDM)
	*	不同頻率來區分
+	time-division multiplexing (TDM)
	*	將時間分成不同的time slot， 不同的time slot傳不同的東西
+	code-division multiplexing (CDM)
	*	以特殊的編碼方式來區分（同time同frequency）
	*	其他的編碼方式，對只會這一種編碼方式的來講只是一個background
		noise
	*	只要background noise 不太大，掩蓋原本的，基本上不會有影響

#Spread Spectrum
+	讓攔截通訊（interception）和幹擾，破壞通訊（jamming）變得困難
+	Frequency-Hopping
	*	不同的時間點收不同的frequency
	*	有同樣的hopping pattern 就收得到資料
	*	有兩個資料，只要有不同的hopping pattern就不互相影響
	*	IEEE 802.11 300ms 跳一次
+	Direct Sequence
	*	把資料跟另外一串以知的bit 做exclusive or 再送出

#transmission media
+	guided media
	*	twisted pair - 雙絞線
	*	coaxial cable - 銅軸電纜
	*	optical fiber - 光纖
	
+	unguided media
	*	infrared(IR) - 紅外線:  
		會被亮色的物體反射  
		在室外會被陽光幹擾，所以需要加大功率，但是加大功率卻會傷害眼
		睛
	*	Microwave radio :  
		長距離  
		ISM（industrial，scientific，and medical） bands  
		美國制定的任何人在美國都可以用的頻段  
		915MHz  
		2.4MHz  
		5.8MHz

# LAN
-	organization of IEEE 802
	*	802.1
	*	802.2 LLC
	*	不同的physical和mac layer 有不同的號碼（802.X）但LLC只有802.
		2,之後會講爲什麼
	+	LLC 在 MAC的上面
-	Ingredient of a LAN
	*	Topology ： 連接網絡的方法
	*	Transmission medium
	*	Medium Access Control (MAC) ： 不同的transmission medium 有
		不同的mac

LAN topology
-	bus: 
	*	share medium
	*	一個人在傳所有人都知道
	*	問題：會有collision,所以需要有MAC
	+	在末端放上terminator，資料到了末端就會被消除，不需要考慮如何
		消除資料
-	tree
	*	邏輯上與bus相似
	+	signal要多強？  
		把功率加強  
		在網絡上加上repeater ：重復發送信號，所以repeater通常是雙向
-	Ring
	+	有兩種標準：802.3（contention） 和802.5（token）
	+	802.3 還有很多人在用，802.5 現在很少人在用了。因爲如果token
		不見了，網絡就crash了
-	star
	*	邏輯上與bus相似
	+	hub 和 repeater 的差異：repeater只有雙向，hub有multiport
	+	repeater,hub第一層，router第三層
	+	header hub （HHUB）

以上是最常用的4種

MAC
-	polling
	*	類似開會，主席問誰要發言，如果有多人，只選其中一個
-	round robin
	*	輪流
-	reservation
	*	預約制
-	contention
	+	想傳就傳
	+	當傳輸量少的時候，碰撞的幾率小，如brusty network，這個方法的
		效率就很好。

LAN hub and switch
-	hub
	+	一個時間點只能有一個station傳
	+	雖然跟shared medium bus 相似，但是還是有好處：當一個點出問題
		可以直接disable它
-	Lan switch
	+	lan switch跑到第二層，看到mac address 知道要傳到那個電腦
	+	devices不用做出什麼改變throughput就可以增加
	+	scales： 可覆蓋範圍，例：有一種方法2臺電腦效能很好，數量一多
		效能就不好，就是scale不高
	+	有storge and forward 和 cut through 兩種
	+	storge and forward： 資料進來存下來了，在傳出去，好處：錯誤
		率低，壞處：慢
	+	cut though： 資料header一進來就知道要往那裏送，好處：快，壞
		處：錯誤率較高
-	adaptive switch
	+	開始是用cut through的方式傳
	+	計算 error rate
	+	如果error rate 太高，換成用storge and forward 的方式傳

Protocol Reference model
-	LLC:problide one or more service access points (SAPs)

LLC
-	802.2的LLC不會做error detection
-	LLC會以爲雙方是互相對聯的，實際上是下面一層MAC解決了鏈接的問題

two level of addressing
-	MAC address：表示硬體的位置，（理論上）不會重復, trailer:做error detection
-	LLC address：

Generic MAC Frame
-	MAC control —— header
-	Destination MAC address —— header
-	Source MAC address —— header
-	LLC PDU —— payload
-	CRC —— trailer

bridge 
-	跑到第二層
-	不會改變資料
-	與router的不同點
	+	bridge在第二層，router在第三層
	+	routing方法不同
-	與lan switch差異
	+	都跑到第二層
	+	bridge 都是storge and forward，lan switch 有兩種
	+	lan switch有特別的設計，通常會快很多

networking device
-	第一層：repeater，hub
-	第二層：bridge，lan switch
-	第三層：router
-	第四層：gateway
	+	gateway：相連兩種不同的網絡

# ethernet LAN
802.3
-	define 
	+	physical layer
	+	MAC layer：CSMA/CD —— contention的方式

precursors of CSMA/CD
-	pure ALOHA
	+	方式：A傳給B，等待B回傳A讓A知道收到，如果有一段時間沒回復，A
		就重傳
	+	不一定同時傳輸才會碰撞，只有重疊到就會碰撞
-	Slotted ALOHA
	+	同是pure ALOHA 的方式，但增加TDM，每個time slot開始的時候才
		能傳，所以碰撞的時候只有兩個同時傳的時候。

CSMA(carrier sense multiple access)
-	carrier sense：每次要傳的時候都去check傳輸媒介
-	類似講話的時候先聽一下有沒有人講話，沒有人在講話才講話
-	還是會碰撞，碰撞情況：
	+	兩邊聽的時候發現沒有人傳，兩邊同時傳
	+	一個先傳，但是因爲delay，另一邊聽的時候以爲沒有人傳，然後傳
-	又分三類：
	1.	non-persistent
	2.	1-persistent
	3.	p-persistent //p代表幾率
	4.	相同點：碰撞的時候，back off
-	non-persistent
	+	類似家裏有多臺電話，當拿起一只發現有人在講話，就掛掉，等過一整子再聽
	+	當放下的那一瞬間，另一方傳完了，還是會等一段時間才聽  
		好處：碰撞率會降低，因爲聽到有人傳會過一下再聽，這段空檔內有人剛好拿起來聽到沒人傳，他就傳，前一個人回來聽又聽到有人傳又再等。  
		壞處：浪費時間
-	1-persistent
	+	聽到沒有人傳，一定會傳
	+	優點：資源使用率高
	+	缺點：因爲是一直等到別人不傳馬上傳，只要有兩人以上同時在聽，就會碰撞，碰撞率高。
-	p-persistent
	+	聽到沒有人傳，p的幾率會傳，1-p的幾率不傳
	+	優點：與1-persistent相同，可以避開1-persistent的碰撞
	+	缺點：碰撞率高。
-	performance
	+	當np>1，就可能會碰撞，n：機械數量，p：傳輸幾率
	+	碰撞後就會再和新的要傳輸的人碰撞
	+	throughput will drop to zero
	+	所以，np最好小於1
	+	所以p要set很小，傳輸等待的時間會要更久

CSMA/CD （CD：Collision Detection）
-	當你發現已經碰撞了，就不要傳了
-	會花多久會detect collision
	+	最壞的情況下，2×propagation delay
-	persistence
	+	IEEE 802.3 uses 1-persistent
	+	collision detection和線的長度有關
	+	Binary exponential backoff：  
		如果傳輸失敗，等2^n的時間單位再傳，在傳了嘗試了16次之後放棄
	+	新傳的人成功率高於失敗重傳的人

carrier sense && collision detection
-	higher voltage swings == jamming signal
-	IEEE802.3 最長的cable 只能500m
	+	signal會衰減
	+	collision detection和max（propagation deley）有關，而max（propagation deley）和cable的長度有關。

# 10-Mbps Ethernet
-	自己看

# collision domain
-	用hub||repeater鏈接collision 會互相影響，爲了分開他們，把hub||repeater換成第2層以上的就可以把他們分開。

# supplementary：security
encryption
-	沒有加密的文件：plaintext，cleartext
-	加密後的文件：ciphertext

two categories
-	secret-key algorithm
	+	加密和解密用同一把鑰匙
	+	如：你家大門
-	public-key algotithm
	+	加密和解密用不同的鑰匙
	+	如：交大宿舍的房門

### secret key
substitution ciphering
-	把一個字換成另一個字
-	caesar cipher：shift alphabet

DES （data encryption standard）

AES：Advance encryption standard

### public key
PGP：pretty good privacy（可下載軟體）
有public key 和 secret key
-	public key ： 加密
-	secret key ： 解密

RSA
-	用兩個很大的質數相乘，得到public key

MAC：message authentication code
-	資料借由secret key 和 mac 演算法進行演算，的到mac，附加在原本資料，在另一端的到了附加mac的資料後在以相同的secret key 以mac演算法進行演算，如果算出來的mac與原本的mac一樣則無問題，否則data有問題
-	檢查資料有沒有被串改：data integrity
-	電話公司在用，爲了判斷身份
-	常用的演算法：hash function

hash function
-	unkeyed hash
	-	message digest 5 （MD5）： linux傳帳密是用這個，已被破解

# wireless LANs

# 作業

+	ack 
	*	1端送data給2端，2端如果收到了回傳一個東西給1端，讓1端知道2端已經收到了

# 注
-	IETF： 制定標準的機構，網絡架構，TCP
-	IEEE： 制定標準的機構，最多人用他們制定的LAN的標準（只要是802的幾乎都是LAN的標準）
-	第二層的封包叫frame， 第3層叫packet，第四層叫segment，所有統稱PDU
-	throughput：傳多少進去，傳多少出來
-	KISS：keep it simple and stupid
-	SAP: service access point
-	repeater 和 hub 把兩個10公尺接起來==自己拉一條20公尺的線
