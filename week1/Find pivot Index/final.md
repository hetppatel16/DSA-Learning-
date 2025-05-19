```cpp
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int n = nums.size();
        for(int i=1;i<n;i++){ // calculate prefix sum
            nums[i]+=nums[i-1];
        }
        //as we need left most pivot element
        //rest everything is small maths nothing to explain more if you try your own
        if(nums[n-1]==nums[0]) return 0;
        for(int i=1;i<n-1;i++){
            if(nums[i-1]==(nums[n-1]-nums[i])) return i;
        }
        if(nums[n-2]==0) return n-1;
        return -1;
    }
};



/*
time complexity:-O(n)
space complexity:-O(1)

and yuppp this is one of the best solution for this question from my side and also on leetcode
it beats 100% in time comp and ~95% in space comp.
*/