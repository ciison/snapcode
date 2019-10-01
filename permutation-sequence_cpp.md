### [第 k 个序列](https://leetcode-cn.com/problems/permutation-sequence/) cpp 版本



```cpp
class Solution {
public:
    string getPermutation(int n, int k) {
	auto iota = iotax(n);
	vector<int> vec(0);

	for (; iota.size() != 0;) {
	
		auto f = fa(n - 1);
		auto row = k / f;
		auto col = k % f;
		if (col == 0) {
			row -= 1;
			vec.push_back(iota[row]);
			auto bg = vector<int>(0);
			auto ed = vector<int>(0);
			for (int i = 0; i < iota.size(); i++) {
				if (i == row) {
					continue;
				}
				bg.push_back(iota[i]);
			}

			// ... 
			

			iota.clear();
			iota = vector<int>(bg.begin(), bg.end());
			
			//(iota.begin(), iota.end());
			std::reverse(iota.begin(), iota.end());
			
			for (int i = 0; i < iota.size(); i++) {
				vec.push_back(iota[i]);
			}

			iota.clear();

		}
		else {
			vec.push_back(iota[row]);
			auto bg = vector<int>(0);
			//auto ed = vector<int>(0);
			for (int i = 0; i < iota.size(); i++) {
				if (i == row) {
					continue;
				}
				bg.push_back(iota[i]);
			}
			/*
			for (int i = row + 1; i < iota.size(); i++) {
				ed.push_back(iota[i]);
			}

			*/

			iota.clear();
			iota = vector<int>(bg.begin(), bg.end());
			/*for (int i = 0; i < ed.size(); i++) {
				iota.push_back(ed[i]);
			}*/
			
			n -= 1;
			k = col;
		}

	}
	string str;
	for (auto c : vec) {
		str += std::to_string(c);
	}
	return  str;
    }
    
    vector<int> iotax(int n) {
	vector<int> vec(n);
	for (auto i = 0; i < n; i++) {
		vec[i] = i +1;
	}
	return vec;
}
int fa(int n) {
	auto s = 1;
	for (int i = 1; i <= n; i++) {
		s *= i;
	}
	return s;
}
};
```

