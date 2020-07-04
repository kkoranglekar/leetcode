# 515. Find Largest Value in Each Tree Row

# Solution

Approach- BFS
To solve the given problem we need to make use of a Breadth First Search. In BFS, we start by pushing the root node into a queue. Then, we remove an element(node) from the front of the queuequeue. For every node removed from the queuequeue, we add all its children to the back of the same queuequeue. We keep on continuing this process till the queuequeue becomes empty. In this way, we can traverse the given tree on a level-by-level basis.

The steps to be performed are listed below:
1. Check if the root is not null and add to empty queue q.
2. Initialize size to size of queue and maax to Integer.MIN_VALUE
3. pop from the node from the queue and compare it's value with max. If greater than max, assign the value to max.
4. If left or right child exist to the node add them to the queue.
5. Iterate step 3 & 4 till size of queue.
7. store the value of max into ArraList.
8. Goto Step 2 until queue is not empty.
9. return the ArrayList.

# Complexity Analysis

Time complexity : O(n). 
The whole tree is traversed atmost once. Here, nn refers to the number of nodes in the given binary tree.

Space complexity : O(m). 
The size of queue or temp can grow upto atmost the maximum number of nodes at any level in the given binary tree. Here, m refers to the maximum mumber of nodes at any level in the input tree.


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

