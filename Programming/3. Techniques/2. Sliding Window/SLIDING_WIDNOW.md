---
layout: default
title: Sliding Window
parent: Problem-Solving Patterns
grand_parent: Programming
has_children: true
nav_order: 2
permalink: /programming/problem-solving-pattern/sliding-window
tags: [Problem-Solving Pattern]
date: 2025-01-01
---

# Sliding Window
{% include post-meta.html %}

---

# When Sliding Window might be use d?
- Problem is related to string or array
- We are asked to find sub-array or substring
- We might be asked to get somthing largest or smallest in the window
- We might be given some windows of size k in the arrays or string

---

#  Common Use Cases for Sliding Window

####  Finding Maximum/Minimum in a Subarray of Fixed Size  
**Example:** Maximum in every subarray of size \( k \)  
**Problem:** Given an array, find the maximum of every contiguous subarray of size \( k \).  
**Solution:** Instead of recomputing for each window from scratch, use a **deque** to maintain the maximum efficiently.  

---

####  Finding a Subarray with a Given Sum  
**Example:** Longest subarray with sum ≤ \( k \)  
**Problem:** Given an array of numbers, find the longest subarray with a sum ≤ \( k \).  
**Solution:** Use a **variable-size sliding window** to dynamically expand and shrink the window while maintaining the sum.  

---

####  String Processing & Pattern Matching  
**Example:** Find anagrams of a pattern in a string  
**Problem:** Given a string \( s \) and a pattern \( p \), find all start indices where \( p \)'s anagrams appear in \( s \).  
**Solution:** Use a **fixed-size sliding window** to maintain character counts and efficiently compare with the pattern.  

---

####  Data Stream Processing  
**Example:** Moving average over the last \( k \) elements  
**Problem:** In a real-time data stream, compute the moving average of the last \( k \) numbers.  
**Solution:** Use a **queue** or **circular buffer** to maintain the sum of the last \( k \) elements.  

---

####  Longest Substring Without Repeating Characters  
**Example:** Finding the length of the longest substring with unique characters  
**Problem:** Given a string, find the longest substring without repeating characters.  
**Solution:** Use a **variable-size sliding window** with a **hash set** to track unique characters.  

---

####  Image Processing (Convolution)  
**Example:** Applying a kernel filter over an image  
**Problem:** In image processing, a **convolution filter** (like a blur or edge detection) needs to be applied over a moving window of pixels.  
**Solution:** Use a **sliding window approach** to process pixels efficiently.  

---

####  Network Protocols (TCP Flow Control)  
**Example:** Sliding Window Protocol  
**Problem:** In **TCP congestion control**, data packets are sent in a window size that dynamically adjusts to network conditions.  
**Solution:** Use a **sliding window** to track sent and acknowledged packets.  

---

# Types of Sliding Window  
###  Fixed-size Sliding Window  
- The window moves one step at a time while keeping its size constant.  
- **Example:** Moving average over last \( k \) elements.  


###  Variable-size Sliding Window  
- The window size changes dynamically based on conditions.  
- **Example:** Longest subarray with sum ≤ \( k \).  

---

# Why Use Sliding Window?  
✅ **Optimized Performance** – Reduces time complexity from **O(n²) to O(n)** in many cases.  
✅ **Efficient Memory Usage** – Avoids storing unnecessary elements.  
✅ **Streaming Data Processing** – Can handle **real-time and large-scale data** effectively.  
