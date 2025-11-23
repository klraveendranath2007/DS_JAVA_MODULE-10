# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE:27-10-2025
## AIM:
To design and implement a Python program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start the program.  
2. Define a `Node` class with data, left, and right references.  
3. Create an `insert()` function to insert nodes into the BST following BST rules.  
4. Create a `search()` function to find a Book ID in the BST.  
5. Build the BST using given Book IDs.  
6. Search for a specific Book ID entered by the user.  
7. Display whether the Book ID exists in the tree.  
8. End the program.    

## Program:
```java
/*
Program to constructs a Binary Search Tree (BST) using given Book IDs 
Developed by: K L RAVEENDRANATH
RegisterNumber:  212224060212
*/

import java.util.*;

public class BookIDSearch {
    static class Node {
        int data;
        Node left, right;
        Node(int data) {
            this.data = data;
        }
    }

    public static Node insert(Node root, int key) {
        if (root == null) return new Node(key);
        if (key < root.data) root.left = insert(root.left, key);
        else root.right = insert(root.right, key);
        return root;
    }

    public static boolean search(Node root, int key) {
        if (root == null) return false;
        if (root.data == key) return true;
        if (key < root.data) return search(root.left, key);
        else return search(root.right, key);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Node root = null;
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }
        int q = sc.nextInt();
        while (q-- > 0) {
            int key = sc.nextInt();
            System.out.println(search(root, key) ? "Found" : "Not Found");
        }
    }
}
```

## Output:
<img width="494" height="219" alt="image" src="https://github.com/user-attachments/assets/526e0abd-f53c-426c-b427-ae5d40ebbfe1" />




## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
