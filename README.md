### Resume_Sample

1. 架構是從我們的專題再延伸出來，將有關題庫的部分移除，Redis有保留，可以日後要應用時使用
2. 專題連結 https://github.com/iii-cutting-edge-tech-lab/Chatbot_Project_cc103.git
3. docker-compose.yml 可開啟chatbot_line、chatbat_redis、chatbot_ngrok、chatbot_aip、chatbot_db等五個docker container
- chatbot_line : 主要與line@官網溝通，設計的邏輯及樣板都是在此docker container 設計
- chatbot_redis : 之前專題是用來儲存考題的 memoty storage
- chatbot_ngrok : 將line@傳送的https格式轉為 http 格式
- chatbot_aip : 各 api 接口，主要是將 menu 及 user 的資訊做業務邏輯處理到資料庫
- chatbot_db : 儲存資料
- get_ngrok_url.sh : 使用腳本將 url 抓出來

#### 步驟 :
1. step 0 :將所有資料為 FanPeter 取代為你要得名稱
2. step 1 : 使用 docker-compose 指令將5個 container 開啟
‵‵‵
docker-compose up -d
‵‵‵
3. step 2 : 抓出ngrok的url
‵‵‵
bash get_ngrok_url.sh
‵‵‵
4. step 3 : 將檔案secret_key的內容填寫上去
- 先到 https://developers.line.me 創建新的 provider -> 填完相關資訊後，創建新channel -> Messaging API 
- 產生的 url 填寫到 Line 官網的 Webhook URL 項
- 將 Channel secret 、 Channel access token 、Your user ID 、 ngrok的 url 填寫到 secret_key 檔案中
5. step 4 : 建立 menu (菜單的圖檔可以自行設計)
- 執行 FanPter_Line/code/menu_id.ipynb 到第3個 cell 時，將產生的 rich-menuid 貼到secret_key 檔案中的相對應位置
- 再次執行 FanPter_Line/code/menu_id.ipynb 的第2個 cell，重新擷取必要資訊
- 執行第4、5 cell
6. step 5 : 開啟 API Server
- 執行 FanPeter_Dev/code/code.ipynb -->Run All
7. step 6 : 客製化自己的內容
- 將圖片upload上 FanPter_Line/code/images
- 將 FanPter_Line/code/app.ipynb內容的圖片路徑、uri都更改成自己的
8. step 7 : 開啟Line Server
- 執行 FanPeter_Line/code/app.ipynb --> Run All
9. step 8 :掃描QR code 驗證

