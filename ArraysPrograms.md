# Java Array Programming Questions

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


## There is an array with every element repeated twice except one. Find that element?

	Code Snippet:
	
		Map<Integer, Long> map = Arrays.stream(array).boxed().collect(Collectors.groupingBy(Function.identity(),Collectors.counting()));
		map.entrySet().stream().filter(e -> e.getValue() ==1 ).findFirst().get().getKey();
		
		
		public static int findNumber(int [] array) {
			int result = 0;
			
			for(int v : array) {
				result ^= v;
			}
			return result;
		}
	
		public static void main(String[] args) {
			int [] array = {1,1,2,2,3,4,5,5,3};
			int num = findNumber(array);
			System.out.println(num);
		}
			
			
	Order of Algorithm:
	
		Time Complexity: O(n)
		space complexity = O(1)
		
		
		
## How to find kth smallest and Largest element in unsorted array?

	Code Snippet:
	
		public class KthSmallestAndLargest {
			public static int findKthSmallest(int array[], int kthSmallest) {
				Arrays.sort(array);
				return array[kthSmallest - 1];
			}

			public static int findKthLargest(int array[], int kthLargest) {
				Arrays.sort(array);
				return array[array.length - kthLargest];
			}
		}
	
	
-	Create Max Heap and Min Heap of around Array and can return the Kth values from it

## How to find common elements in three sorted array?

	Examples:

		input1 = {1, 5, 10, 20, 40, 80}
		input2 = {6, 7, 20, 80, 100}
		input3 = {3, 4, 15, 20, 30, 70, 80, 120}
		Output: 20, 80




## How to find top two numbers from an integer array? 

	Code Snippet:
	
		public class FindTopTwoNumbers {
	
			public static void findTopTwo(int array[]) {
			
				if(array!= null && array.length < 2) {
					throw new IllegalArgumentException("Invalid Array");
				}
				int firstLargest = 0;
				int secondLargest = 0;
				if(array[0] < array[1]) {
					firstLargest  = array[1];
					secondLargest = array[0];
				}
				for(int i = 2; i < array.length; i++) {
					if(array[i] > firstLargest) {
						secondLargest = firstLargest;
						firstLargest = array[i];
					} else if(array[i] < firstLargest && array[i]> secondLargest) {
						secondLargest = array[i];
					}
				}
				
				System.out.printf("Top two Numbers in Arrays are: %d and %d",firstLargest, secondLargest);
			}

			
			public static void main(String[] args) {
				int [] array = {10,30,80,90,90,70,30,20,80,40,60};
				findTopTwo(array);
			}
		}
		
	Order of Algorithm:
	
		Time Complexity: O(n)
		Space Complexity: O(1)
		
		
## How to find the smallest positive integer value that cannot be represented as sum of any subset of a given array?

	Code Snippet:
	
		public class Smallestpositiveinteger {

			public static int smallestPositiveInteger(int array[]) {
				int smallestPositiveInt = 1;
				
				for(int i = 0; i < array.length; i++) {
					if(array[i] <= smallestPositiveInt) {
						smallestPositiveInt += array[i];
					}
				}
				return smallestPositiveInt;
			}

			public static void main(String[] args) {
				int [] array = {1,4,5,7,8};
				int smallestPositive = smallestPositiveInteger(array);
				System.out.println(smallestPositive);
			}

		}
	Order of Algorithm
		
		Time Complexity : O(n)
		Space Complexity: o(1)
		
		
## How to rearrange array in alternating positive and negative number?

	Code Snippet:
	
	
		public class AlternateArrangements {
 
			public static int [] reArrange(int[]array) {
				
				int pivot = 0;
				int left = 0;
				int right = array.length -1;
				
				while (left < right) {
					while(left <= right && array[left] < pivot) {
						left++;
					}
					while(right >= left && array[right] > pivot) {
						right--;
					}
					if(left < right) {
						swap(left, right, array);
						left ++;
						right --;
					}
				}
				
				left = 1;
				int splitPoint = 0;
				while(array[splitPoint] < 0) {
					splitPoint++;
				}
				right = splitPoint;
				
				while(array[left] < 0 && right < array.length) {
					swap(left, right, array);
					left +=2;
					right++;
				}
				return array;
			}
			
			private static void swap(int i , int j, int array[]) {
				int temp = array[i];
				array[i] = array[j];
				array[j] = temp;
			}
			
			
			public static void main(String ...strings ) {
				int array[]= { 1, 2, -3, -4, -5, 6, -7, -8, 9, 10, -11, -12, -13, 14 };		
				array = reArrange(array);
				System.out.println(Arrays.toString(array));
			}
		}
		
	Order of Algorithm:

		Time Complexity: O(n)
		Space Complexity: O(1)



## How to remove duplicates from array in place?

	Code Snippet:
	
		public class RemoveDuplicatesInPlace {
			public static int removeDuplicates(int [] array) {
			int j = 0;
			
			
			Arrays.sort(array);
			for(int i= 0; i< array.length - 1; i++) {
				if(array[i]!=array[i+1]) {
					array[j++] = array[i];
				}
			}
			array[j++] = array[array.length -1];
			System.out.println(Arrays.toString(array));
			return j;
		}
	
		public static void main(String[] args) {
			int [] array = {10,30,40,20, 10,50,80,30,20,90};
			int index = removeDuplicates(array);
			
			for(int i = 0; i< index; i++) {
				System.out.print(array[i]+" ");
			}
		}
	}

	Order of Algorithm:
	
		Time complexity: O(n)
		Space Complexity: O(1)
		
## How to remove a given element from array in Java?

	Code Snippet:
	
		public class RemoveElementFrArray {
	
			public static int removeElement(int [] array, int element) {
				int j = 0;
				int i = 0;
				for (i = 0; i < array.length; i++) {
					if(array[i] != element) {
						array[j++] = array[i];
					} 
				}
				
				int temp []  = Arrays.copyOf(array, j);
				System.out.println(Arrays.toString(temp));
				return j ;
			}
			
			
			public static void main(String[] args) {
				int [] array = {10,20,10,30,40,50,10,10};
				int index = removeElement(array,10);
				for(int i = 0; i< index; i++) {
					System.out.print(array[i]+" ");
				}
			}
		}

	
	Order of Algorithm:
		
		Space Complexity: O(1)
		Time Complexity: O(n)
		
## How to merge sorted array?


	Code Snippet:
	
		public static int[] mergeSortedArray(int []a, int b[]) {
		
			int [] result  = new int[a.length + b.length];
			int i = 0, j = 0, k = 0;
			
			while(i < a.length && j < b.length) {
				if(a[i] == b[j]) {
					i++;
					continue;
				}
				result[k++] = a[i] < b[j]? a[i++]: b[j++];
			}
			
			// first way of copying remaining elements
			System.arraycopy(a, i, result, k, a.length - i);
			System.arraycopy(b, j, result, k, b.length - j);
			System.out.println(Arrays.toString(result));
			
			// first way of copying remaining elements
	//		while(i < a.length) {
	//			result[k++] = a[i++];
	//		}
	//		
	//		while(j < b.length) {
	//			result[k++] = b[j++];
	//		}
			
	//		System.out.println(Arrays.toString(result));
			
			return result;
		}
	
	
	
	Order of Algorithm:
	
		Time Complexity: O(n)
		Space Complexity:	O(n)
		
		
## 	How to find sub array with largest product in array of both positive and negative number?

	Code Snippet:
	
		
		public class MaxProductSubArray {
		
		public static int maxProduct(int [] array) {
			
			// product till ith index. 
			int minVal = array[0]; 
			int maxVal = array[0]; 
		  
			int maxProduct = array[0]; 
		  
			for (int i = 1; i < array.length; i++) 
			{ 
		
				// When multiplied by -ve number, 
				// maxVal becomes minVal 
				// and minVal becomes maxVal. 
				if (array[i] < 0) 
				{ 
					int temp = maxVal; 
					maxVal = minVal; 
					minVal =temp; 
				  
				} 
		  
				// maxVal and minVal stores the 
				// product of subarray ending at arr[i]. 
				maxVal = Math.max(array[i], maxVal * array[i]); 
				minVal = Math.min(array[i], minVal * array[i]); 
		  
				// Max Product of array. 
				maxProduct = Math.max(maxProduct, maxVal); 
			} 
		  
			// Return maximum product found in array. 
			return maxProduct; 
		}
		
		
		public static void main(String[] args) {
			int array[] = {2,3, -2,-4};
			System.out.println(maxProduct(array));;
			
		}

	}
	
	Output:
		
		Time Complexity :O(n)
		Space Complexity : O(1)


## 	How to find sub array with maximum sum in an array of positive and negative number?

	Code Snippet:
	
		public class MaxSumSubArray {

		public static void findMaxSum(int[] array) {
			
			int max_end_here,max_so_far, start, end , s;
			max_end_here = max_so_far = start = end = s = 0;
			
			for (int i = 0; i < array.length; i++) {
				max_end_here += array[i];
				
				if(max_end_here < 0) {
					max_end_here = 0;
					s = i  + 1;
				} else 	if(max_so_far < max_end_here) {
					max_so_far = max_end_here;
					start = s;
					end = i;
				}
			}
			
			System.out.println("Maximum Sum of Contigious Array is : "+ max_so_far);
			System.out.println("Starting Index: "+ start);
			System.out.println("Ending Index: "+end);
		}
		
		public static void main(String[] args) {
			int [] array = {-2, -3, 4, -1, -2, 1, 5, -3};
			findMaxSum(array);
		}

	}
	
	Order of Algorithm:
	
		Time Complexity: O(n)
		Space Complexity : O(n)
		
## Find a pair with maximum product in array of Integers?


	Code Snippet:
	
		public class PairWithMaximumProduct {

			public static void findPairs(int[] array) {
				int negA, negB, posA, posB;
				negA = negB = posA = posB = Integer.MIN_VALUE;

				for (int i = 0; i < array.length; i++) {

					if (array[i] > posA) {
						posB = posA;
						posA = array[i];
					} else if (array[i] > posB) {
						posB = array[i];
					}

					if (array[i] < 0 && Math.abs(array[i]) > Math.abs(negA)) {
						negB = negA;
						negA = array[i];
					} else if (array[i] < 0 && Math.abs(array[i]) > Math.abs(negB)) {
						negB = array[i];
					}
				}

				if (negA * negB > posA * posB) {
					System.out.println(negA + " : " + negB);
				} else {
					System.out.println(posA + " : " + posB);
				}

			}

			public static void main(String[] args) {
				int array[] = { 7, 9, 0, -8, -9, -7, -8, 6, 8,-9 };
				findPairs(array);
			}
		}

	Order Of Algorithm:
		
		Time Complexity: O(n)
		Space Complexity : O(1)
		
	
##  Write a program to find length of longest consecutive sequence in array of integers


	Code Snippet:
	
		public class ConsequetiveUsingSet {

			public static int findLongestConsequetive(int array[]) {
				Set<Integer> set = new HashSet<>();
				
				int maxLength = 0;
				
				for(int v : array) {
					set.add(v);
				}
				
				for(int v : array) {
					if(!set.contains(v - 1)) {
						continue;
					}
					
					int length = 1;
					int k = v;
					while(set.contains(--k)) {
						set.remove(k);
						++length;
					}
					k = v;
					while(set.contains(++k)) {
						set.remove(k);
						++length;
					}
					
					maxLength = Math.max(maxLength, length);
				}

				return maxLength;
			}
			
			public static void main(String ...strings) {
				int [] array = {1,3,0,1,2,3,8,9,10,11,12,13};
				int length = findLongestConsequetive(array);
				System.out.println(length);
			}
		}

		
		
		Program 2:
			
			public class SubSequent {

				public static Integer[] findLongestConsequent(int[] array) {
					List<Integer> tempList = new ArrayList<>();
					List<List<Integer>> finalList = new ArrayList<>();
					int lastNum = array[0];
					tempList.add(lastNum);

					for (int v : array) {
						if (v - 1 == lastNum) {
							lastNum = v;
							tempList.add(lastNum);
						} else {
							finalList.add(tempList);
							lastNum = v;
							tempList = new ArrayList<>();
							tempList.add(lastNum);
						}
					}
					
					List<Integer> longestList = new ArrayList<>();
					for(List<Integer> v: finalList) {
						if(v.size() > longestList.size()) {
							longestList = v;
						}
					}
					return longestList.stream().toArray(Integer[]::new);
				}
				
				public static void main(String...strings) {
					int [] array = {1,2,10,15,1,2,3,4,5,6,1,2};
					Integer[] longestConseq = findLongestConsequent(array);
					System.out.println(Arrays.toString(longestConseq));
				}
			}

----------------------------------------------------------------------
	
## How to get the index of an array element?	

	
	Code Snippet:
	
	
		public static int findIndex(int [] array, int element) {
			
			int low = 0;
			int high = array.length - 1;
			
			while(low <= high) {
				int mid = (low + high)/2	
				if(array[mid] == element) {
					return mid;
				} else if (key < array[mid]) {
					high = mid - 1;
				} else if (key > array[mid]) {
					low = mid + 1;
				}
			}
			return -1;
		}
-------------------------------------------------------	
## How to create sub array from array

	Code Snippet:
	
		String[] bestIndianCreditCards = {"ICICI Instant Platinum Credit Card", "Standard Chartered Platinum Rewards Credit Card", "Citibank Platinum Credit Card", "SBI Gold Credit Card", "Yatra SBI Credit Card", "HDFC Platinum Plus Credit Card", "HDFC Solitaire Credit Card"}; 
		// let's create sub array in Java 
		String[] sbiCards = new String[2]; System.arraycopy(bestIndianCreditCards, 3, sbiCards, 0, 2);
-------------------------------------------------------
## Given a max-heap represented as an array, Return the kth largest element without modifying the heap.
## Given a sorted array, find all the numbers that occur more than n/4 times.	
## Check if array can represent preorder traversal of binary search tree
## Find the smallest range that includes at least one number from each of the k lists
## Write 2 functions to serialize and deserialize an array of strings
## You are given array A and arrayB, write a function to shuffle arrayA and so you can get countA > countB
## How to randomly select a number in an array in Java?	
## ## How to find minimum value in a rotated sorted array?
## Given an array of of size n and a number k, find all elements that appear more than n/k times? 	
## How find the first repeating element in an array of integers? 
## How to find first non-repeating element in array of integers?
	
	

