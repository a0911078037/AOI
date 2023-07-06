# AOI
利用 scikit-learn 二元分類器，判斷 PCB 上的元件是否為 defect  
模型選用 C-Support Vector Classification
## Method
目標是要做出一個二元分類器，將 PCB 上的元件，進行標記過後，  
判斷是電阻 (resistor) 又或者是電容 (capacitor) 。而標記這件事已經在  
annotations 裡面的 json 檔可以看到了 (bbox) 屬性。所以目前剩下要做的部分，  
就是一個二元分類器判斷出元件類型。  
在資料前處理的部分，利用 opencv 套件將照片類型的檔案讀取，並且長寬進  
行重新調整 (640*480) ，因為發現在測試資料上面，照片的大小並不一致  
之後將 annotations 裡面的 train.json 檔案進行讀取，把每張照片所標記起來  
的位置進行裁切，並賦予 label。而因為每張照片上的元件大小以及位置都不一致，所以最後會再一次的調整大小 (64*128)，
盡量將測試資料標準化。  
最後再將照片轉成數值型態，並將數值轉成 0 到 1 之間，再把維度降階成一維 (flatten)。
## Result
Precision versus recall img:  
![img](https://github.com/a0911078037/AOI/blob/main/git_img/result.png)
