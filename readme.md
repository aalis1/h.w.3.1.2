# Расчет бонусов в зависимости от суммы переменных
##### Программа позволяет рассчитвать бонусы клиентов в зависимости от суммы переменных а и в.
### Установка программы
###### Для установки программы создать в VS Code папку, в ней  файл calcBonus.js. и поместить в него следующий код
```javascript
const calculateBonus = (a, b) => {
  let bonus;
  const sum = a + b;
  debugger; //программа видит значание а и в, получает сумму
  sum > 50 ? (bonus = 50) : (bonus = sum);
  debugger; //программа посчитала бонуc
  return bonus;
};

console.log(calculateBonus(-570, -838));
```
###### Запустить проект с дебаггером.Убедиться, что код работает, происходят остановки выполнения кода, виден скоуп текущего статуса работы скрипта.Программа видит значения "а" и "в" и правильно рассчитывает сумму и бонус.
### Тестирование программы
- Инициировать новый проект командой ```npm init -у``` в терминале. Получить package.json файл. 
- Проверить, внести изменения, если необходимо.
- Установить cypress командой в терминале ```npm install cypress```. Добавится папка node modules. 
- Папку node modules добавить в .gitignore
- Установить jest командой ```npm install --save-dav jest``` в терминале
- В package.json файле в скрипте "test" указать - jest
- Создать файл calcBonus.test.js для тестов
- В файле calcBonus.js содать экспорт кода командой ```module.exports = calculeteBonus;```
- В файле calcBonus.test.js командой ```const.calculeteBonus = require(`./calcBonus.js`)``` импортировать код и сделать его видимым для тестирования.
- Написать тесты проверок следующих состояний:
    - сумма > 50
    - сумма = 50
    - сумма < 50
    - сумма = 0
    - сумма отрицательных чисел
    - сумма нулевых значений
    - null + null
    - text + text
Получился код

```javascript
test("test on sum > 50", () => {
  expect(calculateBonus(38, 36)).toBe(50);
});

test("test on value = 0", () =>{
  expect(calculateBonus(0, 0)).toBe(0);
 });

test("test on sum < 50", () => {
  expect(calculateBonus(8, 6)).toBe(14);
 });

test("test on sum = 50", () => {
  expect(calculateBonus(38, 12)).toBe(50);
 });

test("test on value negative values", () => {
  expect(calculateBonus(-10, -45)).toBe(-55);
});

test("test on big number", () => {
  expect(calculateBonus(2438540000, 382340020)).toBe(50);
 });

test("test on null", () => {
   expect(calculateBonus(null, null)).toBe(NaN);
 });

test("test on text", () => {
  expect(calculateBonus("text", "text")).toBe("text is not a number");
 });

``` 