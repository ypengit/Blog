### #500 Keyboard Row
**Description:**
>Given a List of words, return the words that can be typed using letters of alphabet on only one row's of American keyboard like the image below.

**Example**
>Input: ["Hello", "Alaska", "Dad", "Peace"]  
>Output: ["Alaska", "Dad"]  

**Node**
>You may use one character in the keyboard more than once.
>You may assume the input string will only contain letters of alphabet.

**Code**
```C++
class Solution {
public:
	bool test(string s)
	{
		transform(s.begin(), s.end(), s.begin(), ::tolower);
		unordered_set<string> line1 = { "q", "w", "e", "r", "t", "y", "u", "i", "o", "p" };
		unordered_set<string> line2 = { "a", "s", "d", "f", "g", "h", "j", "k", "l" };
		unordered_set<string> line3 = { "z", "x", "c", "v", "b", "n", "m" };
		
		unordered_set<string>::iterator it;
		
		string s2 = s.substr(0, 1);

		it = line1.find(s2);

		int type = -1;

		if (it != line1.end())
		{
			type = 1;
		}		
		it = line2.find(s2);
		if (it != line2.end())
		{
			type = 2;
		}		
		
		it = line3.find(s2);
		if (it != line3.end())
		{
			type = 3;
		}

		unordered_set<string> targetSet;

		switch (type)
		{
		case 1:targetSet = line1; break;
		case 2:targetSet = line2; break;
		case 3:targetSet = line3; break;
		default:
			break;
		}

		for (int i = 0; i < s.size();i++)
		{
			string s1 = s.substr(i,1);
			unordered_set<string>::iterator it;
			it = targetSet.find(s1);
			if (it == targetSet.end())
			{
				return false;
			}

		}
		return true;

	}
	vector<string> findWords(vector<string>& words) {
		vector<string> str;
		for (int i = 0; i < words.size(); i++){
			if (!test(words[i]))
			{
				continue;
			}
			str.push_back(words[i]);
		}
		return str;
	}
};
```