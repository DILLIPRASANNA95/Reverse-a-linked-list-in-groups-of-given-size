# Reverse-a-linked-list-in-groups-of-given-size
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None


def reverse_in_groups(head, k):
    if not head or k <= 1:
        return head

    current = head
    prev = None
    count = 0

    while current and count < k:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
        count += 1
    if current:
        head.next = reverse_in_groups(current, k)

    return prev


def print_linked_list(head):
    current = head
    while current:
        print(current.data, end=" -> ")
        current = current.next
    print("None")

head = Node(1)
head.next = Node(2)
head.next.next = Node(3)
head.next.next.next = Node(4)
head.next.next.next.next = Node(5)
head.next.next.next.next.next = Node(6)
head.next.next.next.next.next.next = Node(7)
head.next.next.next.next.next.next.next = Node(8)

print("Original Linked List:")
print_linked_list(head)

k = 3  

head = reverse_in_groups(head, k)

print("Modified Linked List:")
print_linked_list(head)
