# 知识迁移能力 和为S的连续正数序列

* 小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列？输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序。

* 双指针begin、end分别记录队列的头尾，count记录当前队列的总和。循环结束条件为begin>（sum-1）/2，此时构不成至少两个的一个合格序列。每次循环开始维护队列至满足count<=sum，然后判断当前队列是否是一个满足题目条件的值，是则记录结果。之后扩展队列，加入下一个数，进入下个循环。

```
import java.util.ArrayList;
public class Solution {
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
        ArrayList<ArrayList<Integer>> anslist = new ArrayList<ArrayList<Integer>>();
        int begin = 1;
        int end = 2;
        int count = begin + end;
        while (begin <= (sum-1)/2) {
            while (count > sum) {
                count -= begin;
                begin++;
            }
            if (count == sum && (end - begin >0)) {
                ArrayList<Integer> list = new ArrayList<Integer>();
                for (int i = begin; i <= end; i++) {
                    list.add(i);
                }
                anslist.add(list);
            }
            end++;
            count += end;
        }
        return anslist;
    }
}
```