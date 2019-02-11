#	Arrays


-	Array is a linear Data structure
-	Data is Stored continuously in Array
-	Reading is faster in Array, using index
-	Updating or deleting element in middle of Array is Computational Task

----------------------------------------------------------

## Find Min or Max or Array

	
	Code Snippet:
	
		public int findMin(int [] array) {
			int min = array[0];
			
			for(int i = 1; i < array.length; i++) {
				if(array[i] < min) {
					min = array[i];
				}
			}
			return min;
		}
----------------------------------------------------------

## Find Sub Sequence matching to Element


	Code Snippet:
	
		public static void findSubsequence(int [] array, int element) {
		int start = 0;
		int sum = array[0];
		for(int i = 1; i<array.length; i++) {
			sum += array[i];
			while(sum > element) {
				sum -= array[start];
				start++;
			} 
			if(sum == element) {
				for(int j = start; j<=i; j++) {
					System.out.println(array[j]);
				}
			}
		}
	}
	
----------------------------------------------------------
	
## Find all the pairs in Array whose sum is equals to given number or How to find all pairs on integer array whose sum is equal to given number? 


	Code Snippet:
	
		1.	 TC: O(n log n)
			
			findThePairs(int [] array, int sumNumber) {
				
				 Arrays.sort(array);
				 
				 int i = 0;
				 int j = array.length - 1;
				 
				 
				 while( i < j ) {
				 
					if (array[i] + array[j] == sumNumber) {
						System.out.println("Pairs: of Item: "+element+ " ("+arr[i]+","+arr[j]+")");
						j--;
						i++;
					} else if (array[i] + array[j] < sumNumber) {
						i++;
					} else if (array[i] + array[j] > sumNumber) {
						j--;
					}
				 }
			} 


		2. Brute Force Way: TC O(n^2)
		
			findThePairs(int [] array, int sumNumber) {
				for(int i = 0; i < array.length; i++) {
					for(int j = i + 1; j < array.length; j++) {
						if(array[i] + array[j] == sumNumber) {
							System.out.println("Pairs: of Item: "+element+ " ("+arr[i]+","+arr[j]+")");	
						}
					}
				}
			}
	
----------------------------------------------------------	

## Find all the Leaders in the Array


	Code Snippet:
	
	
		void findLeaders(int [] array) {
			int max = array[array.length - 1];
			Syso("Leaders of Array are: ");
			syso(max);
			
			for(int i = array.length - 2; i >= 0; i--) {
				if (max < array[i]) {
					syso(array[i]);
					max = array[i];
				}
			}
			
		}
----------------------------------------------------------

## Move all the Zero to End of Array


	Code Snippet of Moving Zero's to End:
	
		iint[] moveZeroToEnd(int []array) {
			int counter = 0;	
			for (int i = 0; i < array.length; i++) {
				if(array[i] != 0) {
					array[counter] = array[i];
					counter++;
				}
			}
			Arrays.fill(array, counter, array.length, 0);
			return array;
		}

----------------------------------------------------------
## Move all the Zero to Beginning of Array	
	Code Snippet of Moving Zero's to End:
	
		public static int[] moveZeroToBeginning(int array[]) {
			int counter = array.length -1;

			for(int i = array.length -1;i>=0; i--) {
				if(array[i]!=0) {
					array[counter] = array[i];
					counter--;
				}
			}

			while(counter >= 0) {
				array[counter] = 0;
				counter--;
			}
			return array;
		}
----------------------------------------------------------

## 	Reverse an Array

	Code Snippet:
	
		public static int[] reverseArray(int [] array) {
			int i = 0;
			int j = array.length - 1;
			
			while (i < (i + j) / 2) {
				array[i] = array[i] + array[j];
				array[j] = array[i] - array[j];
				array[i] = array[i] - array[j];
				i++;
				j--;
			}
			return array;
		}
----------------------------------------------------------		
## Second Largest Element of Array:

	Code Snippet:
	
		public static void findSecondLargest(int [] array) {
		
				if(array.length < 2) {
					System.out.println("Invalid Array.");
					return;
				}
				
				int firstLargest = array[0];
				int secondLargest = array[1];
				
				if(firstLargest < secondLargest) {
					firstLargest = array[1];
					secondLargest = array[0];
				}
				
				for(int i =2; i < array.length; i++) {
					if(array[i] > firstLargest) {
						secondLargest = firstLargest;
						firstLargest = array[i];
					} else if(array[i] < firstLargest && array[i] > secondLargest) {
						secondLargest = array[i];
					}
				}
			}			
			System.out.println("Second Largest of Array is: "+ secondLargest);
		}
-------------------------------------------------

## Find a Missing Number in a Array

	
	Code Snippet:
	
		public static void missingNumbersInArray(int[] array, int totalCount) {

			int missingCount = totalCount - array.length;
			BitSet bs = new BitSet(totalCount);
			for (int num : array) {
				bs.set(num - 1);
			}

			System.out.println("Missing in Array: " + Arrays.toString(array) + " with Missing Count: " + missingCount);
			int lastMissingIndex = 0;
			for (int i = 0; i < missingCount; i++) {
				lastMissingIndex = bs.nextClearBit(i);
				System.out.println(++lastMissingIndex);
			}
		}

-------------------------------------------------
## Find Duplicates in an Array or How to find duplicate number on Integer array in Java? 

	Code Snippet with TC o(n^2):

		public static void findDuplicatesNx2(int array[]) {
			for (int i = 0; i < array.length; i++ ) {
				for (int j = i + 1; j < array.length; j++ ) {
					if(array[i] == array[j]) {
						System.out.println(array[i]);
					}
				}
			}
		}

	Code Snippet:
	
		public static void findDuplicatesUsingSet(int[] array) {
			Set<Integer> set = new HashSet<>();
			
			for(int number : array) {
				if(!set.add(number)) {
					System.out.print(number +" ");
				}
			}
		}

	Code Snippet using Java 8:
	
		public static void findDuplicatesFrequency(int []array) {
		
			Map<Integer, Long> duplicatesMap =  Arrays.stream(array).boxed()
			.collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()));
			duplicatesMap.entrySet().stream().filter(m -> m.getValue()>1)
			.forEach(m -> System.out.println(m.getKey()+": "+ m.getValue()));
			
		}
----------------------------------------------------------------------------------------

##	Search an Element in Array or How to check if array contains a number in Java?


	Code Snippet of Binary Search:
	
		public static boolean binarySearch(int [] array, int element) {
			if(array!= null && array.length < 1) {
				throw new IllegalArgumentException("Invalid Array.");
			}
			Arrays.sort(array);
			int low = 0;
			int high = array.length -1;
			
			while(low < high) {
				int mid = (low + high)/2;
				
				if(array[mid] == element) {
					return true;
				} else if(element < array[mid]) {
					high = mid - 1;
				} else {
					low = mid + 1;
				}
			}
			return false;
		}
	
	
	Code Snippet of Searching with Generics Method:
	
		public  static <T> boolean isExists(final T[] array, final T object) {
			return Arrays.asList(array).contains(object);
		}
		
		public static <T> boolean contains(final T [] array, final T v) {
			
			for(final T e: array) {
				if( e == v || e != null || e.equals(v)) {
					return true;
				}
			}
			return false;
		}
			

----------------------------------------------------------------------------------------
## How to find largest and smallest number in unsorted array? 

	Code Snippet:
	
		public static void findMinAndMax(int [] array) {
		
			int largest = Integer.MIN_VALUE;
			int lowest = Integer.MAX_VALUE;
			
			for(int number : array) {
				if(number > largest) {
					largest = number;
				} else if(number < lowest) {
					lowest = number;
				}
			}
			
			System.out.println("Max: "+ largest +" Min: "+ lowest);
		}
----------------------------------------------------------------------------------------
## How to find repeated numbers in an array if it contains multiple duplicates?  or First Non-repeated chars?

	Code Snippet of NonRepeatingChar:
	
		public static char findFirstNonRepeatingChar(String string) {
			Map<String, Long> charCount = string.chars().mapToObj(ch -> String.valueOf((char) ch))
					.collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()));
			String ch = charCount.entrySet().stream().filter(m -> m.getValue() == 1).findFirst().get().getKey();
			return ch.charAt(0);
		}
		
	
	Code Snippet of NonRepeating Element:	
		public  static int findFirstNonRepeatingElement(int [] array) {
			int firstNonRepeatingElement = Integer.MIN_VALUE;
			
			Map<Integer, Long> map = new LinkedHashMap<>();
			
			for(int number : array) {
				map.put(number, map.containsKey(number)? 1 + map.get(number) : 1);
			}
			System.out.println(map);
			for(Entry<Integer, Long> e : map.entrySet()) {
				if(e.getValue() == 1) {
					firstNonRepeatingElement = e.getKey();
					break;
				}
			}
			return firstNonRepeatingElement;
		}
-------------------------------------------------------
## How to find first Repeating Element in Array

	Code Snippet of Finding first Repeating Element:
	
	
		public static int findFirstRepeatingElement(int array[]) {
		
			Set<Integer> nonRepeating = new LinkedHashSet<>();
			List<Integer> repeating = new ArrayList<>();
		
			for(int e : array) {
				
				if(nonRepeating.contains(e)) {
					nonRepeating.remove(e);
					repeating.add(e);
				} else {
					nonRepeating.add(e);
				}
				
			}
			
			return  repeating.get(0);
		}

-------------------------------------------------------

## Write a program to remove duplicates from array in Java? 

	Code Snippet:
	
		public static int[] removeDuplicatesFromArray(int []array) {
	
			if(array != null && array.length < 1) { 
				throw new IllegalArgumentException();
			}
			
			Arrays.sort(array);
			int previous = array[0];
			
			for(int i = 1; i < array.length; i++) {
				
				if(array[i]== previous) {
					array[i] = 0;
				} else {
					previous = array[i];
				}
			}
			System.out.println(Arrays.toString(array));
			
			return array;
		}
-------------------------------------------------------

## Write a program to find intersection of two sorted arrays in Java? 

	Code Snippet:
	
		public static Integer[] findIntersection(int[] a, int[] b, int[] c) {
			int i = 0, j = 0, k = 0;
			List<Integer> intersectionList = new ArrayList<>();
			while (i < a.length && j < b.length && k < c.length) {
				if (a[i] == b[j] && b[j] == c[k]) {
					intersectionList.add(a[i]);
					i++;
					j++;
					k++;
				} else if (a[i] < b[j])
					i++;
				else if (b[j] < c[k])
					j++;
				else
					k++;
			}
			return intersectionList.stream().toArray(Integer[]::new);
		}
		
		public static void main(String[] args) {
			int a[] = {1,2,3,5,6,8,9,11,13};
			int b[] = {2,3,4,5,7,8,11,12};
			int c[] = {2,3,4,5,7,9,10,11,13};
			Integer[] iAr = findIntersection(a,b,c);
			System.out.println(Arrays.toString(iAr));
		}
		
	Time Complexity:

		O(n log n) if Arrays are not sorted
		O(n) if Arrays are sorted


	













































































































































































































