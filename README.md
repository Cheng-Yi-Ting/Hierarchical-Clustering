# Hierarchical Clustering (階層式分群法)
此專案以Python3進行開發，使用scikit-learn以新聞資料進行TF-IDF，結合HAC實作的範例。
階層式分群法（hierarchical clustering）透過一種階層架構的方式，將資料層層反覆地進行分裂或聚合，以產生最後的樹狀結構，常見的方式有兩種：

如果採用聚合的方式，階層式分群法可由樹狀結構的底部開始，將資料或群聚逐次合併
如果採用分裂的方式，則由樹狀結構的頂端開始，將群聚逐次分裂。

本範例將針對聚合式（由下而上）階層分群法來進行說明。

### Hierarchical Clustering Introduction:
```
聚合式階層分群法（agglomerative hierarchical clustering）由樹狀結構的底部開始層層聚合。一開始我們將每一筆資料視為一個群聚（cluster），假設我們現在擁有n筆資料，則將這n筆資料視為n個群聚，亦即每個群聚包含一筆資料：

step1. 將每筆資料視為一個群聚 Ci, i=1 1 to n.
step2. 找出所有群聚間，距離最接近的兩個群聚 Ci、Cj
step3. 合併 Ci、 Cj 成為一個新的群聚
step4. 假如目前的群聚數目多於我們預期的群聚數目，則反覆重複步驟二至四，直到群聚數目已將降到我們所要求的數目。

在步驟二中，何謂「距離最接近的兩個群聚 Ci、Cj」呢？事實上在定義兩個群聚之間的距離，有各種不同的方式，每一種方式所得到的結果都不太相同。這些常用的群聚距離的定義可以說明如下。

單一連結聚合演算法（single-linkage agglomerative algorithm）：群聚與群聚間的距離可以定義為不同群聚中最接近兩點間的距離

完整連結聚合演算法（complete-linkage agglomerative algorithm）：群聚間的距離定義為不同群聚中最遠兩點間的距離

平均連結聚合演算法（average-linkage agglomerative algorithm）：群聚間的距離則定義為不同群聚間各點與各點間距離總和的平均

沃德法（Ward's method）：群聚間的距離定義為在將兩群合併後，各點到合併後的群中心的距離平方和

```
