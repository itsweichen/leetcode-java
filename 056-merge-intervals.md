## Merge Intevals

> Given a collection of intervals, merge all overlapping intervals.

### Solution

还可以用图的方法来解。

**Sorting**

注意Sorting怎么写，以及把所有情况要考虑清楚。

复杂度主要在 sorting 上。

* Time: $O(nlogn)$
* Space: $O(n)$

```java
// 21 ms
class Solution {
    public List<Interval> merge(List<Interval> intervals) {
        List<Interval> res = new ArrayList<>();
        
        if (intervals.size() == 0) {
            return res;
        }
        
        Collections.sort(intervals, new Comparator<Interval>() {
            @Override
            public int compare(Interval a, Interval b) {
                return a.start < b.start ? -1 : a.start == b.start ? 0 : 1;
            }
        });
        
        int localMin = intervals.get(0).start;
        int localMax = intervals.get(0).end;
        for (Interval i: intervals) {
            if (i.start > localMax) {
                res.add(new Interval(localMin, localMax));
                localMin = i.start;
                localMax = i.end;
            } else {
                if (i.end > localMax) { // this is necessary! -> [[1,4],[2,3]]
                    localMax = i.end;
                }
            }
        }
        res.add(new Interval(localMin, localMax));
        
        return res;  
    }
}
```

