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
private const int _sampleValue;
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
- Классы, интерфейсы, структуры (PascalCase)
```csharp
private class Class
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
