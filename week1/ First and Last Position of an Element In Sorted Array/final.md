```cpp

//accepted by platform

//using binary search

int firstOccurrence(vector<int>& arr, int n , int k){ // to claculate first occurrence of the target
    int startIdx=0,endIdx=n-1;
    int ans=-1;
    while(startIdx<=endIdx){
        int midIdx = startIdx + (endIdx - startIdx)/2;
        if(arr[midIdx]==k){
            if(midIdx!=0 && arr[midIdx-1]!=k){ // if k is not there before midIdx then it will won't check further
                return midIdx;
            }
            ans=midIdx;
            endIdx=midIdx-1;
        }
        else if(k>arr[midIdx]) startIdx=midIdx+1;
        else endIdx=midIdx-1;
    }
    return ans;
}

int lastOccurrence(vector<int>& arr, int n , int k){ // to claculate last occurrence of the target
    int startIdx=0,endIdx=n-1;
    int ans=-1;
    while(startIdx<=endIdx){
        int midIdx = startIdx + (endIdx - startIdx)/2;
        if(arr[midIdx]==k){
            if(midIdx!=n-1 && arr[midIdx+1]!=k){ //if k is not there after midIdx then it will won't check further
                return midIdx;
            }
            ans=midIdx;
            startIdx=midIdx+1;
        }
        else if(k>arr[midIdx]) startIdx=midIdx+1;
        else endIdx=midIdx-1;
    }
    return ans;
}

pair<int, int> firstAndLastPosition(vector<int>& arr, int n, int k)
{
    int firstPos=firstOccurrence(arr,n,k);
    int lastPos=lastOccurrence(arr,n,k);
    return make_pair(firstPos,lastPos);
}


/*
time complexity is O(2*log n) ~ O(log n)
space complexity is O(1)
solution accepted and this is my final solution for this question but still it left behinf 50% of solvers
so we can still need more optimized solution

-Initially I used a nested binary search once I found the target value. Although logically correct, it caused a TLE because each search added extra log(n) complexity inside another binary search loop.
- The optimized approach uses two *independent* binary searches: one for the first occurrence, one for the last.
- Both searches follow the standard binary search template but with slight tweaks to check for boundaries.
- This improves clarity and efficiency.
*/