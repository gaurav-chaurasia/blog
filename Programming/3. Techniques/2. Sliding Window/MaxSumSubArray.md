---
layout: default
title: Max Sum Sub Array
parent: Sliding Window
grand_parent: Problem-Solving Patterns
nav_order: 2
permalink: /programming/problem-solving-pattern/sliding-window/max-subarray-of-size-k
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

#define DEB(x) cout << "[ " << #x << " ==> " << x << " ]\n";
#define w(x) int x; cin>>x; while(x--)
#define endl '\n'
#define all(x) begin(x), end(x)
#define f first
#define s second
#define MAX_CHAR 256
#define MOD (int)1e9+7

class Solution {

public:
    void maximum_sum_subarray_of_size_k(int n, vector<int> arr, int k) {
        int mx = INT_MIN;
        int sum = 0;

        // start and end of the window
        int j = 0, i = 0;

        while (j < arr.size()) {
            sum += arr[j];

            // below condition is segnifies that windows is smaller then expected
            // so we need to increment the j to increase the window size
            if (j - i + 1 < k) {
                j++;
            }
            // once window size j - i + 1 == k, our case
            // this is the condition where we get one solution to our problem
            // but we are not sure if this is the max, so we need to compare with max
            // from this time onward we are going to imcrement start and end togather to move the windows
            // and we have to make sure to include the next element and exclude the prev element from the windows
            else if (j - i + 1 == k) {
                mx = max(sum, mx);
                sum -= arr[i];
                i++; j++;
            }
        }
        DEB(mx);
    }

};

 
int main() {
    ios::sync_with_stdio(false);
    cin.tie(0);
    Solution* SOL = new Solution();
    
    int n = 7;
    int k = 3;
    vector<int> arr = {2, 5, 1, 8, 2, 9, 1};
    SOL->maximum_sum_subarray_of_size_k(n, arr, k);
    
    delete SOL;
    return 0;
}


```

