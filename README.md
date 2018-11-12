# Resume_Sample

#架構是從我們的專題再延伸出來，將有關題庫的部分移除，Redis有保留，可以日後要應用時使用
#專題連結 https://github.com/iii-cutting-edge-tech-lab/Chatbot_Project_cc103.git
#docker-compose.yml 可開啟chatbot_line、chatbat_redis、chatbot_ngrok、chatbot_aip、chatbot_db等五個docker container
#chatbot_line : 主要與line@官網溝通，設計的邏輯及樣板都是在此docker container 設計
#chatbot_redis : 之前專題是用來儲存考題的memoty storage
#chatbot_ngrok : 將line@傳送的https格式轉為http格式
#chatbot_aip : 各api接口，主要是將menu及user的資訊做業務邏輯處理到資料庫
#chatbot_db : 儲存資料
#get_ngrok_url.sh : 使用腳本將url抓出來

#step 1 : 使用docker-compose指令將5個container開啟
docker-compose up -d

#step 2 : 抓出ngrok的url
bash get_ngrok_url.sh

#step 3 : 將檔案secret_key的內容填寫上去
#先到 https://developers.line.me 創建新的provider -> 填完相關資訊後，創建新channel -> Messaging API 
#產生的url填寫到Line官網的Webhook URL項
#將Channel secret 、 Channel access token 、Your user ID填寫到secret_key檔案中

#step 4 : 建立menu (菜單的圖檔可以自行設計)
#執行FanPter_Line/code/menu_id.ipynb到第3個cell時，將產生的 rich-menuid 貼到secret_key檔案中的相對應位置
#再次執行FanPter_Line/code/menu_id.ipynb的第2個cell，重新擷取必要資訊
#執行第4、5 cell

#step 5 : 開啟API Server
#執行FanPeter_Dev/code/code.ipynb -->Run All

#step 6 : 客製化自己的內容
#將圖片upload上 FanPter_Line/code/images
#將FanPter_Line/code/app.ipynb內容的圖片路徑、uri都更改成自己的

#step 7 : 開啟Line Server
#執行 FanPeter_Line/code/app.ipynb --> Run All

#step 8 :掃描QR code 驗證

