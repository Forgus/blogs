---
title: 二叉树的搜索算法
date: 2020-05-08
catalog: true
tags:
- 算法
---

## 深度优先搜索

深度优先搜索（Depth First Search），一般用递归实现，算法比较巧妙，关键在于寻找遍历的套路。

### 前序遍历

```java
public void dfs(TreeNode x) {
  if(x == null) {
    return;
  }
  //do something
  dfs(x.left);
  dfs(x.right);
}
```



### 中序遍历

```java
public void dfs(TreeNode x) {
  if(x == null) {
    return;
  }
  dfs(x.left);
  //do something
  dfs(x.right);
}
```

中序遍历可以按顺序访问二叉搜索树中的节点。

### 后序遍历

```java
public void dfs(TreeNode x) {
  if(x == null) {
    return;
  }
  dfs(x.left);
  dfs(x.right);
  //do something
}
```

## 广度优先搜索

广度优先搜索（Breadth First Search），即层序遍历，一般用队列加两层循环实现，外层循环遍历树的层次，内循环遍历每一层的节点。

### 自顶向下层序遍历

```java
public void bfs(TreeNode x) {
  if(x == null) {
    return;
  }
  Queue<TreeNode> queue = new LinkedList<>();
  queue.add(x);
  while(!queue.isEmpty()) {
    int count = queue.size();
    while(count > 0) {
      TreeNode node = queue.poll();
    	//do something
      if(x.left != null) {
        queue.add(x.left);
      }
      if(x.right != null) {
        queue.add(x.right);
      }
      count --;
    }
  }
}
```

### 自底向上层序遍历

可以用自顶向下遍历法的套路，在具体处理上反转结果。