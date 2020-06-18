### Method 1: Inorder Traversal

BST 的 in-order traversal 会得到一个递增的序列
类似于 LC.98

```cpp
class Solution {
public:
    int kthSmallest(TreeNode* root, int k) {
        inOrder(root, k);
        return res;
    }
private:
    int cnt = 0;    // 访问了第几个节点
    int res = 0;
    void inOrder(TreeNode* root, int k) {
        if (!root || cnt > k) return;   // cnt > k 说明找到了
        inOrder(root->left, k);
        cnt += 1;
        if (cnt == k) {
            res = root->val;
            return; // 大大提升效率，不用再向右找了
        }
        inOrder(root->right, k);
    }
};
```
Time complexity: O(n)

### Method 2: Iteration (Stack)
```cpp
class Solution {
public:
    int kthSmallest(TreeNode* root, int k) {
        int cnt = 0;
        stack<TreeNode*> stk;
        
        while (root || !stk.empty()) {
            while (root) {  // 当前节点不为空就一直往左走
                stk.push(root);
                root = root->left;
            }
            root = stk.top();
            stk.pop();
            cnt += 1;
            if (cnt == k) return root->val; // 找到了
            root = root->right;
        }
        return -1; // not found
    }
};
```
速度跟 recursion 差不多
但是空间竟然更少。。。

### Method 3: Binary Serach

time complexity: O(N) best, O(N^2) worst

```java
// 用JAVA 写的，看一看就好，不是最优解
public int kthSmallest(TreeNode root, int k) {
      int count = countNodes(root.left);    数一下左子树有多少个节点
      if (k <= count) {
          return kthSmallest(root.left, k);
      } else if (k > count + 1) {
          return kthSmallest(root.right, k-1-count); // 1 is counted as current node
      }
      
      return root.val;
  }
  
  public int countNodes(TreeNode n) {
      if (n == null) return 0;
      
      return 1 + countNodes(n.left) + countNodes(n.right);
  }
```