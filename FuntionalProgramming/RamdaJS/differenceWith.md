## differenceWith
> Finds the set (i.e. no duplicates) of all elements in the first list not contained in the second list. Duplication is determined according to the value returned by applying the supplied predicate to two list elements.

## 표현
```
((a, a) → Boolean) → [a] → [a] → [a]
```
- `((a, a) → Boolean)` 첫번째 인자로는 술어 함수를 받는다. 이때 술어함수의 두 매개변수는 동일한 타입이다.
- `→ [a] →` 두번째 인자로는 배열을 받는다. 배열 안의 모든 원소는 술어함수의 첫번째 매개변수와 동일한 타입이어야 한다.
- `→ [a] →` 세번째 인자로도 배열을 받는다. 배열 안의 모든 원소는 술어함수의 두번째 매개변수와 동일한 타입이어야 한다.
- `→ [a]` 두 번째 리스트의 원소에서 세번째 리스트의 원소를 각각 비교하여 술어함수를 만족하는 원소를 두 번째 리스트에서 제외한 배열을 반환한다.

## 설명
- 첫 번째 인자로는 술어 함수를 받는다. 
- 두 번째 인자는 남길 대상이 들어간 배열을 받고,
- 세 번째 인자는 제외할 대상이 들어간 배열을 받는다.
- 두 번째 인자와 세 번재 인자의 원소들을 카르테시안 곱으로 비교하여 두번째 인자를 리스트의 원소를 술어함수의 첫번째 인자로 세 번째 인자 리스트의 원소를 술어함수의 두번째 인자로 넣어 술어함수가 참이 되는 원소를 두 번째 리스트에서 제외한 결과를 반환한다.

## 예제
```
const cmp = (x, y) => x.a === y.a;
const l1 = [{a: 1}, {a: 2}, {a: 3}];
const l2 = [{a: 3}, {a: 4}];
R.differenceWith(cmp, l1, l2); //=> [{a: 1}, {a: 2}]
```
- `(x, y) => x.a === y.a` 오브젝트 2개를 받아 두 오브젝트의 `a` 어트리뷰트의 값이 동일한지 확인하는 술어함수이다.
- `R.differenceWith(cmp, l1, l2)` 두 번째 인자의 리스트에서 세 번째 인자의 리스트에 속한 원소를 제외하는데 주어진 술어 함수를 만족하는 원소를 제외한다.
- l1의 `{a: 1}`와 l2의 `{a: 3}`, `{a: 4}`를 비교하고, l1의 `{a: 2}`와 l2의 `{a: 3}`, `{a: 4}`를 비교하고, l1의 `{a: 3}`와 l2의 `{a: 3}`, `{a: 4}`를 비교한다. 이때 비교는 cmp함수이며 이 술어함수의 결과가 참이 되는 경우 `l1`의 원소 리스트에서 제거되는 대상이 된다. (비교의 순서는 설명을 위한 예를 들기 위한 것이므로 정확하지는 않다.)

## Reference
- https://ramdajs.com/docs/#differenceWith
