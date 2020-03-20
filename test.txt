# notes

<link rel="stylesheet" href="/css/atom-one-dark.css">
<script src="/js/highlight.pack.js"></script>
<script> hljs.initHighlightingOnLoad(); </script>

```cpp
#include <iostream>

using namespace std;

template<class T>
struct Node {
    T element;
    Node<T> *next = nullptr;
};

template<class T>
struct DoubleNode : Node<T> {
    Node<T> *previous;
};

template<class T>
class List {
protected:
    Node<T> *head;
    Node<T> *current;
    int length = 0;
public:
    List() {
        head = new Node<T>();
        current = head;
    }

    int Length() { return length; }

    virtual void Add(T data) = 0;

    virtual bool Delete(T data) = 0;

    virtual bool Update(T old, T data) = 0;

    virtual bool Search(T data) = 0;
};

template<class T>
class SingleList : public List<T> {
public:
    void Add(T data) override {
        auto *next = new Node<T>{data, nullptr};
        this->current->next = next;
        this->current = this->current->next;
        this->length++;
    }

    bool Delete(T data) override {
        auto previous = this->head;
        auto current = previous->next;
        while (current != nullptr) {
            if (current->element == data) {
                auto removed = current;
                previous->next = current->next;
                delete (removed);
                this->length--;
                return true;
            }
            previous = current;
            current = current->next;
        }

        return false;
    }

    bool Update(T old, T data) override {
        auto current = this->head;
        while (current->next != nullptr) {
            current = current->next;
            if (current->element == old) {
                current->element = data;
                return true;
            }
        }
        return false;
    }

    bool Search(T data) override {
        auto current = this->head;
        while (current->next != nullptr) {
            current = current->next;
            if (current->element == data) {
                return true;
            }
        }
        return false;
    }
};

template<class T>
class SingleCycleList : public SingleList<T> {

};

template<class T>
class DoubleList : public List<T> {
public:
    void Add(T data) override {

    }

    void Delete(T data) override {

    }

    void Update(T old, T data) override {

    }

    bool Search(T data) override {
        return false;
    }
};
```



```http
POST /task?id=1 HTTP/1.1
Host: example.org
Content-Type: application/json; charset=utf-8
Content-Length: 137

{
  "status": "ok",
  "extended": true,
  "results": [
    {"value": 0, "type": "int64"},
    {"value": 1.0e+3, "type": "decimal"}
  ]
}
```



