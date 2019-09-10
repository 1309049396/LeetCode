

# 题解
**暴力解法**

```java
public static int longestCommonSubstring(String s1, String s2) {

        char[] str1 = s1.toCharArray();
        char[] str2 = s2.toCharArray();
        int l1 = str1.length;
        int l2 = str2.length;
        if (l1 == 0 || l2 == 0) {
            return 0;
        }

        //最大长度
        int maxLength = 0;
        int start1 = -1;
        int start2 = -1;
        for (int i = 0; i < l1; i++) {
            for (int j = 0; j < l2; j ++) {
                int m = i;
                int n = j;
                //相同子串的长度
                int length = 0;
                while (m < l1 && n < l2) {
                    if (str1[m] != str2[n]) {
                        break;
                    }
                    m++;
                    n++;
                    length++;
                }
                if (length > maxLength) {
                    maxLength = length;
                }
            }
        }
        return maxLength;
    }
```

**动态规划（没理解）**

```java
public static int longestCommonSubstring(String str1, String str2) {
        int len1 = str1.length();
        int len2 = str2.length();
        int result = 0;     //记录最长公共子串长度
        int c[][] = new int[len1+1][len2+1];
        for (int i = 0; i <= len1; i++) {
            for( int j = 0; j <= len2; j++) {
                if(i == 0 || j == 0) {
                    c[i][j] = 0;
                } else if (str1.charAt(i-1) == str2.charAt(j-1)) {
                    c[i][j] = c[i-1][j-1] + 1;
                    result = Math.max(c[i][j], result);
                } else {
                    c[i][j] = 0;
                }
            }
        }
        return result;
    }
```