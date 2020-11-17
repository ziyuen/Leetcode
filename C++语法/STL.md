## Set / multiSet
set和multiset容器的插入和删除元素接口跟其他容器也非常类似，但在细节上却存在差别。
c.insert(elem): 在容器中插入元素elem的一份拷贝，并返回新元素的iterator位置；如果是set容器，同时还返回是否插入成功的标志。
c.insert(pos, elem): 在容器中插入元素elem的一份拷贝，并返回新元素的iterator位置；因为set和multiset容器的元素是自动排序的，所以pos位置只是插入位置的一个提示，设置恰当的话，可以提高插入元素的效率。
c.insert(beg, end): 在容器中插入[beg, end)范围中所有元素的拷贝，没有返回值。
c.erase(val): 删除容器中所有值为val的元素，返回删除元素的数目。
c.erase(pos): 删除容器中位置pos处的元素，没有返回值。
c.erase(beg, end): 删除容器中[ben, end)范围内所有的元素，没有返回值。
c.clear(): 删除容器中所有元素，使容器成为空容器。
其中我们重点说一下c.insert(elem)接口。对于set容器，它的定义如下： pair<iterator, bool> insert(const TYPE& val);而对于multiset容器，它的定义如下：iterator insert(const TYPE& val);它们的不同就是set容器的insert接口返回的是一个pair<iterator, bool>，而multiset容器的insert接口直接返回一个iterator。这是因为set容器中不允许有重复的元素，如果容器中已经存在一个跟插入值相同的元素，那么插入操作就会失败，而pair中的bool值就是标识插入是否成功的。而multiset不存在这个问题。

## Deque 双端队列
可以 push_front(), pop_front(), push_back(), pop_back()
通过 front() 访问第一个元素 以及 通过 back() 访问最后一个元素。

## 自定义堆

最小堆：priority_queue<int, vector<int>, greater<int>> min_heap;

```cpp
#include <iostream>
#include <queue>

using namespace std;

typedef struct packet {
    int priority;
    std::string name;

    friend bool operator<(const packet& a, const packet& b) {
        return a.priority > b.priority;
    }

}
packet;

struct comparator
{
    bool operator()(const packet * a, const packet *b)
    {
        return a->priority > b->priority;
    }
};

//comparator f; edit - no need for this forgot to comment oops

int main() {
    std::priority_queue<packet*,vector<packet*>,comparator> packets; // i add comparator and vector<packet*> here

    packet* p1 = new packet();
    packet* p2 = new packet();
    packet* p3 = new packet();

    p1->priority = 200;
    p2->priority = 20;
    p3->priority = 89;

    p1->name= "test";
    p2->name = "test2";
    p3->name = "test3";

    packets.push(p1);
    packets.push(p2);
    packets.push(p3);

    std::cout << "first: " << packets.top()->name;
    packets.pop();
    std::cout << "second: " << packets.top()->name;
    packets.pop();
    std::cout << "third: " << packets.top()->name;
    packets.pop();

    return 0;
}
```