<br/>

# [JavaScript] 기본 복습

<br/>

## 04. Scope

변수를 선언하는 방법에는`var` , `let` , `const`   3가지가 있다.  

먼저 var는 변수를 선언하고, 선택적으로 초기화할 수 있다. ES5에서는 대표적인 변수로 사용되었지만 ES6부터는 `let` 과 `const` 가 많이 사용되었다. 그 이유는 호이스팅(Hoisting) 에 있다. `let`과 `const`도 호이스팅의 대상이긴 하지만 `var`와 달리 `undefined`로 초기화 하지 않는다.

<br/>

### 호이스팅 (Hoistiong)

> "변수의 선언과 초기화를 분리한 후, 선언만 코드의 최상단으로 옮기는" 것.  따라서 변수를 정의하는 코드보다 사용하는 코드가 앞서 등장할 수 있다.  다만 선언과 초기화를 함께 수행하는 경우, 선언 코드까지 실행해야 변수가 초기화된 상태가 됨을 주의!

```js
age = 6;
age++;
console.log(age);

var age;
```

<br/>



### lexical scope와 closure

```js
    // 전역변수 age, name, height
    let age = 27;
    let name = "jin";
    let height = 179;

    function outerFn() {
      let age = 24; // 지역으로 선언 (위의 전역변수와 다름)
      name = "jimin"; // 전역변수 name 재할당
      let height = 178;// 지역으로 선언 (위의 전역변수와 다름)

      function innerFn() {
        age = 26; // 전역변수 age 재할당
        let name = "suga"; //지역으로 선언
        return height;
      }

      innerFn(); // 함수 실행시킴 

      console.log(age); // 26 
   	  console.log(name); // "jimin"

      return innerFn;
    }

    const innerFn = outerFn(); //함수 실행시킴 

   	console.log(age); // 27 (전역)
   	console.log(name); // "jimin" (outerFn()에서 재할당됨)
   	console.log(innerFn()); // 178 
```


<br/>



## 6. Types-part2

**참조 자료형을 변수에 할당할 경우, 데이터의 주소가 저장됩니다**

* 원본을 재할당해도 복사본도 주소를 공유하기 때문에 함께 변경됨  

```js
    const num = ["1", "2", "3"];
    let newNum = num; //주소가 복사됨

    num.push("A"); // ["1", "2", "3", "A"] 이때 newNum도 함께 바뀜 (주소를 공유해서)
    console.log(newNum === num) //true
    num[1] = "B";//재할당 ["1", "B", "3", "A"] 이때 newNum도 함께 바뀜 (주소를 공유해서)
    console.log(num[1] === newNum[1]) //true
```

* 값이 같아보여도 선언된 변수가 다르면 주소가 다름 

```js
    const nums1 = [1, 2, 3];
    const nums2 = [1, 2, 3];
 	console.log(nums1 === nums2) //false 값은 같지만 주소가 다름 
 	
    const person = {
      son: {
        age: 9,
      },
    };

    const boy = person.son; // boy = { age: 9 }
    boy.age = 20; // boy = { age: 20 } 재할당
    console.log(person.son.age) // 20
	console.log(person.son === boy) // true 주소값 공유
	console.log(person.son === { age: 9 }) //false
	console.log(person.son === { age: 20 }) //값은 같지만 주소값이 달라서 false임
```

<br/>


## 07. Array

**Array 메소드 slice를 확인합니다**

```js
const arr = ["A", "B", "C", "D"]

console.log(arr.slice(0)) // ["A", "B", "C", "D"] => arr 전체복사 
console.log(arr.slice(1)) // ["B", "C", "D"] => 1번째 인덱스부터 끝까지 복사 
console.log(arr.slice(3, 100)) // ["D"] => 3번째 인덱스부터 끝까지 복사 
```



## 08. Object

### this

> 대부분의 경우 this의 값은 함수를 호출한 방법이 결정합니다. 실행하는 중 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다.

* 객체의 메소드 

```js
// 객체 또는 클래스 안에서 메소드를 실행한다면 this는 Object 자기 자신
var o = {
  prop: 37,
  f: function() {
    return this.prop; // 이때 객체이므로 this는 o를 가리킴 
  }
};

console.log(o.f()); // 37
```

<br/>


### 얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy)

* 얕은 복사는 주소값의 복사를, 깊은 복사는 값 자체의 복사를 나타냄 
* 객체를 할당하여 복사하는 것 주소를 복사하는 것 => 얕은 복사 
* 원시 자료형에서의 할당하여 복사하는 것은 값 자체가 복사되는 것 => 깊은복사 
* 객체의 깊은 복사를 하기 위해서?

 **Object.assign()**

>**`Object.assign()`** 메서드는 출처 객체들의 모든 [열거 가능](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/propertyIsEnumerable)한 [자체 속성](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)을 복사해 대상 객체에 붙여넣습니다. 그 후 대상 객체를 반환합니다.


<br/>
<br/>


