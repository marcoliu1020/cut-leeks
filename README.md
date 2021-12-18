# 進擊的韭菜

# 題目描述
幣圈裡面，有一種暱稱叫做 韭菜 的生物，如果你想要低價買入他們手上的比特幣，放出一些恐慌訊息，他們馬上就會賣掉；相反的，如果你想要高價賣出你手上的囤貨，你只要放出利好消息，他們就會蜂蛹買入。

# 輸入說明
第一行有一個整數 N (N <= 999,999,999,999)，代表有 n 個韭菜由左至右排成一排，這些韭菜手上都持有比特幣，由最左邊的韭菜開始編號： 1, 2, 3, ..., N。
第二行有一整數 M (M <= 999999)，接下來會有 M 次割韭菜的行為。
接下來 M 行每行有兩個整數 [i, j]。表示對從 i 到 j 的這堆韭菜進行收割。

# 輸出說明
請輸出最後有多少韭菜還沒有賣掉比特幣？

# 範例輸入：
5 // N.
3 // M.
1 3 // [i, j].
3 5 // [i, j].
1 5 // [i, j].

# 範例輸出：
4

# 分析
每一輪會有5個韭菜要被割，我們會割3次，
第一輪割1 2 3，剩4 5
第二輪割3 4 5，剩1 2
第三輪割1 2 3 4 5，剩
最後剩1 2 4 5，四個韭菜


```
#!/usr/bin/python
# -*- coding: utf-8 -*-

def cut_leeks(leeks=5, cuts=[[1,3], [3,5], [1,5]]):
    leeks = set(range(1, leeks+1))
    
    remain = 0
    for c, cut in enumerate(cuts, start=1):
        cut = set(range(cut[0], cut[1]+1)) # cut leeks from [i, j] *include j
        left_leeks = list(leeks - cut)
        remain += len(left_leeks)
        #print(f'第{c}輪: {left_leeks} 未被收割')

    print(f'最後剩{remain}個韭菜')
    
cut_leeks()
```
