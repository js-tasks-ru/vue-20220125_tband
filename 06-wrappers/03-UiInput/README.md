# UiInput

👷🏻 _Задача нормальной сложности_\
💼 _Часть проекта_

<!--start_statement-->

## Основная часть

Требуется закончить реализацию компонента ввода **UiInput**.

- Входные параметры:
  - `small` - логический параметр, отображать ли поле маленьким классом `.form-control_sm`;
  - `rounded` - логический параметр, отображать ли поле с закруглёнными углами классом `.form-control_rounded`;
  - `multiline` - логический параметр, использовать ли многострочное поле ввода (`textarea`);
- Модель компонента - значение поля ввода;
- Компонент должен быть прозрачной обёрткой над нативным полем ввода: атрибуты, установленные на компонент, должны
  наследоваться на полем ввода;
- На поле ввода (`input` или `textarea`) должен быть `ref` со значением `input` для доступа к элементу при необходимости
  (например, для использования его методов);
- У компонента должен быть метод `focus`, устанавливающий фокус на поле ввода;
- Компонент должен иметь слоты `left-icon` и `right-icon` для передачи иконок в блоки `.input-group__icon`:
  - Если соответствующий слот передан, требуется добавлять классы `.input-group_icon` и `.input-group_icon-left` и/или
    `.input-group_icon-right`;
  - Блоки `.input-group__icon` должны выводиться только, когда в них передано содержимое.

## Дополнительная часть

Стандартные модификаторы `trim` и `number` работают на `v-model` компонентов из коробки. В отличие от стандартного
модификатора `lazy`.

Изучите
[документацию по добавлению модификаторов в `v-model`](https://v3.vuejs.org/guide/component-custom-events.html#handling-v-model-modifiers)
и реализуйте [модификатор `lazy`](https://v3.vuejs.org/guide/forms.html#lazy) у компонента. В решении также могут помочь
[динамические аргументы директив](https://v3.vuejs.org/guide/template-syntax.html#dynamic-arguments).

При решении дополнительной части раскомментируйте последний блок тестов задачи.

<img src="https://i.imgur.com/PpH8Dhh.gif" alt="Example" style="max-width: 100%" />

<!--end_statement-->

---

### Инструкция

📝 Для решения задачи отредактируйте файл: `components/UiInput.vue`.

🚀 Команда запуска для ручного тестирования: `npm run serve`;\
приложение будет доступно на [http://localhost:8080/06-wrappers/03-UiInput](http://localhost:8080/06-wrappers/03-UiInput).

✅ Доступно автоматическое тестирование: `npm test UiInput`.