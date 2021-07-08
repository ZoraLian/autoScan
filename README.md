# autoScan
test for autoScan

## 0708進度
已將click事件定義於onCreate中，並用來開啟/關閉是否要計算world point的method。(Boolean autoScanMode)

### 目前遇到的問題：
1. android.view.ViewRootImpl$CalledFromWrongThreadException: Only the original thread that created a view hierarchy can touch its views. (目前已解，用runOnUiThread)
2. autoScan因為放在on draw frame裡，會隨著frame更新被一直重複call，導致運算量過大、卡頓
3. 每一frame的取x y間隔要是多少？現在每100計算一次，還是很卡...
4. 要如何儲存大量計算資料？

### 待研究
1. Handler
2. 開啟新執行緒
3. queue來換資訊

## 建議如下:
1.  click  事件定義時機應於 contrructor 中 或是 suface Create envent 中，請參考 Activity 生命週期，其他類型的事件定義亦同
2.  click 事件可用於 (開啟/關閉) 是否要計算world point ，計算工作仍於 onDrawFrame 中完執行，避免因 frame 生命週期結束導到無法取得 frame 資訊。
3.  可於 constructor or suface created 中建新的 thread 用以計算 world point，利用 queue 來換資訊，資訊內容有，計算world point 之必要資訊，如 width 、 height 、 modelProjection Matrix 、depth map image、caream image 等

## 附註
point cloud helper 路徑：hello_ar_java\app\src\main\java\com\google\ar\core\examples\java\common\helpers
