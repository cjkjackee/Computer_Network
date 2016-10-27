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
	*	不同的physical和mac layer 有不同的號碼（802.X）但LLC只有802.2,之後會講爲什麼
-	Ingredient of a LAN
	*	Topology ： 連接網絡的方法
	*	Transmission medium
	*	Medium Access Control (MAC) ： 不同的transmission medium 有不同的mac

LAN topology
-	bus: 
	*	share medium
	*	一個人在傳所有人都知道
	*	問題：會有collision,所以需要有MAC
-	tree
	*	邏輯上與bus相似
-	Ring
-	star
	*	邏輯上與bus相似  
以上是最常用的4種

# 作業

+	ack 
	*	1端送data給2端，2端如果收到了回傳一個東西給1端，讓1端知道2端已經收到了

# 注
-	IETF： 制定標準的機構，網絡架構，TCP
-	IEEE： 制定標準的機構，最多人用他們制定的LAN的標準（只要是802的幾乎都是LAN的標準）
