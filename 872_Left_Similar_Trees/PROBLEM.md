# Leaf-Similar Trees

## Mô tả 
-   Xem xét tất cả giá trị của nút lá một cây nhị phận. Theo thứ tự từ trái qua phải, giá trị của các nút lá tạo thành chuỗi giá trị được gọi là ```left value sequence```
-   Xét cây nhị phân sau:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```
- ```left value sequence``` = (1, 3, 6, 9)

- Xét input là hai cây nhị phân ```root1``` và ```root2```. Kiểm tra hai cây nhị phân có cùng ```left value sequence``` hay không ?


### Ví dụ

#### Ví dụ 1:
-   Input
 
```
    root1

       2
      / \
     2   5
    / \   \
   2   1   2

    root2

       1
      / \
     7   6
    /   / \
   2   1   2
```
-   Output:  ``` true ```
