# Tree

## Implementing the Tree Abstraction

```python
def tree(label, branches=[]):
    for branch in branches:
        assert is_tree(branch), 'branches must be trees'
    return [label] + list(branches)

def label(tree):
    return tree[0]

def branches(tree):
    return tree[1:]

def is_tree(tree):
    if type(tree) != list or len(tree) < 1:
        return False
    for branch in branches(tree):
        if not is_tree(branch):
            return False
    return True

def is_leaf(tree):
    return not branches(tree)
```

## Tree Processing

Processing a leaf is often the base case of a tree processing function.
The recursive case typically makes a recursive call on each branch, then aggregates.

### Count Leaves

```python
def count_leaves(t):
    if is_leaf(t):
        return 1
    else:
        return sum([count_leaves(b) for b in branches(t)])
```

### Printing Trees

```python
def print_tree(t, indent=0):
    print("  " * indent + str(label(t)))
    for b in branches(t):
        print_tree(b, indent + 1)
```

### Summing Paths

```python
def print_sums(t, so_far):
    so_far += label(t)
    if is_leaf(t):
        print(so_far)
    else:
        for b in branches(t):
            print_sums(b, so_far)
```

### Counting Path

The function returns the number of paths from the root to any node in tree `t` for which the labels along the path sum to total.

```python
def count_path(t, total):
    if label(t) == total:
        found = 1
    else:
        found = 0
    return found + sum([count_paths(b, total - label(t)) for b in branches(t)])
```
