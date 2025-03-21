# CodeStyle
## Правила ведения

## Среда разработки
- Настроить ide (sonar)
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
- Абстрактные классы
```csharp
private class BaseHuman
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
- Порядок оформления класса ?? ( приватные, константы, инъекции и тд )
  Каждый блок - отдельный регион
    - Константы
    - События / Делегаты
    - private, [ser] - группируем по логике / свойства
    - Конструктор( если монобех - public void Init(..))
    - Monobehavior - жизн. цикл
    - public method
    - private method
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
- Вложенные классы ?? --
- Функции ?? --
- Автосвойства ?? +-
- GetComponent ??
- Корутины ?? async/await, task ??
- Тернарные операции ?? int i = x < 0 ? 0 : 1; ++
- var или явные типы ?? основа - явные, опционально - var
- типизация ?? ++
- Использование атрибутов (RequerComponent, CustomEditor, свои атрибуты) ??
- События в OnEnabled += , в OnDisable -= ++
## Архитектура
- Разделение логики на уровни:
   - Presentation Layer - Отвечает за рендер, UI и анимации.
   - Application Layer - Мост между бизнес-логикой и Unity-компонентами. Зависит от MonoBehavior. (GameManager, LevelManager)
   - Domain Layer - Основная игровая логика. Чистый C#, не зависящий от Unity API. ( PlayerData, InvetoryItem )
   - Infrastructure Layer - Отвечает за работу с файлами, сетью, базами данных, аппаратными API. (SaveSystem, LoadSystem, NetworkService)
- Использование DI (Zenject?, VContainer?, ServiceLocator, Bootstrap) ++
- Соблюдение SOLID (время? - стоит?) +-
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
- Использование абстракций ?? не прямые зависимости, а интерфейсы??, абстрактые классы?? уклон на интерфейсы
## Структура проекта
- Assets
  - Scenes
  - Scripts
    - Infrastructure
    - Domain 
    - Application
    - Presentation 
  - Prefabs
  - Materials
  - Animations
  - Resources
  - Addressables
