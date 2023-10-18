#java 

# Unchecked 
```
ArrayList list1 = new ArrayList();
```
- Flexibility
	- Any object can be added to `list1`

- Issues
	- Need to cast before use, possibly even check for instance type.
	```
	if(list1.get(1) instanceof Integer)
	{
		Integer i1 = (Integer)list1.get(1);
	}
	```
# Parameterised type 
```
ArrayList<Integer> list1 = new ArrayList();
```

- When you specify object type
- No need to case before use as referring to elements will need to be type checked
	- `Integer i1 = list1.get(1);`
- 