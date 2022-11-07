
<br/>

# [JavaScript] 배열

<br/>

### 배열 

* **배열은 순서가 있는 값**, 순서는 인덱스라고 부르며 1부터 시작이 아닌 0부터 시작한다.

* 대괄호를 이용하여 배열을 만들고 각 원소(element)는 쉼표로 구분해준다. 

* 값은 인덱스를 이용하여 접근
* 배열의 크기를 넘어간 상태에서 값을 물어본다면 undefined가 출력된다.

```js
let fruits = ['apple', 'banana', 'pineapple'];
fruits[2] = 'banana';
fruits[3] = undefined;
```

* 이차원 배열의 표현 

```js
let age = [[15, 20], [26,18], [34, 48]];
age[0] = [15, 20];
age[0][1] = 20;
```
<br/>

|    &nbsp;   |  &nbsp;0  &nbsp; |  &nbsp;1 &nbsp;  |
| :---: | :--: | :--: |
| &nbsp;**0** &nbsp;| &nbsp; 15 &nbsp; |  &nbsp;20 &nbsp; |
| &nbsp;**1** &nbsp;|  &nbsp;26 &nbsp; | &nbsp; 18 &nbsp; |
| &nbsp;**2**&nbsp; |  &nbsp;34 &nbsp; | &nbsp; 48 &nbsp; |

<br/>

#### 배열과 반복문

반복문을 이용하여 요소를 한번씨 출력하기 위해서는? 조건을 만족하며 출력하기 

* 숫자(n)는 0부터 시작 
* 숫자(n)는 배열의 길이보다 작을 때까지 반복
* 숫자(n)는 1씩 증가 

```js
let age = [20, 18, 34];

for(let n = 0; n < age.length; n++) {
	console.log(age[n]);
}
```

<br/>

반복문을 이용하여 요소를 모두 더한값을 출력하기 위해서는? 조건을 만족하며 출력하기 

* 숫자(n)는 0부터 시작 
* 숫자(n)는 배열의 길이보다 작을 때까지 반복
* 숫자(n)는 1씩 증가 
* sum 에 age[n]값 더해주기 

```js
let age = [20, 18, 34];
let sum = 0;

for(let n = 0; n < age.length; n++) {
	sum = sum + age[n];
	// sum += age[n];
}
```


> **let  sum = 0 으로 초기화를 해주는 이유는?**
>
> let sum;  일때 sum = undefined 이다. 이때 숫자와 더해지게 되면 undefined + 18 = NaN 이 출력된다. 



#### 배열의 메소드 

* 배열의 길이 : `length`

```js
let age = [20, 18, 34];
age.length // 3
```

* 배열의 요소의 추가 : `push`

```js
let age = [20, 18, 34];
age.push(48);
let age = [20, 18, 34, 48];
```

* 배열의 마지막 요소의 삭제 : `pop`

```js
age.pop(); //48
let age = [20, 18, 34];
```

* 배열의 맨 앞 요소 추가 : `unshift`

```js
age.unshift(70);
let age = [70, 20, 18, 34];
```

* 배열의 맨 앞 요소 삭제 : `shift`

```js
age.shift();
let age = [20, 18, 34];
```

<br/>

* 특정 값이 배열인지 아닌지 판별 : `Array.isArray`

```js
let age = [20, 18, 34];

typeof age; //'object' => 타입을 알 수 없음  
Array.isArray(age) // true
```

* 배열을 시각화하여 콘솔에 찍어보기 

```js
let age = [20, 18, 34];
console.table(age);
```

![image-20220510100107677](https://user-images.githubusercontent.com/104333249/172046201-bec0b97b-3e1a-4bda-9447-6523da5751cb.png)

<br/>

* 특정 값이 배열에 포함되어 있는지 확인 :  `indexOf, includes`
* 특정 값이 있다면 인덱스가 출력되고, 없다면 -1을 출력한다.

```js
let word = ['hi', 'hello', 'bye'];

word.indexOf('hi') // 0
word.indexOf('hello') // 1
word.indexOf('good') // -1

word.indexOf('bye') !== -1 // true (존재여부 판단 가능)
```

=> hasElement (배열, 찾으려는 엘리먼트) // true, false

```js
finction hasElement(arr, element) {
	isPresent = arr.indexOf(element) !== -1;
	return isPresent;
}
```

* 아쉽게도 true, false만 알아낼 수 있고 인덱스는 알아낼 수 없다.
* 브라우저 호환성에서 Internet Explorer 에서는 사용 불가 

```js
let word = ['hi', 'hello', 'bye'];
word.includes('hi') //true
word.indexOf('good') // false
```



* `slice(시작할 요소, 끝낼 요소) ` => 시작할 요소는 포함하고, 끝낼 요소는 포함하지 않는다.
* 배열 원본이 변경되지 않는다. (immutable) 




<br/>
<br/>




