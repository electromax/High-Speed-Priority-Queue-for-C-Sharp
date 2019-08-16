# High Speed Priority Queue for C&#35;

### Features ###
* Faster (for path-finding, at least) than any other C# priority queue out there!
* Easy to use
* **Configurable priority type** (numbers, dates, strings, whatever IComparable!) - in comparison to the BlueRaja's project where priorities must be floating-point numbers (accurate as of October 2016, when my Pull request was rejected; you can check yourself how BlueRaja [is doing now](https://github.com/BlueRaja/High-Speed-Priority-Queue-for-C-Sharp/wiki/Using-the-FastPriorityQueue))
* No dependencies on third-party libraries
* Free for both personal and commercial use
* Implements `IEnumerable<T>` for LINQ support!
* Fully unit-tested
* Has a **stable priority queue** implementation _(ie. if two items are enqueued with the same priority, they'll be dequeued in the same order they were enqueued)_
* Takes advantage of the new [forced inline support](http://msdn.microsoft.com/en-us/library/system.runtime.compilerservices.methodimploptions%28v=vs.110%29.aspx) when compiling under .Net 4.5, for even faster speeds
* Should work on .Net versions as old as .Net 2.0

### Is this software free? ###

**Yes!**  See the [license page](https://github.com/BlueRaja/High-Speed-Priority-Queue-for-C-Sharp/wiki/License) for more details.

### Getting Started ###

This project contains two priority queue implementations - one that's super-fast without thread-safety, safety checks, etc (_FastPriorityQueue_), and one that's easy/safe to use (_SimplePriorityQueue_).

```csharp
public class MyNode : FastPriorityQueueNode<int>
{
    // Put custom properties here
    public string Name { get; private set; }
            
    public MyNode(string name)            
    {                
        Name = name;            
    }
}

// Then...

FastPriorityQueue<MyNode, int> queue = new FastPriorityQueue<MyNode, int>(MAX_SIZE);
MyNode myNode1 = new MyNode("Alice");
queue.Enqueue(myNode1, 10);
MyNode myNode2 = new MyNode("Bob");
queue.Enqueue(myNode2, 5);

// Later ...
MyNode nextNode = queue.Dequeue();
Console.WriteLine(nextNode.Name); // Bob
nextNode = queue.Dequeue();
Console.WriteLine(nextNode.Name); // Alice
```csharp
