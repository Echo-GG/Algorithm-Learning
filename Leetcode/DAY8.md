## Evaluate Reverse Polish Notation


You are given an array of strings tokens that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

Note that:

The valid operators are '+', '-', '*', and '/'.
Each operand may be an integer or another expression.
The division between two integers always truncates toward zero.
There will not be any division by zero.
The input represents a valid arithmetic expression in a reverse polish notation.
The answer and all the intermediate calculations can be represented in a 32-bit integer.

```C++

class Solution {
	public:
	bool isNumber(string str){
		if(str!="+" && str!="-" && str!="*" && str!="/")
		return true;
		return false;
	}
	
	int Calculate(int n1, int n2, string op){
		if(op=="+")
		return n1 + n2;
		if(op=="-")
		return n1 - n2;
		if(op=="*")
		return n1 * n2;
		if(op=="/")
		return n1 / n2;
		return -1;
	}
	
	int evalRPN(vector<string>& tokens) {
		stack<int> st;
		for(string str:tokens){
			if(isNumber(str)){
				st.push(stoi(str));
			}
			else{
				int n2 = st.top();
				st.pop();
				int n1 = st.top();
				st.pop();
				int res = Calculate(n1,n2,str);
				st.push(res);
			}
		}
		return st.top();
	}
};

```
