[实现Trie树]()

 **[Trie](https://baike.baidu.com/item/%E5%AD%97%E5%85%B8%E6%A0%91/9825209?fr=aladdin)** （发音类似 "try"）或者说 **前缀树** 是一种树形数据结构，用于高效地存储和检索字符串数据集中的键。这一数据结构有相当多的应用情景，例如自动补完和拼写检查。

请你实现 Trie 类：

* `Trie()` 初始化前缀树对象。
* `void insert(String word)` 向前缀树中插入字符串 `word` 。
* `boolean search(String word)` 如果字符串 `word` 在前缀树中，返回 `true`（即，在检索之前已经插入）；否则，返回 `false` 。
* `boolean startsWith(String prefix)` 如果之前已经插入的字符串 `word` 的前缀之一为 `prefix` ，返回 `true` ；否则，返回 `false` 。

**示例：**

<pre><strong>输入</strong>
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
<strong>输出</strong>
[null, null, true, false, true, null, true]

<strong>解释</strong>
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // 返回 True
trie.search("app");     // 返回 False
trie.startsWith("app"); // 返回 True
trie.insert("app");
trie.search("app");     // 返回 True
</pre>

**思路：**

Trie 树板子题，注意指针和格式


```cpp
class Trie {
public:
    bool isWord;
    Trie* children[26];

    Trie() {
        isWord = false;
        memset(children, 0, sizeof(children));
    }
  
    void insert(string word) {
        Trie* node=this;
        for(int i=0;i<word.size();i++){
            if(node->children[word[i]-'a']==NULL)
                node->children[word[i]-'a']=new Trie();

            node=node->children[word[i]-'a'];
        }
        node->isWord=true;
    }
  
    bool search(string word) {
        Trie* node = this;
        for(int i=0;i<word.size();i++){
            if(node->children[word[i]-'a']==NULL)
                return false;

            node=node->children[word[i]-'a'];
        }
        return node->isWord;
    }
  
    bool startsWith(string prefix) {
        Trie* node = this;
        for(int i=0;i<prefix.size();i++){
            if(node->children[prefix[i]-'a']==NULL)
                return false;

            node=node->children[prefix[i]-'a'];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
