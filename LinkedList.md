0. Common Structure for all problems
====================================

    public class Node {
      private int val;
      private Node next;

      public Node(int val, Node next) {
        this.val = val;
        this.next = next;
      }

      public int getVal() {
        return this.val;
      }

      public Node getNext() {
        return this.next;
      }

      public void setVal(int val) {
        this.val = val;
      }

      public void setNext(Node next) {
        this.next = next;
      }
    }


1. Iterate down a list
======================

    public int count(Node root, int input) {
      if(root == null)
        return;
      Node temp = root;
      int counter = 0;

      while(temp != null) {
        if(temp.getVal() == input)
          counter++;
        temp = temp.getNext();
      }

      return counter;
    }


2. Get nth
==========

    public int getNth(Node root, int n) {
      if(root == null)
        return;
      Node temp = root;
      int counter = 0;

      while(temp != null) {
        if(counter == n)
          return temp.getVal();
        temp = temp.getNext();
        counter++;
      }
      throw new Exception("n is out of bounds");
    }

3. Delete list
==============

    public void deleteList(Node root) {
      if(root == null)
        return;
      Node temp = root;

      while(temp != null) {
        Node next = temp.getNext();
        temp.setNext(null);
        temp = next;
      }
      root = null;
    }

4. Pop
======

    public int pop(Node root) {
      if(root == null)
        return;
      Node temp = root;

      int retVal = temp.getVal();
      temp = temp.getNext();
      root = temp;

      return retVal;
    }

5. InsertNth
============

    public void insertNth(Node root, int index, int data) {
      if(root == null)
        return;

      Node temp = root;
      int counter = 0;

      if(index == 0) {
        Node newNode = new Node(data, temp);
        root = newNode;
      } 
      else {
        while(temp != null) {
          if(counter == index-1) {
            node newNode = new Node(data, null);
            temp.setNext(newNode);
            newNode.setNext(temp.getNext());
          }
          counter++;
          temp = temp.getNext();
        }
      }
    }

6. SortedInsert
===============

    public void sortedInsert(Node root, int data) {
      if(root == null || root.getVal() > data) {
        Node newNode = new Node(data, root);
        root = newNode;
      }
      else {
        Node temp = root;
        while(temp.getNext()!=null && temp.getNext().getVal() > data) {
          temp = temp.next;
        }
        Node newNode = new Node(data, temp.next);
        temp.setNext(newNode);
      }
    }

17. Reverse
===========

    public void reverse(Node root) {
      Node curr = root;
      Node prev = null;
      Node first = null;

      while(prev != null) {
        first = prev;
        prev = curr;
        curr = curr.next;
        prev.setNext(first);
      }
      root = prev;
    }












