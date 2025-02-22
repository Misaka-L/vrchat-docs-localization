# VRChat 安全和信誉系统

::: warning 🚧待处理的更新
此部分正在计划更新！VRChat 名牌和安全系统界面最近发生了变化，因此例图可能不准确。但是功能保持不变。
:::

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-1.png)

VRChat 安全和信誉系统是目前实施的 VRChat 信誉系统的新扩展。它旨在保护玩家免受捣蛋鬼们的全屏特效着色器、烦人音效与糟糕的麦克风收音、视觉干扰或恶意粒子特效，或者其他用于搞毁您在 VRChat 中体验的种种手段。

该系统的设计目的在于**将控制权交还给玩家**，允许玩家决定何时何地、以何种方式看到各种模型功能，其中不乏一些使用不当会干扰他人或代表恶意的功能。

请务必注意，此系统目前处于 **BETA** 阶段，内容可能会随版本更新或补丁而更改。

安全和信誉系统的设计使您即使保持默认设置也可以确保您不会被恶意模型攻击到。恶意玩家的模型的各种功能会被自动屏蔽，以便让您在 VRChat 中获得更加良好的体验。

该系统有两个重要组成部分，即信誉系统和安全系统。接下来的部分将更加详细地介绍这些功能。

## 信誉系统

信誉系统已在 VRChat 中实现！它决定玩家何时才能上传内容 - 您可能听说过我们之前称呼的 “内容门槛”。然而该系统不仅仅可以确定您是否能够上传内容 —— 它还通过玩家行为来决定 “信任程度”，这是许多变量的总和。我们可以轻松调整其算法，因此我们可以随着时间的推移对其进行调整。

### 信誉级别

玩家的信任度转化为我们称之为 “信誉级别” 的东西，它衡量玩家在 VRChat 上花费了多少时间，他们贡献了多少内容，他们结交了多少朋友，以及许多其他因素。这些级别如下：

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-2.png)

您只需玩 VRChat 即可获得这些级别 - 随着您探索世界，结交朋友和创建内容，您将获得更多的信任，这决定了您的信誉级别。

当您打开快捷菜单时，等级会显示在名牌上。其他时刻，它们会被折叠并在正常游玩时不可见。

**朋友**是一个特殊的信誉级别。您添加为的好友的用户将拥有普通防护级别中所有的模型功能，您也可以像自定义任何其他信誉级别一样自定义它们。

“**游客**” 与 “**新玩家**” 之间的过渡是一个特殊的过程 - 在游客成为新玩家后，在使用 VRChat 帐户期间，他们便可以将内容上传到 VRChat。玩家在升级到此级别时会收到通知，并将被引导到 VRChat 文档页面以帮助玩家入门创建内容。

在将来的版本中，玩家在变换信誉级别时将收到通知。

“**知名玩家**” 及以上级别的所有级别也可以关闭名牌上的级别显示。您可以选择将自己的名牌显示为 “玩家”，这会将其名牌转换为玩家颜色，并且还**会相应更改安全系统对待他们模型的方式以匹配玩家模板**。这适用于出于任何原因不希望炫耀其更高级别的玩家。

默认情况下，**知名**和**可信**玩家将显示其级别。使用级别切换会将您恢复为**玩家**。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-3.png)

此外，还存在一个名为 “**劣迹玩家**” 的特殊级别。这些玩家给其他玩家带来了不少的困扰，当您打开快捷菜单时，他们的名牌上方会有一个标识。大多数时候，这些玩家的模型将被完全屏蔽。您很可能不会经常看到这些玩家 - 而这显而易见是一件喜事！

最后，游戏中还有着 “**VRChat 团队**” 级别，只有 VRChat 团队成员才拥有。当 VRChat 团队成员打开 “DEV” 标签时，您可以选中他们并在快捷菜单中查看到标签。如果您怀疑带有 “DEV” 标签的玩家是否确实在 VRChat 团队中，只需打开快捷菜单，选中他们，然后查看他们的信誉级别即可。如果模型缩略图下没有显示 “VRChat Team”，则该玩家并不是 VRChat 团队的成员，并且可能试图诈骗玩家。您可随时截取屏幕截图并将这位玩家报告给审核团队！

如果 VRChat 团队成员没有打开 “DEV” 标签，他们将会被显示为一般玩家。

### 安全系统有什么用？

“**安全**” 是一个新的菜单选项卡，它允许您配置如何与各个级别的玩家相处，并在 VRChat 中以此为规则为您呈现内容。这会影响玩家在 VRChat 中的许多方面：

- **语音** — 将玩家的麦克风静音或取消静音 (语音聊天)。
- **模型** — 隐藏或显示玩家的模型以及所有模型功能。当模型被隐藏时，它会显示一个机器人占位模型。
- **玩家图标** — 控制一定信誉级别的玩家自定义图标的可见性。当此级别玩家的图标被隐藏时，它会被覆盖一层马赛克效果。
- **模型音频** — 启用或禁用来自玩家模型本身 (而不是麦克风) 的声音效果。
- **动画** — 启用或禁用玩家模型上的自定义动画
- **着色器** — 禁用后，玩家模型上的所有着色器都将转换为标准着色器。着色器屏蔽系统背后的技术细节在我们的[着色器屏蔽系统](/creators.vrchat.com/avatars/shader-fallback-system.md)文档页面中有详细说明。
- **粒子和光源** — 启用或禁用玩家模型上的粒子系统以及任何光源。这也会阻止线渲染器和轨迹渲染器组件。
每个级别都有自己独特的设置预设。为了说明这一点，以下是安全菜单的屏幕截图：

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-4.png)

此菜单中有**四个主要元素**需要注意。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-5.png)

顶部的一排叫 “**防护强度**”，这是我们开发的安全系统的预设设置。这些预设应该可以满足大部分需求 —— 但是，您也可以在 “个性化” 预设中完全自定义它们，这是一种特殊的模式，您可以在其中创建适合自己的设置。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-6.png)

中间是您选择的**防护强度**的**详细设置**。它们涵盖了安全系统的每个元素，如果您选择个性化强度，则可以根据需要自由切换它们。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-7.png)

底部是**所有信誉级别的列表**。在您选择了某一个防护强度后，您可以选择每个级别，看看该级别的模型功能是如何被安全系统配置的。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-8.png)

安全模式下方**蓝色区域**内的文本会随着您选择不同的模式而变化。**底部的文本**也会随着您浏览菜单而更改，并有助于提示您选中的 UI 元素。

完成此设置后关闭菜单。这些设置将会被应用，您将看到这些设置对您周围的玩家模型即刻生效。

我们已经调整好了系统预设，以便大多数玩家可以将系统保留为 “正常”。大多数玩家不必执行任何操作，安全系统将正常工作。如果您希望**根据自己的喜好自定义防护强度**，您可以通过**个性化防护强度**自由安排。

您可以通过单击菜单右上角的 “**重置自定义设置**” 来**重置自己的自定义设置**。

最后，您可能会注意到系统中 “安全模式” 的设置已消失。那是因为它们已被吸收到安全系统中。按下安全模式的按键 (桌面上的 Shift+Esc，VR 中的两个触发器 + 两个菜单按钮) 会将您的防护级别更改为个性化，并关闭所有级别的所有设置 (除了好友的语音)。此行为目前会擦除您的自定义设置，因此我们计划在未来的更新中实施专用的 “安全” 防护强度。

### 隐藏或显示特定玩家的模型

您可能会遇到一些尽管有着较高信任等级但在使用着您不愿意看到的模型的玩家。您可以**选择该玩家，然后在其社交面板中选择 “隐藏模型”**。这将隐藏该玩家的模型并禁用除语音以外的所有功能。您只需再次单击该按钮即可重新启用玩家的模型和功能，该按钮被标记为 “显示模型”。

如果您想将显示模型的控制权返还给安全系统，只需单击 “跟随安全设置”。

**如有必要，您可以禁用整个系统。**选择 “无” 防护强度将显示每个级别的几乎所有功能，或者创建一个个性化防护强度，其中包含所有级别的所有功能。但是，我们不建议使用此设置，除非您信任目前房间的每个人。这并不会影响 Nuisance 玩家继续被屏蔽 —— 除非您明确取消隐藏它们，否则他们将始终隐藏所有内容。

**您可以通过两种方式对某位玩家覆盖这些预设。**第一种方法是选择一个被当前安全设置隐藏其模型或功能的玩家，找到 “显示模型”，然后单击它。这将显示模型和所有模型功能，无论您当前处于什么安全模式。“隐藏模型” 的作用恰恰相反——无论您在什么安全模式下，该玩家的模型都会被隐藏。选择 “跟随安全设置”，让您使用的安全模式管理该玩家的模型可见性。

第二种方式是直接交朋友！**好友在普通防护强度中没有隐藏任何功能。**我们会假设您完全信任您的朋友们。因此，他们的模型功能将在预设防护强度中完全开启。如果出于某种原因，您想隐藏朋友的模型，您仍然可以使用 “隐藏模型” 按钮进行操作。

## 安全模式

根据您使用的[控制器](/docs.vrchat.com/docs/controls)，有一个快捷方式可以立即禁用您周围所有玩家的所有功能。这被称为 “**安全模式**”。

在 VR 设备上，同时扣下两个扳机键 (Trigger) 并按下两个菜单按钮将会启用此模式。在 PC 上，同时按下 Shift 和 Esc 将启用此模式。

启用后，安全系统将被设置为个性化模式，并关闭所有在场玩家的模型功能。文本将出现在屏幕中间，解释刚刚发生的事情。此操作将直接覆盖您的自定义设置。所有玩家的模型都将被隐藏，非好友玩家的所有语音都将被禁用。

要想关闭安全模式，请将安全系统设置回您使用的上一个模式。如果您使用的是个性化模式，则需要手动将设置重置回安全模式前的状态。

## 快捷菜单的 “扫描模式”

当您打开快捷菜单时，您将能够看到有关玩家名牌的更多信息，以及查看有关玩家的信息。它充当 “扫描仪”，在快捷菜单打开时提供更多信息。如果您指向玩家，您将获得此玩家的基本信息。单击玩家将显示更多详细信息。这将显示他们的模型缩略图，他们的名字，他们的信誉级别以及其他信息。

### 与玩家交互

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-9.png)

正如您在左上角看到的，当您使用扫描模式指向玩家时，面板将显示玩家的模型封面和名称。他们的信誉级别显示在他们模型缩略图的下方，并且缩略图会以适当的颜色突出显示。在右侧，您可以看到他们的当前状态。状态下方的文本框是一个 “小提示”，它将根据您指向的内容为您提供有用的信息。

选中玩家会弹出更详细的社交菜单。

![img](/docs.vrchat.com/images/vrchat-safety-and-trust-system-10.png)

使用此菜单还可以向玩家发送好友请求，打开和关闭其语音，以及查看玩家的详细信息 (这将显示该玩家的完整社交菜单)。单击 “屏蔽”/“取消屏蔽” 按钮将切换玩家的屏蔽状态。

单击顶部的 “上一个” 和 “下一个”，您可以滚动浏览房间中的所有玩家。这对于您了解您对玩家做了何种设置、您静音了谁、以及您的朋友是谁等非常有用。

“警告” 和 “踢出” 是当您是房主时可用的按钮 - 它允许您根据您的所需调整房间人员。“返回” 将带您回到上一个菜单页面，而这大概率会是快捷菜单。

### 隐藏和显示模型

在社交快捷菜单中，单击 “跟随安全设置” 将允许您选择安全模式来确定如何显示该玩家的模型。选择 “显示模型” 或 “隐藏模型” 将覆盖您当前的安全模式设置，并显示/隐藏模型和所有功能。

点击 “显示模型” 是覆盖单个玩家防护强度的最简单方式！

### 名牌处的显示信息

在大多数时刻，安全和信誉系统不会干涉到您的体验。玩家的信誉级别仅在您打开快捷菜单时可见。

名牌左上角会显示该玩家的信誉级别。这同样仅在您打开快捷菜单时显示。

## 信誉系统如何运作？

信誉系统的内部工作原理不宜透露，以此阻止玩家有意滥用这个机制进行恶意行为。无论如何，提高信誉级别最好的方法就是玩 VRChat —— 花时间探索、结交朋友和创作内容 (一旦您获得了创作许可) 都可以帮助您提高您的信誉级别，并会展示您模型的更多功能。

我们想指出有这么几件事不会提高您的信誉级别：

- 在房间内傻站着或者挂机 (AFKing)。
- 上传大量粗糙劣质的内容。
- 一下子加一大堆的好友。

## 我该如何保护自己免受恶意玩家的侵害？

我们构建了一个经久耐用的系统，它能够检测和缓解对玩家声誉的攻击。虽然我们无法分享缓解这些类型攻击的确切细节，但我们都做好了准备，并且可以轻松调整参数以适应我们没有预见到的潜在问题。我们已经为这些类型的问题做好了准备，并有能力快速适应不断出现的问题。
