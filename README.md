# Computer_Network
Network layer
	功用：routing，flow control
	就算是頻寬無限大還是需要進行flow control 防止不正當的使用者

Transport Layer
	功能：provide reliable link，重組信息
	爲什麼data link layer 已經進行錯誤重傳了，這層還要進行一次？
	因爲可能是router crash，或wire壞掉。
Session Layer（實用中沒有用到）
	功能：連接的權限，連接路徑
	大多數時間不需要建立路徑（網絡是以packet solution的方式），所以就直接不需要
Presentation Layer (實用中沒有用到)
	功能：加密，壓縮，轉換編碼;
	因爲不是很重要（理由同上一層），所以就直接不做
	
