```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int startIdx=0,endIdx=nums.size()-1;
            while(startIdx<=endIdx){
                int midIdx=startIdx + (endIdx-startIdx)/2;
                if(nums[midIdx]==target) return midIdx;
                if(target>=nums[0]){
                        if(nums[midIdx]<nums[0] || target<nums[midIdx]) endIdx=midIdx-1;
                        else startIdx=midIdx+1;
                }
                else{
                        if(nums[midIdx]>=nums[0] || target>nums[midIdx]) startIdx=midIdx+1;
                        else endIdx=midIdx-1;
                }
            }
        return -1;
    }
};