class Solution {
    public int maxSubArray(int[] nums) {
        int maxSoFar = nums[0], maxEndinghere = nums[0];
       
        for(int i=1;i<nums.length;i++) {
            if(maxEndinghere+nums[i] > nums[i]) maxEndinghere += nums[i];
            else maxEndinghere = nums[i];
            if(maxSoFar < maxEndinghere) maxSoFar = maxEndinghere;
        }
        return maxSoFar;
    }
}

拆分为subproblem，从左到右，找出每个index对应的最大值。。
一直到最后一个index。。。
https://www.youtube.com/watch?v=2MmGzdiKR9Y