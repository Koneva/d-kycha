﻿# Реализация приоритетной очереди на основе d-кучи, упорядоченной таблицы и бинарного дерева и её применение для построения остовного дерева графа с помощью алгоритма Краскала.

## Содержание

* [Постановка задачи](#Постановка-задачи)
* [Руководство пользователя](#Руководство-пользователя)
	* [Использование реализации пирамидальной сортировки](#Использование-реализации-пирамидальной-сортировки)
    * [Использование реализации алгоритма Дейкстры](#Использование-реализации-алгоритма-Дейкстры)
	* [Использование реализации алгоритма Крускала](#Использование-реализации-алгоритма-Крускала)
* [Руководство программиста](#Руководство-программиста)
	* [Используемые программы](#Используемые-программы)
	* [Общая структура репозитория](#Общая-структура-репозитория)
	* [Описание структуры решения](#Описание-структуры-решения)
	* [Описание структур данных](#Описание-структур-данных)
		* [D-куча](#d-куча)
		* [Бинарное дерево](#Бинарное-дерево)
			* [Бинарное поисковое дерево](#Бинарное-поисковое-дерево)
			* [АВЛ-дерево](#АВЛ-дерево)
		* [Таблицы](#Таблицы)
			* [Просматриваемые таблицы](#Просматриваемые-таблицы)
			* [Упорядоченные таблицы](#Упорядоченные-таблицы)
		* [Приоритетные очереди](#Приоритетные-очереди)
		* [Графы](#Графы)
      * [Разделенные множества](#Разделенные-множества)
	* [Описание алгоритмов](#Описание-алгоритмов)
		* [Пирамидальная сортировка](#Пирамидальная-сортировка)
		* [Алгоритм Дейкстры](#Алгоритм-Дейкстры)
		* [Алгоритм Крускала](#Алгоритм-Крускала)
	* [Программная реализация структур данных](#Программная-реализация-структур-данных)
		* [Программная реализация d-кучи](#Программная-реализация-d-кучи)
		* [Программная реализация бинарного поискового дерева](#Программная-реализация-бинарного-поискового-дерева)
		* [Программная реализация АВЛ-дерева](#Программная-реализация-АВЛ-дерева)
		* [Программная реализация просматриваемых таблиц](#Программная-реализация-просматриваемых-таблиц)
		* [Программная реализация упорядоченных таблиц](#Программная-реализация-упорядоченных-таблиц)
		* [Программная реализация приоритетной очереди на основе D-кучи](#Программная-реализация-приоритетной-очереди-на-основе-D-кучи)
		* [Программная реализация приоритетной очереди на основе бинарного поискового дерева](#Программная-реализация-приоритетной-очереди-на-основе-бинарного-поискового-дерева)
		* [Программная реализация приоритетной очереди на основе упорядоченной таблицы](#Программная-реализация-приоритетной-очереди-на-основе-упорядоченной-таблицы)
		* [Программная реализация разделенных множеств](#Программная-реализация-разделенных-множеств)
		* [Программная реализация графа](#Программная-реализация-графа)
* [Заключение](#Заключение)
* [Литература](#Литература)


##Постановка задачи

1. Разработать статические библиотеки, реализующие следующие структуры данных:
	- D-кучу;
	- Бинарное поисковое дерево;
	- АВЛ-сбалансированное дерево;
	- Графы
	- Разделенные множества
	- Просматриваемую таблицу;
	- Упорядоченную таблицу;
	- Приоритетную очередь, основанную на d-куче;
	- Приоритетную очередь, основанную на бинарном поисковом дереве;
	- Приоритетную очередь, основанную на упорядоченной таблице;
2. Написать тестирующую программу для каждой структуры данных с помощью Google C++ Testing Framework.
3. Написать приложение для демонстрации работы d-кучи (пирамидальная сортировка).
4. Написать приложение для демонстрации работы приоритетной очереди, основанной на d-куче (алгоритм Дейкстры):
	- входные данные - связный неориентированный взвешенный граф без петель со стартовой вершиной;
	- выходные данные:
	    - список вершин;
	    - список кратчайших путей до каждой вершины графа;
	    - список предшествующий вершин.
5. Написать приложение для демонстрации работы приоритетных очередей и разделенных множеств (алгоритм Крускала):
	* входные данные - связный неориентированный взвешенный граф без петель;
	* выходные данные - граф, представляющий минимальное остовное дерево для исходного графа.

##Руководство пользователя

###Использование реализации пирамидальной сортировки

####Запуск приложения и ввод данных

Программа предназначена для сортировки D-кучи.
Для запуска приложения нужно открыть исполняемый файл `sample_sort.exe`.
Программа запросит арность кучи, затем количество элементов. Программа автоматически заполнит дерево, с учетом ваших данных, и на экран выведется сначала исходная куча, затем отсортированная.

####Пример:

После запуска программа встретит вас довольно радостным экраном:

![1](/kartinki/1.png)

После ввода необходимых данных, на ваш экран будет выведен результат сортировки:

![2](/kartinki/2.png)


###Использование реализации алгоритма Дейкстры

####Запуск приложения и ввод данных

Программа предназначена для поиска кратчийших путей во взвешенном неориентированном графе от любой вершины до всех остальных вершин графа.
Для запуска приложения нужно открыть исполняемый файл `sample_deykstra.exe`.
Программа попросит ввести количество вершин графа и количество ребер. Затем необходимо ввести минимальное и максимальное значения весов ребер. Также будет запрошен номер стартовой вершины. Результатом будет вывод номеров всех вершин, кратчайших путей от стартовой вершины и номеров предшествующих вершин.

####Пример:

1) Вводим количество вершин графа

![3](/kartinki/3.png)

2) Теперь количество ребер графа

![4](/kartinki/4.png)

3) Ну и минимальное и максимальное значения весов рёбер графа

![5](/kartinki/5.png)

4) Граф готов. Теперь необходимо выбрать стартовую вершину

![6](/kartinki/6.png)

Программа выведет результат алгоритма

![7](/kartinki/7.png)


###Использование реализации алгоритма Крускала

####Запуск приложения и ввод данных

Программа предназначена для построения минимального остовного дерева для взвешенного неориентированного графа. 
Для запуска приложения нужно открыть исполняемый файл `sample_kruskal.exe`.
Программа потребует ввести тип данных, с помощью которого будет использоваться приоритетная очередь и количество вершин графа. Затем запросит каким образом заполнять граф. Результатом работы программы будет вывод списка ребер, составляющих минимальное остовное дерево.

####Пример

1) Вводим тип данных для приоритетной очереди

![8](/kartinki/8.png)

2) Теперь вводим количество вершин графа и количество рёбер

![9](/kartinki/9.png)

3) Введём способ заполнения графа. В данном случае выбрано ручное заполнение графа. Введем рёбра и их веса

![10](/kartinki/10.png)

Если выбрать автоматическое заполнение графа, программа запросит минимальное и максимальное значение графа.
Для ввода графа из файла, надо создать файл "file.txt" с необходимыми данными и поместить его в корне диска C.

4) Программа завершила работу и вывела результат на экран

![11](/kartinki/11.png)


##Руководство программиста

###Используемые программы

В ходе выполнения работы использованы следующее ПО:
- Среда разработки Microsoft Visual Studio 2012.
- Фреймворк для написания автоматических тестов Google Test.
- Система контроля версий Git.

###Общая структура репозитория

Репозиторий содержит следующие директории и файлы:

* [`gtest`](https://github.com/AleksandrLykov/d-kycha/tree/master/gtest) - библиотека GoogleTest.
* [`include`](https://github.com/AleksandrLykov/d-kycha/tree/master/include) - директория для размещения заголовочных файлов и реализаций структур данных.
* [`sample`](https://github.com/AleksandrLykov/d-kycha/tree/master/samples) - директория для размещения исходных кодов приложений.
* [`test`](https://github.com/AleksandrLykov/d-kycha/tree/master/test) - директория для размещения тестов.
* [`sln`](https://github.com/AleksandrLykov/d-kycha/tree/master/sln) - директория с файлими решений (на данный момент Visual Studio 2012).
* [`kartinki`](https://github.com/AleksandrLykov/d-kycha/tree/master/kartinki) - директория с картинками для отчета;
* 

###Описание структуры решения

Решение состоит из 14 проектов:

* `AVL` - статическая библиотека, содержащая объявление и реализацию шаблонного класса `AVL`.
* `bintree` - статическая библиотка, содержащая объявление и реализацию шаблонного класса `bintree`.
* `d_heap` - статическая библиотека, содержащая объявление и реализацию шаблонного класса `DHeap`.
* `graph` - статическая библиотека, содержащая объявление и реализацию шаблонного классов `graph`.
* `gtest` - фреймворк Google Test.
* `queue_bintree` - статическая библиотека, содержащая объявление и реализацию шаблонного класса приоритетной очереди, основанной на бинарном поисковом дереве `BQueue`.
* `queue_dheap` - статическая библиотека, содержащая объявление и реализацию шаблонного класса приоритетной очереди, основанной на D-куче `HQueue`.
* `queue_table` - статическая библиотека, содержащая объявление и реализацию шаблонного класса приоритетной очереди, основанной на упорядоченной таблице `TQueue`.
* `sample_deykstra` - консольное приложение для демонстрации работы алгоритма Дейкстры.
* `sample_kruskal` - консольное приложение для демонстрации работы алгоритма Крускала.
* `sample_sort` - консольное приложение для демонстрации работы пирамидальной сортировки.
* `set` - статическая библиотека, содержащая объявление и реализацию шаблонного класса `sets`.
* `table` - статическая библиотека, содержащая объявление и реализацию шаблонных классов `Table`, `ScanTable`, `SortTable`.
* `tests` - консольное приложение для проверки правильности реализации классов `AVL`, `bintree`, `DHeap`, `graph`, `BQueue`, `HQueue`, `TQueue`, `sets`, `ScanTable`, `SortTable`.


###Описание структур данных

####D-куча
D-куча - завершенное d-арное дерево, содержащее набор однотипных элементов, со следующими свойствами:
- каждый узел, не являющийся листом, за исключением, быть может, одного имеет ровно d потомков. Один узел, являющийся исключением, может иметь от 1 до d-1 потомка;
- если h - глубина дерева, то для любого i = 1, ..., k-1 такое дерево имеет ровно d^i узлов глубины i;
- количество узлов глубины k в дереве глубины k может варьироваться от 1 до d^k;
- каждый узел имеет вес. Иначе говоря, каждому узлу дерева присвоен ключ такого типа данных, на котором определен порядок сравнения;
- ключ элемента, приписанного узлу i, не превосходит ключа любого из своих потомков.

######Основные операции
* Транспонирование `trans` (трудоемкость = O(1))
* Всплытие `vsplyt` (трудоемкость = log(n));
* Погружение `pogryzh` (трудоемкость = О(d*log(n));
* Вставка элемента `push` (трудоемкость = О(log(n));
* Удаление элемента c минимальным ключом `delet` (трудоемкость = О(log(n));
* Удаление элемента с заданным ключом `deletzadan` (трудоемкость = О(log(n));
* Окучивание `okych` (трудоемкость = О(log(n)).

####Бинарное дерево

#####Бинарное поисковое дерево
Бинарное поисковое дерево - это двоичное дерево, обладающее следующими свойствами:
* каждый узел имеет не больше двух потомков;
* любое поддерево является бинарным поисковым деревом;
* значение ключа любого узла левого поддерева меньше значения ключа корневого узла;
* значение ключа любого узла правого поддерева больше значения ключа корневого узла.
 
######Основные операции
* Вставка элемента `insert` (трудоемкость = log(n));
* Удаление элемента `Delete` (трудоемкость = log(n));
* Поиск элемента `FindKey` (трудоемкость = n);
* Обходы:
    * Обход в прямом порядке `workAroundForward`;
    * Обход в обратном порядке `workAroundReverse`;
    * Симметричный обход `workAroundSymmetr`;
    * Обход в ширину `workAroundAcross`;
    * Обход в глубину `workAroundDepth`.

#####АВЛ-дерево
АВЛ-дерево - сбалансированное по высоте бинарное поисковое дерево, обладающее дополнительным свойством:
* для каждой вершины дерева высота её двух поддеревьев различается не больше чем на 1.

######Основные операции
* Вставка элемента `insert` (трудоемкость = log(n));
* Удаление элемента `Delete` (трудоемкость = log(n));
* Балансировка дерева `Balance`. В неё входят:
    * Однократный левый поворот `rotateLeft`(трудоемкость = O(1));
    * Однократный правый поворот `rotateRight`(трудоемкость = O(1));
    * Двукратный правый поворот `doubleRotateRight`(трудоемкость = O(1));
    * Двукратный левый поворот `doubleRotateLeft`(трудоемкость = O(1));
    * Баланс фактор `BFactor`(трудоемкость = O(1)).


####Таблицы

#####Просматриваемые таблицы
Таблица - динамическая структура данных, хранящая однотипные элементы. Записи хранятся в векторе памяти в порядке добавления (добавление производится в конец таблицы). При удалении записи просиходит перепаковка (сдвиг всех записей ниже текущей на одну позицию вверх).

######Основные операции
* Поиск элемента с заданнымключом `search`;
* Вставка элемента `insert`;
* Удаление элемента `erase`.

#####Упорядоченные таблицы
Упорядоченная таблица - это просматриваемая таблица, данные в которой отсортированы по невозрастанию/неубыванию ключей. Причем при вставке и удалении происходят перепаковки.

######Основная операция
* Сортировка элементов `sort` (трудоемкость = log(n)).

####Приоритетные очереди
Приоритетная очередь — это динамическая структура данных, содержащая элементы, каждый из которых имеет определенный приоритет. Элемент с более высоким приоритетом находится перед элементом с более низким приоритетом. Если у элементов одинаковые приоритеты, они располагаются в зависимости от своей позиции в очереди. 

######Основные операции:
* Вставка элемента `push`;
* Удаление элемента с максимальным приоритетом `pop`;
* Получение элемента с максимальным приоритетом `top`;
* Проверка очереди на пустоту `isEmpty`.

####Разделенные множества
Разледенные множества - абстрактный тип данных, предназначенный для представления коллекции k попарно непересекающихся можеств.

######Основные операции
* Создание множества `makesets` (трудоемкость = О(1));
* Объединение множеств `unionsets` (трудоемкость = О(n));
* Поиск множества `findsets` (трудоемкость = О(1)).

###Описание алгоритмов

####Пирамидальная сортировка
1. На вход поступает 2 значения: арность кучи и количество элементов.
2. Формируется куча с данными условиями.
3. Просматривается минимальный элемент кучи и кладется в результирующую кучу.
4. Минимальный элемент D-кучи меняется с последним.
5. Размер D-кучи уменьшаем на 1.
6. Погружаем нулевой элемент.
7. Если размер кучи положителен, переход к п.3, иначе алгоритм завершается.

Таким образом, возвращаемые значения будут отсортированы по возрастанию.

####Алгоритм Дейкстры

1. На вход поступает количество вершин, рёбер, минимальное и максимальное значение веса ребра.
2. Исходя из заданных условий формируется граф `graph`.
3. Задается стартовая вершина `s`.
4. Создается массив для отметки посещения вершины `vis`. Всем элементам (кроме `vis[s] = s`) присваивается -1.
5. Создается результирующий массив расстояний `dist` (все элементы равны `MAX`, `dist[s] = 0`).
6. Создается приоритетная очередь, в которую кладется расстояние от текущей вершины до неё же.
7. Вынимается минимальный элемент.
8. Если метка вынутого элемента больше метки, хранящейся в массиве `dist`, переходим к следующему шагу.
9. Проходим по всем ребрам от текущей вершины. Если результирующее расстояние от смежной вершины больше, чем результирующее расстояние до вынутой в пункте 7 вершины в сумме с меткой ребра, вынутого в пункте 9, то:
		- В `vis`  по номеру смежной вершины кладется значение вершины, вынутой на этапе 7.
		- В `dist` по номету смежной вершины пишется новое значение расстояния, равное сумме результирующего расстояния до вынутой в пункте 7 вершины и меткои ребра, вынутогов пункте 9.
		- Обработанное ребро кладется в очередь.
10. Выполняем пункты 7-9 до тех пор, пока очередь не опустеет.
11. На выходе получим 2 массива: 
    - Массив `dist` содержит кратчайшие расстояния до каждой вершины графа `graph`.
    - Массив `vis` содержит предшествующие вершины.

####Алгоритм Крускала

1. На вход поступает количество вершин `n`, рёбер, минимальное и максимальное значение веса ребра(если автоматическое заполнение).
2. Исходя из заданных условий формируется граф `graph`.
3. Создается приоритетная очередь из ребер графа `queue` (приоритет по весу ребра).
4. Создается разделенное множество из всех вершин `set`.
5. Вынимается ребро из приоритетной очереди.
6. Если вершины, вынутые из очереди не принадлежат одному множеству, то 2 множества (под номерами вершин) объдиняются, а данное ребро добавляется в результирующий граф `tree`.
7. Если количество вершин `tree` не превышает количество `n-1` и если очередь не пуста, то переходим к п.5, иначе алгоритм завершается.

В результате работы алгоритма имеется набор ребер, составляющих минимальное остовное дерево для данного графа.

###Программная реализация структур данных

####Программная реализация d-кучи
В работе D-куча представлена классом `DHeap`, содержащим изложенные ниже методы:
- `getidx (int)` -  возвращает индекс родителя.
- `trans (const int, const int)` - транспонирование 2-х елементов
- `vsplyt (int)` - операция всплытие.
- `pogryzh (int)` - операция погружения.
- `minchild (int)` - минимальный "ребенок".
- `delet ()` - операция удаления минимального элемента.
- `deletzadan (int)` - операция удаления элемента с заданным индексом.
- `push (HType)` - вставка элемента.
- `okych ()` - операция окучивания.
- `vyvod ()` - вывод кучи на экран.
- `operator == (const DHeap<HType>&)const` - проверка на равенство.
- `operator=(const DHeap<HType>&)` - перегрузка оператора `=`.
- `getKolvo()` - возвращает количество элементов в куче
- `getKey(int)` - возвращает ключ заданного элемента.

####Программая реализация бинарного поискового дерева
Узел дерева представляется классом `Node`, содержащим следующие поля:
* `HType data` - данные.
* `Node<HType>* left` - указатель на левого потомка.
* `Node<HType>* right` - указатель на правого потомка.
* `Node<HType>* parent` - укаазатель на родителя.
* `int balance` - баланс поддерева.

Бинарное поисковое дерево представлено классом `bintree`, содержащим следующие методы:
* `CopyTree (Node<TType> *)` - копирование дерева.
* `insert (Node<TType>*&, const Node<TType> *)` - вставка элемента.
* `Delete (Node<TType>*&, const TType &)` - удаление элемента.
* `Findkey (Node<TType>*, const TType &)` - поиск элемента по ключу.
* `FindMax (Node<TType>*)` - поиск максимального элемента.
* `FindMin (Node<TType>*)` - поиск минимального элемента.
* `FindNext (Node<TType>*, Node<TType>*)` - поиск элемента, следующего за заданным.
* `FindPrevious (Node<TType>*, Node<TType>*)` - поиск элемента, предыдущего за заданным.
* `workAroundAcross (Node<TType>*)` - обход в ширину.
* `workAroundForward (Node<TType>*)` - прямой обход.
* `workAroundReverse (Node<TType>*)` - обратный обход.
* `workAroundSymmetr (Node<TType>*)` - симметричный обход.
* `workAroundDepth (Node<TType>*)` - обход в глубину.
* `operator== (const bintree<TType>&)const` - проверка на равенство.
* `getSize()` - возвращает количество элементов.
* `getHeight(Node<TType>*)` - высота поддерева

####Программая реализация АВЛ-дерева
АВЛ-дерево представлено классом `AVL`, наследуемым от класса `bintree`, содержащим нижеизложенные методы:
* `BFactor(Node<TType>*)` - баланс фактор дерева.
* `rotateRight(Node<TType> *&)` - однократный правый поворот.
* `rotateLeft(Node<TType> *&)` - однократный левый поворот.
* `doubleRotateRight (Node<TType> *&)` - двукратный правый поворот.
* `doubleRotateLeft (Node<TType> *&)` - двукратный левый поворот.
* `Balance (Node<TType>*&)` - балансировка дерева.
* `insert (const TType& k)` - вставка элемента, содержащая вспомогательную функцию `recursInsert (Node<TType>*&, Node<TType>*)`.
* `Delete (const TType& k)` - удаление элемента, содержащая вспомогательную функцию `recursDelete (Node<TType>*&, const TType&)`.

####Программая реализация просматриваемых таблиц
Запись в таблице представлена классом `TabRecord`, содержащим следующие поля:
* `typ key` - идентификатор.
* `TType data` - ключ.

База для всех таблиц представлена классом `Table`, содержащим чисто виртуальные методы:
* `search (typ)` - поиск элемента по идентификатору.
* `insert (typ, TType)` - вставка элемента.
* `erase (typ)` - удаление элемента
* `isEmpty ()` - проверка на пустоту.
* `GetCount ()` - возвращает текущее количество записей.
* `reset ()` - сбрасывает указатель на `0`.
* `goNext ()` - переход к следующей записи.
* `isTabEnded ()` - возвращает `1`, если таблица закончилась, и `0` если нет.

Просматриваемые таблицы представлены классом `ScanTable`, содержащим следующие методы:
* `search (typ k)` - поиск элемента.
* `insert (typ k, TType Data)` - вставка элемента.
* `erase(typ k)` - удаление элемента.
* `print()` - вывод таблицы на экран.

####Программая реализация упорядоченных таблиц
Упорядоченные таблицы наследуются от класса `ScanTable` и представлены классом `SortTable`, содержащим нижеизложенные методы:
* `sort()` - сортировка данных.
* `search (typ key)` - поиск элемента.
* `insert(typ k, TType Data)` - вставка элемента.
* `erase(typ k)` - удаление элемента.
* `min ()` - возвращает минимальный элемент.


####Программая реализация приоритетной очереди на основе D-кучи
Приоритетная очередь на основе D-кучи представлена классом `HQueue`, содержащим следующие методы:
* `push(const HType)` - вставка элемента.
* `pop()` - удаление элемента с максимальным приоритетом.
* `isEmpty()` - проверка на пустоту.
* `top()` - возвращает элемент с максимальным приоритетом.
* `vyvod()` - вывод очереди на экран.
* `getSize ()` - возвращает количество элементов в очереди.
* `operator ==(const HQueue<HType>&)const` - проверка на равенство.

####Программная реализация приоритетной очереди на основе бинарного поискового дерева
Приоритетная очередь на основе бинарного поискового дерева представлена классом `BQueue`, содержащим следующие методы:
* `push(const HType)` - вставка элемента.
* `pop()` - удаление элемента с максимальным приоритетом.
* `isEmpty()` - проверка на пустоту.
* `top()` - возвращает элемент с максимальным приоритетом.
* `print()` - вывод очереди на экран.
* `getSize ()` - возвращает количество элементов в очереди.
* `operator ==(const HQueue<HType>&)const` - проверка на равенство.

####Программная реализация приоритетной очереди на основе упорядоченной таблицы
Приоритетная очередь на основе упорядоченной таблицы представлена классом `TQueue`, содержащим следующие методы:
* `push(typ k, TType a);` - вставка элемента.
* `pop()` - удаление элемента с максимальным приоритетом.
* `isEmpty()` - проверка на пустоту.
* `top()` - возвращает элемент с максимальным приоритетом.
* `print()` - вывод очереди на экран.
* `getSize ()` - возвращает количество элементов в очереди.

####Программая реализация разделенных множеств
Разделенные множества представлены классом `sets`, содержащим следующие методы:
* `makesets (int)` - создает одноэлементное множество.
* `findsets (int)` - возвращает главный элемент множества
* `unionsets (int, int)` - объединяет множества.
* `vyvod()` - выводит множества на экран.
* `getsets(int)` - возвращает массив, в котором: 1-элемент - количество элементов в данном множестве, последующие элементы - данное множество.

####Программая реализация графа
Ребра графа представлены классом `edge`, содержащим:
* `int o` - стартовая вершина
* `int k` - конечная вершина
* `HType weight` - вес ребра

Граф представлен классом `Graph`, содержащим следующие методы:
* `createGraph (HType, HType)` - создает граф (на вход принимается минимальное и максимальное значение веса ребра).
* `addEdge(int, int, HType)` - добавляет ребро с заданными условиями (откуда, куда, вес).
* `delEdge(int, int)` - удаляет заданное ребро
* `getKolvo()` - возвращает количество вершин
* `getEdgeSize()` - возвращает максимальное количество рёбер.
* `getRealSize()` - возвращает реальное количество рёбер.
* `getEdge(int)` - возвращает ребро.
* `getWeight(int, int)` - возвращает вес ребра
* `print()` - вывод граф на экран

##Заключение
В ходе лабораторной работы:
* Были реализованы структуры данных:
 - "D-куча"
 - "Бинарное поисковое дерево"
 - "АВЛ-сбалансированное дерево"
 - "Таблица"
 - "Просматриваемая таблица"
 - "Упорядоченная таблица"
 - "Приоритетная очередь на основе D-кучи"
 - "Приоритетная очередь на основе бинарного поискового дерева"
 - "Приоритетная очередь на основе упорядоченой таблицы"
 - "Графы"
 - "Разделенные множества"
с использованием шаблонных классов. 
* Написано тестирующее приложение, которое покрывает все методы, используемые в указанных классах. Все тесты успешно пройдены. 
* Написаны консольные приложения:
- Пирамидальная сортировка массива.
- алгоритм Дейкстры для поиска кратчайших путей от любой стартовой вершины связного неориентированного взвешенного графа без петель, реализованного на основе приоритетной очереди на базe D-кучи.
- алгоритм Крускала для построения минимального остовного дерева неориентированного взвешенного графа без петель, реализованного на основе приоритетных очередях на базе D-кучи, бинарного поискового дерева и упорядоченной таблицы.

##Литература
1. Кормен Т., Лейзерсон Ч., Риверст Р., Штайн К. Алгоритмы. Построение и анализ. - М.: Издательский дом "Вильямс". - 2005. - 1290с.
2. Алексеев В.Е., Таланов В.А. Графы. Модели вычислений. Структуры данных: Учебник. – Нижний Новгород: Изд-во ННГУ, 2005. 307 с.
