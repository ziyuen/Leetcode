    public int strStr(String s, String t) {
        if (t.isEmpty()) return 0; // edge case: "",""=>0  "a",""=>0
        for (int i = 0; i <= s.length() - t.length(); i++) {
            for (int j = 0; j < t.length() && s.charAt(i + j) == t.charAt(j); j++)
                if (j == t.length() - 1) return i;
        }
        return -1;
    }

Better method:
    https://www.youtube.com/watch?v=BXCEFAzhxGY

时间复杂度：假设 haystack 和 needle 的长度分别是 n 和 k，对于每一个 i ，我们最多执行 k - 1 次，总共会有 n 个 i ，所以时间复杂度是 O（kn）。

空间复杂度：O（1）。