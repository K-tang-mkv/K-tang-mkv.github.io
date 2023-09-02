# Iterator in C++

An iterator is an object (like a pointer) that points to an element inside the container. We can use iterators to move through the contents of the container.

* **Convenience in programming:**

It is better to use iterators to iterate through the contents of containers as if we will not use an iterator and access elements using [] operator, 
then we need to be always worried about the size of the container, whereas with iterators we can simply use member function end() and iterate through the contents without having to keep anything in mind. 

```cpp
// C++ program to demonstrate iterators

#include <iostream>
#include <vector>
using namespace std;
int main()
{
	// Declaring a vector
	vector<int> v = { 1, 2, 3 };

	// Declaring an iterator
	vector<int>::iterator i;

	int j;

	cout << "Without iterators = ";
	
	// Accessing the elements without using iterators
	for (j = 0; j < 3; ++j)
	{
		cout << v[j] << " ";
	}

	cout << "\nWith iterators = ";
	
	// Accessing the elements using iterators
	for (i = v.begin(); i != v.end(); ++i)
	{
		cout << *i << " ";
	}
	return 0;
}
```

