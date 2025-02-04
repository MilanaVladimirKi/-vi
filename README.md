# Текстовый редактор vi. 

vi — серия текстовых редакторов операционных систем семейства UNIX. 

На самом деле существует ряд программ, либо в точности повторяющих поведение Vi (например, nVi), либо очень похожих на Vi, но со значительно расширенными возможностями (например, Vim). 

## 1. Какие режимы существуют у редактора vi?

**Режим команд** (Command mode) - используется для выполнения команд. 

В командном режиме – вводимый текст - это команда редактору, нажатие клавиши считается командой и немедленно исполняется (но никогда не отображаются). Командный режим используется для перемещения курсора, операций вырезания и вставки и прочих действий, не связанных с набором текста;


**Режим вставки** (Insert mode) - используется для ввода текста. 

В режиме вставки – нажатие клавиши - вставка соответствующего символа;


**Режим командной строки**.

В режиме командной строки – вводимый текст это длинная команда, для завершения которой используется клавиша Enter.

Чтобы ее вызвать нужно в командном режиме ввести «:». В результате в последней строке появятся символы «..» – приглашение командной строки. 

Редактор будет находиться в этом режиме до тех пор, пока не будет нажата клавиша Enter, после чего редактор перейдет в командный режим. 


Все команды командного режима имеют одинаковую базовую форму: сначала идет необязательный номер строки или диапазон номеров строк, затем следует команда: :[firstline][,lastline] command

Если номера строк не указаны, команда будет применена к текущей строке. Например, чтобы удалить строки с 10 по 20 включительно, нужно воспользоваться командой :10,20d

Базовой командой для поиска и замены в командном режиме является команда substitute, которая может быть введена в короткой форме s. 

Базовая команда substitute выглядит следующим образом: :s/search/replacement/flags

Единственным необходимым аргументом является строка поиска. Параметры replacement и flags являются опциональными. 

Все аргументы должны разделяться знаком прямого слеша «/», что не совсем удобно при работе с именами файлов. 

Редактор vi требует, чтобы все прямые слеши заменялись знаками обратного слеша «\». Поэтому команда замены с указанным путем будет выглядеть следующим образом: :s/\/usr\/bin\/file1/\/usr\/bin\/file2\//

## 2. Прокомментируйте диаграмму переключения режимов vi. 

Работа в редакторе начинатся с командного режима. 

Чтобы ввести текст, необходимо перейти из командного режима в режим вставки, нажав клавишу «i» (insert – вставка). После этого в последней строке появится сообщение о том, что редактор находится в режиме вставки «--INSERT--». 

Также чтобы перейти из командного режима в режим вставки можно нажать клавищи: "o", "O", "a" и, возможно, другие.

В режиме вставки можно вводить текст, завершая строку нажатием клавиши Enter.

Чтобы перейти из режима вставки в командный режим, необходимо нажать клавишу «ESC». 

Для переключения из командного режима в режим вставки существует много способов, а для выхода из режима вставки только один – нажатие клавиши «ESC».

Для перехода из Командного режима в режим Командной строки, используется клавиша ":". 

Для возвращения из режима Командной строки в командный режим, можно нажать Enter и «ESC». 

## 3. Как получать помощь по использованию vi? 

Важно уметь получать помощь по Vi. Для этого необходимо:

1) перевести Vi в режим командной строки, нажав «:»
2) ввести команду help и нажать клавишу Enter

Для того, чтобы закрыть справочную страницу, нужно ввести команду :g

## 4. Расскажите о командах позиционирования курсора и их использованию. Приведите примеры.

**Команды позиционирования курсора могут комбинироваться с другими командами**, например: 

j Перемещение курсора на одну строку вниз, k Перемещение курсора на одну строку вверх; 

n Повторение последнего поиска в том же направлении, начиная с текущей позиции курсора; 

N Повторение последнего поиска в противоположном направлении, начиная с текущей позиции курсора; 

`’ Возврат на последнюю строку, с которой осуществлялся переход или поиск; 

w Перемещение курсора на одно слово вперед, b Перемещение курсора на одно слово назад. 

Примеры того, как можно команды d и y комбинировать с командами перемещения: 

dfa Удаление символов, начиная с текущего положения курсора вправо до первой буквы «а», которая также удаляется. Мнемоническое правило: удалять все символы, пока не встретится буква «а».

5yta Копирование символов, начиная с текущего положения курсора вплоть до пятого появления буквы «а».

dn Удаление символов, начиная с текущего положения курсора до первого соответствия самого последнего поиска. Здесь команда d комбинируется с командой перемещения n. 

5dd Удаление текущей строки и четырех следующих строк. Команде dd предшествует количество повторений, равное 5. 

d5i Удаление следующих пяти символов, начиная с текущего положения курсора. Команда d комбинируется с командой перемещения 5i.

d`a Удаление символов, начиная с текущего положения курсора вплоть до позиции с отметкой «а». Команда d комбинируется с командой `a в качестве команды перемещения.

И есть **Команды позиционирования курсора, которые не могут комбинироваться с другими командами**, например: 

Ctrl+F Перемещение курсора на одну экранную страницу вперед, Ctrl+B Перемещение курсора на одну экранную страницу назад. 

## 5. Расскажите о командах вставки. Приведите примеры. 

Существует множество способов перехода в режим вставки, например: 

i Переход в режим вставки. Курсор перед символом. 

I Переход в режим вставки. Курсор перед первым непустым символом строки.

a Переход в режим вставки. Курсор после символа. 

A Переход в режим вставки. Курсор после последнего непустого символа строки. 

## 6. Расскажите о командах изменения. Приведите примеры их использования. 

Есть часто  используемые команды изменения, например: 

C Удаление всего, что следует после курсора, до конца строки, затем осуществляется переход в режим вставки.

S Изменение (замена) текущей строки полностью. Удаляет весь текст текущей строки и выполняет переход в режим вставки.

Есть Шаблоны использования команд изменения, например: 

2cw Удаление двух слов и переход в режим вставки; альтернативный вариант – удаление двух следующих слов. 

cta Удаление всего вплоть до следующего появления буквы «а» с последующим переходом в режим вставки. Является комбинацией команды c и команды перемещения ta. 

5cta Удаление всего вплоть до пятого появления буквы «а» с последующим переходом в режим вставки. 

5S Удаление текущей строки и последующих 4 строк с последующим переходом в режим вставки.

## 7. Расскажите о командах вырезания, вставки и удаления. Приведите примеры. 

Эти команды отличаются от команд изменения тем, что они не используются в режиме вставки. При вводе этих команд необходимо находиться в командном режиме. 

Как и большинство команд, эти команды могут повторяться, то есть, если ввести 5p, то вставка в редактор содержимого буфера будет выполнена 5 раз.

Примеры команд вырезания, вставки и удаления: 

D Удаление всего, начиная с текущего положения курсора до конца строки. Данные сохраняются в буфере по умолчанию. 

d{motion} Удаление определенного количества символов, начиная с текущего положения курсора. Количество символов определяется аргументом motion. Для удаления текущей строки надо вводить dd. Данные сохраняются в буфере по умолчанию. 

y{motion} Копирование определенного количества символов в регистр. Количество символов определяется аргументом motion. Для копирования текущей строки в буфер обмена надо вводить yy.

Команды вставки и удаления могут принимать один аргумент с меткой motion, который сообщает редактору, какой фрагмент текста необходимо удалить или скопировать. Аргументом motion может быть любая из команд перемещения курсора.

# Практика

## Вариант 1

![текст](https://sun9-21.userapi.com/impg/ltjvBCgeH0FYplEJXakSGmDZ5PO88pdJX1SIVw/-Jyur7KzsfM.jpg?size=579x885&quality=95&sign=4a00c25aa92d9c83c915ea0f3fb254e4&type=album) 

![текст](https://sun9-53.userapi.com/impg/nU-Lng6zvVfvt7kVT0eFTQsmeZ-Tro6EP2lWUg/vLOuqNDOY04.jpg?size=551x876&quality=95&sign=6d4addd7e9ac4768ef81df886dd7badf&type=album) 

![текст](https://sun9-43.userapi.com/impg/oGSRpBZZDWzvI-f-XxJG-E97ku1eePva6GA-yw/jgLX2TVawBE.jpg?size=549x348&quality=95&sign=2ee22ca76f74f323a6b708f19e777e9f&type=album) 


## Вариант 2

![текст](https://sun9-78.userapi.com/impg/jXdrzckJQF2vGfrxB5KO8u78pYIesh2hktlSsg/6VFNtgyl45s.jpg?size=861x706&quality=95&sign=c5af018c43c24b17d415532af6d91b26&type=album) 

![текст](https://sun9-45.userapi.com/impg/EdXQVK4oC0xBsiHTFUORGV-oZlqpAaZlnCuKGw/bXd1-Q97oH4.jpg?size=616x905&quality=95&sign=df6d3c0b0313581578185069ddec6d99&type=album) 

## Вариант 3 

![текст](https://sun9-11.userapi.com/impg/fplRmm-V1cKtRXzymoVkHV8JWhAPogIImwQCrg/R0PJWZF5gZk.jpg?size=1130x597&quality=95&sign=d6ba37d9608e2e9d50c8c517fe25d310&type=album) 

![текст](https://sun9-60.userapi.com/impg/L2NHWiKnt6YleW-A8ZWszTRwBPLykrxlIN2GDw/d2LBYKEvbtY.jpg?size=479x441&quality=95&sign=2896a1733c75596bf48c2610879291d7&type=album) 

![текст](https://sun9-73.userapi.com/impg/QvPA-7epTYPlYTTeJrsDdeXzgKZXtQQHwTO8lQ/-VpDiCgp8tk.jpg?size=564x566&quality=95&sign=200cd011daee9a7e0731b7f34dd46daf&type=album) 

![текст](https://sun9-29.userapi.com/impg/l6H-KuYWxZWRz-qpzxtEjuix2xigZhiMGSttDw/xJlqe7Zz8ZY.jpg?size=577x560&quality=95&sign=b73744e9e2a24c59dacf69014868e0b8&type=album) 

![текст](https://sun9-26.userapi.com/impg/GDmDL45tSrZHp3RWZoTEYQmNmh1a0fWOP4wwdw/jnU5CKngRus.jpg?size=560x511&quality=95&sign=245c7ec3fb9e963aeb5c8e0840cb91b8&type=album) 