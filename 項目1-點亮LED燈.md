# 項目1-點亮LED燈
## 說明
   點亮LED燈，是一個最基本的入門應用程式，不但生成的速度快，同時也用來檢驗使否正確設定好程式開發環境。
## 電路圖
![image](https://github.com/SimonTseng72/TEMI-MCBV3/assets/41949130/46bf12a5-44be-4683-a5a7-98f1448062a6)電路中使用RGB共陰極之三色LED燈，
R、G、B LED的陽極連接330 歐姆的電阻，與ESP32 MCU模組的 IO27、IO26、IO32連接 ![image](https://github.com/SimonTseng72/TEMI-MCBV3/assets/41949130/09c46a66-9877-43f3-8f1c-81043987c551)
故韌體程式令IO27、IO26、IO32其中一腳輸出高準位(1、HIGH、true)，即可使對應的LED亮。
其中:
   紅色LED燈為LED_R ，接於IO27
   綠色LED燈為LED_G ，接於IO26
   藍色LED燈為LED_B ，接於IO32

