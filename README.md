# Tree_Traversal_Search

> ## 🤯 Breath First Search (BFS) animation: :octocat:
![breadth_first_search](breadth_first_search.gif)


> ## Node class creation: :octocat:
``` js
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}
```
> ## class method creation for Tree Traverse Search: :octocat:
> ## BFS(), DFSPreOrder(), DFSPostOrder(), DFSInOrder()
``` js
class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        var newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        var current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                } 
                current = current.right;
            }
        }
    }
    find(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }
    contains(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }
    BFS(){
        var node = this.root,
            data = [],
            queue = [];
        queue.push(node);

        while(queue.length){
           node = queue.shift();
           data.push(node.value);
           if(node.left) queue.push(node.left);
           if(node.right) queue.push(node.right);
        }
        return data;
    }

    DFSPreOrder(){
        var data = [];
        function traverse(node){
            data.push(node.value);
            if(node.left) traverse(node.left);
            if(node.right) traverse(node.right);
        }
        traverse(this.root);
        return data;
    }

    DFSPostOrder(){
        var data = [];
        function traverse(node){
            if(node.left) traverse(node.left);
            if(node.right) traverse(node.right);
            data.push(node.value);
        }
        traverse(this.root);
        return data;
    }

    DFSInOrder(){
        var data = [];
        function traverse(node){
            if(node.left) traverse(node.left);
            data.push(node.value);
            if(node.right) traverse(node.right);
        }
        traverse(this.root);
        return data;
    }
}

                                   //       10
                                   //   6       15
                                   // 3   8	      20
```
> ## run code and results: :octocat:
``` js
var tree = new BinarySearchTree();
tree.insert(10);
tree.insert(6);
tree.insert(15);
tree.insert(3);
tree.insert(8);
tree.insert(20);
console.log(tree)
// BinarySearchTree {
//   root: Node {
//     value: 10,
//     left: Node { value: 6, left: [Node], right: [Node] },
//     right: Node { value: 15, left: null, right: [Node] }
//   }
// }
console.log(tree.BFS()) // [ 10, 6, 15, 3, 8, 20 ]

console.log(tree.DFSPreOrder()) // [ 10, 6, 3, 8, 15, 20 ]
console.log(tree.DFSPostOrder()) // [ 3, 8, 6, 20, 15, 10 ]
console.log(tree.DFSInOrder()) // [ 3, 6, 8, 10, 15, 20 ]
```


![breadth_first_search](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/breadth_first_search.png)
![depth_first_search_pre_fig](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_pre_fig.png)
![depth_first_search_pre](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_pre.png)
![depth_first_search_pos_fig](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_pos_fig.png)
![depth_first_search_pos](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_pos.png)
![depth_first_search_in_fig](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_in_fig.png)
![depth_first_search_in](https://github.com/NoriKaneshige/Tree_Traversal_Search/blob/master/depth_first_search_in.png)
