```cpp
class Solution {
public:
int findMidIdx(int startIdx,int endIdx){
    return startIdx+(endIdx-startIdx)/2;
}
int binarySearch(vector<int>& nums,int target,int startIdx,int endIdx){
    while(startIdx<=endIdx){
        int midIdx=findMidIdx(startIdx,endIdx);
        if(nums[midIdx]==target) return midIdx;
        else if(nums[midIdx]>target) endIdx=midIdx-1;
        else startIdx=midIdx+1;
    }
    return -1;
}
    int findPivotIndex(vector<int>& nums){
        int startIdx=0,endIdx=nums.size()-1;
        while(startIdx<endIdx){
            int midIdx=findMidIdx(startIdx,endIdx);
            if(midIdx==0){
                if(nums[0]>nums[1]) startIdx=1;
                else return 0;
            }
            else if(nums[midIdx]>nums[0]) startIdx=midIdx+1;
            else endIdx=midIdx;
        }
        return startIdx;
    }
    int search(vector<int>& nums, int target) {
        int startIdx=0,endIdx=nums.size()-1;
        int pivot=findPivotIndex(nums);
        int checkIdx = binarySearch(nums,target,startIdx,endIdx);
        if(checkIdx!=-1) return checkIdx;
        
        if(nums[0]>target) return binarySearch(nums,target,pivot,endIdx);
        else return binarySearch(nums,target,startIdx,pivot-1);
        return -1;  
    }
};