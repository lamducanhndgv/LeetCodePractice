# LỜI GIẢI 

## Cách giải 1: Duyệt cây bằng DFS ( Iterative )

#### Ý tưởng 
-   Lấy ví dụ *input 1*:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
-   Ta đảo hai **node** con của ```Node(4)``` , ta được cây như sau:
```
     4
   /   \
  7     2
 / \   / \
6   9 1   3
```
-   Tiếp tục đảo tiếp **node** con của ```Node(7)``` và ```Node(2)```, ta được:
```
     4
   /   \
  2     7
 / \   / \
3   1 9   6
```
-   Hoàn thành việc đảo cây nhị phân.
-   Vậy ý tưởng là duyệt mọi **node** của cây, ở mỗi **node** ta thực hiện đảo left thành right và ngược lại. 

#### Coding

```python
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        if not root:
            return root
        queue = []
        queue.append(root)
        while len(queue):
            temp_node = queue.pop()
            # Invert 2 two child node
            tmp = temp_node.left 
            temp_node.left = temp_node.right
            temp_node.right = tmp
            
            if temp_node.left:
                queue.append(temp_node.left)
            if temp_node.right:
                queue.append(temp_node.right)
        
        return root
```