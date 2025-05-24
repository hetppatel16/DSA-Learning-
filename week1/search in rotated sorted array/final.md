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

/*
time complexity:-O(log n) , space complexity:-O(1)
the code use binary search approch to getting correct answer which is seems best for this question.
in this solution i see if the array is rotated as discribe in question the it has two monotonic parts.
part 1:- increasing value upto maximum value of entire array
part 2:- increasing value but all less then nums[0] (as per questions rotation discription)
so we need to find it our target is may be lie on part 1 or part 2.
there is too many same things repeted in both parts like both needs standard binary search.
now once we found where can the target may there.
we can cut down rest part by binary search and by checking mid element is >=nums[0]  or mid element is < nums[0].

for example we found that we need to search in part 1 but if the mid element is < nums[0] (it means that it is on part 2) so we reduced the end index.

hope i explanation is understandable
*/