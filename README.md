# AVLTree

A fully templated generic C++ implementation of an AVL self-balancing binary search tree.

## Features

- Template support for any key and data types
- Automatic balancing with LL, RR, LR, and RL rotations
- Insertion and deletion with O(log n) time complexity
- Search and containment checks
- Inorder traversal with balance factors for debugging
- Construct AVL tree from sorted arrays
- Merge two AVL trees into one in linear time
- Get previous and next in-order keys
- Extract keys and/or data in sorted order or in a given range

## Class Overview

### `Node<K, T>`

Represents a single node in the AVL tree.

#### Attributes:
- `K key`: the key used for BST ordering
- `T data`: the value stored in the node
- `Node *left_son, *right_son, *parent`: child and parent pointers
- `int height`: height of the node for balancing

#### Methods:
- `update_height()`: Recomputes the height
- `balance_factor()`: Computes the balance factor (left height - right height)

---

### `AVLTree<K, T>`

Represents the AVL Tree structure.

#### Core Methods:
- `insert(const K &key, const T &data)`: Inserts a node with key and data
- `remove(const K &key)`: Removes node by key
- `find(const K &key, T *found_data)`: Finds node and writes data
- `contains(const K &key)`: Checks if key exists
- `print_inorder_with_bf()`: Prints in-order with heights and balance factors

#### Tree Construction:
- `AVLTree(K sorted_keys[], T sorted_data[], int size)`: Builds tree from sorted arrays
- `build_from_two_merged_trees(const AVLTree &t1, const AVLTree &t2)`: Merges two AVL trees into one

#### Data Export:
- `to_sorted_keys_and_data(K keys[], T data[])`
- `to_sorted_ranged_keys_and_data(...)`

#### Navigation:
- `get_prev_inorder(const K&)`
- `get_next_inorder(const K&)`

## Example

```cpp
AVLTree<int, std::string> tree;
tree.insert(10, "apple");
tree.insert(5, "banana");
tree.insert(15, "cherry");

std::string result;
if (tree.find(10, &result) == AVL_TREE_SUCCESS) {
    std::cout << "Found: " << result << std::endl;
}

tree.print_inorder_with_bf();
