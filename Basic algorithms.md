Tree Traversal

```
// preorder
void preorder(Node root) {
    if (!root) {
        // visit - your code goes here
        preorder(root.left);
        preorder(root.right);
    }
}

// postorder
void postorder(Node root) {
    if (!root) {
        postorder(root.left);
        postorder(root.right);
        // visit - your code goes here
    }
}

// inorder
void postorder(Node root) {
    if (!root) {
        postorder(root.left);
        // visit - your code goes here
        postorder(root.right);
    }
}
```

QuickSort
```
public:
void quicksort(vector<int>& array) {
    if (array.size() > 1)
        quicksort(array, 0, array.size() - 1);
}

private:
void swap(vector<int>& array, int left, int right) {
    int temp = array[left];
    array[left] = array[right];
    array[right] = temp;
}

void quicksort(vector<int>& array, int leftEnd, int rightEnd) {
    int left = leftEnd;
    int right = rightEnd;
    int pivot = array[(leftEnd + rightEnd)/2];
    do {
        while (array[left] < pivot) {
            left += 1;
        }
        while (array[right] > right) {
            right -= 1;
        }
        if (left <= right) {
            swap(array, left, right);
            left += 1;
            right -= 1;
        }
    } while (left <= right);
    if (leftEnd < right) {
        quicksort(array, leftEnd, right);
    }
    if (left < rightEnd) {
        quicksort(array, left, rightEnd);
    }
}
```


