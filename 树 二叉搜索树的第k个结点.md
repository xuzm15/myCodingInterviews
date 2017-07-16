# 树 二叉搜索树的第k个结点

* 给定一颗二叉搜索树，请找出其中的第k大的结点。例如， 5 / \ 3 7 /\ /\ 2 4 6 8 中，按结点数值大小顺序第三个结点的值为4。

* 二叉搜索树的中序遍历即为从大到小的排序，找到中序遍历的第k个输出值，即为所求。

给定一颗二叉搜索树，请找出其中的第k大的结点。例如， 5 / \ 3 7 /\ /\ 2 4 6 8 中，按结点数值大小顺序第三个结点的值为4。

```
/*
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    
    private int index = 0;
    
    TreeNode KthNode(TreeNode pRoot, int k)
    {
        if (pRoot == null) {
            return null;
        }
        TreeNode ansLeft = KthNode(pRoot.left, k);
        if (ansLeft != null) {
            return ansLeft;
        }
        index++;
        if (index == k) {
            return pRoot;
        }
        
        TreeNode ansRight = KthNode(pRoot.right, k);
        if (ansRight != null) {
            return ansRight;
        }
        return null;
    }
}
```