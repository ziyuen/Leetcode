// Use binary serach in sorted array with increasing order.

public int searchInsert(int[] nums, int target) {
    int low = 0, high = nums.length-1;
    while(low <= high){
        // or use mid = low + (high - low)>>1 to prevent overflow 
        // if low and high are very big
        int mid = (low+high)/2; 
        if(nums[mid] == target) return mid;
        else if(nums[mid] > target) high = mid-1;
        else low = mid+1;
    }
    return low;
}

时间复杂度： O(log n)
空间复杂度： O(1)