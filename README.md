# 目的
利用「HW2_hash_practice.ipynb」讀取「hw2_data.txt」，並統計出以下兩點：
1. 總共有多少個不重複的英文字
2. 每一個英文字出現次數為何

其中「HW2_hash_practice.ipynb」以Python dictionary 進行程式撰寫。

# 執行結果
>總共有 10 個不重複的英文字: <br>
詞彙 Fries 出現次數: 76 <br>
詞彙 Steak 出現次數: 46 <br>
詞彙 Pho 出現次數: 19 <br>
詞彙 Rib 出現次數: 33 <br>
詞彙 Burger 出現次數: 196 <br>
詞彙 Coke 出現次數: 145 <br>
詞彙 Taco 出現次數: 57 <br>
詞彙 Pizza 出現次數: 83 <br>
詞彙 Potato 出現次數: 3 <br>
詞彙 Cheese 出現次數: 234 <br>

# 程式碼
```
def hash_function(key):
    # 將詞彙轉換為ASCII碼，加總後除以100取餘數作為 Hash value
    ascii_sum = sum(ord(char) for char in key)
    return ascii_sum % 100

def count_unique_words(data):
    # 初始化一個空字典用於統計詞彙出現次數
    word_count = {}
    # 初始化一個空集合用於記錄不重複的英文字
    unique_words = set()

    # 逐行讀取資料
    for line in data.split('\n'):
        # 如果行為空，跳過此行
        if not line:
            continue
        
        # 取得詞彙
        word = line.strip()

        # 更新詞彙出現次數
        if word in word_count:
            word_count[word] += 1
        else:
            word_count[word] = 1
        
        # 將詞彙加入不重複的集合
        unique_words.add(word)

    return word_count, unique_words

def main():
    # 讀取資料
    with open('hw2_data.txt', 'r', encoding='utf-8') as file:
        data = file.read()

    # 呼叫函式計算結果
    word_count, unique_words = count_unique_words(data)

    # 顯示統計結果
    print("總共有", len(unique_words), "個不重複的英文字:")
    for word in unique_words:
        count = word_count[word]
        print("詞彙", word, "出現次數:", count)

if __name__ == "__main__":
    main()
``` 
