## LRU Cache

> Design and implement a data structure for [Least Recently Used (LRU) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU). It should support the following operations: `get` and `put`.
>
> `get(key)` - Get the value (will always be positive) of the key if the key exists in the cache, otherwise return -1.
>
> `put(key, value)` - Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.

### Solution

Use a HashMap for key-value. The key point is how to maintain least-recently-used tracking.

Naive idea is to use a list, and move the element to top of the list every time. 

* This will take linear time for get and put.

Another idea is to use Timestamp.

* Use another HashMap for key-timestamp.
* For get it takes O(1) time but for put it still takes O(n) time to find out the element that needs to be evicted by traversing the HashMap.

Now we can see the bottleneck is to find out the element. Sorting defnitely takes more than O(1) time, can we use a List then?

We can maintain a LinkedList, and use a HashMap to get that element and move it using O(1) time.

```java
// 5%
class LRUCache {

    private Map<Integer, Integer> keyValueMap = new HashMap<>();
    private LinkedList<Integer> list = new LinkedList<>(); // List interface does not have `addFirst` method
    private Map<Integer, Integer> keyNodeMap = new HashMap<>();
    private int size = 0;
    private int capacity;

    public LRUCache(int capacity) {
        this.capacity = capacity;
    }
    
    public int get(int key) {
        if (!keyValueMap.containsKey(key)) {
            return -1;
        }
        
        markUse(key);
        
        return keyValueMap.get(key);
    }
    
    public void put(int key, int value) {
        if (capacity == 0) return;
        
        // if exists
        if (keyValueMap.containsKey(key)) {
            markUse(key);
            keyValueMap.put(key, value);
            return;
        }
        
        if (size == capacity) {
            evictLeastRecentlyUsed();
            size--;
        }
        
        keyValueMap.put(key, value);
        Integer node = new Integer(key);
        keyNodeMap.put(key, node);
        list.addFirst(node);
        size++;
    }
    
    private void evictLeastRecentlyUsed() {
        Integer nodeToEvict = list.pollLast();
        keyValueMap.remove(nodeToEvict.intValue());
        keyNodeMap.remove(nodeToEvict.intValue());
    }
    
    private void markUse(int key) {
        Integer node = keyNodeMap.get(key);
        list.remove(node);
        list.addFirst(node);
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```

