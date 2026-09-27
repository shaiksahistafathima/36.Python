# 36.Python
Trees


class Node:
    def __init__(self,data):
        self.data = data
        self.left = None
        self.right = None
        #crate a tree
root=Node(10)
root.left=Node(5)
root.right=Node(15)
root.left.left=Node(2)
root.left.right=Node(6)
root.right.left=Node(13)
root.right.right=Node(20)
#preorder : root ->left->right
def preorder(root):
    if root==None:
        return
    print(root.data,end=" ")
    print(root.left,end=" ")
    print(root.right,end=" ")
#inorder
def inorder(root):
    if root==None:
        return
    print(root.left,end=" ")
    print(root.data,end=" ")
    print(root.right,end=" ")
#postorder
def postorder(root):
    if root==None:
        return
    print(root.left,end=" ")
    print(root.right,end=" ")
    print(root.data,end=" ")
#level order
def levelorder(root):
    if root == None:
        return
queue=[root]
while(len(queue))>0:
    current=queue.pop(0)
    print(current.data,end=" ")
    if current.left !=None:
        queue.append(current.left)
       if current.right !=None:
        queue.append(current.right)
#search technique
def search (root,value):
    if root == None:
        return False
    if root == data:
        return True
    left_result = search(root.left,value)
    if left_result == True:
        return True
    return search(root.right,value)
#count total nodes
def count_nodes(root):
    if root == None:
        return 0
    left_count = count_nodes(root.left)
    right_count = count_nodes(root.right)
    return 1+left_count+right_count
#count leaf nodes
def count_leaf(root):
    if root == None:
        return 0
    if(root.left=None and root.right==None):
        return 1
    
    return count_leaf(root.left)+count_leaf(root.right)
#count internal nodes
def count_internal(root):
    if root == None:
        return 0
    if(root.left=None and root.right==None):
        return 0
    
    return count_internal(root.left)+count_internal(root.right)
#height
def height(root):
    if root == None:
        return 0
    left_height=height(root.left)
    right_height=height(root.right)
    if left_height >right_height:
        return 1+left_height
    return 1+right_height
#finding min value
def find_max(root):
    if root == None:
        return None
        
    maximum = root.data
    left_max = find_max(root.left)
    right_max = find_max(root.right)
    
    if left_max != None and left_max > maximum:
        maximum = left_max
    if right_max != None and right_max > maximum:
        maximum = right_max
        
    return maximum
#finding max value
def find_max(root):
    if root==None:
        return None
    maximium=root.data
    left_min=find_min(root.left)
    right_min=find_min(root.right)
    if left_min!=None and left_min <minimum:
        minimum=left_min
    if left_min != None and right_min<minimum:
        minimum=right_min
    return mi
    
    
#count edges
def count_edges(root):
    nodes=count_nodes(root)
    if nodes == 0:
        return 0
    return nodes-1
#13. find depth of a nodes
def find_depth(root,value,depth):
    if root ==None:
        return -1
    if root.data ==value:
        return depth
    left_result = find_depth(root.left,value,depth+1)
    if left_result!=-1:
        return left_result
    return find_depth(root.right,value,depth+1)
    
#14 find level of a node
def find_level(root):
    depth=find_depth(root,value):
    if depth==-1:
        return -1
    return depth+1
#15.find parent
def find_parent(root,value):
    if root == None:
        return None
    if root.left != None and root.left==value:
        return root.data
    if root.right !=None and root.right==value:
        return root.data
    left_result=find_parent(root.left,value)
    if left_result != None:
        return root.left
    return find_parent(root.right,value)
    
#16.find sibling
def find_sibling((root,value)):
    if root == None:
        return None
    if root.left !=None and root.left.data==vlaue:
        if root.right!=None:
            return root.right.data
        else:
            return None
    if root.right !=None and root.left.data==vlaue:
        if root.left!=None:
            return root.left.data
        else:
            return None
    left_result=find_sibling(root.left,value)
    if left_result!=None:
        return left_result
    return find_sibling(root.right,value)
    
#18.mirror table
def mirror(root):
    if root == None:
        return
    temp=root.left
    root.left=root.right
    root.right=temp
    mirror(root.left)
    mirror(root.right)
#19.compare two trees
def compair(root1,root2):
    if root1==None and root2==None:
        return True
    if root1==None or root2==None:
        return False
    if root1.data !=root2.data:
        return False
    left_comp=compair(root1.left,root2.left)
    right_comp=compair(root1.right,root2.right)
    return left_comp and right_comp
#check empty tree    
def empty(root1,root2):
    if root1 == None:
        return True
    else:
        return False

# 21. INSERT NODE
def insert(root, value):
    new_node = Node(value)
    if root == None:
        return new_node
    queue = [root]
    while len(queue) > 0:
        current = queue.pop(0)
        if current.left == None:
            current.left = new_node
            return root
        else:
            queue.append(current.left)
        if current.right == None:
            current.right = new_node
            return root
        else:
            queue.append(current.right)

# 22. DELETE NODE
def delete(root, value):
    if root == None:
        return None
    if root.left == None and root.right == None:
        if root.data == value:
            return None
        else:
            return root
    queue = [root]
    target = None
    last = None
    parent = None
    while len(queue) > 0:
        current = queue.pop(0)
        if current.data == value:
            target = current
        if current.left != None:
            parent = current
            queue.append(current.left)
        if current.right != None:
            parent = current
            queue.append(current.right)
        last = current
    if target == None:
        return root
    target.data = last.data
    queue = [root]
    while len(queue) > 0:
        current = queue.pop(0)
        if current.left == last:
            current.left = None
            break
        if current.right == last:
            current.right = None
            break
        if current.left != None:
            queue.append(current.left)
        if current.right != None:
            queue.append(current.right)
    return root

print("Preorder:")
preorder(root)
print("\n\nInorder:")
inorder(root)
print("\n\nPostorder:")
postorder(root)
print("\n\nLevel Order:")
levelorder(root)
print("\n\nTotal Nodes:")
print(count_nodes(root))
print("\nLeaf Nodes:")
print(count_leaf(root))
print("\nInternal Nodes:")
print(count_internal(root))
print("\nHeight:")
print(height(root))
print("\nMinimum:")
print(find_min(root))
print("\nMaximum:")
print(find_max(root))
print("\nEdges:")
print(count_edges(root))
print("\nDepth of 7:")
print(find_depth(root, 7, 0))
print("\nLevel of 7:")
print(find_level(root, 7))
print("\nParent of 7:")
print(find_parent(root, 7))
print("\nSibling of 7:")
print(find_sibling(root, 7))
print("\nChildren of 5:")
print(find_children(root, 5))
print("\nSearch 12:")
print(search(root, 12))
print("\nSearch 50:")
print(search(root, 50))
print("\nIs Tree Empty?")
print(is_empty(root))
    
    
    
    
    
    
    
    
    











