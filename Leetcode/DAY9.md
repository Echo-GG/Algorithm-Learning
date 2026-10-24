## Exclusive Time of Functions


On a \textbf{single-threaded} CPU, we execute a program containing $n$ functions. Each function has a unique ID between $0$ and $n-1$.

Function calls are stored in a \textbf{call stack}: when a function call starts, its ID is pushed onto the stack, and when a function call ends, its ID is popped off the stack. The function whose ID is at the top of the stack is \textbf{the current function being executed}. Each time a function starts or ends, we write a log with the ID, whether it started or ended, and the timestamp.

You are given a list \texttt{logs}, where \texttt{logs[i]} represents the $i$-th log message formatted as a string:

\begin{quote}
	\texttt{\{function\_id\}:\{start | end\}:\{timestamp\}}
\end{quote}

For example, \texttt{0:start:3} means a function call with function ID $0$ \textbf{started at the beginning} of timestamp $3$, and \texttt{1:end:2} means a function call with function ID $1$ \textbf{ended at the end} of timestamp $2$.

Note that a function can be called \textbf{multiple times, possibly recursively}.

A function's \textbf{exclusive time} is the sum of execution times for all function calls in the program. For example, if a function is called twice, one call executing for $2$ time units and another call executing for $1$ time unit, the \textbf{exclusive time} is $2+1=3$.

Return the \textbf{exclusive time} of each function in an array, where the value at the $i$-th index represents the exclusive time for the function with ID $i$.

```C++
class Solution {
	public:
	vector<int> exclusiveTime(int n, vector<string>& logs) {
		vector<int> res(n,0);
		stack<int> st;
		int prevTime = 0;
		for(string log:logs){
			// stringstream ss(log);
			// string idStr,type,ts;
			// getline(ss,idStr,':');
			// getline(ss,type,':');
			// getline(ss,ts,':');
			int p1 = log.find(':');
			int p2 = log.find(':',p1+1);
			string idStr = log.substr(0,p1);
			string type = log.substr(p1+1,p2-p1-1);
			string ts = log.substr(p2+1);
			
			int id = stoi(idStr);
			int time = stoi(ts);
			
			if(type == "start"){
				if(!st.empty()){
					res[st.top()] += time - prevTime;
				}
				st.push(id);
			} else if(type == "end"){
				if(!st.empty()){
					res[st.top()] += time - prevTime + 1;
					st.pop();
					time++;
				}
			}
			prevTime = time;
			
		}
		return res;
	}
};
```
