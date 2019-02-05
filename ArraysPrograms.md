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
	
## Find all the pairs in Array whose sum is equals to given number


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
## Find Duplicates in an Array

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
			.collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
			duplicatesMap.entrySet().stream().filter(m -> m.getValue()>1)
			.forEach(m -> System.out.println(m.getKey()+": "+ m.getValue()));
			
		}
----------------------------------------------------------------------------------------

##	Search an Element in Array
	
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
























































































































































































































