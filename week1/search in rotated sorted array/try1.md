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

/*
time complexity:-O(3*log n)~O(log n) (but needs more iterations then requires may be improve at some point)
space complexity:-O(1)
in this solution i tried 3 binary search to finad correct answer.
like first i try normal binary search in which if the target is found then return the index.
if not present(not found by simple binary search due to the array is not monotonic completely.
this is required due to some test cases is sorted not rotated so the code only for rotated sorted array won't works correctly).
then it goes to find pivot element (in my case pivot is smallest one which is dividing two monotonic parts ).
now by just checking in which part the target may be present we just apply normal binary search on that monotonic part only
*/