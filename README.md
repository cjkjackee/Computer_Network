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
+	code-division multiplexing (CDM)
	
# 作業

+	ack 
	*	1端送data給2端，2端如果收到了回傳一個東西給1端，讓1端知道2端已經收到了

