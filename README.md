/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */

//           //////////////////ATISHAY\\\\\\\\\\\\\\\\           \\
//           \\\\\\\\\\\\\\\\\\\JAIN//////////////////           \\

public class NodeInfo{
    int height;
    int diameter;
    public NodeInfo(int height, int diameter){
        this.height=height;
        this.diameter=diameter;
    }
}

class Solution {
    public int diameterOfBinaryTree(TreeNode root) {
        NodeInfo ans = dia(root);
        return ans.diameter;
    }

    public NodeInfo dia(TreeNode root){
        if(root==null){
            return new NodeInfo(0,0);
        }
        NodeInfo left = dia(root.left);
        NodeInfo right = dia(root.right);
        int diameter = Math.max(Math.max(left.diameter, right.diameter), left.height+right.height);
        int height = Math.max(left.height,right.height)+1;

        return new NodeInfo(height, diameter);
    }
}
