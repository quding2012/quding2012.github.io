
输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字，例如，如果输入如下4 X 4矩阵： 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 则依次打印出数字1,2,3,4,8,12,16,15,14,13,9,5,6,7,11,10.
**通过画图来整理思路，循环的打印的时候把例外情况作为 case 单独测试校验**
```
function printMatrix(matrix)
{
    var row=matrix.length;
    var col=matrix[0].length;
    var res=[];
    if(row==0||col==0){
        return result;
    }
 //   print(result, martix, matrix.length, matrix[0].length, 0, 0);
   // return result;
    
    var left = 0;
    var top = 0;
    var right = col-1;
    var bottom = row-1;
    while (left<=right && top<=bottom) {
        // top
        for (var i=left; i<=right; i++) {
            res.push(matrix[top][i]);
        }
        // right
        for (var i=top+1; i<=bottom; i++) {
            res.push(matrix[i][right]);
        }
        // bottom
        if (top != bottom) {
            for (var i=right-1; i>=left; i--) {
                res.push(matrix[bottom][i]);
            }
        }
        // left
        if (left != right) {
            for (var i=bottom-1; i>top; i--) {
                res.push(matrix[i][left]);
            }
        }
        
        left++;top++;right--;bottom--;
    }
    
    return res;
}
```

操作给定的二叉树，将其变换为源二叉树的镜像。
```
/* function TreeNode(x) {
    this.val = x;
    this.left = null;
    this.right = null;
} */
function Mirror(root)
{
    // write code here
    if (root==null) return null;
    
    var node = root.left;
    root.left = root.right;
    root.right = node;
    
    Mirror(root.left);
    Mirror(root.right);
}
```

输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）
```
/*function RandomListNode(x){
    this.label = x;
    this.next = null;
    this.random = null;
}*/
function Clone(pHead)
{
    // write code here
    if (pHead==null) return null;
    
    var cur = pHead;
    var tmp = null;
    while (cur) {
        tmp = new RandomListNode(cur.label);
        tmp.next = cur.next;
        cur.next = tmp;
        cur = cur.next.next;
    }
    
    //followRandow(pHead);
    cur=pHead;
    while (cur) {
        cur.next.random = cur.random;
        cur = cur.next.next;
    }
    
    //var newHead = divide(pHead);
    var pNewHead = pHead.next;
    cur=pHead;
    var clone;
    while (cur) {
        var clone = cur.next;
        cur.next = clone.next;
        
        if (clone.next == null) {
            clone.next = null;
        } else {
            clone.next = clone.next.next; 
        }
        
        cur = cur.next;
    }
    
    return pNewHead;
}

```

```
private int minDist = Integer.MAX_VALUE; // 全局变量或者成员变量
public void minDistBT(int i, int j, int dist, int[][] w, int n) {
    if (i == 0 && j==n) {
        if (mindDist > dist) mindDist = dist;
        return;
    }

    if (i<n) minDistBT(i+1, j, dist, w, n);
    if (j<n) minDistBT(i, j+1, dist, w, n);
}
```


```

```