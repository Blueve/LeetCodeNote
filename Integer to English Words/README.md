Integer to English Words
==========

## C++


```cpp
class Solution {
public:
    string numberToWords(int num) {
        vector<string> num_dict = 
            {"Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"};
        vector<string> ten_dict = 
            {"Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"};
        vector<string> hun_dict =
            {"Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"};
        vector<string> bit_dict = 
            {"Thousand", "Million", "Billion"};
        if(num == 0) return "Zero";
        string words;
        int p = 0;
        while(num)
        {
            int abc = num % 1000;
            num /= 1000;
            
            int bc = abc % 100;
            int a = abc / 100;
            
            if(bc && bc < 20)
            {
                if(bc < 10) words = num_dict[bc] + ' ' + words;
                else words = ten_dict[bc - 10] + ' ' + words;
            }
            else if(bc)
            {
                int b = bc / 10;
                int c = bc % 10;
                
                if(c) words = num_dict[c] + ' ' + words;
                if(b) words = hun_dict[b - 2] + ' ' + words;
            }
            
            if(a) words = num_dict[a] + " Hundred " + words;
            if(num % 1000 && num || num && num < 1000)
                words = bit_dict[p] + ' ' + words;
            ++p;
        }
        words.pop_back();
        return words;
    }
};
```
