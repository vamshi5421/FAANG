# Word Distance
Given a list of words and two wordsword1_and_word2, return the shortest distance between these two words in the list.

```
Example:
Assume that words =["practice", "makes", "perfect", "coding", "makes"].

Input: word1 = “coding”, word2 = “practice”
Output: 3
Input: word1 = "makes", word2 = "coding"
Output: 1
```

# Optimal Solution - Two Pointers
```
class Solution {
public :
    int shortestDistance(String[] wordsDict, String word1, String word2){
        int index1 = -1, index2 = -1;
        int min = Integer.MAX_VALUE;
        for(int i = 0; i < wordsDict.length(); i++){
            if(wordsDict[i].equals(word1)){
                index1 = i;
            }
            if(wordsDict[i].equals(word2)){
                index2 = i;
            }
            if(index1 !=-1 && index2 !=-1){
                min = Math.min(min, Math.abs(index1 - index2));
            }
        }

        return min;
    }
```