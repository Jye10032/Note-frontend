# 最小覆盖字串

[最小覆盖字串](https://leetcode.cn/problems/minimum-window-substring/description/?envType=study-plan-v2\&envId=top-100-liked)

给你一个字符串 s 、一个字符串 t 。返回 s 中涵盖 t 所有字符的最小子串。如果 s 中不存在涵盖 t 所有字符的子串，则返回空字符串 "" 。

**注意：**

对于 t 中重复字符，我们寻找的子字符串中该字符数量必须不少于 t 中该字符数量。 如果 s 中存在这样的子串，我们保证它是唯一的答案。

**示例 1：**

输入：s = "ADOBECODEBANC", t = "ABC" 输出："BANC" 解释：最小覆盖子串 "BANC" 包含来自字符串 t 的 'A'、'B' 和 'C'。 **示例 2：**

输入：s = "a", t = "a" 输出："a" 解释：整个字符串 s 是最小覆盖子串。 **示例 3:**

输入: s = "a", t = "aa" 输出: "" 解释: t 中两个字符 'a' 均应包含在 s 的子串中， 因此没有符合条件的子字符串，返回空字符串。

**提示：**

m == s.length n == t.length 1 <= m, n <= 105 s 和 t 由英文字母组成

**思路：** 滑动窗口，先用一个 map 统计 t 中每个字母的个数，然后遍历s，用一个 map 记录当前窗口的元素，另一个 map 记录当前窗口已满足的元素数量，当满足最小数量时维持这个最小数量，l 不断增加缩小窗口大小。

```
/**
 * @param {string} s
 * @param {string} t
 * @return {string}
 */
var minWindow = function(s, t) {
    var ms=new Map(),mt=new Map(),ck=new Map(),sum=0,l=0,ans=s;
       
    for(let i=0;i<t.length;i++)
    {
        if(!mt.get(t[i]))sum++;
        mt.set(t[i],(mt.get(t[i])||0)+ 1);
    }
    //console.log(sum);
    for(let i=0;i<s.length;i++)
    {    
        ms.set(s[i], (ms.get(s[i]) || 0) + 1);
        if(mt.get(s[i])&&mt.get(s[i])==ms.get(s[i])){
             //console.log(i+'\n');
            if(!ck.get(s[i])){
                
                ck.set(s[i],1);
                sum--;
            }
        }
        
        //console.log(ms[s[i]]);
        //console.log(ms.get('B')+" "+i+' '+l+'\n');
        if(mt.get(s[i])<=ms.get(s[i])){
            
            if(sum==0){
                while(!mt.get(s[l])||(mt.get(s[l])&&ms.get(s[l])>mt.get(s[l])))
                {
                    if(mt.get(s[l]))ms.set(s[l], ms.get(s[l]) - 1);
                    l++;
                    if(l==s.length)break;
                    //console.log(ms.get('B')+' '+l+i+'\n');
                }
                if(ans.length>i-l+1)
                {
                    ans=s.slice(l,i+1);
                }
            }
            //console.log(l+" "+i+'\n'+sum)
        }
    }
    while(!mt.get(s[l])||mt.get(s[l])&&ms.get(s[l])>mt.get(s[l]))
    {       
        ms.set(s[l], ms.get(s[l]) - 1);
        
        l++;
        if(l==s.length)break;
        
    }
    //console.log(l);
    if(ans.length>s.length-l)
    {
        ans=s.slice(l);
    }
    //console.log(sum);
    if(sum!=0)return "";
    return ans;
};
```
