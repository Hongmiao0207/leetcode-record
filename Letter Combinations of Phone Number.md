Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![](../Leetcode_Pictures/Snipaste_2022-02-08_09-37-35.png)

Example1:
```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

Example2:
```
Input: digits = ""
Output: []
```

Example3:
```
Input: digits = "2"
Output: ["a","b","c"]
```

Constraints:

a. 0 <= digits.length <= 4
b. digits[i] is a digit in the range ['2', '9']

暴力破解:
```java
class Solution {
    public List<String> letterCombinations(String digits) {

        if ("".equals(digits)){
            return new ArrayList<String>();
        }

        char[] digitsCharArray = digits.toCharArray();

        int digitsLength = digitsCharArray.length;

        if(1 == digitsLength){
            return getLetterArray(String.valueOf(digitsCharArray[0]));
        }

        List<String> firstLetterArray = new ArrayList<>();
        List<String> secondLetterArray = new ArrayList<>();
        List<String> thirdLetterArray = new ArrayList<>();
        List<String> fourthLetterArray = new ArrayList<>();
        List<String> answer = new ArrayList<>();

        for(int i = 0; i < digitsLength; ++i){

            if (i == 0){
                firstLetterArray = getLetterArray(String.valueOf(digitsCharArray[i]));
            }else if(i == 1){
                secondLetterArray = getLetterArray(String.valueOf(digitsCharArray[i]));
            }else if(i == 2){
                thirdLetterArray = getLetterArray(String.valueOf(digitsCharArray[i]));
            }else if(i == 3){
                fourthLetterArray = getLetterArray(String.valueOf(digitsCharArray[i]));
            }

        }

        if (!fourthLetterArray.isEmpty()){
            for(String firstLetter : firstLetterArray){
                for(String secondLetter : secondLetterArray){
                    for (String thirdLetter : thirdLetterArray){
                        for (String fourthLetter : fourthLetterArray){
                            answer.add(firstLetter + secondLetter + thirdLetter + fourthLetter);
                        }
                    }
                }
            }
        }else if(!thirdLetterArray.isEmpty()){
            for(String firstLetter : firstLetterArray){
                for(String secondLetter : secondLetterArray){
                    for (String thirdLetter : thirdLetterArray){
                        answer.add(firstLetter + secondLetter + thirdLetter);
                    }
                }
            }
        }else {
            for(String firstLetter : firstLetterArray){
                for(String secondLetter : secondLetterArray){
                    answer.add(firstLetter + secondLetter);
                }
            }
        }

        return answer;
    }

    public List<String> getLetterArray(String s){
        List<String> answer = new ArrayList<>();
        if("2".equals(s)){
            answer.add("a");
            answer.add("b");
            answer.add("c");
        }else if("3".equals(s)){
            answer.add("d");
            answer.add("e");
            answer.add("f");
        }else if("4".equals(s)){
            answer.add("g");
            answer.add("h");
            answer.add("i");
        }else if("5".equals(s)){
            answer.add("j");
            answer.add("k");
            answer.add("l");
        }else if("6".equals(s)){
            answer.add("m");
            answer.add("n");
            answer.add("o");
        }else if("7".equals(s)){
            answer.add("p");
            answer.add("q");
            answer.add("r");
            answer.add("s");
        }else if("8".equals(s)){
            answer.add("t");
            answer.add("u");
            answer.add("v");
        }else if("9".equals(s)){
            answer.add("w");
            answer.add("x");
            answer.add("y");
            answer.add("z");
        }
        return answer;
    } 

}
```

![](../Leetcode_Pictures/Snipaste_2022-02-08_09-42-40.png)

