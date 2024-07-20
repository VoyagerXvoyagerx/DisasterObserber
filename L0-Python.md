# L0-Python
1. Word Count 代码
```python
import re
from collections import defaultdict

def wordcount(text):
    # 去掉标点符号，只保留单词和空格
    text = re.sub(r'[^\w\s]', '', text)
    
    # 将所有单词转换为小写
    text = text.lower()
    
    # 将文本分割成单词列表
    words = text.split()
    
    # 使用defaultdict来存储单词及其出现次数
    word_count = defaultdict(int)
    
    # 统计每个单词的出现次数
    for word in words:
        word_count[word] += 1
    
    return dict(word_count)

# 示例输入
text = """
Hello, this is Zheng Yijie.
I am learning InternLM.
InterLM is a great work!
"""

# 调用函数并打印结果
print(wordcount(text))
```

2. debug页面
可以在左侧查看变量、添加变量值到watch界面，在代码处打断点。将`word_count`变量添加到watch页面，并在循环中打断点，观察`word_count`中k-v的变化。

![debug界面](https://github.com/user-attachments/assets/16f315aa-665b-4a25-ad4d-783f04065e8e)

continue 2 次，可以看到`word_count`中多了2个k-v对
![step2](https://github.com/user-attachments/assets/f8be1e85-aff3-446f-b880-43944af3eb8f)
在continue 2次，`word_count`中的k-v对增加4次
![debug4](https://github.com/user-attachments/assets/2c4e148c-26e6-451f-bc54-818aa0db7fee)


运行结果：
```bash
(base) root@intern-studio-007047:~#  cd /root ; /usr/bin/env /root/.conda/bin/python /root/.vscode-server/extensions/ms-python.debugpy-2024.8.0-linux-x64/bundled/libs/debugpy/adapter/../../debugpy/launcher 56169 -- /root/word_counter.py 
{'hello': 1, 'this': 1, 'is': 2, 'zheng': 1, 'yijie': 1, 'i': 1, 'am': 1, 'learning': 1, 'internlm': 1, 'interlm': 1, 'a': 1, 'great': 1, 'work': 1}
```
