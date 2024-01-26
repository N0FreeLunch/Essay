## omit
> Returns a partial copy of an object omitting the keys specified.
- 지정한 키를 누락시킨 부분적인 속성을 갖는 오브젝트의 카피를 반환한다.

> See also pick.

### 설명
- `omit`은 제외시키다, 누락시키다, 빠뜨리다의 의미를 가지고 있다. 여기서는 '~하게 하다'의 사역의 의미로 사용되었으며, 지정한 키의 속성을 오브젝트에서 제거한 오브젝트를 반환하는 역할을 한다.
- 두 번째 인자로 받은 오브젝트에서 첫 번째 인자에 배열로 나열한 이름에 해당하는 오브젝트의 키를 제거한 결과를 반환한다.
- 첫 번째 인자로는 키의 값을 문자열로 나열한 인덱스형 배열을 받고, 두 번째 인자로는 오브젝트를 받아서 오브젝트의 키에서 첫 번째 인자에서 지정한 문자열에 해당하는 키를 갖는 속성을 제거한 오브젝트를 반환한다.

### 표현
```
[String] → {String: *} → {String: *}
```
- 첫 번째 인자로는 `[String] →` 문자열을 원소로 하는 배열을 받는다.
- `→ {String: *} →` 두 번째 인자로는 첫 번째 인자의 배열 내의 문자열 원소와 매칭할 수 있도록 문자열을 키를 가진 오브젝트를 받는다.
- `→ {String: *}` 두 번째 인자의 오브젝트에서 첫 번째 인자에 지정한 원소의 값과 같은 키값을 가진 속성을 제외한 오브젝트를 반환한다.

### 예제
```
R.omit(['a', 'd'], {a: 1, b: 2, c: 3, d: 4}); //=> {b: 2, c: 3}
```
- 제거 하고자 하는 속성은 `'a'`와 `'d'`이다. `{a: 1, b: 2, c: 3, d: 4}`에서 속성 `a` 와 속성 `d`를 제거하면, 속성 `b`와 속성 `c`가 남는다. 따라서 반환된 결과 값은 두 속성과 그 속성의 값을 가진 `{b: 2, c: 3}`가 된다.

## Reference
- https://ramdajs.com/docs/#omit