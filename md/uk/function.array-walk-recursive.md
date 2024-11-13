---
navigation:
  - function.array-values.md: « array_values
  - function.array-walk.md: array_walk »
  - index.md: PHP Manual
  - ref.array.md: Функції для роботи з масивами
title: array_walk_recursive
origin_hash: ddf652f5224dc9f1fa9671347921941ca401ea50
---
# array_walk_recursive

(PHP 5, PHP 7, PHP 8)

array_walk_recursive — Рекурсивно застосовує функцію користувача до кожного елементу масиву

### Опис

```methodsynopsis
array_walk_recursive(array|object &$array, callable $callback, mixed $arg = null): bool
```

Застосовує функцію користувача `callback` до кожного елементу масиву `array`. Функція обробляє кожен елемент багатовимірного масиву.

### Список параметрів

`array`

Вхідний масив

`callback`

Зазвичай, `callback` приймає два параметри. Першим параметром є значення елемента масиву `array`, а другим - його ключ.

> **Зауваження** :
> 
> Якщо потрібно, щоб функція `callback` змінила значення у масиві, визначте перший параметр `callback` як [посилання](language.references.md). Тоді всі зміни будуть застосовані до елементів масиву.

`arg`

Якщо вказано необов'язковий параметр `arg`, то він буде переданий третім параметром функції `callback`

### Значення, що повертаються

Повертає **`true`** у разі успішного виконання або \*\*`false`\*\* у випадку виникнення помилки.

### Приклади

**Приклад #1 Приклад використання** array_walk_recursive()\*\*\*\*

```php
<?php
$sweet = array('a' => 'apple', 'b' => 'banana');
$fruits = array('sweet' => $sweet, 'sour' => 'lemon');

function test_print($item, $key)
{
    echo "$key містить $item\n";
}

array_walk_recursive($fruits, 'test_print');
?>
```

Результат виконання наведеного прикладу:

```
a містить apple
b містить banana
sour містить lemon
```

Зверніть увагу, що ключ '`sweet`' ніколи не відображається. Будь-який ключ, що містить значення типу array, не передаватиметься у функцію.

### Дивіться також

-   [array_walk()](function.array-walk.md) - Застосовує задану користувачем функцію кожного елемента масиву
