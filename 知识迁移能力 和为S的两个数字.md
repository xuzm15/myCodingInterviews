# 知识迁移能力 和为S的两个数字

* 输入一个递增排序的数组和一个数字S，在数组中查找两个数，是的他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

* 前后双指针夹逼，a[i]+a[j]<sum时，i++，因为此时要增大和只能向后移动i，移动j的话就重复测试了j之后的点，<时同理。

```
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> FindNumbersWithSum(int [] array,int sum) {
        ArrayList<Integer> ans = new ArrayList<Integer>();
        int i=0;
        int j=array.length-1;
        while (i<j) {
            if (sum == array[i] + array[j]) {
                ans.add(array[i]);
                ans.add(array[j]);
                break;
            }
            if (array[i] + array[j] < sum) {
                i++;
            } 
        	else {
                j--;
            }
        }
        return ans;
    }
}
```