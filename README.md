# Sum-of-subset
Mini project 
import java.util.*;

public class SumOfSubsets {

    static int[] set = new int[12];
    static int target;

    public static void findSubsets(int index, int currentSum, List<Integer> subset) {

        // If target is reached, print subset
        if (currentSum == target) {
            System.out.println(subset);
            return;
        }

        // If sum exceeds or no more elements
        if (index == set.length || currentSum > target) {
            return;
        }

        // Include current element
        subset.add(set[index]);
        findSubsets(index + 1, currentSum + set[index], subset);

        // Backtrack (remove last element)
        subset.remove(subset.size() - 1);

        // Exclude current element
        findSubsets(index + 1, currentSum, subset);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter 12 integers:");
        for (int i = 0; i < 12; i++) {
            set[i] = sc.nextInt();
        }

        System.out.println("Enter target sum:");
        target = sc.nextInt();

        System.out.println("\nSubsets with sum " + target + " are:");

        findSubsets(0, 0, new ArrayList<>());

        sc.close();
    }
}
