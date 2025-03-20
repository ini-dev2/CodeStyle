# CodeStyle
## Именования
- Переменные (camelCase)
```csharp
private int sampleValue;
```
- Константы (UPPER_CASE)
```csharp
private const int SAMPLE_VALUE;
```
- Приватные, инъекции (_camelCase)
```csharp
private int _sampleValue;
```
- События
```csharp
private event Action _onPlayerDie;
```
- "Свойства"- события
```csharp
public event Action OnPlayerDie
{
    add
    {
        //логика
    }
    remove
    {
        //логика
    }
}
```
- Методы (PascalCase)
```csharp
private void SampleMethod()
{
    //логика
}
```
- Классы, структуры (PascalCase)
```csharp
private class Class
{
    //логика
}
```
- Интерфейсы
```csharp
private interface IInterface
{
    //логика
}
```
- Перечисления (PascalCase + Enums)
```csharp
private enum SampleEnums
{
    //логика
}
```
## Оформление
- Убирать лишнии пробелы
- Удалять пустые строки
- Удалять не используемые namespace
- Закрывать конструкции {}, даже при одной строчке
```csharp
if (x > 0)
{
    //логика
}
```
- Пустые строки между методами
```csharp
private void Method1()
{
    //логика
}

private void Method2()
{
    //логика
}
```
