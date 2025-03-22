# OOP_lectures
Материал лекцонных занятий ООПиП бгуир

# 1-я лк. Основные принципы ООПиП
## 1.1 Основные принципы, методы
Любая программа всегда представляет собой набор инструкций **процессора** в двоичном коде.
у
В связи с увеличением объемов программ, становится невозможным удерживать в памяти все детали реализации. Необходимо выделять главное и отбрасывать ненужное (повышать степень абстракции программы)
- sloc - source line of code

В языке с первым шагом к абстракции были *функции* (прототип, реализация, вызов).
Следующий шаг стало создание *пользовательских типов*, которые позволяют сгруппировать информацию в естественном для программируемой области виде.

В языке С++ таким средством являются *классы* (class), которые идентичны структурам, но отличаются только атрибутом доступа, спецификатором доступа по умолчанию.
Язык С не поддерживает ООП, хотя у него есть языковые конструкции, которые позволяют реализовать ООП.

### Процедурное программирование VS ООП

	Процедурное программирование делает упор на обработку данных с помощью АЛГОРИТМА
Для этого язык С реализует передачу параметров в функцию и возврат ею результата.

Язык С++ расширяет язык С средствами, которые поддерживают ООП:
1) Абстракции
2) Инкапсуляция
3) Полиморфизм *
4) Наследование
5) Повторное использование кода

Принципы ООП:
1) Инкапсуляция
2) Наследование
3) Полиморфизм

Функции языка С в языке С++ становятся *методами* и предназначены для доступа к содержимому класса. Прямой доступ к содержимому класса **невозможен**. Данные и методы инкапсулированы в классе.

	Класс - неделимая единица
Типичная программа С++ состоит из набора объектов, взаимодействующих между собой посредством вызова методов.

### INHERITANCE (наследование)
	Позволяет использовать методы другого класса без повторения их реализации.
	(Code Reuse)
Наследование позволяет ***расширить*** существующие классы, **сохраняя** их функциональность и **добавляя** им новые свойства и методы. Класс, который расширяется называется *базовым*, который расширяет - дочерний (derived class/производный класс).

В языке С++ реализовано множественное наследование (multiple inheritance), которое во многих языках (Java, С#) запрещено.

### Полиморфизм (многообразный)
	Свойство, которое позволяет одно и то же имя использовать для двух и более похожих, но технически разных задач.
В С++ полиморфизм:
1) Перегрузка функции (function overloading)
2) Перегрузка оператора (operator overloading)
### Классы
Класс предназначен С++ для абстрагирования автоматизируемой информации в пользовательский тип данных.
Класс это чертеж, схема, описание.
При создании класса ***НИКОГДА*** не выделяется память (может быть в зачете).

Объект - это переменная типа class и под объект *всегда* выделяется память.

# 2-я лк. Наследование. Inheritance
#ООПиП 
## Наследование
	Наследование - один из принципов ООП, который позволяет создавать новые классы (наследники (подклассы, производные)) из уже существующих (базовых (родительских)). 
	
Это приводит к повторному использованию кода (code reuse) производный класс получает **ВСЕ** возможности базового класса, но может быть усовершенствован, за счет добавления новых возможностей. При этом базовый класс остается неизменным. 

Стрелка генерализации на диаграммах UML **ВСЕГДА** указывает на базовый класс. 

Атрибутом по умолчанию при наследовании между классами является *private*.

Наследование должно отвечать на вопрос "Является Х". 
	"Ученик НЕ является университетом" - наследование недопустимо

модификатор доступа *Protected* используется если необходимо, чтобы поле или метод класс были доступны внутри текущего класса и в любом другом дочернем классе.

*private* компоненты не наследуются. Т.е элементам с атрибутом private базового класса дочерние классы доступа не имеют. 
Конструкторы и деструкторы **НЕ** наследуются, но для создания объектов дочернего класса всегда используется конструкторы всех базовых классов.

Для разрушения объекта дочернего класса деструкторы вызываются начиная с дочернего класса и вверх по иерархии до деструктора самого верхнего класса.
### Переопределение методов (Overriding)
В производном классе методы могут иметь такое же имя, как и в базовом. Сигнатура метода при этом должна совпадать. При этом реализации в базовом и дочернем классе будут различны. Это называется *переопределение метода*

Сигнатура метода не включает в себя возвращаемый тип.
Для того, чтобы понять, какой метод базового или дочернего класса необходимо вызвать, компилятор анализирует тип объекта, для которого этот метод вызвался.

При необходимости к реализации метода базового класса, необходимо указать его имя и оставить оператор расширения области видимости.

Иерархия классов не дублирует организационную структуру предприятия. Часто в иерархии классов самый верхний класс является настолько общим, что его необходимо сделать абстрактным. Важно учитывать комбинации атрибутов доступа.

Схема доступов:

| public<br>protected<br>private | ->public->    | public<br>protected    |
| ------------------------------ | ------------- | ---------------------- |
| public<br>protected<br>private | ->protected-> | protected<br>protected |
| public<br>protected<br>private | ->private->   | private<br>private     |
Обычно поля открытые или защищенные. Методы - открытые.

### Множественное наследование
Класс может быть производным от двух и более классов.
*Это называется множественным наследованием*

При множественном наследовании, конструкторы вызываются в порядке, в котором указываются базовые классы при наследовании.

Если в двух базовых классах, присутствуют методы с одинаковыми сигнатурами. А в дочернем такого нет, то возникает неоднозначность (какой метод из какого класса надо вызвать)
Эту неоднозначность можно устранить указав:

	имя базового класса оператора :: и имя нужного метода
Во многих языках программирования множественное наследование классов запрещено. Но при этом разрешено множественное наследование интерфейсов.
## Связи
Наследование не является единственной связью между классами.
Например есть связь *Агрегация,* *Композиция*, *Ассоциация*, *Зависимость* и другие

Пример:
Машина и транспортное средство связаны связью **Наследование**, но библиотека и книга связаны связью "*Содержит, включает*" (Т.е **Агрегация**).
### Основные связи, когда класс находится в классе
- Агрегация
- Композиция

Есть понятие *контейнера* и *части*
- Контейнер - факультет
- Часть - студент, сотрудник факультета

При агрегации разрушения контейнера не приводит к разрушению части.
При композиции разрушение контейнера приводит к разрушению части.
