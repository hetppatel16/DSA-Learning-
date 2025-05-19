```cpp
class Solution {
public:
    int pivotIndex(vector<int>& nums) {
        int n=nums.size();
        int leftIdx=0,rightIdx=n-1;
        int leftSum=0,rightSum=0;
        int pivotIdx= leftIdx + (rightIdx-leftIdx)/2;
        while(leftIdx<pivotIdx) leftSum+=nums[leftIdx++];
        leftIdx--;
        while(pivotIdx<rightIdx) rightSum+=nums[rightIdx--];
        rightIdx++;
        while(leftIdx>=0 && rightIdx<=n-1){
            if(leftSum>rightSum){
                leftSum-=nums[leftIdx--];
                rightSum+=nums[--rightIdx];
                pivotIdx--;
            }
            else if(leftSum<rightSum){
                leftSum+=nums[++leftIdx];
                rightSum-=nums[rightIdx++];
                pivotIdx++;
            }
            if(leftSum==rightSum) return pivotIdx;
        }
        return -1;
    }
};


/*
time complexity:- more then O(n)
as i try to solve this by two pointers methods this is also mix of it with binary search so it can reduced time complexity.  but You know what my problem is i want to reduce time complexity maximum and ended up too more and more complex code but that codes also less efficient.

i know i am in learning face so this may be critical if not get my focus on this type of things


just like below code is even more complex and less efficient with few changes though it can give correct output maybe.
*/


class Solution {
public:
int mid(int start,int end){
    return start + (end-start)/2;
}
    int pivotIndex(vector<int>& nums) {
        int n = nums.size();
        int startIdx=0,endIdx=n-1;
        int leftIdx = 0, rightIdx = n-1;
        int leftSum = 0, rightSum = 0;
        int pivotIdx = mid(startIdx,endIdx);
        while (leftIdx < pivotIdx) leftSum += nums[leftIdx++];
        leftIdx--;
        while (pivotIdx < rightIdx) rightSum += nums[rightIdx--];
        rightIdx++;
        while (leftIdx >= 0 && rightIdx <= n - 1) {
            if (leftSum > rightSum) {
                endIdx=pivotIdx-1;
                pivotIdx=mid(startIdx,endIdx);
                while(pivotIdx>=leftIdx) leftSum-=nums[leftIdx--];
                while(pivotIdx<rightIdx) rightSum+=nums[--rightIdx];

            } 
            else if(leftSum < rightSum){
                startIdx=pivotIdx+1;
                pivotIdx=mid(startIdx,endIdx);
                while(pivotIdx>=leftIdx) leftSum+=nums[++leftIdx];
                while(pivotIdx<rightIdx) rightSum-=nums[rightIdx++];
            }
            if (leftSum == rightSum) return pivotIdx;
        }
        return -1;
    }
};