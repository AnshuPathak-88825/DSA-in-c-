# Counting Subsets with Given Sum - Dynamic Programming
## Problem Statement
Given an array of integers arr and a target sum val, the task is to count the number of subsets of arr that add up to the given sum val
### DP Approach
``` #include <bits/stdc++.h>
using namespace std;

int CountSubsetSum(vector<int>& arr, int val, int n)
{
	int count=0;
    vector<vector<int>> dp(n,vector<int>(val+1,0));
    for(int i=0;i<arr.size();i++)
    {
        dp[i][0]=1;
    }
    for(int i=1;i<n;i++)
    {
        for (int j = 1; j < val+1; j++)
        {
            if(arr[i-1]<=j)
            {
                dp[i][j]=dp[i-1][j]+dp[i-1][j-arr[i-1]];
            }
            else
            {
                dp[i][j]=dp[i-1][j];
            }
        }
        
    }
    return dp[n-1][val];
}
int main()
{
	vector<int> arr = { 3, 3, 3, 3 };
	cout << CountSubsetSum(arr, 6, arr.size()+1);
}
```