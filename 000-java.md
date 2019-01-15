

**What is a view of a collection?**

* It's just another way to look at the object backing the view.

You can think of the implementation of `keySet()` view like this

```java
class KeySet implements Set<K> {
  private final Map<K, V> map;

  public boolean contains(Object o) {
    return map.containsKey(o);
  }

  ...
}
```

* For example, `Arrays.asList()` returns a *view* of the original array. It does not copy the elements to a new list but rather creates a list that contains a reference to the array and operates based on that.

Ref - https://stackoverflow.com/questions/18902484/what-is-a-view-of-a-collection