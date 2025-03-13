---
layout: default
title: Accurences of Anagram
parent: Sliding Window
grand_parent: Problem-Solving Patterns
nav_order: 2
permalink: /programming/problem-solving-pattern/sliding-window/accurences-of-anagram
tags: [Problem-Solving Pattern, Sliding Window]
date: 2021-05-27
---

# Maximum Sum Subarray of Size K
{% include post-meta.html %}

---


```cpp
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using pi = pair<int, int>;

#define DEB(x) cout << "[ " << #x << " ==> " << x << " ]";
#define w(x) int x; cin>>x; while(x--)
#define endl '\n'
#define all(x) begin(x), end(x)
#define sz(x) (int)(x).size()
#define f first
#define s second
#define MAX_CHAR 256
#define MOD (int)1e9+7

class Solution {

public:
    void count_accurences_of_anagram(string str, string pattern) {
        int n = str.size();
        int k = pattern.size();
        int count, ans = 0;
        unordered_map<char, int> mp;
        
        // keeping count of char in pattern
        for (int i = 0; i < k; i++) 
            mp[pattern[i]]++;
        
        // keeping num of distinct element in pattern
        count = mp.size();

        int i = 0, j = 0;
        while (j < str.size()) {
            if (mp.find(str[j]) != mp.end()) {
                if (mp[str[j]] == 1) {
                    count--;
                }
                mp[str[j]]--;
            }

            if (j - i + 1 < k) {
                j++;
            }
            else if (j - i + 1 == k) {
                if (count == 0) {
                    ans++;
                }

                if (mp.find(str[i]) != mp.end()) {
                    if (mp[str[i]] == 0) {
                        count++;
                    }
                    mp[str[i]]++;
                }
                i++;
                j++;
            }
        }

        cout << ans << endl;
    }

};

 
int main() {
    Solution* SOL = new Solution();
    
    string str = "aabaabaa";
    string pat = "abaa";
    SOL->count_accurences_of_anagram(str, pat);
    
    delete SOL;
    return 0;
}


```