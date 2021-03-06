+++
title="3Sum"
date=2020-05-11

[taxonomies]
tags = ["Array"]
authors = ["Allan Phu"]
+++

## Problem Link

[https://leetcode.com/problems/3sum](https://leetcode.com/problems/3sum)

## How to solve

Iterate through the first `N - 2` numbers, fixing each number as a possible first number in our triplet. At each iteration, we use two pointers, `lo` and `hi`. We initialize `lo` to point to the first number after `i`, and `hi` to point to the last number. Move both pointers inwards until you find two numbers that when summed with `i`, make a valid triplet.

## Complexity Analysis

## Time: O(N<sup>2</sup>)

The outer for loop runs at least N - 2 times. In the worst case, the inner for-loop will have to run O(N) times.

## Space: O(log N)

nums.sort() uses log N space for function calls.

## Solutions

## Python

``` python
def threeSum(self, nums: List[int]) -> List[List[int]]:
    nums.sort()
    ans = []

    for i in range(len(nums) - 2):
        if nums[i] > 0:
            return ans
        if i > 0 and nums[i - 1] == nums[i]:
            continue

        l = i + 1
        r = len(nums) - 1

        while l < r:
            sum_triple = nums[i] + nums[l] + nums[r]

            if sum_triple > 0:
                r -= 1
            elif sum_triple < 0:
                l += 1
            else:
                ans.append([nums[i], nums[l], nums[r]])
                while l < r and nums[l] == nums[l + 1]:
                    l += 1
                while l < r and nums[r - 1] == nums[r]:
                    r -= 1
                l += 1
                r -= 1

    return ans
```

## Go

``` go
import "sort"

func threeSum(nums []int) [][]int {
    sort.Ints(nums)
    ans := make([][]int, 0)

    for i := 0; i < len(nums) - 2; i++ {
        if nums[i] > 0 {
            return ans
        } else if (i > 0) && (nums[i - 1] == nums[i]) {
            continue
        }

        l := i + 1
        r := len(nums) - 1

        for l < r {
            sum_triple := nums[i] + nums[l] + nums[r]

            if sum_triple < 0 {
                l += 1
            } else if sum_triple > 0 {
                r -= 1
            } else {
                ans = append(ans, []int{nums[i], nums[l], nums[r]})

                for (l < r) && (nums[l] == nums[l + 1]) {
                    l += 1
                }
                for (l < r) && (nums[r] == nums[r - 1]) {
                    r -= 1
                }
                l += 1
                r -= 1
            }
        }
    }
    return ans
```

## Rust

``` rust
    pub fn three_sum(mut nums: Vec<i32>) -> Vec<Vec<i32>> {
        if nums.len() < 3 {
            return Vec::<Vec<i32>>::new();
        }
        nums.sort();
        let mut ans: Vec<Vec<i32>> = Vec::new();

        for i in 0..nums.len() - 2 {
            if nums[i] > 0 {
                return ans;
            } else if (i > 0) && (nums[i - 1] == nums[i]) {
                continue;
            }

            let mut l = i + 1;
            let mut r = nums.len() - 1;

            while l < r {
                let mut sum_triple = nums[i] + nums[l] + nums[r];

                if sum_triple < 0 {
                    l += 1;
                } else if sum_triple > 0 {
                    r -= 1;
                } else {
                    ans.push(vec![nums[i], nums[l], nums[r]]);

                    while (l < r) && (nums[l] == nums[l + 1]) {
                        l += 1;
                    }
                    while (l < r) && (nums[r] == nums[r - 1]) {
                        r -= 1;
                    }
                    l += 1;
                    r -= 1;
                }
            }
       }
        ans
    }
}
```
