# UiFormGroup1

👶🏻 _Несложная задача_\
💼 _Часть проекта_

<!--start_statement-->

Требуется разработать компонент **UiFormGroup** - группу элемента формы. В этом компоненте будут выводиться элементы
формы, возможно, с `<label>` и стилями для вставки элемента формы в форму.

- Входные параметры:
  - `inline` - логический параметр, является ли группа инлайн, а не блочной, по умолчанию `false`;
  - `label` - необязательный строковый параметр с текстом label-а;
- Если параметр `inline` истинный, то блок должен иметь класс `.form-group_inline`;
- Если передан текст в `label`, то требуется вывести блок `<label>` с этим текстом;
- Содержимое компонента должно выводиться через слот по умолчанию.

<img src="https://i.imgur.com/lOsKsfu.png" alt="Example" />
<!--end_statement-->

---

### Инструкция

📝 Для решения задачи отредактируйте файл: `components/UiFormGroup.vue`.

🚀 Команда запуска для ручного тестирования: `npm run serve`;\
приложение будет доступно на [http://localhost:8080/04-vue-cli/01-UiFormGroup](http://localhost:8080/04-vue-cli/01-UiFormGroup).

✅ Доступно автоматическое тестирование: `npm test UiFormGroup1`.
