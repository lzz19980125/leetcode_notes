# 前k个高频元素（leetcode 215，347）

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i:nums){
            map.put(i,map.getOrDefault(i,0)+1);
        }
        PriorityQueue<Map.Entry<Integer,Integer>> pq = new PriorityQueue<>(new Comparator<Map.Entry<Integer,Integer>>(){
            public int compare(Map.Entry<Integer,Integer> entry1,Map.Entry<Integer,Integer> entry2){
                return entry1.getValue()-entry2.getValue();
            }
        });
        for(Map.Entry<Integer,Integer> entry:map.entrySet()){
            if(pq.size()<k){
                pq.add(entry);
            } else{
                pq.add(entry);
                pq.poll();
            }
        }
        int [] result = new int [k];
        int i=0;
        for(Map.Entry<Integer,Integer> entry:pq){
            result[i] = entry.getKey();
            i++;
        }
        return result;
    }
}
```

