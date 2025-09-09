# Indexes-of-Subarray-Sum
/**********
Q.The Indexes of Subarray Sum problem asks to find the start and end (left and right) 1-based indices of the first continuous subarray within an unsorted array of non-negative integers that adds up to a given target sum. If no such subarray exists, you return an array containing just the element -1. 
************/
class Solution {
public:
    vector<int> subarraySum(vector<int> arr, int target) {
        int n = arr.size();
        int start = 0, end = 0;
        int current_sum = 0;

        while (end < n) {
            current_sum += arr[end];

            while (current_sum > target && start < end) {
                current_sum -= arr[start];
                start++;
            }

            if (current_sum == target) {
                return {start + 1, end + 1}; // 1-based index
            }

            end++;
        }

        return {-1};
    }
};
