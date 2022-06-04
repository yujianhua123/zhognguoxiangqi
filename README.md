# zhognguoxiangqi
import java.util.Scanner;
import java.util.*;
public class Main{

    static  int[][] dir={{1, 2}, {1, -2}, {-1, 2}, {-1, -2}, {2, 1}, {2, -1,}, {-2, 1}, {-2, -1}};
    public static void main(String[] args) {

        System.out.println(bfs());

    }

    private static int bfs() {
        int min=Integer.MAX_VALUE;
        int[][] arr= new int[9][9];
        Scanner scanner = new Scanner(System.in);
        int x1=scanner.nextInt();
        int y1=scanner.nextInt();
        int x2=scanner.nextInt();
        int y2=scanner.nextInt();
        if (x1==x2&&y1==y2) return 0;
        LinkedList<int[]> queue = new LinkedList<>();
        queue.add(new int[]{x1,y1,0});
        arr[x1][y1]=1;

        while (!queue.isEmpty()){
            int[] poll = queue.poll();
            x1=poll[0];
            y1=poll[1];
            if (x1==x2&&y1==y2) break;
            for (int i = 0; i < dir.length; i++) {
                int m=x1+dir[i][0];
                int n=y1+dir[i][1];
                if (m<1||m>8||n<1||n>8){
                    continue;
                }
                if (arr[m][n]==1) continue;
                //符合条件的8个均入队
                queue.addLast(new int[]{m,n,poll[2]+1});
                if (m==x2&&n==y2){
                    min=Math.min(poll[2]+1,min);
                }
            }
        }
        return min;
    }
}
