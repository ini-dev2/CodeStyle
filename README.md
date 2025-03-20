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
## Организация кода
- Лямбда-выражения для однострочных методов
```csharp
{
    private void Log() => Debug.Log("Log");
}
```
- Когда использовать свойство, когда метод (свойство - качество объекта(жизни), метод - поведение (нанесение урона))
```csharp
public class Player
{
// свойство как качество объекта Player
    private int Health { get; private set; } = 100;
    public bool IsDead => Health <= 0;
}
public class Player
{
    private int Health { get; private set; } = 100;
    public void TakeDamage(int amount)
    {
        Health -= amount;
        if (Health < 0) Health = 0;
    }
}
```
- Вложенные классы ??
- Функции ??
## Архитектура
- Разделение логики на уровни:
   - Presentation Layer - Отвечает за рендер, UI и анимации.
   - Application Layer - Мост между бизнес-логикой и Unity-компонентами. Зависит от MonoBehavior. (GameManager, LevelManager)
   - Domain Layer - Основная игровая логика. Чистый C#, не зависящий от Unity API. ( PlayerData, InvetoryItem )
   - Infrastructure Layer - Отвечает за работу с файлами, сетью, базами данных, аппаратными API. (SaveSystem, LoadSystem, NetworkService)
- Использование DI (Zenject?, VContainer?, ServiceLocator, Bootstrap)
- Соблюдение SOLID (время? - стоит?)
- Паттерны (ситуации, где и как)
- ООП
   - Инкапуслирование данных
```csharp
{
    private int result;
    public int Result => result;  
}

{
    private event Action _onPlayerDie;
    public event Action OnPlayerDie
    {
        add
        {
            if (value is not null)
            {
                //логика
            }
        }
        remove
        {
            //логика
        }
    }
}
```
- Использование абстракций ?? не прямые зависимости, а интерфейсы??, абстрактые классы??
## Структура проекта
-Assets
  -Scenes
  -Scripts
    -Infrastructure
    -Domain 
    -Application
    -Presentation 
  -Prefabs
  -Materials
  -Animations
  -Resources
  -Addressables
