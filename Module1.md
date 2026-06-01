# AI-Language-Model-Learning
本地端電腦架設大語言模型初體驗
AnythingLLM + Meta Llama 3.2 7/11b




By Albert Tsai

研究動機
想試用最新最熱門的網頁板大語言模型,但最近常常顯示「server busy！」想到似乎可以用自已的電腦架設本地端的LLM AI模型。

實作過程
準備工作: 問ChatGPT應該如何進行
Q1. 架設本地端的LLM AI模型, 如何依據我的電腦的記憶體容量,選擇最佳的模型?
Q2. Mac Air M2 最適合的模型的大小
在回答有看到回應: 量化壓縮…最適合11B參數 的模型，建議使用 Q4 量化版本…, 推薦的運行方式
Q3. 什麼是量化?
將模型的數據精度降低，在縮減數據的過程中提高運算速度並且盡量維持精度



Q4. AnythingLLM
AnythingLLM 是一款開源的 LLM 應用框架，主要用來 本地運行 LLM 並處理自訂文件（如 PDF、Markdown、TXT 等）…
決定使用AnythingLLM：首先依照平台下載及安裝AnythingLLM，再下載模型，並進行工作區的設定

<img width="330" height="211" alt="image" src="https://github.com/user-attachments/assets/64c57bef-7c9e-4975-9a47-637c7607bf09" />


AnythingLLM 完裝後，設定->下載LLM 模型 ->點選 Llama 3.2 11B 自動下載



<img width="330" height="210" alt="image" src="https://github.com/user-attachments/assets/8b811aad-4d07-4480-95cd-69077b5c6882" />


自定一個工作區名稱->設定工作區的LLM模型



<img width="366" height="277" alt="image" src="https://github.com/user-attachments/assets/82af0acf-f027-4c7d-9502-fa26189b91de" />


然而我的m2晶片跑不動，於是之後的實驗都是使用3b運行




成果展現
首先再對自主學習1中的第一個基本計算機程式除錯，仍然可以正確修正錯誤

<img width="366" height="196" alt="image" src="https://github.com/user-attachments/assets/33a62b1e-7155-4e4d-9d1f-fca5c740f6c5" />

修正基本計算機程式錯誤



同樣指令測試本地模型

<img width="365" height="173" alt="image" src="https://github.com/user-attachments/assets/e2bb2c76-5370-4359-8c13-01a81c1af2e2" />

請本地AI模型寫一個簡單的Python計算機程式



同樣指令測試本地模型

<img width="364" height="187" alt="image" src="https://github.com/user-attachments/assets/74435558-191e-40ab-84f1-6e7cf96c51f4" />

請本地AI模型寫一個(圖形化)簡單的Python計算機程式



用中文問，模型會用中文回答(除語法除外)

<img width="364" height="190" alt="image" src="https://github.com/user-attachments/assets/543aace7-b72f-4699-98b8-35d03348cc2e" />

中文問，請本地AI模型寫一個簡單的Python計算機程式



實例測試
Q1: 請比較25坪以上的除甲醛空氣清淨機
回答只有三個產品，但没有之前廣告常見的品牌(Sharp)

<img width="1156" height="633" alt="image" src="https://github.com/user-attachments/assets/664cd21b-5453-4875-a36f-27db6075e43d" />








目前資料庫中符合的空氣清淨機只有三種

步驟: 點選工作區上傳的icon->上傳文件(pdf,txt…) 或網站連結 (AnythingLLM會爬蟲) -> 存到工作區

<img width="605" height="567" alt="image" src="https://github.com/user-attachments/assets/e633b38a-2f58-40dd-a273-579e928f000f" />

                               





最後步驟，將新資料注入工作區資料庫(Pin)

<img width="430" height="125" alt="image" src="https://github.com/user-attachments/assets/7c3704ac-7176-48d5-b13a-c45ecbbfd595" />




Q2: 請比較25坪以上的除甲醛空氣清淨機
問同樣的問題，真的看到新產品(紅框)的正確資料顯示在比較表。

<img width="433" height="210" alt="image" src="https://github.com/user-attachments/assets/5255fbc6-0070-4ebe-a609-e40928c591f8" />







反思與收穫
一步一步在本地端電腦架設大語言模型是我第一次的體驗，不過在一開始安裝的時候仍然遇到了一個問題，在裝語言模型的時候，11B的版本在我的筆電上面運行不了，後來裝3B的就跑得動，而且也很順暢，在語言學習的過程中，我也加入資料讓語言模型有更多資訊可以判斷，這稱為RAG（擷取增強生成）。不過目前的測試只是用比較簡單的程式，並沒有辦法完全比較本地端的這個中小規模的語言模型與真正雲端上的大規模語言模型的差別。

將大語言模型架設在本地端的電腦，雖然因為本地端電腦的算力及記憶體只能執行比較小規模的語言模型，但是已經可以看到在測試中顯現出同樣的程式除錯以及資訊處理比較的能力，而且在本地端電腦運行可以避免大家目前在討論的資料上雲端的資訊安全問題，因為資料都是在自己的本地端的電腦。

參考資料
AnythingLLM：打造個人AI知識庫　完全在本機運行！
用 LM Stuidio 5 分鐘架設自己的 AI 聊天機器人
大型語言模型-[初階]建立基於RAG方案的專屬私有知識庫教學
7 個本地運行模型的最佳LLM 工具
