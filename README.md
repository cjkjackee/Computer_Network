# Computer_Network

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
+	讓攔截通訊（interception）和破壞通訊（jamming）變得困難
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
	+	hub第一層，router第三層
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



# 作業

+	ack 
	*	1端送data給2端，2端如果收到了回傳一個東西給1端，讓1端知道2端已經收到了

# 注
-	IETF： 制定標準的機構，網絡架構，TCP
-	IEEE： 制定標準的機構，最多人用他們制定的LAN的標準（只要是802的幾乎都是LAN的標準）
-	第二層的封包叫frame， 第3層叫packet，第四層叫segment，所有統稱PDU
-	throughput：傳多少進去，傳多少出來
-	KISS：keep it simple and stupid
