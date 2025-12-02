# Контекст по запуску примеров TIJ4

- Проект: `C:\Projects\TIJ4\code\TIJ4-code`
- Источник: учебные примеры Thinking in Java 4e.

## Правки
- Добавлен пакет `package access;` во все классы в `examples/access` (Dinner, ChocolateChip, ChocolateChip2, Cake, IceCream, ImportedMyClass, LibTest, Lunch, OrganizedByAccess, Pie, PrintTest, QualifiedMyClass, SingleImport, FullQualification).
- Пакеты подпапок не менялись (`access.dessert`, `access.cookie2`, `access.mypackage`).
- Создан `.vscode/settings.json`:
  ```json
  {
    "java.project.sourcePaths": ["examples"],
    "java.project.outputPath": "out",
    "java.debug.settings.buildBeforeLaunch": "always",
    "java.debug.settings.forceBuildBeforeLaunch": true
  }
  ```
  Это делает `examples` корнем исходников и `out` — корнем классов, плюс всегда пересобирает перед Run.

## Проверка сборки
```powershell
cd C:\Projects\TIJ4\code\TIJ4-code
javac -sourcepath examples -d out examples\access\*.java examples\access\dessert\Cookie.java examples\access\cookie2\Cookie.java examples\access\mypackage\MyClass.java
java -cp out access.Dinner
```
Вывод: `Cookie constructor`.

## Как запускать в VS Code
- Обязательно установлен Java Extension Pack.
- `Ctrl+Shift+P` → `Java: Clean Java Language Server Workspace` после правок.
- Auto Build включён (значок в статус-баре).
- Открыть `examples/access/Dinner.java`, нажать Run над `main` — плагин соберёт в `out` и запустит `access.Dinner`.

## Почему была ошибка `Could not find or load main class access.Dinner`
- После добавления `package access;` старые `.class` не пересобрались, в `out` не было `access/Dinner.class`. Полная пересборка или авто‑build решает проблему.
