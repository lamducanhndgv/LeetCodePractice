# LỜI GIẢI

## Cách giải 1: Duyệt cây (Đệ quy)

#### Ý tưởng
-   Duyệt toàn bộ cây
-   Nếu tồn tại ít nhất 1 node có giá trị ```node.val``` khác với ```root.val``` thì trả về kết quả ```false```
-   Ngược lại, trả về kết quả ```true```

#### Coding
```python
class Solution:
    def inorderTraversal(self, node, value):
        if node:
            if node.val != value:
                return False
            flag1 = self.inorderTraversal(node.left, value)
            flag2 = self.inorderTraversal(node.right, value)
            return flag1 and flag2
        return True
    
    def isUnivalTree(self, root: TreeNode) -> bool:
        return self.inorderTraversal(root, root.val)
```

## Cách giải 2: Duyệt cây theo chiều ngang ( Breath First Search )

#### Ý tưởng 
-   Tương tự ý tưởng trên
-   Chú ý: với cách duyệt theo chiều ngang, ta có thể ngừng việc duyệt cây ở độ sâu thấp nếu tồn tại node khác giá trị sớm trong quá trình duyệt. 

#### Coding 
```python
class Solution(object):
    def isUnivalTree(self, root):
        def bfs(node):
            index = 0
            queue = [node]
            while index < len(queue):
                tmp = queue[index]
                if tmp.val != root.val:
                    return False
                if tmp.left:
                    queue.append(tmp.left)
                if tmp.right:
                    queue.append(tmp.right)
                index += 1
            return True
    
        result = True
        if root:
            result = bfs(root)
        return result
```