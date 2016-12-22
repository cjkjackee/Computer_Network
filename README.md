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
		2.4GHz  
		5.8GHz

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
-	802.11
	-	在1997年制定出來，但wireless的設備之前就有了
	-	只定義到第二層
-	802.11i
	-	安全
-	802.11e
	-	QoS （quality of service）
	-	802.11 跟 802.3一樣，不能確定越早出去的越早到，802.11e是爲了改善這件事
-	BSS：basic service set
	-	subset
-	ESS：extended service set
	-	最大的那一圈
-	STA：station

infrastructure
-	AP（access point）是一個bridge
-	傳資料一定要通過AP
-	離AP越近傳輸率越快，反之亦反
-	會有一個distribution System
	-	把多數的BSS連在一起形成ESS

Ad Hoc
-	又稱independent mode
-	direct communication ： STA直接對連
-	資料可以互傳
-	如果信號不夠強，可以通過其他人幫忙傳（dynamic routing）

802.11 protocol entities
-	station management
	-	聯系MAC和phy layer
-	MAC layer management
 	-	synchronization
	-	power management
	-	roaming：從AP1到AP2轉換
	-	MIB（management information base）：遠端管理設備用的資料
-	PLCP （phy layer 上層sublayer）
	-	SAP
	-	function for carrier sense：看設備有沒有在傳資料
- PMD （phy 下層sublayer）
	-	modulation and encoding ： 把信號轉成資料
-	MAC entity
	-	basic access
	-	fragmentation ： 把資料切成小塊
	-	encryption

802.11 service
-	association：連上網絡
-	reassociation：離開後重新臉上網絡/ 從一個BSS換到另一個BSS
-	disassociation：離開網絡
-	authentication：認證
	-	shared key：只要有密碼就可以用
	-	proprietary authentication extensions：自定義的認證方式，如：網頁認證
-	privacy
	-	一開始定義的加密方法WEP（wired equibalent privacy）
	-	station to station 的加密：所以如果資料經過AP，加密的就只有station到AP和AP到station那一段
	-	只有payload有加密

802.11 Protocol Architecture
-	有兩個MAC
-	PCF
	-	protocol：polling
-	DCF
	-	protocol：CSMA/CA

MAC
-	一個mac可以support多個physical layer
-	DCF（distributed coordination function）
	-	contention algorithm
-	PCF（point coordination function）
	- optional

Inter Frame Space（IFS）
-	SISF（short inter frame space）
	-	transmitor 和 receiver 同一時間只有一個在工作
	-	要傳的時候transmitor要打開，打開需要時間
	-	硬體運作需要的時間
-	PISF（PCF IFS）
	-	polling需要用的時候需要的時間
	-	SIFS + setup time
-	DIFS（DCF IFS）
	-	SIFS + 兩個setup time

### DCF
-	collision detection (CD) 不容易做
	-	因爲要邊聽邊傳
-	collision avoidance （CA）代替
	-	預防有collision發生
	-	聽到IDLE不傳，繼續聽到DIFS，DIFS沒有人傳才傳
	-	防止前面已經有人傳了，造成的碰撞
	-	還是有可能碰撞：兩個機器同時聽到IDLE，同時在等DIFS，同時傳
	-	聽到medium是busy，聽到DIFS也不穿，繼續等contention window（0～7個time slot隨便選），如果還是沒有人傳就傳，有人傳就停下來，等medium IDLE 了繼續聽完剩下的contention window，如果聽完剩下的contention window還是沒有傳出去，在從0～15選一過再聽，再不行，重復，知道號碼0～255試了16次，就不傳。
	- 因爲0～7歲隨便選，選到相同的幾率很小，減少collision
	-	傳成功的人要等一個contention window，防止傳成功的人，一直傳下去
	-	可能碰撞幾率：剩下的contention window都相同
	-	大部分時間都在聽：因爲receive比較省電，transmit比較耗電，一直在receive好過一直collision，一直transmit
	-	PHY layer 有CCA（clear channel assessment）會做carrier sence

#### CSMA/CA + ACK protocol
-	只用於unicast（一對一傳輸）
-	receiver 在受到資料後，CRC（作用：error detection）是對的，就回傳ack
-	沒有收到就從傳
- destination 收到的時候要等SIFS的時間才ack
	-	確定資料沒有錯
	-	要從receive換成transmit需要時間，而需要的時間正好是SIFS
-	ACK一定會傳成功
	-	要回傳ack代表當時只有source一個人在傳
	-	雖然要等SIFS但是SIFS比所有人要等的時間都短，所以一定是會回傳。

#### hidden terminal
-	一臺存在的機器，但是另外一臺機器不知道它的存在。
-	CSMA/CA會有問題
	-	A，B，C三臺機器，A,C互相不知道對方的存在（訊號互相覆蓋不到對方，詳細圖看講義），A，和C,都想要傳資料給B，假設A先傳，C因爲不知道A的存在，等完DIFS後就傳給B，如果A和B還沒傳完，就會collision

#### virtual sensing
-	爲了解決hidden terminal的問題
-	同上面的假設，A在傳的時候會發出RTS（request-to-send），告訴範圍內的人要傳資料，要傳多久，B如果有收就會發出CTS（clear-to-send），告訴範圍內的人它要收資料，要收多久，C收到CTS就知道B在接收資料
-	NAV （net ）
-	流程（詳細看講義）
	1.	source要傳資料，先聽，聽到是IDLE，等DIFS，然後傳RTS
	2.	destination收到RTS，傳出CTS
	3.	source收到CTS，傳出資料
	4.	destination收到資料，傳出ACK
-	NAV（RTS）就是2-4的時間，這段時間內不能傳

### PCF
superframe
-	有兩個部分：
	-	contention-free period
	-	contention period
-	就是有兩個不同的時間有兩個不同的傳輸方式，例：20分鍾polling，80分鍾CSMA/CA
-	假設過了一百分鍾還沒傳完，如剩下20分鍾，讓它傳完，PCF時間不縮短，縮短DCF的時間
-	兩臺機器一臺用PCF，一臺用DCF，用PCF的會搶贏

### Scanning
-	passive scanning
	-	AP會發出beacon（AP發出來的image，告訴設備它的存在）
-	active scanning
	-	設備主動發出訊號，等probe response（AP的回復）

無線網絡有三種模式
-	Tx
	-	transmit
	-	最耗電
-	Rx
	-	receive
-	sleep
	-	最省電

### roaming approach
-	SNR(signal noise ratial) = S/N
-	SNR低於40%的時候尋找可以用的另一個AP
	-	低於40%就找的原因：可能會有找不到的風險
-	另一個AP的SNR高於50%的時候就連上
	-	不馬上換的原因：可能下一個時間點另一個AP的SNR不一定會上升
	-	乒乓效應：馬上換可能會一直交換AP

### power management
-	能進sleep就盡量sleep
-	過了一段時間聽一下，看有沒有東西要收
-	如果在sleep mode，有人送東西給你，AP會收起來
-	在起來聽的時候AP會告訴你有人要傳東西。
-	TIM（traffic indication map）：一個map用來表示有人有資料要送給station

### 802.11b
-	傳輸率最高爲11Mbps
	-	離AP太遠可能會講到1Mbps

### 802.11a
-	2.4GHz的幹擾太嚴重
-	用5.8GHz

### 802.11n
-	improving 802.11a && 802.11g
	-	54Mbps～600Mbps
-	增加了 multiple-input multiple-output （MIMO）
	-	多根天線
	-	最好相隔45度，效能最好

### 802.11e
-	改善MAC quality of service（QoS）
-	利用SIFS和contention window的特點就可提高一個人的成功率
	-	SIFS 短，成功率高
	-	contention window 越長成功率越低
- enhanced distributed channel access（EDCA）
	-	改善DCF
	-	增加了AIFS，有四個等級，最短的AIFS==DIFS
	-	contention window size relies on QoS parameter
	-	可以傳成功後不用等contention window繼續傳，但有限制次數，次數defined by transmission opportunity（TXOP）

### Wi-Fi（Wireless Fidelity）Certification
-	Wi-Fi，不是一種網絡，是一種certification
	-	是802.11網絡的認證

# IP
-	IP：internet protocol
	-	第三層的運作方式
-	ip功能：
	-	addressing
	-	route packets
	-	fragmentation

### IP address
-	ip address 代表host的 ID 和 location
-	要代表location的理由：routing比較容易，之要找netid（前幾個bit）
	-	router不用存全世界的IP來對
- IP只有在特定的subnet才能用

### format of IPv4 Address
-	有class A~E
-	分class理由：
	-	每個人要連上網絡的機器都不一樣
-	class A：第一個bit是0，有2^24個hostid
-	class B：前兩個bit是10，最多有2^16個hostid
-	class C：前三個bit是110,最多有2^8個hostid
-	class D：前四個bit是1110
-	class E：前四個bit是1111
-	subnetting
	-	爲了區分，在hostid裏切一段，成爲subnettid
	-	好處：router不用存完所有的hostid，可依據subnetid先送往subnetid所在的地方，再送給hostid，如地址，如果沒有分區，郵差要記完所有的地方，有分區，就可先送到各區，再送
	-	subnet mask：決定subnet要切在那裏，前面都是1,0的地方是hostid
	-	如：255.255.255.0 前面16個bit是netid（class B的netid有16bit），8個bit是subnetid，8個bit是hostid
	-	考試不一定要換10進位

### supernetting
-	多筆address都送到同一個地方
	-	（192.168.48.0,3）代表192.168.48.0,192.168.49.0,192.168.50.0 都是送到同一個地方
	- 分散就不行了
	-	概念上是這樣，實做不同
-	實際上：
	-	10/8 == 10.0.0.0/8（前8bit不變，後面的都可變）,代表有2^（32-8）個IP address，代表10.0.0.0～10.255.255.255都是同樣的地方
	-	128.211.168.0/21, "/21"是slash notation1
-	supernetting == classless addressing

### IPv4 header （圖看講義）
-	payload 不固定所以要有total length
-	time to live ： packet 可能一直routing，沒有傳出去，當過來一定時間就丟掉，不是真的算packet的live time，而是規定packet被router處理過多少次
	-	真正的單位：hop count
- protocol：這個packet用的protocol，udp還是tcp
-	header checksum：資料是否修改，出錯，的出錯機制的訊息
-	identifier：有100個ip的packet是同一個的，identifier就是去儲存他們是否是同一個ip的packet
-	flags：有100個packet，不能確定他們是誰會先到，所以flag就儲存他們的順序，位置，
	-	flag==1,最後一個packet
-	fragment offset： packet的位置信息（同上）
-	option && padding：
	-	一定要4byte的倍數
	-	padding的功能：options不一定是4的倍數，padding就是塞一些無用信息給進去，或者是沒有option，隨便亂塞東西，讓攔截的人不知道是什麼

### IP routing
1.	先查routing table 找到符合的IP address
2.	查routing table，找到符合的net id
3.	都查不到，送default

在routing的時候如果header的destination address和routing table不符合，header會不會改？
-	不會，source ip address 和 destination ip address 都不會變
-	利用外面第二層layer的MAC header，這層的source MAC address就是這段期間內送資料的人，destination MAC address這段時間內要收資料的人。
-	送的方法
	-	host 送出來會問大家要送給誰
	-	router收到就回host，讓host送給router
	-	所以就可以知道destination MAC address

### address resolution protocol (ARP)
-	associate ip address with MAC address
	-	把ip和mac address 對應起來
-	不知道destination就問，怎麼問？
	- broadcast ARP REQUEST
	-	有這個IP address的node就回傳 ARP REPLY
-	ARP cache：
	-	如果要傳100個packet，host問了一次，要收的人就reply，host不用問100次，記在ARP cache 要傳給誰就好
	-	記20分鍾
-	gratuitous ARP
	-	trigger other node to update their ARP caches：node有要變動就跟host講，讓host update
-	proxy ARP
	-	代替要收的人回應，就像host要傳給destination可是是用router連接，router會代替destination回應host

### addressing types
-	unicast
	-	一對一傳
	-	address of a single interface
	-	delivery to single interface
-	Multicast
	-	傳給特定多數人
	-	address of a set of interface
	-	delivery to all interface in the set
-	broadcast
	-	傳給所有人
	-	只broadcast 到subnet的所有人，不是真的所有人
	-	address of all interface
	-	delivery to all interface on the Network
	-	ip 最後是255的是用來做broadcast的
broadcast 有分兩種：
-	limited broadcast
	-	傳給自己的subnet
	-	又稱 local network broadcast address
	- address：32個1
-	direct broadcast
	-	broadcast 到特定的 subnet
	-	address：hostid都是1

### zero in IP address
-	當一開機沒有IP address 的時候就有0.0.0.0的IP address
-	這個IP address 只會連到DHCP
-	得到IP address後就不會是0.0.0.0了

### address authority
-	分配IP address 的組織
-	IANA:Internet Assigned Number Authority
	-	1998年後就不再運作了，因爲負責人死了
-	ICANN：Internet Corporation for Assigned Names and Numbers
-	TWNIC：Taiwan Network Information Center

# DHCP
-	dynamic host configuration protocol

### addressing issue
-	要連上網就傲有IP
-	static IP address
	-	一直都是這個IP
-	dynamic IP address
	-	開機才有

### why DHCP
-	movable network
	-	移動之後，IP不能用，要拿到另一個IP

### BOOTP（BOOTstrap Protocol）
-	讓沒有硬碟的電腦可以取得IP
-	問題
	-	不能動態去assign
	-	這臺是什麼IP就是什麼IP

###DHCP
-	RFC 2131
	-	RFC： IETF 的標準，request for comment
-	application layer protocol
	-	幫忙把第三曾的IP address寫進去
-	a mechanism rather than a policy
- messages 是從BOOTP messages 改過來
-	省時間

### IP address allocation
-	automatic allocation
	-	自動給IP
-	dynamic allocation
	-	只給你用一段時間
-	manual allocation
	-	網管手動打IP address 然後用DHCP server assign IP給client

### terminology
-	看講義圖
-	lease
	-	像籤約，可以用多久。
	- 好處：不用了也不講，IP就被佔用着

### DHCP Messages
- 看講義，老師不細講

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
- fragmentation： 切成小塊
-	unicast： 一對一傳
-	broadcast：一對多傳輸（傳給所有人）
-	multicast：一對多傳輸（傳個特定多數人）
-	wireless ethernet compatibility alliance（WECA）：Wi-Fi 認證機構
- RFC： IETF 的標準，request for comment
