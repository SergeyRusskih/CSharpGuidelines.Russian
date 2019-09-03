---
title: Рекомендации по использованию фреймворка
permalink: /framework-guidelines/
classes: wide
search: true
sidebar:
  nav: "sidebar"
---

### <a name="av2201"></a> Используйте псевдонимы типов C# вместо типов из пространства имен `System`  (AV2201) ![](/assets/images/1.png)
Например, используйте `object` вместо `Object`, `string` вместо `String` и `int` вместо `Int32`. Эти псевдонимы были введены для того, чтобы сделать примитивные типы первоклассными членами языка C#, так что используйте их должным образом.

**Исключение:** При ссылке на статические элементы таких типов обычно принято использовать полное CLS имя, например, `Int32.Parse()` вместо `int.Parse()`.

### <a name="av2202"></a> Предпочитайте "синтаксический сахар" использованию имплементаций (AV2202) ![](/assets/images/1.png)
Синтаксический сахар делает код более выразительным. Абстракции делают последующий рефакториг легче (и иногда позволяют лучше оптимизировать производительность).

Предпочитайте:

	(string, int) tuple = ("", 1);

вместо:

	ValueTuple<string, int> tuple = new ValueTuple<string, int>("", 1);

Предпочитайте:

	DateTime? startDate;

вместо:

	Nullable<DateTime> startDate;

Предпочитайте:

	if (startDate != null) ...

вместо:

	if (startDate.HasValue) ...

Предпочитайте:

	if (startDate > DateTime.Now) ...

вместо:

	if (startDate.HasValue && startDate.Value > DateTime.Now) ...

Предпочитайте:

	(DateTime startTime, TimeSpan duration) tuple1 = GetTimeRange();
	(DateTime startTime, TimeSpan duration) tuple2 = GetTimeRange();

	if (tuple1 == tuple2) ...

вместо:

	if (tuple1.startTime == tuple2.startTime && tuple1.duration == tuple2.duration) ...

### <a name="av2207"></a> Не оставляйте в коде строки, которые должны быть изменены во время развертывания приложения (AV2207) ![](/assets/images/3.png)
Например, строки подключения, адреса серверов и т.д. Используйте файлы ресурсов, свойство `ConnectionStrings` класса `ConfigurationManager` или класс `Settings`, генерируемый Visual Studio. Поддерживайте актуальные значения настроек через `app.config` или `web.config` (а не в каком-либо другом месте).

### <a name="av2210"></a> Осуществляйте сборку с наивысшим уровнем предупреждений (AV2210) ![](/assets/images/1.png)
Сконфигурируйте свое рабочее окружение таким образом, чтобы использовать **Уровень предупреждений 4** для компилятора C# и включите опцию **Treat warnings as errors** (считать предупреждения за ошибки). Это позволит компилировать код с наивысшим уровнем качества из возможного.

### <a name="av2220"></a> Избегайте использования LINQ для простых выражений (AV2220) ![](/assets/images/3.png)
Вместо:

	var query = from item in items where item.Length > 0 select item;

лучше воспользоваться методом из пространства имен `System.Linq`:

	var query = items.Where(item => item.Length > 0);

Второй пример более читабельный.

### <a name="av2221"></a> Используйте лямбда-выражения вместо анонимных методов (AV2221) ![](/assets/images/2.png)
Лямбда-выражения служат более красивой альтернативой анонимным методам. Таким образом, вместо:

	Customer customer = Array.Find(customers, delegate(Customer customer)
	{
		return customer.Name == "Tom";
	});

используйте лямбда-выражение:

	Customer customer = Array.Find(customers, customer => customer.Name == "Tom");

или даже лучше это: 

	var customer = customers.FirstOrDefault(customer => customer.Name == "Tom");

### <a name="av2230"></a> Используйте ключевое слово `dynamic` только при работе с объектами этого типа (AV2230) ![](/assets/images/1.png)
Ключевое слово `dynamic` было введено для работы с динамическими языками. Их использование создает серьезный затор производительности (performance bottleneck), поскольку компилятор вынужден сгенерировать некоторое количество дополнительного кода.

Используйте `dynamic` только при обращении к членам динамически созданного экземпляра класса (при использовании класса `Activator`) в качестве альтернативы `Type.GetProperty()` и `Type.GetMethod()` или при работе с типами COM Iterop.

### <a name="av2235"></a> Старайтесь использовать `async/await` вместо `Task` (AV2235) ![](/assets/images/1.png)
Использование новых ключевых слов C# 5.0 упрощает создание и чтение кода, что, в свою очередь, упрощает его поддержку. Даже если вам требуется создавать многочисленные асинхронные операции. Например, вместо того, чтобы делать так:

	public Task<Data> GetDataAsync()
	{
	  return MyWebService.FetchDataAsync()
	    .ContinueWith(t => new Data(t.Result));
	}

объявляйте метод следующим образом: 

	public async Task<Data> GetDataAsync()
	{
	  string result = await MyWebService.FetchDataAsync();
	  return new Data(result);
	}

**Подсказка:** Вы можете использовать `async` и `await` даже если вам нужно работать с .NET Framework 4.0. Просто установите [Async Targeting Pack](http://www.microsoft.com/en-us/download/details.aspx?id=29576).
