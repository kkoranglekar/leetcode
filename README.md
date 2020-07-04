# leetcode 515. Find Largest Value in Each Tree Row

class Solution {
    public List<Integer> largestValues(TreeNode root) {
        
        List<Integer> ans = new ArrayList<Integer>();
        Queue<TreeNode> q =new LinkedList<>();
        TreeNode temp;
        if(root != null)
            q.offer(root);
        
        while(!q.isEmpty())
        {
            int size = q.size();
            int max = Integer.MIN_VALUE;
           for(int i = 0 ; i < size ; i++)
           {
               temp = q.poll();
               max = Math.max(max , temp.val);
               
                if(temp.left != null)
                   q.offer(temp.left);
                if(temp.right != null)
                   q.offer(temp.right);
           }
            ans.add(max);
        }
        
        return ans;
    }
}
