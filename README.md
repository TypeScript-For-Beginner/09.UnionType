<aside>
π‘ Union Typeμ TypeScriptκ° κ°μ§λ νμ μ€ νλλ‘ νλμ κ°μ΄ μ¬λ¬κ°μ νμμ κ°μ§λ κ²½μ° μ¬μ©νλ€. OR μ°μ°μμ²λΌ βAμ΄κ±°λ Bμ΄λ€β λΌλ μλ―Έλ₯Ό κ°λλ€.

</aside>

## 9.1 μ λμ¨νμ μ§μ 

νμ΄ν λ¬Έμλ₯Ό μΆκ°ν΄ μ¬λ¬ κ°μ νμμ μ§μ ν΄ μ€ μ μλ€. OR μ°μ°μμ κ°μ΄ `A | B`λ‘ ννμ΄ λλ€.

> μμ  9-1

```tsx
let text: string | number = 22;
text = "22";
```

## 9.2 μΈν°νμ΄μ€ μ λμ¨

μ λμ¨ νμμ΄ μΈν°νμ΄μ€λ₯Ό μ°κ²°νμ λ λͺ¨λ  νμμ κ³΅ν΅ μμ±μλ§ μ κ·Όν  μ μλ€.

> μμ  9-2

```tsx
interface Ujin {
  name: string;
  age: number;
}

interface Dabin {
  name: string;
  character: string;
}

function combine(person: Ujin | Dabin) {
  person.name; // μ μ λμ
  person.age; // νμμ€λ₯
  person.character; // νμμ€λ₯
}
```

μ μ½λλ₯Ό λ³΄λ©΄ `combine()` ν¨μ λ§€κ°λ³μμ νμμ `Ujin`, `Dabin` μΈν°νμ΄μ€μ μ λμ¨ νμμΌλ‘ μ§μ νμλ€. λ§€κ°λ³μμ νμμ΄ `Ujin`λ λ  μ μκ³  `Dabin`λ λ  μ μμΌλ κ°μ²΄μ μμ±μΈ `name`, `age`, `character` λͺ¨λ μ¬μ©ν  μ μμ κ²μ΄λΌ μκ°νμ§λ§, `combine()` ν¨μλ₯Ό νΈμΆν  λ μ΄λ€ νμμ΄ μ¬μ§ μ μ μκΈ° λλ¬Έμ μ΄λ€ νμμ΄ λ€μ΄μ€λ  μ€λ₯κ° μ λλ λ°©ν₯μΌλ‘ νμμ μΆλ‘ νκ² λλ€. λͺ¨λ  νμμ κ³΅ν΅μ μΈ μμ±μλ§ μ κ·Όν  μ μκΈ° λλ¬Έμ `person.name`μ μ μ μλνμ§λ§, `person.age`μ `person.character`λ νμ μ€λ₯κ° λλ€. μ΄λ νμν κ²μ΄ μ λμ¨ νμκ°λμ΄λ€.

## 9.3 μ λμ¨ νμ κ°λ

μ λμ¨ νμμΌλ‘ μ μΈν λ³μλ κ°μ²΄λ₯Ό μ¬μ©ν΄μΌ ν  κ²½μ° κ·Έλλ‘ μ¬μ©νλ©΄ μ€λ₯κ° λ  μ μλ€. νμμ€ν¬λ¦½νΈλ μ λμ¨ νμμ μ΄ν΄ν  λΏ μ λμ¨ νμ λ΄μ λ¬΄μμ΄ μλμ§λ λΆμνμ§ λͺ»νλ€. μ΄λ° κ²½μ° λ°νμ νμ κ²μ¬λ₯Ό μΆκ°νμ¬ νμμ΄ μ΄λ μͺ½μ ν΄λΉνλμ§ νμ μ ν΄μ€μΌνλ€. μ΄λ¬ν κ³Όμ μ νμ κ°λλΌκ³  νλ€.

### 9.3.1 μμ νμ μλ³

μμ νμμ `typeof` μ°μ°μλ₯Ό μ΄μ©ν΄ νμ κ²μ¬λ₯Ό ν  μ μλ€.

> μμ  9-3

```tsx
function combine(input1: number | string, input2: number | string) {
	let result;
	if (typeof input1 === 'number' && typeof input2 === "number') {
		result = input1 + input2;
	} else {
		result = input1.toString() + input2.toString();
	}
	return result;
}

console.log(combine('hello', 'world')) // helloworld
console.log(combine(10, 10)) // 20
```

### 9.3.2 **ν΄λμ€ κ°μ²΄ μλ³**

μμ±μ ν¨μλ₯Ό λ°ννλ class κ°μ²΄λ `typeof`λ‘ κ²μ¬νλ©΄ βobjectβλ§μ λ°ννκΈ° λλ¬Έμ `instanceof` μ°μ°μλ₯Ό μ΄μ©ν΄ νμ κ²μ¬λ₯Ό νλ€. `instanceof` μ°μ°μλ μμ±μμ νλ‘ν νμμ΄ κ°μ²΄μ νλ‘ν νμ μ²΄μΈμ μλμ§ κ²μ¬νλ€.

> μμ  9-4

```tsx
class Ujin { }
class Dabin { }

const combine(user: Ujin | Dabin) {
	if (user instanceof Ujin) {
		user.jjeu_jjeu()  // userκ° Ujin ν΄λμ€μ κ°μ²΄
	} else {
		user.bong_gug()   // userκ° Dabin ν΄λμ€μ κ°μ²΄
	}
}
```

### 9.3.3 μΌλ° κ°μ²΄ μλ³

μλ°μ€ν¬λ¦½νΈμ κ°μ²΄λ¦¬ν°λ΄κ³Ό λ¬λ¦¬ νμμ€ν¬λ¦½νΈμμλ κ°μ²΄ νμμ μ§μ ν  λ μΈν°νμ΄μ€λ₯Ό μ¬μ©νμ¬ κ°μ²΄μ λͺ¨μμ μ§μ ν  μ μλ€.

> μμ  9-5

```tsx
interface Cat {
  meow(): string;
}

interface Dog {
  bowwow(): string;
}
```

```tsx
function checkType(pet: Cat | Dog) {
  if ("meow" in pet) {
    (pet as Cat).meow();
  } else {
    (pet as Dog).bowwow();
  }
}
```

if λ¬Έμ μ‘°κ±΄μ ν΅ν΄μ pet νμμ μ²΄ν¬μμ§λ§ if λ¬Έ λ΄λΆμμ as λ¬Έμ ν΅ν΄ ν λ² λ μ΄λ€ κ°μ²΄μΈμ§ μλ €μ£Όμ΄μΌ νλ€.

### 9.3.4 null μ²΄ν¬

λ¬Έμμ΄μ κ°μ΄ μ‘΄μ¬νμ§ μλ κ²½μ°μ μ¬μ©νλ€. string | nullμ΄λΌκ³  μ λμ¨ νμμ μ§μ νμ λ κ°μ΄ nullμ΄μ΄μ stringμΌλ‘ μ¬μ©ν  μ μκ±°λ nullμ΄ μλ κ²½μ° μμΈ μ²λ¦¬λ₯Ό νκ³  μΆμ λ μ¬μ©νλ€.

> μμ  9-6

```tsx
function nullCheck(val: string | null): number {
  if (val != null) {
    return val;
  } else {
    return 0;
  }
}
```
