---
### JavaScript Best Practice Guide
---

__1. Избегай глобальных переменных.__

Сведи к минимуму использование глобальных переменных будь то все типы данных, объекты или функции. Глобальные переменные могут быть перезаписаны другими скриптами!
```
//Плохо
let firstNum = 4;
let secondNum = 9;
let sum = () => {
  firstNum + secondNum;
}
//Хорошо
let sum = () => {
  let firstNum = 4;
  let secondNum = 9;
  firstNum + secondNum;
}
```
__2. Обязательно ставь точку с запятой.__

Каждое предложение должно отделяться точкой с запятой. В некоторых случаях ставить точку с запятой попросту необходимо, иначе вы получите сообщение о синтаксической ошибке. Пример:
```
function returnPerson (name) {
  return //JS автоматически поставит точку с запятой здесь
  {
    name : name
  };
}
```
```
//Плохо
let luke = {}
let leia = {}
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
})
// Хорошо
let luke = {};
let leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});
```

__3. Избегайте  автоматического преобразования типов.__

JavaScript является слабо типизированным. Неявное преобразование может привести к неожиданным результатам.
```
//Плохо
let x = 5 + "7";  // x.valueOf() is 57,  typeof x is a string
//Хорошо
let x = 5 + 7;  // x.valueOf() is 12,  typeof x is a number
```

__4. Используй === и !== вместо == и !=.__

Нестрогое сравнение == и != всегда преобразует типы данных в соответствующие типы перед сравнением. Неявное преобразование типов может привести к дальнейшим ошибкам в коде.
```
//Плохо
1 == '1'; //true
0 == ' '; //true
//Хорошо
1 === '1'; //false
0 === ' '; //false
```

__5. Не используйте new Object(), new Array().__

Не создавайте объекты и массивы через конструкторы new Oject и new Array соответственно. Это неудобно, также можно использовать меньшее количество кода.
```
// Плохо
let items = new Array();
let items = new Object();
// хорошо
let items = [];
let items = {};
```

__6. Инициализируйте переменные при их объявлении.__

Это поможет избежать неопределенных значений.
```
//Плохо
let name;
let age;
name = 'Ksu';
age = 25;
//Хорошо
let name = 'Ksu';
let age = 25;
```

__7. Использование фигурных скобок.__

Всегда используй фигурные скобки. Единственное где можно опустить использование скобок это в однострочных выражениях. Неиспользование скобок может привести к некорректной работе кода.
```
//Плохо
if(someVariableExists)  
  x = false
//Хорошо
if(2 + 2 === 4) return 'nicely done';
if(someVariableExists) {  
  x = false;  
  anotherFunctionCall();  
}
```
__8. Объявляйте переменные для 'for" вне циклов.__

Когда выполняете долгий цикл «for» не заставляйте делать движок больше работы чем нужно.

```
//Плохо
for(var i = 0; i < someArray.length; i++) {  
  var container = document.getElementById('container');  
  container.innerHtml += 'my number: ' + i;  
  console.log(i);  
}  
//Хорошо
var container = document.getElementById('container');  
for(var i = 0, len = someArray.length; i < len;  i++) {  
  container.innerHtml += 'my number: ' + i;  
  console.log(i);  
}  
```
__9. Всегда заканчивай switch с default.__

Это позволит уловить и понять ошибку, если она появится.

```
//Плохо
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
    day = "Tuesday";
    break;
}
//Хорошо
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
    day = "Tuesday";
    break;
  default:
    day = "Unknown";
}
```
__10. Избегайте использования eval().__

Функция eval() позволяет выполнить команду записанную в строковой переменной, которая передается в качестве параметра в eval.

Это замедлит программу , а также предполагает возникновение огромной дыры безопасности приложения.
```
//Плохо
eval( "сonsole.log('hello!');" );
//Хорошо
сonsole.log('hello!');  //Можно просто написать непосредственно код
```
