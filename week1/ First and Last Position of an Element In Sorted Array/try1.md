```cpp

pair<int, int> firstAndLastPosition(vector<int>& arr, int n, int k)
{
    int firstPos=-1,lastPos=-1;
    int startIdx=0,endIdx=n-1;
    while(startIdx<=endIdx){  //binary search
        int midIdx = startIdx + (endIdx-startIdx)/2;
        if(arr[midIdx]==k){  //if target found
            int endK=midIdx;
            while(startIdx<=endK){  // on the basis of target found i use nested binary search to find first occurennce
                int midFirst = startIdx + (endK-startIdx)/2;
                if(arr[midFirst]==k){
                    if(midFirst==0 || arr[midFirst-1]!=k){ // if it is first element or before its not the same element then it is the first occurennce
                        firstPos=midFirst;
                        break;
                    }
                    else endK=midFirst-1;
                }
                else startIdx=midFirst+1;
            }
            int startK=midIdx;
            while(startK<=endIdx){ //on the basis of target found i use nested binary search to find last occurennce too
                int midLast = startK + (endIdx-startK)/2;
                if(arr[midLast]==k){
                    if(midLast==n-1 || arr[midLast+1]!=k){ // if it is last element or after it not the same element then it is the last occurennce
                        lastPos=midLast;
                        break;
                    }
                    else startK=midLast+1;
                }
                else endIdx=midLast-1;
            }
        }
        else if(k>arr[midIdx]) startIdx = midIdx+1;
        else endIdx = midIdx-1;
    }
    return make_pair(firstPos,lastPos);
}

/*
time complexity :- O(log n * (log m + log m')) where m & m' is reduced size after finding the target(it should be O(log n) but not in this case).
space complexity :- O(1)
the solution is not accepted by Code360 platform due to TLE error(means i need to use more optimized solution in terms of time)
but 5 test cases which is not that big so it can pass without TLE error

and i think logically their is nothing problem in my solution it can give correct output in all test cases but it is bit confusing and less optimized.
*/