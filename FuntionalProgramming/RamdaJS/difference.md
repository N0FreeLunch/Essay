## difference
> Finds the set (i.e. no duplicates) of all elements in the first list not contained in the second list.
- 첫 번째 리스트의 모든 원소에서 두 번째 리스트에 속하지 않은 원소들의 집합을 찾아낸다.
> Objects and Arrays are compared in terms of value equality, not reference equality.
- 오브젝트와 배열은 값의 동일성 관점에서 비교되며 참조 동일성으로는 비교되지 않는다.
> See also [differenceWith](./differenceWith.md), [symmetricDifference](./symmetricDifference.md), [symmetricDifferenceWith](./symmetricDifferenceWith), [without](./without.md).

### 설명
- difference는 수학 집합에서 차집합을 의미한다. 집합 A에서 집합 B의 원소를 뺀 것으로 집합 A에서 A와 B 모두에 속한 교집합의 원소를 뺀 나머지 A의 원소 집합을 의미한다.
- 첫 번째 인자로 배열을 받고 두 번째 인자로 배열을 받아서 첫 번째 인자의 배열에서 두 번째 인자의 배열에 속한 원소를 모두 제외하고 남는 원소로 이뤄진 배열을 반환한다.
- 배열의 원소로는 동일한 형태의 오브젝트도 제외할 수 있다.

### 문법
```
R.difference(list1: Array, list2: Array): Array
```
> `list1`: The first list.
- `list1`: 첫 번째 리스트
> `list2`: The second list.
- `list2`: 두 번째 리스트
> Returns Array The elements in `list1` that are not in `list2`.
- `list1`에는 속하지만, `list2`에는 속하지 않는 원소들의 배열을 반환한다.

### 표현
```
[*] → [*] → [*]
```
- `[*] →`: 첫 번째 인자로 배열을 받는다.
- `→ [*] →`: 두 번째 인자로 배열을 받는다.
- `→ [*]`: 첫 번째 배열에서 두 번째 배열의 원소를 제외하고 남은 원소로 구성된 배열을 반환한다.

### 예제
```js
R.difference([1,2,3,4], [7,6,5,4,3]); //=> [1,2]
R.difference([7,6,5,4,3], [1,2,3,4]); //=> [7,6,5]
R.difference([{a: 1}, {b: 2}], [{a: 1}, {c: 3}]) //=> [{b: 2}]
```
- `[1,2,3,4]`에서 `[7,6,5,4,3]`에 해당하는 원소들을 모두 제외한다. 따라서 `[1,2]`만 남는다.
- `[7,6,5,4,3]`에서 `[1,2,3,4]`에 해당하는 원소들을 모두 제외한다. 따라서 `[7,6,5]`만 남는다.
- `[{a: 1}, {b: 2}]`에서 `[{a: 1}, {c: 3}]`에 해당하는 원소들을 모두 제외한다. 따라서 `[{b: 2}]`만 남는다.

## References
- https://ramdajs.com/docs/#difference
- https://github.com/ramda/ramda/blob/master/test/add.js
- https://github.com/ramda/types/blob/develop/types/add.d.ts
