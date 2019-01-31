# Java-Arrays

## How to initialize an Array in Java


//initialize primitive one dimensional array
int[] arrInt = new int[5];
/initialize Object one dimensional array
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
----------------------------------------------
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
---------------------------------------------------------------
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
-------------------------------------------

## Java String to String Array Example

	Code Snippet:
		
		public class StringToArrayExample {

			/**
			 * This class shows how to convert String to String Array in Java
			 * @param args
			 **/
			public static void main(String[] args) {
				String line = "My name is Pankaj";
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

	
















