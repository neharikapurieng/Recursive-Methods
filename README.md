# Recursive-Methods
//Soliving problems recursively
//import java.lang.reflect.Array;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

/*
 * Requirement:
 * You are required to implement all methods recursively.
 * You receive a zero if there is any occurrence of a loop (e.g., for, while).  
 */
public class RecursiveMethods {
	/**
	 * Return an array storing the first n numbers in a Fibonacci sequence. The
	 * Fibonacci starts with the first two numbers being 1 and 1, then starting from
	 * the 3rd number, it is the sum of the previous two numbers. You can assume
	 * that n is positive. e.g., fibArray(5) returns an array {1, 1, 2, 3, 5}.
	 * 
	 * @param n the first n Fibonacci numbers
	 * @return an array representing the first n Fibonacci numbers
	 * 
	 *         You are forbidden to use the fibList method below to solve this
	 *         problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */

	public int[] fibArray(int n) {
		
		int[] array = new int[n];

		if (n < 1) {
			return null;
		}
		if (n == 1) {
			array[0] = 1;
		}
		if (n == 2) {
			array[0] = 1;
			array[1] = 1;
		}
		if (n > 2) {
			int[] temp = fibArray(n - 1);
			int a = (temp[n - 2] + temp[n - 3]);
			array[n - 1] = a;
			System.arraycopy(temp, 0, array, 0, temp.length);
		}
		return array;
	}

	/**
	 * Return a list storing the first n numbers in a Fibonacci sequence. The
	 * Fibonacci starts with the first two numbers being 1 and 1, then starting from
	 * the 3rd number, it is the sum of the previous two numbers. You can assume
	 * that n is positive. e.g., fibList(5) returns a list {1, 1, 2, 3, 5}.
	 * 
	 * @param n the first n Fibonacci numbers
	 * @return a list representing the first n Fibonacci numbers
	 * 
	 *         You are forbidden to use the fibArray method above to solve this
	 *         problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public List<Integer> fibList(int n) {
		List<Integer> list = new ArrayList<>();

		if (n < 1) {
			return null;
		}
		if (n == 1) {
			list.add(1);
		}
		if (n == 2) {
			list.add(1);
			list.add(1);
		}
		if (n > 2) {
			List<Integer> temp = fibList(n - 1);
			int a = (temp.get(n - 2) + temp.get(n - 3));
			list.addAll(temp);
			list.add(a);
		}
		return list;
	}

	/**
	 * Return whether or not an array represents the first n numbers in a Fibonacci
	 * sequence. The Fibonacci starts with the first two numbers being 1 and 1, then
	 * starting from the 3rd number, it is the sum of the previous two numbers. The
	 * array may or may not be empty. e.g., isFibArray({1, 2}) returns false and
	 * isFibArray({1, 1, 2, 3, 5, 8}) returns true.
	 * 
	 * @param a an array
	 * @return true if input array a (of length n) represents the first n Fibonacci
	 *         numbers; false otherwise.
	 * 
	 *         You are forbidden to use the isFibList method below to solve this
	 *         problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public boolean isFibArray(int[] a) {
		int len = a.length;
		if (len == 0) {
			return false;
		}
		if (len < 3) {
			if (a[0] == 1 && len == 1) {
				return true;
			} else if (a[0] == 1 && a[1] == 1) {
				return true;
			} else {
				return false;
			}
		}

		if (a[len - 1] == (a[len - 2] + a[len - 3])) {
			return isFibArray(Arrays.copyOfRange(a, 0, len - 1));
		}

		return false;
	}

	/**
	 * Return whether or not a list represents the first n numbers in a Fibonacci
	 * sequence. The Fibonacci starts with the first two numbers being 1 and 1, then
	 * starting from the 3rd number, it is the sum of the previous two numbers. The
	 * array may or may not be empty. e.g., isFibList({1, 2}) returns false and
	 * isFibList({1, 1, 2, 3, 5, 8}) returns true.
	 * 
	 * @param a an array
	 * @return true if input list a (of length n) represents the first n Fibonacci
	 *         numbers; false otherwise.
	 * 
	 *         You are forbidden to use the isFibArray method above to solve this
	 *         problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public boolean isFibList(List<Integer> list) {
		int size = list.size();

		if (size == 0) {
			return false;
		}
		if (size < 3) {
			if (list.get(0) == 1 && size == 1) {
				return true;
			} else if (list.get(0) == 1 && list.get(1) == 1) {
				return true;
			} else {
				return false;
			}
		}

		if (list.get(size - 1) == (list.get(size - 2) + list.get(size - 3))) {
			return isFibList(list.subList(0, size - 1));
		}

		return false;
	}

	/**
	 * Given a sorted input array a, return a sorted array of size a.length + 1,
	 * consisting of all elements of array a and integer i.
	 * 
	 * @param a an array that is sorted in a non-descending order
	 * @param i an integer
	 * @return a sorted array of size a.length + 1, consisting of all elements of
	 *         array a and integer i. e.g., insertIntoSortedArray({1, 2, 4, 5}, 3)
	 *         returns a sorted array {1, 2, 3, 4, 5}.
	 * 
	 *         You are forbidden to use the insertIntoSortedList method below to
	 *         solve this problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public int[] insertIntoSortedArray(int[] a, int i) {
		

		int[] sortArr = new int[a.length + 1];

		if (a.length < 1) {
			sortArr[0] = i;
			return sortArr;
		}

		if (a[0] < i) {
			if (a.length == 1) {
				sortArr[0] = a[0];
				sortArr[1] = i;
			} else {

				sortArr[0] = a[0];
				int[] temp = insertIntoSortedArray(Arrays.copyOfRange(a, 1, a.length), i);
				System.arraycopy(temp, 0, sortArr, 1, temp.length);

			}
		} else {
			sortArr[0] = i;
			System.arraycopy(a, 0, sortArr, 1, a.length);
		}

		return sortArr;
	}

	/**
	 * Given a sorted input list, return a sorted list of size list.size() + 1,
	 * consisting of all elements of the input list and integer i.
	 * 
	 * @param list a list that is sorted in a non-descending order
	 * @param i    an integer
	 * @return a sorted list of size list.size() + 1, consisting of all elements of
	 *         the input list and integer i. e.g., insertIntoSortedList({1, 2, 4,
	 *         5}, 3) returns a sorted list {1, 2, 3, 4, 5}.
	 * 
	 *         You are forbidden to use the insertIntoSortedArray method above to
	 *         solve this problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public List<Integer> insertIntoSortedList(List<Integer> list, int i) {
		
		List<Integer> sortLst = new ArrayList<>();

		if (list.size() < 1) {
			sortLst.add(i);
			return sortLst;
		}

		if (list.get(0) < i) {
			if (list.size() == 1) {
				sortLst.add(list.get(0));
				sortLst.add(i);
			} else {

				sortLst.add(list.get(0));
				List<Integer> tempLst = insertIntoSortedList(list.subList(1, list.size()), i);
				sortLst.addAll(tempLst);

			}
		} else {
			sortLst.add(i);
			sortLst.addAll(list);
		}

		return sortLst;
	}

	/**
	 * Given two sorted arrays left and right, return a sorted array of size
	 * left.length + right.length, consisting of all elements of arrays left and
	 * right.
	 * 
	 * @param left  a sorted array
	 * @param right a sorted array
	 * @return a sorted array of size left.length + right.length, consisting of all
	 *         elements of arrays left and right. e.g., mergeSortedArrays({1, 3, 5,
	 *         7}, {2, 4, 6, 8}) returns a sorted array {1, 2, 3, 4, 5, 6, 7, 8}.
	 * 
	 *         You are forbidden to use the mergeSortedLists method below to solve
	 *         this problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public int[] mergeSortedArrays(int[] left, int[] right) {
		
		int[] mergArr = new int[left.length + right.length];

		if (left.length == 0 && right.length == 0) {
			return mergArr;
		} else if (left.length == 0) {
			mergArr = right;
		} else if (right.length == 0) {
			mergArr = left;
		}

		else if (left[0] < right[0]) {

			mergArr[0] = left[0];
			int[] temp = mergeSortedArrays(Arrays.copyOfRange(left, 1, left.length), right);
			System.arraycopy(temp, 0, mergArr, 1, temp.length);
		}

		else if (right[0] < left[0]) {
			mergArr[0] = right[0];
			int[] temp = mergeSortedArrays(left, Arrays.copyOfRange(right, 1, right.length));
			System.arraycopy(temp, 0, mergArr, 1, temp.length);
		}

		return mergArr;
	}

	/**
	 * Given two sorted lists left and right, return a sorted list of size
	 * left.size() + right.size(), consisting of all elements of lists left and
	 * right.
	 * 
	 * @param left  a sorted list
	 * @param right a sorted list
	 * @return a sorted list of size left.size() + right.size(), consisting of all
	 *         elements of lists left and right. e.g., mergeSortedLists({1, 3, 5,
	 *         7}, {2, 4, 6, 8}) returns a sorted list {1, 2, 3, 4, 5, 6, 7, 8}.
	 * 
	 *         You are forbidden to use the mergeSortedArrays method above to solve
	 *         this problem.
	 * 
	 *         Requirement: You are required to implement all methods recursively.
	 *         You receive a zero if there is any occurrence of a loop (e.g., for,
	 *         while).
	 */
	public List<Integer> mergeSortedLists(List<Integer> left, List<Integer> right) {

		List<Integer> mergLst = new ArrayList<Integer>();

		if (left.size() == 0 && right.size() == 0) {
			return mergLst;
		} else if (left.size() == 0) {
			mergLst = right;
		} else if (right.size() == 0) {
			mergLst = left;
		}

		else if (left.get(0) < right.get(0)) {

			mergLst.add(left.get(0));
			List<Integer> tempLst = mergeSortedLists(left.subList(1, left.size()), right);
			mergLst.addAll(tempLst);
		}

		else if (right.get(0) < left.get(0)) {
			mergLst.add(right.get(0));
			List<Integer> tempLst = mergeSortedLists(left, right.subList(1, right.size()));
			mergLst.addAll(tempLst);
		}

		return mergLst;
	}
}
