THIS METHOD IS CALLED HORIZONTAL SCANNING

class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0)  return "";
        String prefix = strs[0];    // fetch the first element
        for(int i = 1;i < strs.length;i++) {    // scan horizontally
            while(strs[i].indexOf(prefix) != 0) {   // if not a substring, indexOf() return -1
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }
        }
        return prefix;
    }
}

Some java basics:
To check if an array is empty, use "arr.length == 0", an empty array is not null
To check if a string is empty, use "isEmpty()", or " str == "" "
To fetch the length of a string, use "length()"
To fetch the size of a arrayList, use "size()" 
To check if a string is a substring of the other string,
use "indexOf()", return the beginning index of the substring. If not, return -1. 

isEmpty()
   分配了内存空间，值为空，是绝对的空，是一种有值（值 = 空）  
""
   分配了内存空间，值为空字符串，是相对的空，是一种有值（值 = 空字串）  
null
   是未分配内存空间，无值，是一种无值(值不存在)

时间复杂度：最坏的情况就是 n 个 长度为 m 的完全一样的字符串，假设 S 是所有字符的和，那么 S = m * n，时间复杂度就是 O（S）。当然正常情况下并不需要比较所有字符串，最多比较 n * minLen 个字符就可以了。

空间复杂度：O（1），常数个额外空间。