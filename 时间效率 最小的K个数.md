# 时间效率 最小的K个数

* 输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

* Top k问题，维护一个容量为k堆，遍历所有值，求第k小时用最大堆，把每个元素和堆顶比较，小的话则堆顶出，新元素进，最后堆顶即为第k小；求第k大时用最小堆，把每个元素和堆顶比较，大的话，堆顶出，新元素进，最后堆顶为第k大。

```
import java.util.ArrayList;
import java.util.PriorityQueue;
import java.util.Comparator;

public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
        ArrayList<Integer> ans = new ArrayList<>();
        if ((k == 0) || (k > input.length)) {
            return ans;
        }
        
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(k, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2 - o1;
            }
        });
        
        for (int i = 0; i < input.length; i++) {
            if (maxHeap.size() < k) {
                maxHeap.offer(input[i]);
            } else if (maxHeap.peek() > input[i]){
                maxHeap.poll();
                maxHeap.offer(input[i]);
            }
        }
        
        for (Integer i : maxHeap) {
            ans.add(i);
        }
        
        return ans;
    }
}
```