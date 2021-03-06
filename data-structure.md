## Data structure

Some basic data structures.

### List
A list holds an ordered collection of items (int, float, string), it is mutable.

- Examples
```
a = [1, 2, 3, 4, 5, 6, 6, 7, 8, 2, 3, 5, 6, 2, 5]
b = [4.4, 3.4, 4.7, 3.2, 2.5, 3.5]
c = ["one", "two", "three", "four", "five"]
```

- Concatenation
```
a + b
```
[1, 2, 3, 4, 5, 6, 6, 7, 8, 2, 3, 5, 6, 2, 5, 4.4, 3.4, 4.7, 3.2, 2.5, 3.5]

- Replicate
```
b * 2
```
[4.4, 3.4, 4.7, 3.2, 2.5, 3.5, 4.4, 3.4, 4.7, 3.2, 2.5, 3.5]

- Math operator element-wise
```
d = [x*2 for x in b];
d
```
[8.8, 6.8, 9.4, 6.4, 5.0, 7.0]

- Append
```
c.append('six');
c
```
['one', 'two', 'three', 'four', 'five', 'six']

- Sort
```
c.sort();
c
```
['five', 'four', 'one', 'six', 'three', 'two']

- Reverse
```
c.reverse();
c
```
['two', 'three', 'six', 'one', 'four', 'five']

- Select an item
```
c[3]
```
'one'

- Change value
```
c[3] = "seven"
c
```
['two', 'three', 'six', 'seven', 'four', 'five']


### Tuple
Tuples are heterogeneous data structures and it is immutable. Tuple is faster than list, but less flexible.

- Examples
```
a = ("apple", 10)
## nested tuple
b = (("book", 20), ("bus", 40))
```

- Select an item
```
a[1]
```
10
```
b[0]
```
('book', 20)
```
b[0][1]
```
20

- Select the second item
```
c = (("apple", 10), ("book", 20), ("bus", 40))
for _, n in c:
    print(n)
```
10<br>
20<br>
40<br>



### Set
Set is unordered distinct collection of items, mutable.

- Examples - create a set
```
a = [1, 3, 3, 2, 5, 6, 6, 7, 8, 2, 3, 5, 6, 2, 5]
a_set = set(a)
a_set
```
{1, 2, 3, 5, 6, 7, 8}

- Remove
```
a_set.remove(8);
a_set
```
{1, 2, 3, 5, 6, 7}

- Add
```
a_set.add(10)
a_set
```
{1, 2, 3, 5, 6, 7, 10}

- Check
```
1 in a_set
```
True

- Another set
```
b_set = {1, 2, 3, 5, 6, 8, 9, 12, 15, 17, 18, 21}
```

- Items in *either* a_set *or* b_set
```
a_set.union(b_set)
a_set | b_set
```
{1, 2, 3, 5, 6, 7, 8, 9, 10, 12, 15, 17, 18, 21}

- Items in *both* a_set *and* b_set
```
a_set.intersection(b_set)
a_set & b_set
```
{1, 2, 3, 5, 6}

- Items in a_set but not in b_set
```
a_set.difference(b_set)
a_set - b_set
```
{7, 10}


### Dictionary
mutable, a set of key-value pairs, access a value by its key.

- An example
```
a_dict = {
  "apple": 10,
  "book": 20,
  "bus": 40,
  "cat": 60
}
```

- Find a value by key
```
a_dict["apple"]
```
10

- Change a value
```
a_dict["book"] = 30
a_dict
```
{'apple': 10, 'book': 30, 'bus': 40, 'cat': 60}

- Add a value
```
a_dict["bike"] = 50
a_dict
```
{'apple': 10, 'book': 30, 'bus': 40, 'cat': 60, 'bike': 50}

- Delete a value, only when the key is in the dict.
```
del a_dict["apple"]
a_dict
```
{'book': 30, 'bus': 40, 'cat': 60, 'bike': 50}

- Check key
```
"apple" in a_dict
```
True

- Print all key and values
```
for x in a_dict:
    print(x, a_dict[x])
```
apple 10<br>
book 30<br>
bus 40<br>
cat 60<br> 
