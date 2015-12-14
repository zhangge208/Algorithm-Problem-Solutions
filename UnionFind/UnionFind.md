#Union Find(Diijoint-set) Data Structures#

##Introduction##
reference：[https://en.wikipedia.org/wiki/Disjoint-set_data_structure](https://en.wikipedia.org/wiki/Disjoint-set_data_structure)

The disjoint-set data structure, also called a union–find data structure or merge–find set, is a data structure that keeps track of a set of elements partitioned into a number of disjoint (nonoverlapping) subsets. It supports two useful operations:

- Find: Determine which subset a particular element is in. Find typically returns an item from this set that serves as its "representative"; by comparing the result of two Find operations, one can determine whether two elements are in the same subset.
- Union: Join two subsets into a single subset.

##Two Operations##
We use the hashmap **father** to store the element and its parent element as key-value.

Let`s see the implement of these operations:

###Find###


	HashMap<Integer, Integer> father = new HashMap<Integer, Integer>();
	
	int find(int x) {
		int parent = father.get(x);
		while(parent != father.get(parent)) {
			parent = father.get(parent);
		}
		return parent;
	}

###Union###

	HashMap<Integer, Integer> father = new HashMap<Integer, Integer>();
	void union(int x, int y) {
		int fa_x = find(x);
		int fa_y = find(y);
		if (fa_x != fa_y) {
			father.put(fa_x, fa_y);
		}
	}

Next we will see how, by using the heuristic **path compression**, we will achieve the asymptotically fastest union find data structure.
The idea **path compression**,which is used for operation **Find**, is to make each node on the find path point directly to the root.

##Compressed_find##

int compressed_find(int x) {
	int parent = father.get(x);
	while(parent != father.get(parent)) {
		parent = father.get(parent);
	}

	int temp = -1;
	int fa = x;
	while (fa != father.get(fa)) {
		temp = father.get(fa);
		father.put(fa

