# IniFiles
Библиотека разработанная для чтение файлов типа \*.ini на C#

Библиотека содержит 5 методов и конструктор

## Конструктор (string name_file)
Подключается к файлу ini.
Объект лучше обьявлять в глобальном пространстве.

```C#
IniFiles ini = new IniFiles("config.ini");
```

## string ReadINI(string Секция, string Ключ)
Читает ini-файл и возращает значение указаного ключа из заданной секции.

```C#
string name = ini.ReadINI("DataBase", "name");
//name == "example.db"
```
```ini
//Пример config.ini
[DataBase]
name = example.db;
```

## void Write(string Секция, string Ключ, string Значение)
Записывает в ini-файл. Запись происходит в выбранную секцию и выбранный ключ.

```C#
ini.Write("DataBase", "name", "test.db");
```
```ini
//Изменение
[DataBase]
name = test.db;
```

## void DeleteKey(string Ключ, string Секция = null)
Удаляем ключ из выбранной секции.

```C#
ini.DeleteKey("name", "DataBase");
```
```ini
[DataBase]
```

## void DeleteSection(string Секция = null)
Удаляем выбранную секцию

```C#
ini.DeleteSection("DataBase")
```

## bool KeyExists(string Ключ, string Секция = null)
Проверяет, есть ли такой ключ в этой секции.
```C#
if(ini.KeyExists("name", "DataBase"))
{
  MessageBox.Show("База данных: " . ini.ReadINI("DataBase", "name"));
}
```
