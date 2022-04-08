## Trie

- 트라이는 단어 자동 완성, 검색 기능에 많이 사용되는 트리 자료구조중 하나입니다.
- 공간 복잡도는 크지만, 빠른 시간안에 단어를 검색할 수 있습니다.
- 루트노드를 시작으로 문자열을 순회하면서 부모 문자를 prefix로 갖는 자식 문자열을 추가함으로써 트리에 삽입합니다.
- 특정 단어를 찾기 위해선, 삽입과 마찬가지로 문자열을 순회하면서 같은 prefix를 갖는 자식 노드와 단어가 같은지 확인합니다.

### 소스코드

```jsx
class Node {
  constructor(value = '') {
    this.value = value;
    this.end = false;
    this.child = {};
  }
}

class Trie {
  constructor() {
    this.root = new Node();
  }

  insert(string) {
    let currentNode = this.root;

    for (let i = 0; i < string.length; i++) {
      const currentChar = string[i];

      if (currentNode.child[currentChar] === undefined) {
        currentNode.child[currentChar] = new Node(
          currentNode.value + currentChar
        );
      }

      currentNode = currentNode.child[currentChar];
    }
    currentNode.end = true;
  }

  search(string) {
    let currentNode = this.root;

    for (let i = 0; i < string.length; i++) {
      const currentChar = string[i];
      if (currentNode.child[currentChar]) {
        currentNode = currentNode.child[currentChar];
      } else {
        return '';
      }
    }
    return currentNode.value;
  }
}

const trie = new Trie();

trie.insert('hello');
console.log(trie.search('hello'));
```
