# Leetcode---1079
Letter Tile Possibilities
//code in java
import java.util.HashSet;
import java.util.Set;

public class Solution {
    public int numTilePossibilities(String tiles) {
        Set<String> result = new HashSet<>();
        boolean[] used = new boolean[tiles.length()];
        backtrack(tiles, "", used, result);
        return result.size();
    }

    private void backtrack(String tiles, String current, boolean[] used, Set<String> result) {
        if (!current.isEmpty()) {
            result.add(current);
        }
        for (int i = 0; i < tiles.length(); i++) {
            if (used[i]) continue;
            used[i] = true;
            backtrack(tiles, current + tiles.charAt(i), used, result);
            used[i] = false;
        }
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        String tiles = "AAB";
        int result = solution.numTilePossibilities(tiles);
        System.out.println("The number of possible sequences is: " + result); // Output: 8
    }
}
