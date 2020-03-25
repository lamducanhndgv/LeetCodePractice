# LỜI GIẢI 

## Cách giải 1: Sử dụng Inorder Traversal và Mảng lưu kết

#### Ý tưởng 
-   Nhận ra rằng output của đề bài chính là kết quả của duyệt theo Inorder.
-   Tạo mảng rỗng ```res``` để lưu các node đã duyệt.
-   Hàm ```inorderTraversal``` dùng để duyệt trung thứ tự ( theo đệ quy ) gồm 2 tham số :
    -   ```node```: Node hiện tại đang duyệt
    -   ```result```: mảng chứa kết quả
-   Trong khi duyệt:
    -    nếu ```res``` rỗng thì thêm ```node``` vào ```res```.
    -    nếu ```res``` đã có phần tử, thì ta gắn ```node``` vào bên phải phần tử ```res``` cuối cùng.
-   Kết quả trả về của bài toán chính là phần tử đầu tiên của ```res```

#### Coding

```python
class Solution:
    def inorderTraversal(self, node, result):
        if node:
            self.inorderTraversal(node.left, result)     
            temp = TreeNode(node.val)     
            if result:
                result[-1].right = temp
            result.append(temp)
            self.inorderTraversal(node.right, result)
            
    def increasingBST(self, root: TreeNode) -> TreeNode:
        res = [] 
        self.inorderTraversal(root, res)
        return res[0]
```

## Cách giải 2  ( Theo Leetcode ): Duyệt và liên kết lại các node trong cây ( Không tạo thêm bộ nhớ phụ )

#### Coding

```python
class Solution:
    def increasingBST(self, root):
        def inorder(node):
            if node:
                inorder(node.left)
                node.left = None
                self.cur.right = node
                self.cur = node
                inorder(node.right)

        ans = self.cur = TreeNode(None)
        inorder(root)
        return ans.right
```
