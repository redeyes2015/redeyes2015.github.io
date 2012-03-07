--- layout: post title: "手動修改code後重編deb package" date: 2011-07-06 comments: false --- 

把原始媽抓回來:

apt-get source code PACKAGE

抓回來之後要編譯前，先把依存的其他lib裝好:

sudo apt-get build-dep PACKAGE

重新打包成.deb, 同時把原始碼patch一遍:

cd PACKAGE_DIR; dpkg-buildpackage

之後作修改只要用make就好

(亂試出來的方法, 感覺不太正式, PACKAGE_DIR/.. 會多一堆.deb檔 -_-a)

  
PS:

要改CFLAGS之類的make參數可以在dpkg-buildpackage之前先作:

export CFLAGS="-g -O0"

之類的環境參數設定

(同樣是亂試出來的方法...)

  
PS2:

dpkg-buildpackage 之後 src/NetworkManager 其實是一個 shellscript

執行後會產生暫時版的"lt-NetworkManager"

可以在 src/.lib/ 裡面找到

  
---  
為什麼會有這篇... 因為想用 gdb 對 Network Manager 除錯

但是下了 -O2 參數編譯出來的版本沒有除錯資訊

用完PS + PS2兩段說的之後就可以除錯了!

