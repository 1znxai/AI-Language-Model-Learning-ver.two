用免費資料及平台學習人工智慧神經網路
用Google Colab 練習類神經網路/深度學習/卷積神經網路




By Albert Tsai
1.研究動機 
人工智能的進步日新月異,常常從網路或報導聽到相關消息或專有名詞，但因為還没有相關知識，無法判斷是否如各方所說是下一次的工業革命，因此，想要學習入門基礎;初步想法是用專家整理好的免費資料及平台,學習人工智能神經網路及深度學習卷積神經網路,並在過程中視情況修正。



平台選擇
在電腦上安裝Python及相關AI套件(例如Tensorflow/Pytorch)



Python虛擬環境 : 使用虛擬環境，主要有兩個好處： 避免了版本衝突：每個Python專案可能需要使用不同版本的套件，虛擬環境可以將每個專案的依賴關係隔離開，獨立安裝不同版本的Python 和相關套件。 並且也可以讓個個環境都是乾淨的，更多套件需要運行大環境也不會雜亂。
依據網路資料可以使用以下幾種:Anaconda/miniconda/venv/virtualenv
Google Colab:全名是 Google Colaboratory，是一個基於雲端的免費 Jupyter 筆記本環境，讓使用者可以在瀏覽器上寫程式碼，並且可以利用 Google 的雲端運算資源執行程式碼
以學習入門的人工智能而言，使用Colab是一種對本地端電腦設備要求較低，不需花時間架設AI平台；且Colab有很多英文或中文化的參考資料，很方便學習，在這個自主練習，先考慮使用Colab  
2.學習資料
“TensorFlow、Keras 和深度學習，不需要博士”
https://codelabs.developers.google.com/codelabs/cloud-tensorflow-mnist

概述: 使用四個.ipynb程式碼，由最簡單的神經網路開始，經過新增圖層,再調整學習率,加上”適度丟棄”;最後使用卷積網路,達到99% 的(推論)準確率; 使用的MNIST人工手寫數字資料集辨識，可以說是AI的”Hello World”，是入門常用的。

<img width="407" height="246" alt="image" src="https://github.com/user-attachments/assets/7052132a-63ec-4fe0-ba1e-46a9e7a98553" />

MNIST人工手寫數字資料集的各種0-9 寫法

<img width="274" height="272" alt="image" src="https://github.com/user-attachments/assets/a7f64b4c-ab62-4e66-aa87-b4652a0c6d85" />

一個28x28的像素圖

了解AI基本名詞
人工智能神經網路:簡稱神經網路（neural network，NNs），在機器學習(Machine Learning)和認知科學領域，是一種模仿生物神經網路（動物的中樞神經系統，特別是大腦）的結構和功能的數學模型或計算模型，用於對函式進行估計或近似 ; 以結構而言,可分為單層,多層神經元網路。
深度學習（英語：Deep Learning）是機器學習的分支，是一種以人工神經網路為架構，對資料進行表徵學習的演算法。深度學習中的形容詞「深度」是指在網路中使用多層神經網路。
訓練(training) : 使用AI模型針對大數據進行”學習”, 揣測人類期待看到的輸出值(output)。				

實作過程
基本模型 keras_01_mnist.ipynb (page 3-5)： 點擊連結後，先在雲端硬碟存成複本，逐一執行儲存格(Cell)或全部執行(Ctrl + F9)。這是一個簡單的模型，根據網頁說明及程式碼， 目前模型只有輸入層及單一稠密層
(Dense layer) , 其過程可以看做是針對輸入 (28x28的灰階像素點) 與一個(稠密層)矩陣進行乘法及加法, 每一次的訓練(Epoch)即是在

<img width="420" height="202" alt="image" src="https://github.com/user-attachments/assets/4419dd78-b712-4ac8-acea-5b2a9d3d5105" />

softmax 公式

<img width="392" height="186" alt="image" src="https://github.com/user-attachments/assets/4fa35c31-6954-4396-a253-15d721b60aac" />

Softmax 運算後，選擇機率最高者, 判斷此28X28輸入為數字6

實驗矩陣中的係數值，經過多次的計算與判斷，趨進更準確的結果。

對每一圖層的”活化函數”選擇: relu、softmax 和 sigmoid (待學習,目前不理解, 先當成一種數學函式)

由目前的網頁資料學習到: 一般而言， 每一圖層的”活化函數”會選擇relu (運算簡單效果也好)，但最後一個Layer的分類會使用Softmax
簡單理解為:  
目前類神經網路最後一層有 10 個神經元，因為我們想將手寫數字分類為 10 個類別 (0,..9)。而是會輸出 0 到 1 之間的 10 個數字，代表該數字是 0、1、2 等: L = [L0、L1、L2、L3、L4、L5、L6、L7、L8、L9]
套用 softmax 時，方法是取得每個元素的指數，然後將向量正規化，一般是將向量除以
「L1」範數 (也就是絕對值的總和)，讓正規化值的總和等於 1，可以解讀為機率

<img width="428" height="170" alt="image" src="https://github.com/user-attachments/assets/c1f12d49-7412-4d0b-bc3c-8e6433b85464" />

將資料路徑指向自己的雲端資料庫

執行時的問題/錯誤修正:
錯誤1，點擊”說明錯誤”，會自動啟動
Gemini AI協助除錯。

The error PermissionDeniedError indicates that the code is trying to access the Google Cloud Storage (GCS) bucket gs://mnist-public without the necessary permissions

此錯誤應該是讀取Google 雲儲存時的權限問題，但採用Gemini的AI coding 建議修改程式再運行無法解決，因為產生其他的設定問題,再依照其建議修改設定仍然無法成功。
後來用搜尋引擎查到，有可能解決的方法
自行下載MNIST資料集
https://www.kaggle.com/datasets/hojjatk/mnist-dataset
解壓縮後有四個資料集檔案
上傳到自己帳號的雲端資料夾
修改程式碼，將資料集檔案路徑指向自己的雲端資料目錄
Ctrl + S 存檔, 逐一執行儲存格(Cell)或全部執行(Ctrl + F9)
錯誤2，點擊”說明錯誤”，啟動Gemini AI協助除錯
The error "ValueError: keyword grid_b is not recognized" is raised because the plt.grid()
解決方法
Gemini 檢查可能是劃圖的功能設定有問題
修改程式碼(def display_digits 函式)中改成: plt.grid(visible=False)
Ctrl + S 存檔,逐一執行儲存格(Cell)或全部執行(Ctrl + F9)
成功, 程式依照設定(BATCH_SIZE = 128 EPOCHS = 10),每批次128個資料集, 共訓練十次 , 每一次共 60000/128 步(steps)

<img width="299" height="190" alt="image" src="https://github.com/user-attachments/assets/600196a3-80ac-4f50-b070-8fe231b52c19" />

基本模型的參數個數報告



<img width="298" height="175" alt="image" src="https://github.com/user-attachments/assets/051c5585-709d-4669-8c63-54b690d9dac9" />

基本模型的本次訓練結果（準確率90%）



<img width="357" height="164" alt="image" src="https://github.com/user-attachments/assets/bb35f255-6d74-463e-89b3-1061ff8e5901" />

基本模型本次訓練結果的圖示化



<img width="326" height="101" alt="image" src="https://github.com/user-attachments/assets/0fcb9393-af36-4b96-9b03-af506638c79e" />

進階模型的參數變多（大約20倍）



<img width="380" height="179" alt="image" src="https://github.com/user-attachments/assets/10fdd038-c77c-44f0-8cac-c4f65aa1b0f5" />

進階模型的準確率提高到97.76%



<img width="443" height="155" alt="image" src="https://github.com/user-attachments/assets/9497d74f-2a28-4133-aaf6-85cac27e2cfb" />

進階模型本次訓練結果的圖示化

  











3.2增加二個Dense layer(p6-7)的模型 及啟用Relu: keras_02_mnist_dense.ipynb 

<img width="313" height="69" alt="image" src="https://github.com/user-attachments/assets/beb87a63-300e-4ac4-a04c-148697c3ff30" />

簡易卷積神經網路模型




<img width="276" height="84" alt="image" src="https://github.com/user-attachments/assets/dd02cdfa-ff0a-44a4-94ef-03211b9030e0" />

進階模型

依照之前的方式，
將此程式碼存成副本，
上傳MNIST資料集到自己的雲端資料夾
修改資料集檔案路徑指向自己的雲端資料目錄;以及
修改plt.grid(visible=False)等，
再Ctrl + S 存檔,逐一執行儲存格(Cell)或全部執行(Ctrl + F9)




<img width="357" height="270" alt="image" src="https://github.com/user-attachments/assets/e1415d21-0130-42b9-a9c0-c0aeba944bed" />

簡易卷積神經網路模型的本次訓練結果的圖示化





3.3簡易卷積神經網路(P10-13) : keras_04_mnist_convolutional.ipynb
此簡易卷積神經模型主要加入卷積層(Conv2D),及Flatten層,本質仍是矩陣的乘加,只是使用者可定義運算矩陣的大小(kernel_size)及個數(filters);
依照同樣的方式修改程式碼(以及額外的新錯誤)並執行




<img width="320" height="149" alt="image" src="https://github.com/user-attachments/assets/794c35bf-3e7d-4c4e-9873-143078a267a9" />

簡易卷積神經網路模型參數變更多 (大約為進階模型2倍)




<img width="428" height="206" alt="image" src="https://github.com/user-attachments/assets/1281ac0d-94e9-47ae-8968-bcf1b2d9d72d" />

簡易卷積神經網路模型的準確率已提高到99.2%

反思與收穫
在一開始接觸參考文件的時候，在google colab很多程式碼都看不懂，但我在使用Gemini AI 除錯配合參考文件，下載可以正常使用的資料集，解決權限問題。在進階模型的研究上花了我比較多時間，比起基本模型，進階像是一個更強的計算機，分成好幾層，每層都會先處理一部分的數據，最後得到更精確的答案。後來詢問學校老師，解答是：增加兩個 Dense Layer，尤其是如果每層的神經元數量不小時，整體的參數數量會急遽上升，所以參數會大20倍。最後則是簡易卷積神經網路模型，在卷積層（Conv2D），模型會使用一個小矩陣（卷積核，Kernel）在輸入圖片上滑動，並對應位置的像素值進行矩陣乘法與加總，得到新的數值，形成新的特徵圖。再用矩陣下去掃描，是這個程式最有趣的地方。

參考資料
 “TensorFlow、Keras 和深度學習，不需要博士” 
https://codelabs.developers.google.com/codelabs/cloud-tensorflow-mnist
【機器學習2021】卷積神經網路 (Convolutional Neural Networks, CNN)
手寫辨識MNIST實作
我的第一支快速利用TensorFlow 2.0建立Fully-connected ANN進行手寫數字(mnist)分類
