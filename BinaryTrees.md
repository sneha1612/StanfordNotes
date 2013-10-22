0. Common Structure for all problems
====================================

    public class Node {
      private int val;
      private Node left;
      private Node right;

      public Node(int val, Node left,Node right) {
        this.val = val;
        this.left = left;
        this.right = right;
      }

      public int getVal() {
        return this.val;
      }

      public Node getLeft() {
        return this.left;
      }

      public Node getRight() {
        return this.right;
      }


      public void setVal(int val) {
        this.val = val;
      }

      public void setLeft(Node left) {
        this.left = left;
      }

      public void setRight(Node right) {
        this.right = right;
      }
    }

1. Lookup
=========

    public boolean lookup(Node root, int data) {
      Node temp = root;
      if(temp == null) 
        return false;

      if(temp.getVal() == data)
        return true;
      else if(data < temp.getVal())
        lookup(temp.getLeft(), data);
      else
        lookup(temp.getRight(), data);
    }

2. Insert
=========

    public Node insert(Node root, int data) {
      Node temp = temp;
      if(temp == null) {
        Node newNode = new Node(data, null, null);
        return newNode;
      }
      else {
        if(data < temp.getVal())
          insert(temp.getLeft(), data);
        else
          insert(temp.getRight(), data);
      }

      return temp;
    }

3. Size
=======

    public int size(Node root) {
      Node temp = root;
      if(temp == null)
        return 0;
      else
        return size(temp.getLeft()) + size(temp.getRight()) + 1;
    }

4. MaxDepth
===========

    public int maxDepth(Node root) {
      Node temp = root;
      if(temp == null)
        return 0;
      else {
        int leftDepth = maxDepth(temp.getLeft());
        int rightDepth = maxDepth(temp.getRight());

        if(leftDepth > rightDepth)
          return leftDepth+1;
        else
          return rightDepth+1;
      }
    }

5. MinValue
===========

    public int minValue(Node root) {
      Node temp = root;
      if(temp == null)
        return;

      while(temp.getLeft() != null) {
        temp = temp.getLeft();
      }
      return temp.getVal();
    }

6. PrintTree
============

    public void printTree(Node root) {
      Node temp = root;

      if(temp == null)
        return;

      printTree(temp.getLeft());
      System.out.println(temp.getVal());
      printTree(temp.getRight());
    }

7. HasPathSum
=============

    public boolean hasPathSum(Node root, int sum) {
      Node temp = root;

      if(temp == null)
        return(sum == 0);
      else {
        int subSum = sum - temp.getVal();
        return (hasPathSum(temp.getLeft(), subSum) || hasPathSum(temp.getRight(), subSum))
      }
    }

8. printPaths
=============

    public void printPaths(Node root) {
      int path[1000];

      printPathsHelper(root, path, 0);

    }

    public void printPathsHelper(Node root, int[] path, int length) {
      Node temp = root;
      if(temp == null) 
        return;

      path[length] = temp.getVal();
      length++;

      if(temp.getLeft() == null && temp.getRight() == null)
        print(path, length);
      else {
        printPathsHelper(temp.getLeft(), path, length);
        printPathsHelper(temp.getRight(), path, length);
      }
    }

    public void print(int[] path, int length) {
      for(int i =0; i<length; i++) {
        System.out.print(path[i]);
      }
      System.out.println();
    }