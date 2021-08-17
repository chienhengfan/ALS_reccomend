這是我從ERP拉出測試資料，以此資料為基礎而建立ALS推薦系統的程式

使用套件:pandas, sklearn

主要演算法:alternating least squares

程式可以切分成以下幾部分

1.將民國年轉成西元年:
  >>>problem: 網路上 iloc[] 在jupyter notebook上可行，但在.py 執行會跳錯 |
  >>>solution: 用另一個dataframe 處理完後再 allocate 回去
  
2.資料清理，生成商品購買次數和顧客關係的 sparse-matrix
  >>>problem: 目前測試用少量資料，沒甚麼問題，但一但資料量龐大， cpu 可能無法運算過於龐大的sparse matrix |
  >>>soluton: 可以用gpu或是 spark 以分散式運算的方式
  
3.利用TruncatedSVD 降維取出主成分，來判斷商品的關聯:
  >>>note: 這其實跟pca有點相似，可以參考 leemeng blog 上關於pca 的文章 |
  >>>note2: 不同於 item_base CF 所使用的 cosine-similarity
  
4.呈現結果:
  >>>這部分令我最困擾，目前用csv檔的方式呈現
  
  
 未來目標:串接系統 or 做成dashboard
