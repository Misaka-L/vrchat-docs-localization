---
upstreamCommit: 4d76fd612a37de18fd85c39062bade59afffb7cf
---

# 自动化测试

ClientSim 有许多不同的测试来验证程序的行为。大多数测试是集成测试，但也支持单元测试。请查看 Unity 的 TestRunner 以查看所有测试。当将 ClientSim 作为包导入时，可以通过在 `“dependencies” :{}` 部分后面的项目包清单中添加以下行来启用测试：
```json
"testables": [
  "com.unity.inputsystem",
  "com.vrchat.clientsim"
]
```

一旦添加，Unity 将导入测试，您将在 Test Runner 窗口中看到它们。

![Test Runner](/clientsim.docs.vrchat.com/images/test-runner.png)

## 单元测试

ClientSim 有一些单元测试，可以验证 Unity Playmode 之外的项目。可以重构更多项目，以便从 MonoBehaviours 中分离出来，使其更适合单元测试。

## 集成测试

ClientSim 现在有一个完整的集成测试框架，可以测试包含的大多数功能。该框架允许发送输入事件并监听 ClientSim 事件，以验证是否发生了适当的操作。此框架也可用于验证特定行为的世界，允许用户创建自己的测试。

### 测试设置

由于 ClientSim 使用 InitializeOnLoad 启动的方式，测试需要修改 Unity 编辑器设置以正确验证行为。在测试环境中，InitializeOnLoad 在播放模式开始之前发生。默认的 Unity 设置在进入播放模式时启用了 Domain Reloading。这意味着在切换到播放模式时，所有变量数据都会被清除。为了解决这个问题，所有 ClientSim 测试必须在禁用 Domain Reloading 的情况下运行。这对于任何从两个测试夹具基类 (ClientSimTestBase 和 ClientSimWorldTestBase) 派生的测试都是自动处理的。

### ClientSimTestHelper

两个集成测试夹具都带有帮助验证特定行为的方法。

* **ClientSimTestHelpers** - 这个类包含了一些有用的方法，以及监听不同的 ClientSim 事件来验证是否发生了操作。

* **ClientSimTestInput** - 这个类允许用户设置任何基于桌面的输入事件的值。

### ClientSimTestBase

从这个类派生的测试夹具用于测试单个预制件，而不是测试整个世界。在测试开始时，ClientSim 的默认行为被禁用。可以加载一个世界或生成一个预制件，但必须手动启动 ClientSim。根据顺序，行为将与通过播放模式正常启动 ClientSim 有所不同。

1. 如果在启动 ClientSim 之前加载了一个世界或预制件，那么任何 VRC SDK 组件都不会链接到 ClientSim，并且会像 ClientSim 被禁用一样启动。在这种情况下，玩家的生成点将按预期工作，因为需要 VRC_SceneDescriptor 来启动 ClientSim 并生成玩家。
2. 如果在启动 ClientSim 之后加载了一个世界或预制件，那么所有 VRC SDK 组件将以正常播放模式中的 ClientSim 行为进行初始化。但在这种情况下，玩家已经生成，并且不会被放置在加载的世界的生成点。

大多数 ClientSim 测试都是以这种格式编写的。加载了一个包含启动 ClientSim 所需的最少组件的场景，启动 ClientSim，然后从那里进行测试，如调用适当的 SDK API 或生成预制件，同时模拟输入事件。

以下是集成测试的列表：

#### 初始化测试
* 测试 ClientSim 在不同设置和初始场景对象下的启动行为。

#### 辅助测试
* 测试各种 ClientSim SDK 辅助类的行为。AudioSpatializer，AVProVideoPlayer，ObjectPool，ObjectSync，没有程序的 Udon 组件，UIShape。

#### 交互测试
* 测试交互系统处理可交互对象的能力。请注意，由于 Udon 需要外部引用并且经常编译，因此无法在包中正确包含，此测试使用模拟可交互对象脚本。

#### 拾取测试
* 测试交互系统、玩家手和输入在不同拾取情况下的行为。

#### 玩家 API 测试
* 测试所有与 VRCPlayerApi 相关的公开方法的行为。

#### 玩家控制器测试
* 测试玩家的移动设置。

#### 站点测试
* 测试使用站点和预期的站点行为。

#### UI 测试
* 使用 VRC_UIShape 组件测试与 Unity UI 的交互。

### ClientSimWorldTestBase

从这个类派生的测试夹具用于测试完整的世界，并验证给定世界的 ClientSim 的启动。测试需要在测试的设置阶段加载给定的世界，然后 ClientSim 将正常启动，就像在测试环境外通过进入播放模式一样。由于 ClientSim 正常启动，因此一次只能运行一个测试，因为所有测试只启动一次播放模式。如果同时运行多个测试，它们将立即失败，并显示警告，只能一次运行一个测试。

默认提供了三个世界测试：
#### 没有世界描述符
* 如果加载了没有世界描述符的场景，测试 ClientSim 将无法启动。

#### 两个玩家
* 在基本世界中正常启动 ClientSim，生成一个远程玩家，并验证两个玩家的所有数据。

#### WorldTestExample
* 这是一个示例测试，展示了用户为他们的世界编写测试的情况。测试包含在 ClientSim 包的样本中，必须导入。测试展示了如何验证一个简单的 “谜题” 世界。
