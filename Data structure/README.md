线性表，右为头左为尾，上为顶下为底。

## 栈
栈（stack）是限定仅在表尾进行插入或删除的线性表。其中添加/移除新项总发生在同一端。
这一端通常称为“栈顶”(top，表尾端)。与栈顶对应的端称为“栈底”（bottom，表头端）。 
栈的底部很重要，因为在栈中靠近底部的项是存储时间最长的。最近添加的项是最先移除的。  
这种排序原则有时被称为** LIFO( Last In First Out，即后进先出)**。  
可以把栈理解为在桌子上，把书一本本叠起来。拿起一本书放在书堆的最上面，当然也只有先拿走上面的书才能拿走下面的书。

#### 栈的基本操作
- Stack() 创建一个空的新栈。 它不需要参数，并返回一个空栈。
- push(item)：在栈的最上方插入元素
- pop()：返回栈最上方的元素，并将其删除
- isEmpty()：查询栈是否为空
- top()，或者称为 peek()：返回栈最上方的元素，并不删除
- size()，返回 item 数量。
##### [栈的具体实现](stack/stack.py)

## 队列
队列（queue）是一种先进先出的（FIFO，First In First Out）线性表。只允许在表的一端插入而在另一端删除。
其中允许插入的一端称为队尾(rear)，允许删除的一端称为队头（front）。
当一个元素从队尾进入队列时，一直向队头移动，直到它成为下一个需要移除的元素为止。
#### 队列的基本操作
- Queue() 创建一个空的新队列。 它不需要参数，并返回一个空队列。
- enqueue(item) 将新项添加到队尾。 它需要 item 作为参数，并不返回任何内容。
- dequeue() 从队头移除项。它不需要参数并返回 item。 队列被修改。
- isEmpty() 查看队列是否为空。它不需要参数，并返回布尔值。
- size() 返回队列中的项数。它不需要参数，并返回一个整数。
##### [队列的具体实现](queue/queue.py)

### 双端队列
双端队列（deque）是限定插入和删除操作在表的两端的线性表。它的两个端点（首部和尾部）都可以进行添加和删除操作。  
在某种意义上，这种混合线性结构提供了单个数据结构中的栈和队列的所有能力。但在实际应用中远不及栈和队列有用。
#### 双端队列的基本操作
- Deque() 创建一个空的新 deque。它不需要参数，并返回空的 deque。
- addFront(item) 将一个新项添加到 deque 的首部。它需要 item 参数 并不返回任何内容。
- addRear(item) 将一个新项添加到 deque 的尾部。它需要 item 参数并不返回任何内容。
- removeFront() 从 deque 中删除首项。它不需要参数并返回 item。deque 被修改。
- removeRear() 从 deque 中删除尾项。它不需要参数并返回 item。deque 被修改。
- isEmpty() 测试 deque 是否为空。它不需要参数，并返回布尔值。
- size() 返回 deque 中的项数。它不需要参数，并返回一个整数。
##### [双端队列的具体实现](queue/deque.py)

### [循环队列](https://www.cnblogs.com/curo0119/p/8608606.html)
在用数组实现队列的时候，当有元素出列，头指针front就向后移动，此时队列前面的空间就空了出来。
每当添加元素，尾指针rear+1，当尾指针rear移动到LENGTH时（数组的最大下标处的地址），再入队会发生假溢出。
也就是说实际上我们开辟的数组还有剩余空间，却因为rear越界表现为溢出。  
为了更合理的利用空间，将队列的首尾相连接。这样当rear移动到LENGTH时，会再从0开始循环。
那当什么时候队列满呢？当rear等于front的时候，无法判断队列为空还是满。有两个方法：  
办法一是设置一个标志变量flag，当front == rear,且flag = 0时为队列空，当front == rear,且flag= 1时为队列满。  
办法二牺牲一个存储空间，front前面不存数据，当rear在front前面的时候就是满了。
#### 循环队列的基本操作
- LoopQueue(size) 创建一个空的新队列，size用于指定循环队列的大小，不输入参数size使用默认值。
- enqueue(item) 将新项添加到队尾。 它需要 item 作为参数，并不返回任何内容。
- dequeue() 从队头移除项。它不需要参数并返回 item。 队列被修改。
- isEmpty() 查看队列是否为空。它不需要参数，并返回布尔值。
- size() 或者 \_\_len\_\_() 返回队列中的项数。它不需要参数，并返回一个整数。
##### [循环队列的实现](queue/loopqueue.py)

### 链表
#### 单链表
- ist() 创建一个新的空单链表，无返回值。
- add(item) 在链表头部插入元素，需要item作为参数，无返回值。
- append(item) 在链表尾部添加元素，需要item作为参数，无返回值。
- insert(pos, item) 在指定位置 pos 插入元素 item。无返回值。
- remove(item) 删除节点值等于 item 的节点。一般无返回值。若没有该值，返回 -1，表示出错。
- search(item) 查找节点是否存在，返回布尔值。空列表返回False。
- isEmpty() 链表是否为空，返回布尔值
- size() 或者 \_\_len\_\_()，返回链表元素个数。
- traverse() 遍历整个链表，无返回值。
##### [单链表的实现](list/lists.py)

#### 循环链表
循环链表(circular linked list)是另一种形式的链式存储结构，
它与单链表不同在于表中最后一个指针域指向头节点。整个链表形成一个环。

#### 双向链表
单向链表只能顺指针往后寻找其他节点。若要寻查节点的直接前趋，则需要从表头指针出发。
为克服单链表的这种单向性的缺点，可利用双向链表（double linked list）。  
双向链表的节点中有两个指针域，其一指向直接后继，另一指向直接前趋。

### [树](https://blog.csdn.net/g360z247j123/article/details/51858563)
树的递归定义如下:
一棵树是一些节点的集合。这个集合可以为空集或非空集；
若树非空，则它由称为根(root)的节点r以及0个或多个非空的(子)树T1，T2，…Tk组成，
这些子树中每一棵树都被来自根r的一条有向的边(edge)所连接。 

####二叉树
二叉树（Binary Tree）是另一种树形结构，它的特点是每个结点至多只有两颗子树（即二叉树中不存在度大于二的节点）。
并且，二叉树的子树有左右之分，其次序不能任意颠倒。
##### [二叉树的实现](tree/BinaryTree.py)
##### [二叉树的分类](https://www.cnblogs.com/sunshineliulu/p/7775063.html)