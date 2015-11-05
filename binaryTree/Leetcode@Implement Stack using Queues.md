#Leetcode@Implement Stack using Queues#

##题目##

Implement the following operations of a stack using queues.

- push(x) -- Push element x onto stack.

- pop() -- Removes the element on top of the stack.

- top() -- Get the top element.

- empty() -- Return whether the stack is empty.

**Notes:**

- You must use only standard operations of a queue -- which means only push to back, peek/pop from front, size, and is empty operations are valid.
 
- Depending on your language, queue may not be supported natively. You may simulate a queue by using a list or deque (double-ended queue), as long as you use only standard operations of a queue.

- You may assume that all operations are valid (for example, no pop or top operations will be called on an empty stack).

##思路##

算法导论

##代码##

	class MyStack {
	    // Push element x onto stack.
	    Queue<Integer> qa = new LinkedList<Integer>();
	    Queue<Integer> qb = new LinkedList<Integer>();
	    
	    public void push(int x) {
	        if (!qa.isEmpty()){
	            qa.add(x);
	        }
	        else{
	            qb.add(x);
	        }
	    }
	
	    // Removes the element on top of the stack.
	    public void pop() {
	        if (!qa.isEmpty()){
	            
	            while (qa.size() > 1){
	                qb.offer(qa.poll());
	            }
	            int temp = qa.peek();
	            qa.poll();
	            return;
	        }
	        else{
	            while (qb.size() > 1){
	                qa.offer(qb.poll());
	            }
	            int temp = qb.peek();
	            qb.poll();
	            return;
	        }
	    }
	
	    // Get the top element.
	    public int top() {
	        if (!qa.isEmpty()){
	            while (qa.size() > 1){
	                qb.offer(qa.poll());
	            }
	            int top = qa.poll();
	            qb.offer(top);
	            return top;
	        }
	        else{
	            while (qb.size() > 1){
	                qa.offer(qb.poll());
	            }
	            int top = qb.poll();
	            qa.offer(top);
	            return top;
	        }
	    }
	
	    // Return whether the stack is empty.
	    public boolean empty() {
	        return qa.isEmpty() && qb.isEmpty();
	    }
	}