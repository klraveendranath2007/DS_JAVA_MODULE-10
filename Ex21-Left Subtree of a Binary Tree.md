# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE:23-10-2025
## AIM:
To design and implement a Python program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Start the program.  
2. Define a Node class to represent each node of the binary tree.  
3. Build the binary tree from a given level order array.  
4. Recursively count the number of nodes in the left subtree of the root.  
5. Display the total count.  
6. End the program.  
   

## Program:
```java
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: K L RAVEENDRANATH
RegisterNumber: 212224060212 
*/

import java.util.*;

class Node {
    int data;
    Node left, right;
    Node(int data) {
        this.data = data;
        this.left = this.right = null;
    }
}

public class Main {

    // Build binary tree in level-order fashion
    static Node buildTree(int[] arr) {
        if (arr.length == 0) return null;
        Node root = new Node(arr[0]);
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        int i = 1;

        while (!q.isEmpty() && i < arr.length) {
            Node current = q.poll();
            if (i < arr.length) {
                current.left = new Node(arr[i++]);
                q.add(current.left);
            }
            if (i < arr.length) {
                current.right = new Node(arr[i++]);
                q.add(current.right);
            }
        }

        return root;
    }

    static int countNodes(Node root) {
        if (root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = sc.nextInt();
        Node root = buildTree(arr);

        if (root.left == null) {
            System.out.println(0);
        } else {
            System.out.println(countNodes(root.left));
        }
    }
}


```

## Output:
<img width="363" height="130" alt="image" src="https://github.com/user-attachments/assets/cdbc918e-d7d7-4554-b46b-a7ce8cae1893" />


## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
