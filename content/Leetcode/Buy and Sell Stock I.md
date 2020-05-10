+++
title="Best Time to Buy and Sell Stock"
date=2020-05-09
+++

## Problem Link
[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

## How to solve

## Complexity Analysis

## Time: O(N)

## Space: O(1)

## Solutions

## Python

``` python
def maxProfit(self, prices: List[int]) -> int:
    minBuy = float("inf")
    maxProfit = 0

    for price in prices:
        minBuy = min(minBuy, price)
        maxProfit = max(maxProfit, price - minBuy)

    return maxProfit
```

## Go

``` go
func maxProfit(prices []int) int {
    var minBuy int = math.MaxInt32
    var maxProfit int = 0

    for _, price := range prices {
        minBuy = Min(minBuy, price)
        maxProfit = Max(maxProfit, price - minBuy)
    }

    return maxProfit
}

func Min(x, y int) int {
    if x < y {
        return x
    }
    return y
}

func Max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```

## Rust

``` rust
pub fn max_profit(prices: Vec<i32>) -> i32 {
    let mut minBuy = std::i32::MAX;
    let mut maxProfit = 0;

    for &price in &prices {
        minBuy = std::cmp::min(minBuy, price);
        maxProfit = std::cmp::max(maxProfit, price - minBuy);
    }

    maxProfit
}
```