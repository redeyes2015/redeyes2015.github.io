--- layout: post title: "Linux System Programming -- Memory" date: 2011-09-19 comments: false categories: - LinuxSystemProgramming --- 

  

  * calloc 比 malloc 好的地方: calloc 配置出來的空間會被要求先全部清空, 因此 1. 不需要手動清空( i.e bzero() ) 2. kernel 或是函式庫可以直接配給程式已知已清空的空間, 基於這兩點, 使用calloc 的效率要比 malloc 高
  * gcc 的 -Wpadded 選項可以開啟在 struct 遇到 alignment 問題時給予額外輸出。
  * 下面這段 code 可能會讓效能不佳，也可能讓整個程式整個結束, 原因: alignment
    
     char greeting[] = "Ahoy Matey";    
     char *c = greeting[1];    
     unsigned long badnews = *(unsigned long *) c;    
    

  * Stack-Based Allocation: alloca(): 直接在 stack 上配置空間, 比起 calloc / malloc 在 heap 上配置, 會快的多。
    * 但是，alloca() 配置出來的空間在呼叫的函式結束後就會消失, 也就不能用以在函式之繼續使用。
    * 不要在函式呼叫的那一行直接用 alloca() 作參數傳進去! 即不要這樣寫: 
    
     some_func_name(arg1,  (alloca(size) ))

    * strdupa / strndupa 就是利用這個機制建立字串複本的.
  * Variable-Length Arrays (VLA):&nbsp_place_holder;C99之後函式內的自動變數就可以在執行期間再指定陣列的大小
    * 也就是說可以寫這樣的code:&nbsp_place_holder;
    
     for(i=0; i&lt; n ; ++i)    
     {    
       char foo[i+1];    
       /* use foo to do some evil! */    
       ...    
     }    
    

    * VLA vs. alloca:&nbsp_place_holder;
      1. 都是配置在 stack 空間, 但是定義有所不同，因此 alloca() 配置的空間在呼叫的函式結束後, 配置出來的空間立即失效, 而 VLA 是在該變數的定義區塊結束後就清楚. 請參考以下:
    
     int func1( int i)    
     {    
       char *array_by_alloca;    
       int i;    
       for( i=0; i<n; ++i)    
       {    
         char array_by_VLA[i];    
         array_by_alloca = alloca(sizeof(char) * n);    
         // ...    
       }    
     }    
    

array_by_VLA 在每次 for 迴圈結束後空間都會先釋放，重新開始後再配置，因此 array_by_VLA 佔的空間為 O( n ), 而
alloca 配置的空間要等到 func1 結束後才釋放，因此 array_by_alloca 所佔空間為 O( n(n+1) / 2)

      2. VLA 的語法只能用來定義陣列; alloca 的用法相對有彈性 
      3. 不要混用這兩者, 會造成不可預期的狀況
  * 由於 struct padding 的問題, 不要對 struct 作 memcmp, 另行撰寫函式逐項比對為佳
  * 在極高的安全需求下，未加密的密碼不應該被 swap out 到硬碟上. 因此可以用 mlock() 指定該 page 應被鎖定於記憶體中. 而每個 process 可鎖定的空間最多只有&nbsp_place_holder;RLIMIT_MEMLOCK bytes, 預設是 32KB.
  *   

