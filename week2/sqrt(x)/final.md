```cpp
class Solution {
public:
    int mySqrt(int x) {
        if(x==0) return 0;
        int left=1;
        int right=x/2+1;
        while(left<right){
            int mid = left + (right-left)/2;
            if(mid<=x/mid){
                if((mid+1)>x/(mid+1)) return mid;
                else left=mid+1;
            }
            else right=mid-1;
            
        }
        return left;
    }
};


/*
time complexity:-O(log(x)) , space complexity:- O(1)
in this approch i try to solve by binary search.
the basic idea is sqrt(x) is always less than or equal to x/2 .
checking the square of mid element is greter than or less than to x.
which is basic binary search.
but as we know the square may be out of the range so i use mid<=x/mid instead of mid*mid<=x
as the question requires only integers as answer so there is no need check as floating number.
and ended up to have left and right such as square of left is less then x but square of right is greater than x and also right-left<=1
so i got the correct answer
*/