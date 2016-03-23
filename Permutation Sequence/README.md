Permutation Sequence
==========

## C++


```cpp
class Solution {
public:
	string getPermutation(int n, int k) {
		static vector<int> f(1, 1);
		for (int i(f.size() + 1); i <= n; ++i)
			f.push_back(f.back() * i);

		string result(n, '1');
		for (int i(0); i < n; ++i)
			result[i] += i;

		--k;
		for (int i(0); k; ++i)
		{
			int index = k / f[n - i - 2] + i;
			
			// Insert result[index] before result[i]
			char tmp = result[index];
			for (int j(index - 1); j >= i; --j)
				result[j + 1] = result[j];
			result[i] = tmp;

			k -= (index - i) * f[n - i - 2];
		}
		return result;
	}
};
```
