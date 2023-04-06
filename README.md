# testcode

#Q1

''' python
def calc_U(arr):
    if len(arr) % 2 == 0:
        # 如果 n 是偶数，则 U = arr [1]× arr [2]×（1÷ arr [3]）× arr [4]×...×（1÷ arr [n-1]）× arr [n]
        U = 1
        for i in range(0, len(arr), 2):
            if arr[i+1] != 0:
                U *= (arr[i] * arr[i+1])
    else:
        # 如果 n 是奇数，则 U = arr [1]× arr [2]×（1÷ arr [3]）× arr [4]×...× arr [n-1]×（1÷ arr [n]）
        U = 1
        for i in range(0, len(arr)-1, 2):
            if arr[i+1] != 0:
                U *= (arr[i] * arr[i+1])
        if arr[-1] != 0:
            U *= (1 / arr[-1])
    return U

def max_U(arr):
    # 对数组进行排序
    arr.sort()
    # 对于每个0元素，将其与相邻的位置交换，将0放在数组末尾
    zero_index = -1
    for i in range(len(arr)):
        if arr[i] == 0:
            zero_index = i
            break
    if zero_index != -1:
        for i in range(zero_index+1, len(arr)):
            if arr[i] != 0:
                arr[zero_index], arr[i] = arr[i], arr[zero_index]
                zero_index += 1
    # 计算U值
    U = calc_U(arr)
    # 将0元素放在数组开头，再计算U值
    if 0 in arr:
        arr.remove(0)
        new_arr = [0] + arr
        new_U = calc_U(new_arr)
        if new_U > U:
            return new_arr
    return arr

# 测试代码
arr =[5,4,3,2,1]
new_arr = max_U(arr)
U = calc_U(new_arr)
print(new_arr, U)
'''


# Q2
''' python
def calc_matches(teamA, teamB):
    result = []
    for b in teamB:
        count = 0
        for a in teamA:
            if a <= b:
                count += 1
        # 如果A队没有参加本场比赛，则将count补充为0
        if count == 0 and len(teamA) < len(teamB):
            count = 0
        result.append(count)
    return result

# 测试代码
teamA = [1, 2, 3]
teamB = [2, 4]
matches = calc_matches(teamA, teamB)
print(matches)
'''

# Q3
''' python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, v):
        self.stack.append(v)
        self.print_top()

    def pop(self):
        if self.is_empty():
            print('EMPTY')
        else:
            self.stack.pop()
            self.print_top()

    def inc(self, i, v):
        if not self.is_empty():
            for j in range(min(i, len(self.stack))):
                self.stack[j] += v
        self.print_top()

    def print_top(self):
        if self.is_empty():
            print('EMPTY')
        else:
            print(self.stack[-1])

    def is_empty(self):
        return len(self.stack) == 0

# 测试代码
stack = Stack()
stack.push(5)
stack.push(3)
stack.inc(2, 1)
stack.pop()
stack.pop()
stack.pop()
'''
