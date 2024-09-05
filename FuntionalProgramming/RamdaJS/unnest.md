## unnest
> Shorthand for R.chain(R.identity), which removes one level of nesting from any Chain.
- `R.chain(R.identity)`을 축약한 함수로서, 어떠한 내포된(nesting) 체인이든 한 레벨을 제거한다.

> See also flatten, chain.

### 설명
- 간단히는, 배열의 원소가 배열로 감싸인 형태일 때 배열로 감싸진 한 단계를 제거한 원소를 나열한 결과를 얻는다.
- 자바스크립트에서 배열의 원소로 '어떤 종류의 값' 또는 '해당 종류의 값이 배열의 원소로 나열된 형태'로 구성되어 있다면 '체인'이라는 자바스크립트 판타지랜드의 모나드 사양을 만족한다.
- `R.chain(R.identity)`은 첫 번째 인자로 어떤 값을 받아서 모나드 형태로 변경하는 함수를 받는데, 이미 체인이라는 배열은 모나드 사양을 만족하기 때문에 항등함수를 넣었을 때 그 반환값은 모나드가 된다. 이 함수는 두 번째 인자로 대상 체인 사양의 배열을 받아 배열의 원소인 내포된(nested) 배열의 원소를 내포하고 있는 배열의 원소로 만든다. 이를 달리 표현한 `R.unnest`도 마찬가지로 동작하지만 두 번째 인자로 체인 사양의 배열을 받는 것이 아닌 첫 번째 인자로 체인 사양의 배열을 받는다.

### 표현
```
Chain c => c (c a) → c a
```
- `Chain c => `: c는 체인 개념을 구현한 것이다. 체인 사양을 만족하는 대표적인 예로는 타입 파라메터 a가 배열의 원소일 때, a 종류의 값 뿐만 아니라, a를 원소로 하는 배열도 원소인 배열은 체인 사양을 만족한다.
- `c (c a) →`: `c a` 타입 a가 체인 개념으로 구현되어 있다면, 이를 체인하여 감싼 `c (c a)`도 체인 개념으로 구현되어 있다. 체인을 만족할 수 있는 여러 대상들이 있을 수 있지만, 자바스크립트 배열로 이를 나타내면 `c a`는 `[a]`에 해당하고, `c (c a)`는 `[a|[a]]`에 해당한다. 체인 사양을 만족하는 값을 넣는다고 범용적인 의미로 봐도 되지만, 간단하게 체인 사양의 배열을 받는다고 보면 된다.
- `→ c a`: 체인이 여러겹으로 감싼 형태 `c (c a)`에서 체인을 한 단계 제거한 형태로 바꾼다. 곧 최외곽 배열의 원소인 내포된 배열의 원소를 최외곽 배열의 원소로 바꾼다.

### 예제
```js
R.unnest([1, [2], [[3]]]); //=> [1, 2, [3]]
R.unnest([[1, 2], [3, 4], [5, 6]]); //=> [1, 2, 3, 4, 5, 6]
```
- `[1, [2], [[3]]]`의 각각의 원소를 보면 `[2]`는 체인으로 한 번 감싸인 형태이며, `[[3]]`는 체인으로 두 단계 감싸인 형태이다. `R.unnest` 함수에 의해 각 원소들의 체인을 한 단계 벗기면 1은 체인을 벗길 수 없으므로 1이며, `[2]`는 1이 되며, `[[3]]`는 `[3]`이 된다.
- `[[1, 2], [3, 4], [5, 6]]`의 각각의 원소를 보면 `[1, 2]`, `[3, 4]`, `[5, 6]` 각각은 체인으로 한 번 감싸인 형태이며, `R.unnest` 함수에 의해 각 원소들의 체인을 한 단계 벗기면　`[1, 2, 3, 4, 5, 6]`가 된다.

## References
- https://ramdajs.com/docs/#unnest