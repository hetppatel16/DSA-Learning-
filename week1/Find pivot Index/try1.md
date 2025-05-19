```cpp
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int n=nums.size();
        int leftIdx=0,rightIdx=n-1;
        int leftSum=0,rightSum=0;
        while(leftIdx<=rightIdx){
            if(leftSum==rightSum){
                if(rightIdx==leftIdx){
                    return rightIdx;
                }
                else{
                    if(nums[leftIdx]>nums[rightIdx]){
                        rightSum+=nums[rightIdx];
                        rightIdx--;
                    }
                    else{
                        leftSum+=nums[leftIdx];
                        leftIdx++;
                    }
                }
            }
            else if(leftSum>rightSum){
                rightSum+=nums[rightIdx];
                rightIdx--;
            }
            else{
                leftSum+=nums[leftIdx];
                leftIdx++;
            }
        }
        return -1;
    }
};


/*
time complexity:-O(n)  (not sure)
space complexity:-O(1)
in this try1 we are trying to find the pivot index by two pointers approch hope you understand how i implimented it , but there are too many logical flows in this code like if sum is equal which is the first iteration over here because i initialized both sum = 0.
so it fall leftSum==rightSum cetagory and ultimataly sum is added up for small elements first.
so ultimataly if there are only negative terms or zeros then it won't work as desired.
so this try1 is rejected.
*/