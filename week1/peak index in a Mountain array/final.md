```cpp
//solved using binary search

class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int n=arr.size(),startIdx=0,endIdx=n-1;
        while(startIdx<=endIdx){ 
            int midIdx=startIdx + (endIdx-startIdx)/2;
            if(midIdx>0 && midIdx<n-1){
                if(arr[midIdx]>arr[midIdx-1] && arr[midIdx]>arr[midIdx+1]){
                    return midIdx; //if at midIdx there is the peak element b'coz there are smaller element on both the side
                }
                else if(arr[midIdx-1]<arr[midIdx+1]) startIdx=midIdx+1; // if its increasing both  the side that means its behind peak element so we need to move forward
                else endIdx=midIdx-1; //otherwise its after the so we need to move back
            }
            else if(midIdx==0) startIdx++; //to safe from index out of bound error
            else endIdx--;
        }
        return 0;
    }
};


/*
time complexity:- O(log n)
space complexity:- O(1)
*/