
PlantUML 使用指南
====================

PlantUML 是一种简单的开源工具，可以通过简洁的文本描述生成 UML 图。以下是如何使用 PlantUML 描述代码、具体的标识符号含义以及时序图中的注意点。

## 1. 基础语法
PlantUML 使用 @startuml 和 @enduml 来标记 UML 图的开始和结束。所有的描述代码都需要在这两个标签之间书写。例如：

```
@startuml
Alice -> Bob: Hello
@enduml
```

这将生成一个简单的时序图，其中 Alice 向 Bob 发送 "Hello" 消息。

## 2. 不同的标识符号

PlantUML 支持多种图表类型和符号，下面是一些常见的符号及其含义：

### 2.1 类图（Class Diagram）
- `class`：定义类，例如 `class User`。
- 继承关系：用 `-->` 表示，例如 `User --> Person`。
- 接口：用 `interface` 关键字表示，例如 `interface Serializable`。

### 2.2 时序图（Sequence Diagram）
- `->`：表示同步消息，例如 `Alice -> Bob: Hello`。
- `-->`：表示异步消息，例如 `Alice --> Bob: Async Hello`。
- `-->`：返回消息，例如 `Bob --> Alice: OK`。
- `:`：消息文本，例如 `Alice -> Bob: Text`。
- `alt`：表示条件逻辑，例如：
    ```
    alt 成功
        Alice -> Bob: Success
    else 失败
        Alice -> Bob: Failure
    end
    ```

### 2.3 活动图（Activity Diagram）
- `( )`：表示开始点和结束点，例如：
    ```
    @startuml
    (*) --> "Start"
    --> "End"
    @enduml
    ```

### 2.4 用例图（Use Case Diagram）
- `actor`：表示一个参与者，例如 `actor User`。
- `usecase`：表示用例，例如 `usecase "Login" as U1`。

### 2.5 组件图（Component Diagram）
- `component`：定义组件，例如 `component Database`。
- 组件之间的连接可以使用 `--` 或 `-->` 来表示，例如：
    ```
    component Backend
    component Database
    Backend --> Database
    ```

## 3. 时序图的注意点
- 时序图中的参与者顺序会影响生成图表的布局，确保参与者按正确的顺序排列。
- 可以用 `participant` 关键字提前声明参与者顺序，例如：
    ```
    participant Alice
    participant Bob
    Alice -> Bob: Hello
    ```
- 使用 `activate` 和 `deactivate` 可以表示对象的活动状态，例如：
    ```
    Alice -> Bob: Hello
    activate Bob
    Bob -> Alice: Hi
    deactivate Bob
    ```
- `alt`、`opt`、`loop` 等关键字可以用于控制流程的不同分支和循环。

## 4. 其他高级特性
- PlantUML 支持定义包结构，使用 `package` 关键字将相关类或组件归组：
    ```
    package "User Management" {
        class User
        class Admin
        User --> Admin
    }
    ```
- 你可以通过定义皮肤参数（skinparam）来自定义图表的样式，例如：
    ```
    skinparam class {
        BackgroundColor Yellow
        ArrowColor Blue
    }
    ```

## 5. 如何在实际项目中使用
在实际项目中，PlantUML 的描述代码通常直接嵌入到文档或代码注释中，方便生成 UML 图并更新文档。你可以使用 PlantUML 的插件集成到 IDE，如 IntelliJ、VS Code 等，或者使用在线生成工具，如 PlantUML 在线编辑器。

---

以上就是 PlantUML 的基本使用方法与一些常见的示例。你可以根据项目需求扩展更多功能。
