class Solution {
    public int lengthOfLastWord(String s) {
        if (s.length() == 0) return 0;
        int lastLen = 0;
        int startLen = s.length()-1;
        
        for(int i = startLen;i>=0;i--) {
            if(!Character.isWhitespace(s.charAt(i))) {
                break;
            } else {
                startLen -= 1;
            }
        }
        for(int j = startLen;j>=0;j--) {
            if(Character.isWhitespace(s.charAt(j))){
                return lastLen;
            } else{
                lastLen += 1;
            }
        }
        return lastLen;
    }
}

Iterate the string from the end.
use String.charAt(i) to get the Character by index
use String.indexOf(c) to get the index of specific Character in the string 