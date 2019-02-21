# Java Interview Questions

-	Arrays are objects which can store collection of same type of elements
-	An array has a certain number of elements in a fixed order
-	Accessing an invalid array index causes an exception
-	Arrays are objects,and are created on the heap, not the stack
-	Big-O Complexity of operations Access Θ(1), Search Θ(n), Insertion Θ(n), Deletion Θ(n)


## Can we change size of array once created?

-	No, we cannot change the size of array once created.
-	If we need dynamic array, consider using ArrayList class, which can resize itself.

## Can we store String in an array of Integer in Java? compile time error or runtime exception?

-	Answer is both yes and no.
-	we cannot store an String in an array of primitive int, it will result in compile time error 
-	But if we create an array of Object and assign String[] to it 
-	And then try to store Integer object on it
-	Compiler won't be able to detect that and it will throw ArrayStoreExcpetion at runtime

## What is difference between ArrayIndexOutfOBounds and ArrayStoreException? 

-	ArrayIndexOutOfBoundsException comes when we tries to access an invalid index on a given array 
-	E.g. negative index or higher index than length - 1
-	While, ArrayStoreException comes when we have stored an element of type other than type of array

## Can we use Generics with array? 

-	No

## Is it legal to initialize an array int i[] = {1, 2, 3, 4, 5};

-	Yes, its perfectly legal. we can create and initialize array in same line in Java


## Difference between a[] and []a in Java?

- 	we can declare an array in Java by either prefixing or suffixing[] with variable
-	There is not much difference between them if we are not creating more than one variable in one line

	Code Snippet:
	
		int a[], b; // first is int array, second is just int variable int[] c, d; // both c and d are integer array

## What is two dimensional array? 

-	Two Dimensional Array in Java is Array of Array

## Do we have three dimensional array in Java?

-	Java supports N dimensional Array
-	Multidimensional Array in Java is Array of Array

## How to iterate over array in Java?

-	Using forEach or Enhanced for Loop
-	for loop

## How to search an array to check if an element exists there?

-	Using Linear Search or Binary Search
-	Binary Search requires elements needs to be sorted
-	java.util.Arrays class provides binarySearch() method to search an element in the array
-	Alternatively, we convert Array to List and use contains() methods

## How to sort an array in Java?

-	Arrays.sort(T[] t);
- 	Arrays.sort(T[] t, Comparator c);

## How to copy array in Java?

-	System.arraycopy(src, srcIndex, dstAr, dstIndex, NoOfElementsToBeCopied);
-	Arrays.copyOf(srcArray, NoOfElementsToBeCopied);
-	Arrays.copyOfRange(srcArray, beginIndex, endIndex);
-	cloning

## How to access elements of array in Java?

- 	Using index from 0 to length -1
-	Invalid index access will result in ArrayIndexOutOfBoundsException

## What is difference between an array and a linked list?

### Array:
	-	Array is fixed in size 
	-	Runtime size modification is not possible
	-	Array requires contiguous memory allocation
	-	Array is good for searching with index 
	-	Adding and removing elements is expansive with Array

### LinkedList:
	- 	LinkedList is dynamic in nature
	-	LinkedList size can grow or shrink at runtime 
	-	LinkedList can be scattered in memory
	-	LinkedList is good for adding and removing elements



## Can we make array volatile in Java? 

- 	Yes, we can make an array volatile in Java
-	But  we can only make the variable which is pointing to array volatile
-	If array is changed by replacing individual elements 
-	Then "happens before guarantee" provided by volatile variables will not held

##  Where does array stored in memory?

-	Heap Memory
-	Since array is object in Java, even if we create array locally inside a method or block, object is always allocated memory from heap


## How do we find duplicate elements in an array?

-	Using set or Java 8

	Code Snippet:
	
		String[] strArray1 = {"abc1", "def1", "mno1", "xyz1", "pqr1", "xyz1", "def1"};
 
		for (int i = 0; i < strArray1.length-1; i++) {
		 
		for (int j = i+1; j < strArray1.length; j++) {
		 
		if( (strArray1[i].equals(strArray1[j])) && (i != j) ) {
		 
		System.out.println("Duplicates : "+strArray1[j]);
		 
		}

##	How do we search a specific element in an array?

-	Arrays.binarySearch();

## Can you tell me the class name of an array in Java?

-	Array is Object in Java and  getClass().getName() will give the class name 

## What is the step to access elements of an array in Java?

-	We can access using “index”.
-	Index starts from Zero(0), so the first element is stored in location zero and the last element will be Array.length – 1.
-	Example:-String strArr[] = new String []{“A”, “B”, “C”, “D”, “E”};
-	strArr[0] means “A” and strArr[2] means “C”.

## Difference B.w Array and ArrayList

-	Array: 
		
	-	Fixed Size
	-	Contains Primitive and Object 
	-	Cant use Generics
	
-	ArrayList:

	-	Dynamic in Size
	-	Supports Generics
	-	Primitive types are not allowed

## We know that Arrays are objects so why cannot we write strArray.length()?

-	Arrays are object references like classes in Java
-	We can use the methods of Object like toString () and another one hashCode () against Array
-	Length is a data item of an array and so it is not a method
-	That’s why we are using strArray.length


## How to check array contains value or not?

	Code Snippets:
		
		First Method:
			
			public static <T> boolean isExists(final T[] array, final T object) {
				return Arrays.asList(array).contains(object); 
			}

			public static <T> boolean isExists(final T[] array, final T object) {
				return Arrays.asList(array).contains(object); 
			}
		Second Method:

			public static <T> boolean contains(final T[] array, final T v) {
			 
					for (final T e : array) { 
						if (e == v || v != null && v.equals(e)) {
						return true;
				 
						} 
					}
				return false;
			} 
			
			
## How to cut or remove an element from the array?

-	We can remove or cut an element using Apache Commons ArrayUtils based on an index
-	ArrayUtils.remove()			

	Code Snippet:
		
		testArr = ArrayUtils.remove(testArr, 2); //removing element at index 2
		
## What is the logic to reverse the array?

	Code Snippets:
		public static void main(String[] args)
		{
			String[] s = new String[]{"My","Leg","is","cut"};
			for(int i=s.length-1; i>=0; i--){
				System.out.println("reverse "+s[i]);
			}
		}
		
## How do you find the second largest element in an array of integers?
## Write a program to sum values of given array
## How do you separate zeros from non-zeros in an array?

## How to fill element (initialize at once) in an array?


-	Array.fill(array name,value) method and
-	Array.fill(array name, starting index, ending index, value)

## Can we extend an array after initialization?


-	We can extend an array after initialization by adding a new array


	Code Snippet:
	
		Public static void main(String[] args) {
 
			String [] names = new String[] { "A", "B", "C" };
			String [] extended = new String[5];
			extended [3] = "D";
			extended [4] = "E";			 
			System.arraycopy(names, 0, extended, 0, names.length);
			 
			//here we are extending with new array extended[3] and extended[4].
			for (String str: extended){
				System.out.println(str);
			}
		}
## Write a program to insert an element and in the specific position in the array?

	Code Snippet:
	
		public static void main(String[] args) {
		
			int[] my_array = {25, 14, 56, 15, 36, 56, 77, 18, 29, 49};
			
			
			if(my_array!= null && my_array.length < 1) {
				return;
			}
			System.out.println("Before Insertion: "+ Arrays.toString(my_array));
			
			Scanner scan = new Scanner(System.in);
			System.out.println("Enter pos:");
			int pos = scan.nextInt();
			
			System.out.println("Enter element");
			int element = scan.nextInt();
			
			my_array[pos -1] = element;
			
			System.out.println("After Insertion: "+ Arrays.toString(my_array));
			
		}

## Write a java program to check the equality of two arrays?

-	Arrays.equals(arrayOne, arrayTwo);
	
##	Write a java program to convert an array to ArrayList and an ArrayList to array?

-	Array to ArrayList:

	Code Snippet:
	
		ArrayList<String> list = new ArrayList<String>(Arrays.asList(array));
		
- 	ArrayList to List

	Code Snippet:
		
		ArrayList<String> list = new ArrayList<String>();
		String[] array = new String[list.size()];  
        list.toArray(array);
		

## What is time complexity of different Array operations in terms of big o notation?

-	Read is O(1)	
-	Insertion is O(n)
-	Search is O(n)
-	Deletion is O(n)






















	
---------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------




























