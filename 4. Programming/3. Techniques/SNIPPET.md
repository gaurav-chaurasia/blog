---
layout: default
title: Snippet
# nav_order: 
parent: Problem-Solving Patterns
grand_parent: Programming
tags: #[]
toc: true
toc_sticky: true
date: 2025-01-01
permalink: /programming/problem-solving-pattern/snippet
---

# Snippets
{: .no_toc }
{% include post-meta.html %}

---

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

--- 


- #### Max-Sum-Subarray
```cpp
    // maximum sum subarray
    int best = 0; sum = 0;
    for (int i = 0; i < n; i++) {
        sum = max(arr[i], sum + arr[i]);
        best = max(best, sum);
    }
```
- #### Binary-Exponentiation
```cpp
    // find a ^ b or a**b in just O( log(b) ) time 
    long long power(long long a, long long b) {
        long long result = 1;
        while (b > 0) {
            if (b % 2 == 1)
                result = (result * a) % MOD;

            a = (a * a) % MOD;
            b /= 2;
        }
        return result;
    }
```

- #### Prime-Factors
```cpp
    // 24 = (2^3)*(3) ==> [2, 2, 2, 3]
    vector<int> prime_factors(int n) {
        vector<int> f;

        for (int x = 2; x*x <= n; x++) {
            while (n%x == 0) {
                f.push_back(x);
                n /= x;
            }
        }

        if (n > 1) 
            f.push_back(n);

        return f;
    }
```
- #### Prime-Number-Seive
```cpp
    vector<int> seive(int n) {
        vector<int> seive(n + 1, true);

        for (int i = 2; i * i <= n; i++) {
            for (int j = 2; j * i <= n; j++) {
                seive[j*i] = false;
            }
        }

        return seive;
    }
```
- #### Binomial-Coefficient
```cpp
    // C(n, r) => nCr
    // C(n, r) = C(n - 1, r - 1) + C(n - 1, r)
    int dp[n + 1][r + 1];
    memset(dp, 0, sizeof(dp));
    
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= min(i, r); j++) {
            if (j == 0 || j == i) {
                dp[i][j] = 1;
            }
            else {
                dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
            }
        }
    }
    // dp[n][r] => represent the answer
```
- #### Permutation-Coefficient
```cpp
    // P(n, r) => nPr
    // P(n, r) = r * P(n - 1, r - 1) + P(n - 1, r)
    int dp[n + 1][r + 1];
    memset(dp, 0, sizeof(dp));

    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= min(i, r); j++) {
            if (j == 0) {
                dp[i][j] = 1;
            }
            else {
                dp[i][j] = dp[i - 1][j] + (j * dp[i - 1][j - 1]);
            }
        }
    }

    return dp[n][r];
```