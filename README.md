----------------------------------------------------- Regular Expressions ------------------------------------------------------------------------

# Методы:

`let z = myRegex.test(myString);`   		 -  Используется для проверки "myString" на выражение внутри шаблона "myRegex". 

Возвращает `true` или `false`;
`let z = myString.match(myRegex);`		 -  Извлекает строку, прописанную в выражении "myRegex".(возвращает массив или массив результатов).

`let z = ("It is.").replace(/is/g,"us");`  -  Метод принимает 2 аргумента(выражение которое соответсвует поиску, замена по найденному).

`let z = (" Hello, World! ").trim(/\s/g);` -  Метод используется для удаления символов в строке(Возвращает модифицированную строку).

`let z = ("This is just").search(/is/);`	 -  Возвращает позицию найденного выражения(не поддерживает глобальный поиск).

`let z = ("http://ua.fm").split(/\/{2}/g);` - Результатом данного выражения станет массив из двух элементов: "http:" и  "ua.fm/"

# Выражения для поиска:

`/\\/`									-  Экранирование символа поиска обратного слеша.

`/dog|cat|bird|fish/, "|"`		   		-  Логическое "или" для нескольких выражений.

`/freeCodeCamp/i,     "/i"`		   		-  Игнорировать регистр.

`/freeCodeCamp/ig	 "/g"`				-  Находит все совпадения в строке,(в данном примере игнорируя регистр)

`/.un/				 "."`				-  Все, что заканчивается на "un".

`/b[iuo]g/ig			"[iug]"`				-  Вернуть результат с любой гласной из предложенных между "b" и "g".(в данном примере все вхождения, игнор регистр).

`/[a-z]/ig			"[a-z]"`				-  Все соответсвия в диапазаоне с "a-z". (в данном примере все вхождения, игнор регистр).

`/[h-s2-6]/ig`							-  Найти вхождения в указанных диапазонах.(в данном примере все вхождения, игнор регистр).

`/[^aeiou0-9]/ig`							-  Исключить из поиска гласные буквы и цифры. (в данном примере все вхождения, игнор регистр).

`/^Cal/`									-  Используется для проверки на размещение слова в начале строки(внимание!!! нету квадратных скобок).

`/caboose$/`								-  Используется для поиска шаблона в конце строки.

`/ss+/g`		где		`"+"` 				-  эквивалентно выражению {1,}, к примеру буквосочетание `"ss"`. ("Mississippi" результатом будет "ss", "ss").

`/Aa*/g`		где		`"*"`					-  эквивалентно выражению {0,}, к примеру все вхожденния `"Aaa.."` (`"Aaaaaaaaaaaaaaaarrrgh!"` результатом будет `"Aaaaaaaaaaaaaaaa"`).

`/<.1*>/g`								-  Найдет все вхождения заданного формата (`Winter is coming` обернутый в тэг h1 вернет открывающийся тэг h1).

`/\w/g`		где		`"\w"`				-  Эквивалентно [A-Za-z0-9_]; "The five boxing wizards jump quickly." в строке вернет массив символов.["T","h"...]

`/\w+/g`									-  Эквивалентно [A-Za-z0-9_]; "The five boxing" вернет ["The", "five", "boxing"].

`/\W/g`									-  Эквивалентно [^A-Za-z0-9_], а значить не соответствует любому алфавитно-численному символу.

`/\d/g`									-  Эквивалентно [0-9];

`/\D/g;`									-  Эквивалентно [^0-9];

`/\s/g`									-  Соответствует нечисловым значениям. Эквивалентен  [ \r\t\f\n\v];

`/\S/g`									-  Эквивалентен [^\r\t\f\n\v];

`/Oh{3,6}\sno/`	где	`{3,6}`				-  Можно указывать диапазаны совпадений, в данном случае результат: Oh от 3 до 6 сивмолов "h", пробел "no";

`{4,}`									-  Диапазон от 4 и больше символов.

`{4}`										-  Только 4 символа.

`/colou?r/`		где	  `?`					-  эквивалентно выражению {0,1}, к примеру проверяет существование символа "u", возвращает оба результата "colour" и "color".

`(?=u)`									-  Проверка на позитивное составляюшую. ("qu").match(/q(?=u)/); // Returns ["q"]

`(?!u)`									-  Проверка на негативную составляющую. ("qt").match(/q(?!u)/); // Returns ["q"]

`/1`										-  Символ количества повторяющихся групп символов.

`/regular(expression)?/`					-  будет соответствовать слову "regular" за которым следует необязательное слово "expression".


# Примеры:

`/^[a-z]{2,}\d*$/i`						- В начале любые буквенные значения, не меньше двух, с любыми количеством числовых значений в конце, игнорируя регистр.

`/(?=\w{5,})(?=\D*\d{2,})/`				- Cоответствует позитивной составляющей не меньше 5 символов(букв, цифр) и п.с. из нечисловых символов, неограниченное количество и числовых, которых 2 и больше.(к примеру "abc123")

`/^(\d+)\s\1\s\1$/`						- Cоответствует 3 группам повторяющихся численных символов, к примеру "42 42 42".

`/^(\s+)|(\s+$)/g`						- Cоответствует всем нечисловым значениям в начале строки и в конце строки.

# Также можно создать конструктор регулярного выражения: 

`var myPattern = new RegExp("q$");`        // Создаем шаблон, находящий букву "q" в конце строки

# Объект RegExp в JavaScript имеет следующие *свойства*(можно передать аргументами при создании):

`source` - собственно текст регулярного выражения
`ignoreCase` - логическое значение обозначающее наличие флага "i", доступно только для чтения
`global` - логическое значение обозначающее наличие флага "g",  доступно только для чтения 
`multiline` - логическое значение обозначающее наличие флага "m",  доступно только для чтения 
`lastIndex` - счетчик, указывающий, с какой позиции в строке начинать поиск

# Методы:

`exec(text)` - выполнение поиска в строке, указанной в качестве параметра, возвращает массив найденных соответствий.
`test(text)` - проверка соответствия регулярному выражению, возвращает true\false.
