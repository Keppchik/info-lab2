# Лабораторная работа 2

## 1. Начинаем писать скрипт
<img width="956" alt="Снимок экрана 2024-10-23 в 14 12 09" src="https://github.com/user-attachments/assets/2a9fef59-3e7b-4ae2-bb68-9e7eb1664622">

  `IFS='.' read -ra arr` - читаем строку разделяем её на элементы через точку и записываем их в массив `arr`
  
  `for i in "${arr[@]}" do echo $i done` - выводим массив, чтобы проверить все ли работает правильно

## 2. Переводим каждый элемент в двоичную СС
<img width="956" alt="Снимок экрана 2024-10-23 в 14 45 27" src="https://github.com/user-attachments/assets/6e3b2dd5-c55b-4a3c-b76e-2f994bb9bcd4">

  
  В цикле `while` происходят следующие действия:
  1) `s=$(( $n % 2 ))` - В переменную `s` записываем остаток от деления на 2 числа, которое хотим перевести в двоичную СС
  2) `bin="$s$bin"` - В начало переменной `bin` записываем переменную `s`
  3) `n=$(( $n / 2 ))` - Число, которое хотим перевести в двоичную СС, делим нацело на 2

## 3. Записываем элементы в одну строку
<img width="955" alt="Снимок экрана 2024-10-23 в 14 56 24" src="https://github.com/user-attachments/assets/56100074-576f-4e42-9ff5-674cdc7e713d">

`otvet="$otvet$bin."` - Записываем в конец переменной `otvet` переменную `bin` и добавляем точку в конце
`otvet="${otvet%?}"` - Удаляем последний элемент строки

## 4. Добавляем недостающие нули
<img width="965" alt="Снимок экрана 2024-10-23 в 15 11 47" src="https://github.com/user-attachments/assets/2b978f46-dd58-438a-b731-544bc5b7e1e4">

`if [ ${#bin} -1t ]` - если длина получившегося числа меньше 8 то выполняются следующие действия:
1) `len=$((8 - ${#bin} ))` - присваиваем переменной `len` количество нулей, которое надо добавить 
2) `bin="O$bin"` - В цикле добавляем к переменной `bin` один ноль, повторяем `len` раз

