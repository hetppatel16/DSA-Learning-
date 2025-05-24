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
