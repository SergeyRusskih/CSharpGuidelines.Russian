---
title: Рекомендации по именованию
permalink: /naming-guidelines/
classes: wide
search: true
sidebar:
  nav: "sidebar"
---

### <a name="av1701"></a> Используйте американский английский язык (AV1701) ![](/assets/images/1.png)

Все члены классов, параметры и переменные должны иметь название с использованием слов из американского английского языка.

- Выбирайте легкое, читаемое, предпочтительно грамматически правильное имя. Например, `HorizontalAlignment` более читаемое наименование, чем `AlignmentHorizontal`.
- Предпочитайте читаемость краткости. Имя свойства `CanScrollHorizontally` лучше, чем `ScrollableX` (отсылка к оси Х ни о чем не говорит).
- Избегайте использования имен, которые конфликтуют с ключевыми словами языка программирования.

### <a name="av1702"></a> Для каждого элемента языка используйте соответствующую нотацию (AV1702) ![](/assets/images/1.png) 

| Элемент языка | Нотация | Пример |
|:--------------------|:----------|:-----------|
| Пространство имен | Паскаль | `System.Drawing` |
| Параметр типа | Паскаль | `TView` |
| Интерфейс | Паскаль | `IBusinessService`
| Класс, структура | Паскаль | `AppDomain`
| Перечисление | Паскаль | `ErrorLevel` |
| Объект перечисления | Паскаль | `FatalError` |
| Ключ ресурса | Паскаль | `SaveButtonTooltipText` |
| Константа | Паскаль | `MaximumItems` |
| Приватное статическое ридонли поле | Паскаль | `RedValue` |
| Приватное поле | Верблюжья | `listItem` |
| Публичное поле | Паскаль | `MainPanel` |
| Свойство | Паскаль | `BackColor` |
| Событие | Паскаль | `Click` |
| Метод | Паскаль | `ToString` |
| Локальная функция | Паскаль | `FormatText` |
| Параметр | Верблюжья | `typeName` |
| Название элемнтов Tuple | Паскаль | `(string First, string Last) name = ("John", "Doe");` <br/>`var name = (First: "John", Last: "Doe");` <br/>`(string First, string Last) GetName() => ("John", "Doe");` |
| Переменные, объявленные с помощью Tuple синтаксиса | Верблюжья | `(string first, string last) = ("John", "Doe");` <br/>`var (first, last) = ("John", "Doe");` <br/> |
| Локальные переменные | Верблюжья | `listOfValues` |

**Примечание:** Чем выше правило в таблице, тем больший приоритет оно имеет.

### <a name="av1704"></a> Не включайте числа в наименования переменных, параметров и типов (AV1704) ![](/assets/images/3.png)
В большинстве случаев только лень может послужить причиной отсутствия ясного и говорящего самого за себя имени. 

### <a name="av1705"></a> Не используйте префиксы в названиях полей (AV1705) ![](/assets/images/1.png)
Например, не используйте `g_` или `s_` чтобы различить между собой статические и нестатические поля. Обычно, если в методе трудно отличить локальные переменные от полей класса, то данный метод слишком громоздок. Вот примеры неправильных наименований: `_currentUser`, `mUserName`, `m_loginTime`.

### <a name="av1706"></a> Не используйте аббревиатуры (AV1706) ![](/assets/images/2.png)
Например, используйте `OnButtonClick` вместо `OnBtnClick`. Избегайте использования одиночных символов в названиях переменных, таких как `i` и `q`. Вместо этого используйте полные слова, такие как `index` и `query`.

**Исключение:** Можно использовать акронимы и аббревиатуры, которые широко распространены в вашем домене. Например, используйте акроним `UI` вместо `UserInterface` и аббревиатуру `Id` вместо `Identity`.

### <a name="av1707"></a> Называйте члены класса, параметры и переменные в соответствии с их назначением, а не типом (AV1707) ![](/assets/images/2.png)
- Используйте наименование, которое указывает на функцию, которую выполняет член класса. Например, название `GetLength` лучше чем `GetInt`.
- Не используйте такие термины, как `Enum`, `Class` или `Struct` в именах.
- Переменные, ссылающиеся на коллекции, должны иметь название во множественном числе.

### <a name="av1708"></a> Именуйте типы, используя словосочетания из существительных или прилагательных (AV1708) ![](/assets/images/2.png)
Например, имя IComponent использует описательное существительное, ICustomAttributeProvider использует сочетание существительных, IPersistable использует прилагательное.
Плохие примеры: `SearchExamination` (страница поиска экзаменов), `Common` (не оканчивается на существительное, не объясняет назначение), `SiteSecurity` (несмотря на то, что с технической точки зрения имя выглядит хорошо, оно ничего не говорит о назначении).

Не используйте термины `Utility` или `Helper` в названиях классов. Классы с такими именами обычно статические и спроектированны без учета принципов объектно-ориентированного программирования (смотрите также [AV1008](/member-design-guidelines#av1008)).

### <a name="av1709"></a> При именовании параметров обобщенных типов используйте описательные имена (AV1709) ![](/assets/images/2.png)
- Всегда добавляйте приставку `Т` к описательным именам параметров типа.
- Всегда используйте описательные имена, если только имя, состоящее из одной буквы, не является полностью понятным без пояснений. В этом случае используйте букву `Т` в качестве имени параметра типа.
- Рекомендуется в имени параметра типа указывать ограничения, накладываемые на параметр типа. Например, параметр, предназначенный только для `ISession`, может быть назван `TSession`.

### <a name="av1710"></a> Не повторяйте имя класса или перечисления в названиях их членов (AV1710) ![](/assets/images/1.png)

	class Employee
	{
		// Неправильно!
		static GetEmployee() {...}
		DeleteEmployee() {...}
		
		// Правильно
		static Get() {...}
		Delete() {...}
		
		// Тоже верно.
		AddNewJob() {...}
		RegisterForMeeting() {...}
	}

### <a name="av1711"></a> Давайте элементам такие названия, которые схожи с элементами связанных с ними классов .NET Framework (AV1711) ![](/assets/images/3.png)
.NET разработчики уже привыкли к паттернам именования, которые используются в .NET Framework. Таким образом, следование этим паттернам поможет им быстрее разобраться в вашем коде. Например, если вы определяете класс, который реализует коллекцию, то назовите методы удаления элемента, его добавления и получения количества элементов такими именами, как `Add`, `Remove` и `Count` вместо `AddItem`, `Delete`, или `NumberOfItems`.

### <a name="av1712"></a> Избегайте коротких имен или имен, которые можно спутать с другими наименованиями (AV1712) ![](/assets/images/1.png)
Несмотря на то, что с технической точки зрения следующее выражение может выглядеть корректно, оно легко может ввести в заблуждение того, кто с ним столкнется :

	bool b001 = (lo == l0) ? (I1 == 11) : (lOl != 101);

### <a name="av1715"></a> Не ленитесь давать подходящие названия свойствам (AV1715) ![](/assets/images/2.png)
- Именуйте свойства с использованием существительных, словосочетаний с существительными или, в крайнем случае, с использованием словосочетаний с прилагательными. 
- Называйте свойство, которое имеет логический тип, используя утвердительные фразы. Например, `CanSeek` вместо `CannotSeek`.
- В наименованиях свойств, которые имеют логический тип, попробуйте использовать приставки `Is`, `Has`, `Can`, `Allows`, или `Supports`.
- Попробуйте дать свойству такое же название, как и у его типа. Когда вы создали свойство, которое имеет тип перечисления, название свойства может быть таким же, как название типа перечисления. Например, если у вас есть перечисление `CacheLevel`, то свойство, возвращающее одно из его значений, также должно иметь название `CacheLevel`.

### <a name="av1720"></a> Именуйте методы, используя связку глагол-объект (AV1720) ![](/assets/images/2.png)
Например, название метода или локальной функции `Show` или связка глагол-объект `ShowDialog`. Хорошее имя должно давать подсказку *что* происходит при вызови и, если возможно, *почему*.

Также не используйте слово `And` в названии метода или локальной функции. Это говорит о том, что метод делает более чем одну вещь, что является нарушением принципа единой ответственности [AV1115](/member-design-guidelines#av1115).

### <a name="av1725"></a> В названиях пространств имен используйте имена собственные, названия модулей (слоев), глаголы и слова, описывающие особенности данного пространства имен (AV1725) ![](/assets/images/3.png)
Например, наименования следующих пространств имен могут служить хорошим примером:

	AvivaSolutions.Commerce.Web
	NHibernate.Extensibility
	Microsoft.ServiceModel.WebApi
	Microsoft.VisualStudio.Debugging
	FluentAssertion.Primitives
	CaliburnMicro.Extensions

**Примечание:** Никогда не допускайте, чтобы в названиях пространств имен содержались названия типов, но если это существительное в его множественной форме, например `Collections`, то это обычно допустимо.

### <a name="av1735"></a> Используйте глагол или словосочетание с глаголом в названии события (AV1735) ![](/assets/images/2.png)
Именуйте событие глаголом или словосочетанием с глаголом. Например: `Click`, `Deleted`, `Closing`, `Minimizing`, `Arriving`. Например, объявление события `Search` может выглядеть следующим образом:

	public event EventHandler<SearchArgs> Search;

### <a name="av1737"></a> Используйте `-ing` и `-ed` для событий, которые должны случиться перед и после какого-либо другого события (AV1737) ![](/assets/images/3.png)
Например, событие, которое предшествует закрытию окна, должно называться `Closing`, а событие, которое возникает после его закрытия, — `Closed`. Не используйте приставки `Before` и `After` или какие-либо суффиксы для идентификации таких событий.

Предположим, вы хотите определить события, которые связаны с процессом удаления некоторого объекта. Дайте событиям имена `Deleting` и `Deleted` и избегайте таких наименований, как `BeginDelete` и `EndDelete`. Именуйте события так, как написано ниже:

- `Deleting`: Произойдет непосредственно перед удалением объекта.
- `Delete`: Произойдет, когда объект должен быть удален обработчиком события.
- `Deleted`: Произойдет, когда объект будет уже удален.

### <a name="av1738"></a> Используйте приставку On в названии обработчика события (AV1738) ![](/assets/images/3.png)
Хорошей практикой является добавлять приставку `On` к названию метода, который обрабатывает событие. Например, если метод обрабатывает событие `Closing`, то название должно быть `OnClosing`.

### <a name="av1739"></a> Используйте символ подчеркивание для параметров лямбда-выражений, которые не имеют значения (AV1739) ![](/assets/images/3.png)
Если вы используете лямбда-выражение, например, чтобы подписаться на событие, и текущие параметры события не имеют значения, используйте следующее условное обозначение, чтобы указать это более конкретно.

	button.Click += (_, __) => HandleClick();

### <a name="av1745"></a> Именуйте группы методов расширений в классе с использованием суффикса "Extentions" (AV1745) ![](/assets/images/3.png)
Если название метода расширения конфликтует с другими элементом или методом расширения, вы должны добавить префикс в виде названия класса к вызову. Их добавление в связанный класс с суффиксом `Extensions` улучшит читаемость.

### <a name="av1755"></a> Добавляйте суффиксы `Async` или `TaskAsync` к названиям асинхронных методов (AV1755) ![](/assets/images/2.png)
Общая рекомендация для методов, которые возвращают `Task`, — это добавлять к ним суффикс `Async`. Однако если метод с таким названием уже существует, используйте вместо этого суффикс `TaskAsync`.
