# autoScan
test for autoScan

建議如下:
1. click  事件定義時機應於 contrructor 中 或是 suface Create envent 中，請參考 Activity 生命週期，其他類型的事件定義亦同
2.click 事件可用於 (開啟/關閉) 是否要計算world point ，計算工作仍於 onDrawFrame 中完執行，避免因 frame 生命週期結束導到無法取得 frame 資訊。
3.可於 constructor or suface created 中建新的 thread 用以計算 world point，利用 queue 來換資訊，資訊內容有，計算world point 之必要資訊，如 width 、 height 、 modelProjection Matrix 、depth map image、caream image 等
