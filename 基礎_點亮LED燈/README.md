
## 說明

點亮LED燈，是一個最基本的入門應用程式，不但生成的速度快，同時也用來檢驗使否正確設定好程式開發環境。

## 電路圖

![alt text](images\1708149608259.png)

電路中使用RGB共陰極之三色LED燈，
R、G、B LED的陽極連接330 歐姆的電阻，與ESP32 MCU模組的 IO27、IO26、IO32連接

![alt text](images\1708149669611.png)
故韌體程式令IO27、IO26、IO32其中一腳輸出高準位(1、HIGH、true)，即可使對應的LED亮。
其中:
紅色LED燈為LED_R ，接於IO27
綠色LED燈為LED_G ，接於IO26
藍色LED燈為LED_B ，接於IO32

## Ardublockly 編輯

### 產生紅色LED燈亮、滅閃爍的積木程式

點擊 ardublockly_run.bat 批次檔，啟動MCBV3版的Ardublockly應用程式
![alt text](images\image.png)

點擊工具列中的"輸入輸出"展開-> 輸出、輸入、音率
![alt text](images\image-1.png)

點擊工具列中的"輸出"後，出現可使電路板MCU腳位輸出的積木
拖曳 所需積木到Arduino 程式積木中

#### 拖曳紅色LED積木

![alt text](images\image-2.png)
拖曳積木，利用Windows 熱鍵 "Ctrl + C" 複製 及 "Ctrl + V" 貼上功能，加速產生重複的積木

修改傳入LED-R腳的立即值，"真"等於"HIGH"等於"true"會將該腳位設定為高準位，"假"等於"LOW"等於"false"會將該腳位設定為低準位。 根據電路圖，LED燈腳位設定為高準位時，LED燈亮，低準位時，LED燈不亮(滅)。
![alt text](images\image-3.png)

#### 拖曳延遲時間積木

延遲積木在"各種各樣" 工具列中，延遲"毫秒"為延遲 N * 1/1000 秒(千分之1)，延遲"微秒"為延遲 N * 1/1000000 秒
![alt text](images\image-4.png)

在主迴圈中，增加延遲積木，增加LED燈亮滅的間隔時間
![alt text](images\image-5.png)

#### 儲存積木程式

![alt text](images\image-6.png)

"Save" 為儲存積木程式，"Open" 為開啟積木程式檔案。
設定存檔檔名為"<a href="LED_R_Blink.xml">LED_R_Blink.xml</a>"

### 上傳紅色LED燈亮、滅閃爍的積木程式至Arduino IDE

![alt text](images\image-7.png)
如上圖所示，滑鼠移動到上傳符號時，![alt text](images\image-8.png)，符號變成籃底，點擊後，即啟動Arduino IDE，並將原始碼同步上傳到Arduino IDE中。

#### 無法啟動

如果無法啟動Arduino IDE，請檢查EDIT-> preferences 中Compiler Location設定，沒有指定到正確的Arduino IDE程式。
![alt text](images\image-9.png)

*Arduino IDE需要使用TEMI協會壓縮的版本,適用於MCBV3電路板的Arduino IDE 下載網址:
https://drive.google.com/file/d/13tvwNZd0RjvDPp21khZYmijjzD2jenMy/view?usp=drive_link

## Arduino IDE 編譯及上傳

### 設定 Arduino IDE

#### 偏好設定

![alt text](images\image-10.png)

如上圖中"檔案" 的 "偏好設定"

![alt text](images\image-11.png)
如上圖，打勾

#### 開發板

![alt text](images\image-12.png)
開發板選擇 TEMI協會(ESP32) --> MCBV3
點選後，選擇MCBV3所連接的序列埠

#### 編譯及上傳

<p>紅色LED燈亮滅 Arduino 原始程式碼:</p>
<pre><code>
void setup() {
  	pinMode(27, OUTPUT);

digitalWrite(27,false );

}

void loop() {
digitalWrite(27,true );
delay(500);
digitalWrite(27,false );
delay(500);

}

當設定確後，點選![alt text](images\image-13.png) 向右箭頭，Arduino IDE進行程式碼的編譯及上傳。

![alt text](images\image-14.png)

當上傳完成後，在Arduino IDE下部，出現"上傳完畢"訊息，以及訊息框中出現

Hash of data verified.
Compressed 199008 bytes to 104248...
Wrote 199008 bytes (104248 compressed) at 0x00010000 in 1.6 seconds (effective 967.2 kbit/s)...
Hash of data verified.
Compressed 3072 bytes to 128...
Wrote 3072 bytes (128 compressed) at 0x00008000 in 0.0 seconds (effective 3510.9 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...

表示設定正確，此時MCBV3電路板 紅色LED燈持續 0.5秒亮0.5秒暗

#### 上傳程式後關閉Adruino IDE

如果設定正確運行，欲修改積木程式，進行下個練習時，請關閉Arduino IDE ，此時Arduino IDE 會記錄當前設定，以備下回啟動時引用。
