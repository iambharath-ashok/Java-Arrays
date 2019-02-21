# Java-Arrays

## How to initialize an Array in Java

	Code Snippet:

		//initialize primitive one dimensional array
		int[] arrInt = new int[5];
		
		//initialize Object one dimensional array
		String[] strArr; //declaration
		strArr = new String[4]; //initialization

		//initialize multidimensional array
		int[][] twoArrInt = new int[4][5];

		//multidimensional array initialization with only leftmost dimension
		int[][] twoIntArr = new int[2][];
		twoIntArr[0] = new int[2];
		twoIntArr[1] = new int[3]; //complete initialization is required before we use the array


		//array initialization using shortcut syntax
		int[] arrI = {1,2,3};
		int[][] arrI2 = {{1,2}, {1,2,3}};


		/invalid because dimension is not provided
		int[] a = new int[];

		//invalid because leftmost dimension value is not provided
		int[][] aa = new int[][5];
--------------------------------------------------------------------------------------------
## Two Dimensional Array in Java

	Code Snippet:
		
		public class TwoDimensional {
			
			public static void main(String[] args) {
				
				String [][] array = new String[2][4];
				for(int i=0; i<array.length; i++) {
					for(int j = 0; j < array[i].length; j++) {
						array[i][j] = "Str" + j;
						System.out.print(array[i][j]+" ");
					}
					System.out.println();
				}
			
			
				int [][] iArray = new int[2][];
				
				iArray[0] = new int[2];
				iArray[1] = new int[3];
				
				for(int row=0; row < iArray.length; row++) {
					for(int column=0; column < iArray[row].length;column++) {
						iArray[row][column] = column;
						System.out.print(iArray[row][column]+" ");
					}
					System.out.println();
				}
			}
		}


		public class MultidimensionalArrayExample {

			public static void main(String[] args) {

				// creating and initializing two dimensional array with shortcut syntax
				int[][] arrInt = { { 1, 2 }, { 3, 4, 5 } };
				for (int i = 0; i < arrInt.length; i++) {
					for (int j = 0; j < arrInt[i].length; j++) {
						System.out.print(arrInt[i][j] + " ");
					}
					System.out.println("");
				}

				// showing multidimensional arrays initializing
				int[][] arrMulti = new int[2][]; // yes it's valid

				arrMulti[0] = new int[2];
				arrMulti[1] = new int[3];

				arrMulti[0][0] = 1;
				arrMulti[0][1] = 2;
				arrMulti[1][0] = 3;
				arrMulti[1][1] = 4;
				arrMulti[1][2] = 5;
				for (int i = 0; i < arrInt.length; i++) {
					for (int j = 0; j < arrInt[i].length; j++) {
						System.out.print(arrInt[i][j] + " ");
					}
					System.out.println("");
				}
			}
		}
-------------------------------------------------------------------------------------------------------------
## Java Array of ArrayList, ArrayList of Array


### Java Array of ArrayList


	Code Snippet 1:
	
		public class JavaArrayOfArrayList {

			public static void main(String[] args) {
				List<String> l1 = new ArrayList<>();
				l1.add("1");
				l1.add("2");

				List<String> l2 = new ArrayList<>();
				l2.add("3");
				l2.add("4");
				l2.add("5");

				List<String>[] arrayOfList = new List[2];
				arrayOfList[0] = l1;
				arrayOfList[1] = l2;

				for (int i = 0; i < arrayOfList.length; i++) {
					List<String> l = arrayOfList[i];
					System.out.println(l);
				}
			}
		}
		
		
	Code Snippet of ArrayStoreException 2:

		public static void main(String[] args) {
		
			List<String>[] list = new ArrayList[2];
			
			list[0] = new ArrayList<>();
			list[1] = new LinkedList<>();
			
			System.out.println(list);
		}
	
	Output:
		
		Exception in thread "main" java.lang.ArrayStoreException: java.util.LinkedList
			at twodimensional.ListArray.main(ListArray.java:15)

			
	Code Snippet of Array with Generics:

		List<String>[] arrayOfList = new List<String>[2];
		
-	Java doesn’t support generic array. It will produce compile time error as “Cannot create a generic array of List<String>”.
		
---------------------------------------------------------------

## Java ArrayList of Array

	Code Snippet:

		public class JavaArrayListOfStringArray {

			public static void main(String[] args) {
				// List of String arrays
				List<String[]> list = new ArrayList<String[]>();
				
				String[] arr1 = { "a", "b", "c" };
				String[] arr2 = { "1", "2", "3", "4" };
				list.add(arr1);
				list.add(arr2);
				// printing list of String arrays in the ArrayList
				for (String[] strArr : list) {
					System.out.println(Arrays.toString(strArr));
				}
			}
		}
--------------------------------------------------------------------------------------

## Java String to String Array Example

	Code Snippet:
		
		public class StringToArrayExample {

			/**
			 * This class shows how to convert String to String Array in Java
			 * @param args
			 **/
			public static void main(String[] args) {
				String line = "My name is Bharath";
				//using String split function
				String[] words = line.split(" ");
				System.out.println(Arrays.toString(words));
				//using java.util.regex Pattern
				Pattern pattern = Pattern.compile("\\s+");
				words = pattern.split(line);
				System.out.println(Arrays.toString(words));
			}
		}
		
-	Java provides a legacy class StringTokenizer  
-	But we should not use it because it doesn’t have option for regular expression and using it is confusing
-	We can use Java regular expressions also to split String into String array in java, learn more about Java regular expression

------------------------------------------------

## Java varargs

-	Java varargs was introduced in Java 1.5
-	Java varargs is also known as java variable arguments

	
	Code Snippet:
	
		public static int sum(int i, int...js ){
			//do something
		}
### Important points about varargs in java
-	Few points to know about varargs in java are:
	-	We can have only one varargs in the method
	-	Only the last argument of a method can be varargs
	-	According to java documentation, we should not overload a varargs method


### Why we should not overload varargs method:

	Code Snippet:
	
		public class VarargsExample {

			public static void main(String[] args) {
				System.out.println(sum(1));
				System.out.println(sum(1,2)); //compiler error, ambiguous method

			}

			public static int sum(int i, int...js ){
				System.out.println("sum1 called");
				int sum = i;
				for(int x : js){
					sum+=x;
				}
				return sum;
			}
			public static int sum(int i, int k, Object...js ){
				System.out.println("sum2 called");
				int sum = i+k;
				for(Object x : js){
					sum+=1;
				}
				return sum;
			}	
		}
		
	Code Snippet:

		public class OverloadingVarArgs {	
			public static void main(String[] args) {
				new OverloadingVarArgs().method(3, 2);
			}
			
			void method(int i, int ... j) {
			}
			
			void method(int i, Integer ... j) {
			}
		}
-	In above example, we will notice that compiler will not complain when we overload methods with varargs
-	But when we try to use it, compiler get’s confused which method to use when mapping the second argument
------------------------------------------------

## Add Elements to Array


-	In java array add elements is not supported because size of an Array in java is fixed
-	We have to provide size of the array when we initialize array in java
-	We can write a utility method that we can use to add elements to an array
-	Create a temporary array, whose size will be the addition of length of array and number of elements to add in the array
-	Then I will copy input array to the temporary array and add the elements and then return it

	Code Snippet:
	
		public class AddToArray {

			public static void main(String[] args) {
				Object[] objArr1 = {"1","2","3"};
				Object[] objArr2 = {"4","5","6"};
				//adding an element to array
				Object[] objArr = add(objArr1, "4");
				System.out.println(Arrays.toString(objArr));
				//adding two arrays
				objArr = add(objArr1, objArr2);
				System.out.println(Arrays.toString(objArr));
				
			}
			
			/**
			 * This method will add elements to an array and return the resulting array
			 * @param arr
			 * @param elements
			 * @return
			 **/
			public static Object[] add(Object[] arr, Object... elements){
				Object[] tempArr = new Object[arr.length+elements.length];
				System.arraycopy(arr, 0, tempArr, 0, arr.length);
				
				for(int i=0; i < elements.length; i++)
					tempArr[arr.length+i] = elements[i];
				return tempArr;
				
			}
		}
----------------------------------------------------------
## Arrays.sort();


	Code Snippet:
	
		public static void main(String[] args) {
			int[] intArr = {1, 4, 2, 6, 3};
			String[] strArr = {"E", "A", "U","O","I"};
			//sort int array
			Arrays.sort(intArr);
			Arrays.sort(strArr);
			
			System.out.println(Arrays.toString(intArr));
			System.out.println(Arrays.toString(strArr));
		}
------------------------------------------------------
## Java String Array to String


	Code Snippet:
	
		String string = Arrays.stream(stringArray).collect(Collectors.joining(""));
------------------------------------------------------
## Java ArrayList to Array

	Code Snippet:	
		
		List<String> stringList = new ArrayList<String>();
		
		stringList.add("abc");
		stringList.add("def");
		stringList.add("mno");
		String[] array = stringList.stream().toArray(String[]::new);	
		
		Person[] array = personList.stream().toArray(value -> new Person[value]);
		Person[] array = personList.stream().toArray(Person[]::new);
		
		
	Code Snippet of Shallow Copy:

		public static void main(String[] args) {
			Person p1 = new Person("Bharath");
			Person p2 = new Person("Lisa");
			
			List<Person> pList = new ArrayList<>();
			pList.add(p1); 
			pList.add(p2);
			
			Person[] pArray = pList.toArray(new Person[0]);
			
			System.out.println("Original List = "+pList);
			System.out.println("Created Array from ArrayList = "+Arrays.toString(pArray));
			
			//let's change the list and array
			pList.get(0).setName("David");
			pArray[1].setName("Ram");
			
			System.out.println("Modified List = "+pList);
			System.out.println("Modified Array = "+Arrays.toString(pArray));
			
		}
		
	Code Snippet of Deep Copy:
	
		public static void main(String[] args) {
			Person p1 = new Person("Bharath");
			Person p2 = new Person("Lisa");
			
			List<Person> pList = new ArrayList<>();
			pList.add(p1); pList.add(p2);

			//convert ArrayList to Array using deep copy
			Person[] pArray = new Person[pList.size()];
			
			for(int i =0; i<pList.size(); i++) {
				Person p = pList.get(i);
				Person temp = new Person(p.getName());
				pArray[i] = temp;
			}
			
			System.out.println("Original List = "+pList);
			System.out.println("Created Array from ArrayList = "+Arrays.toString(pArray));
			
			//let's change the list and array
			pList.get(0).setName("David");
			pArray[1].setName("Ram");
			
			System.out.println("Modified List = "+pList);
			System.out.println("Modified Array = "+Arrays.toString(pArray));

		}
------------------------------------------------------------------------------------
## How to convert Array to ArrayList in Java

### Arrays.asList(T… a): 
-	This method returns the underlying representation of the array in the form of ArrayList
-	The returned ArrayList is fixed-sized and any attempt to modify that will result in UnsupportedOperationException at runtime
-	Also any change in the array will change the elements in ArrayList also
	
	Code Snippet:
	
		 String[] strArr = {"1", "2", "3", "4"};
		 List<String> strList = new ArrayList<String>();
		 strList = Arrays.asList(strArr);
		 strArr[0] = "5";
		 // Arrays.asList()
		//strList.add("5");// code will throw java.lang.UnsupportedOperationException because
		//  returns a fixed-size list backed by the specified array

### Collection.addAll(ArrayList<T> list, T[] t):
-	The array data is copied to the list and both are independent object
-	Once the array is copied, we can modify both the objects independently

	Code Snippet:
		
		strList = new ArrayList<String>();
		Collections.addAll(strList, strArr);
		strList.add("5");
		strArr[0] = "1";

### Primitive Array to ArrayList

	Code Snippet:
	
		int[] iArray = { 1, 3, 5, 6, 7, 8 };
		List<int[]> aList = Arrays.asList(iArray);
		
		IntStream flatMapToInt = aList.stream().flatMapToInt(x -> Arrays.stream(x));
		List<Integer> collect = flatMapToInt.boxed().collect(Collectors.toList());
		collect.add(10);
		System.out.println(collect);
		


### UnsupportedOperationException:
	
	Code Snippet:
	
		String[] sArray = {"a","d","q","e","y"};
		List<String> sList = Arrays.asList(sArray);
		
		sList.add("bharath");
		System.out.println(sList);
		
		

	Output:
	
		Exception in thread "main" java.lang.UnsupportedOperationException
			at java.util.AbstractList.add(AbstractList.java:148)
			at java.util.AbstractList.add(AbstractList.java:108)
			at arrays.copy.ArrayToArrayList.main(ArrayToArrayList.java:24)
----------------------------------------------------------------------

## Java Copy Array – Array Copy in Java


### 4 Ways of copying Array:

-	Object.clone(): 

	-	Since array in java is also an Object, we can use this method to achieve full array copy
	-	This method will not if we want partial copy of the array
	-	New separate Array will be created and elements will be copied from existing Array to new Array
	
-	System.arraycopy(): 

	-	System class arraycopy() is the best way to do partial copy of an array
	-	It provides an easy way to specify the total number of elements to copy and the source and destination array index positions
	-	For example System.arraycopy(source, 3, destination, 2, 5) will copy 5 elements from source to destination, beginning from 3rd index of source to 2nd index of destination
	
-	Arrays.copyOf(sourceArray, noOfElementsToBeCopied): 

	-	If we want to copy first few elements of an array or full copy of array, we can use this method
	-	It’s not versatile like System.arraycopy() but easy to use
	-	This method internally use Syste.arraycopy() method
	
-	Arrays.Arrays.copyOfRange(source, biginIndex, endIndex):

	-	If we want few elements of an array to be copied, where starting index is not 0
	-	We can use this method to copy partial Array
	-	Again this method is also using System.arraycopy() method itself


	Code Snippet:

		Object[] oA = { 1, 4, 5, "ddfd", "ddd", new ArrayList<>(), 2, 34, 343, 34, 35, 4, 5, 4, };
		System.out.println("Origianl Array: "+ Arrays.toString(oA));
		
		Object[] copyOf = Arrays.copyOf(oA, 3);
		System.out.println("Arrays.copyOf 3 elements: "+Arrays.toString(copyOf));
		
		Object[] copyOfBE = Arrays.copyOfRange(oA, 3, 6);
		System.out.println("Arrays.copyOfRange 3 from 3 to 6 elements: "+Arrays.toString(copyOfBE));
		
		Object[] oA2 = new Object[90];
		System.arraycopy(oA, 0, oA2, 5, 8);
		System.out.println("System.arraycopy: "+Arrays.toString(oA2));
		
		Object[] clone = oA.clone();
		clone[0]="abc";
		System.out.println("Original Array: "+Arrays.toString(oA));
		System.out.println("Cloned Array: "+Arrays.toString(clone));
		
	Output:

		Origianl Array: [1, 4, 5, ddfd, ddd, [], 2, 34, 343, 34, 35, 4, 5, 4]
		Arrays.copyOf 3 elements: [1, 4, 5]
		Arrays.copyOfRange 3 from 3 to 6 elements: [ddfd, ddd, []]
		System.arraycopy: [null, null, null, null, null, 1, 4, 5, ddfd, ddd, [], 2, 34, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null, null]
		Original Array: [1, 4, 5, ddfd, ddd, [], 2, 34, 343, 34, 35, 4, 5, 4]
		Cloned Array: [abc, 4, 5, ddfd, ddd, [], 2, 34, 343, 34, 35, 4, 5, 4]


----------------------------------------------------------------------
## Summary:

	System.arraycopy(sourceArray, srcIndex, destArray, dstIndex, src.length);
	Arrays.toString();
	Arrays.sort(T[] t);
	Arrays.sort(T[] t, Comparator c);
	list.stream().toArray(String[]::new);
	Arrays.stream();
	Arrays.asList(T[] t);
	Collection.addAll(ArrayList<T> list, T[] t);
	public static <T> boolean addAll(Collection<? super T> c, T... elements) 

	Copy Array:

		clone()
		System.arraycopy()
		Arrays.copyOf()
		Arrays.copyOfRange()
		
	compare Two Arrays:

		Arrays.compare(T[] t1, TG []t2) 
		
	Fill:
	
		Arrays.fill(srcArray, element);
		Arrays.fill(srcArray, BInd, EInd, element);
	
	deepToString(Object[] o);
	
	
-------------------------------------------------------------

	
## How do you compare two arrays?

int[] numbers1 = { 1, 2, 3 };
int[] numbers2 = { 4, 5, 6 };

System.out.println(Arrays.equals(numbers1, numbers2)); //false

int[] numbers3 = { 1, 2, 3 };
System.out.println(Arrays.equals(numbers1, numbers3)); //true

-------------------------------------------------------------
## What is Arrays.deepToString() method


-	Arrays.deepToString() method is used to get the string representation of multidimensional arrays
-	This method returns the deep contents of the specified array
-	deepToString() method will only work for type Object[] and its Child
	
	Code Snippet:
	
		String[] oneDArray = new String[] {"ONE", "TWO", "THREE", "FOUR", "FIVE"};
        System.out.println("One Dimensional Array : ");
        //Printing one dimensional array contents using deepToString() method
        System.out.println(Arrays.deepToString(oneDArray));
        
        String[][] twoDArray = new String[][] {
            {"ONE", "TWO", "THREE", "FOUR"},
            {"FIVE", "SIX", "SEVEN"},
            {"EIGHT", "NINE", "TEN", "ELEVEN", "TWELVE"}
        };
        	System.out.println("Two Dimensional Array : ");
        	System.out.println(Arrays.deepToString(twoDArray));

        	String[][][] threeDArray = new String[][][] {
			    {
			        {"ONE", "TWO", "THREE"},
			        {"FOUR", "FIVE", "SIX", "SEVEN"}
			    },
			    {
			        {"EIGHT", "NINE", "TEN", "ELEVEN"},
			        {"TWELVE", "THIRTEEN", "FOURTEEN"}
			    },
			    {
			        {"FIFTEEN", "SIXTEEN"} ,
			        {"SEVENTEEN", "EIGHTEEN", "NINETEEN"},
			        {"TWENTY", "TWENTY ONE"}
			    }
			};
		System.out.println("Three Dimensional Array : ");
		//Printing three dimensional array contents using deepToString() method
		System.out.println(Arrays.deepToString(threeDArray));

-------------------------------------------------------------
## What are Jagged Arrays:

-	Jagged Arrays are Arrays with different dimensions

	
	
	Code Snippet:

		int [][] iArray = new int[3][];
		
		iArray[0] = {1,2,4,5,6};
		iArray[1] = {2, 5, 6};
		iArray[2] = {8, 9, 10, 11, 12};
-------------------------------------------------------------		
## Can size of the Array can be Negative

-	No, we will get NegativeArraySizeException

-------------------------------------------------------------
##  Is auto-widening, auto-boxing and auto-unboxing is allowed in Java

-	No, only Upcasting is allowed
-	auto-widening and  auto-boxing is not allowed

	Code Snippet:
	
		Integer[] I = new int[5];   //Compile Time Error : Auto-Boxing not allowed
        int[] i = new Integer[10];   //Compile Time Error : Auto-UnBoxing not allowed
        long[] l = new byte[10];    //Compile Time Error : Auto-widening not allowed
        Object[] o = new String[10];    //No Compile Time Error : Auto-Upcasting is allowed, String[] is upcasted to Object[]
-------------------------------------------------------------

## Anonymous array i.e an array without reference

	Code Snippet:
	
		 public static void main(String[] args) {
			//Creating anonymous array
			System.out.println(new int[]{1, 2, 3}.length);    //Output : 3
			System.out.println(new int[]{47, 21, 58, 98}[1]);   //Output : 21
		}

##  Way of declaring multi dimensional arrays

	Code Snippet:
	
		public static void main(String[] args) {
			int[][] twoDArray;    //Normal way of declaring two-dimensional array
			int[] TwoDArray [];   //Another way of declaring two-dimensional array
			int[][][] threeDArray;  //Normal way of declaring three-dimensional array
			int[] ThreeDArray [][];    //This is also legal
		}

## Declaring the contents to the array without new operator
	
	Code Snippet:
	
		public static void main(String[] args) {
			int[] i = {1, 2, 3, 4};   //This is the correct way
			i = {1, 2, 3 , 4};     //Compile time error
			i = new int[]{1, 2, 3, 4};  //This is also correct way
		}


		A ab[] = new A[]{new A(), new A()};
		System.out.println(Arrays.deepToString(ab));

		
---------------------------------------------------------------------------		


