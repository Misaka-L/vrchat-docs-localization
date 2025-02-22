---
title: "触发器"
upstreamCommit: 2d28c6620b23edebd4c291dc4ab7af049ba0758c
---

# 触发器

触发器是 Avatar SDK 所提供的一类交互组件。它们可以用于联动动画器的参数，进而实现各种有趣的交互效果。

不同于 Unity 自带的碰撞器，SDK 提供的触发器从功能上被分为发送端和接收端，它们分别是 `VRCContactSender`、`VRCContactReceiver`。发送端只是为了被检测而存在，而接收端会检测发送端的接触，然后相应地更新 `参数表` 中的数值。

出于性能考虑，触发器的数量受到[模型性能评级](/creators.vrchat.com/avatars/avatar-performance-ranking-system#pc-limits)的限制。通常来说，您可以为单个人物模型添加至多 256 个触发器。

## 发送端：VRCContactSender
 `VRCContactSender` 组件定义了一个空间体积，当它与 `VRCContactReceiver` 接触时，将发送一个触发器信号。
 
![contacts-59b6e82-2022-04-19_11-53-01_Unity.png](/creators.vrchat.com/images/avatars/contacts-59b6e82-2022-04-19_11-53-01_Unity.png)

- `Root Transform` - 拥有该触发器组件的变换。如果为空，则使用此 GameObject 的变换。

## Shape
本部分包含定义触发器发送端形状的设置。
- `Shape Type` - 该 Contact 使用的碰撞形状类型。
- `Radius` - 碰撞点从 `Root Transform` 原点开始延伸的尺寸。
- `Height` - 沿所选轴的胶囊形状高度。

::: info 译者对 `Height` 的补充说明
当且仅当 `Shape Type` 定义为胶囊形状时，此项生效。
:::

`Position` - 从 `Root Transform` 偏移的位置。
`Rotation` - 从 `Root Transform` 偏移的旋转。

## Filtering
本节包含允许您调整和定义此触发器发送端如何与[触发器接收端](/creators.vrchat.com/avatars/avatar-dynamics/contacts#VRCContactReceiver)交互的设置。

- `Collision Tags` - 一个字符串列表，用于指明什么触发器可影响/被影响。要成功发生碰撞，Sender 和 Receiver 都需要至少一对互相匹配的字符串。Collision Tags 区分大小写。

例如，当发送端与默认的头部[触发器接收端](/creators.vrchat.com/avatars/avatar-dynamics/contacts#VRCContactReceiver)或任何带有 `Face` 标签的自定义[触发器接收端](/creators.vrchat.com/avatars/avatar-dynamics/contacts#VRCContactReceiver) (注意大写 F) 接触时，下面的标签将导致发送端发送一个联系信号！
![contacts-de34d55-2022-04-19_11-53-34_NVIDIA_Share.png](/creators.vrchat.com/images/avatars/contacts-de34d55-2022-04-19_11-53-34_NVIDIA_Share.png)

## 标准碰撞器 (Standard Colliders)
“标准碰撞器” 是一组特殊的触发器。它们特别的地方在于，可以作为发送端与其他人的模型产生互动，并且它们的存在不会影响模型的性能评级。

您可以手动定义每个模型上的标准碰撞器，当然，您也可以选择让 Avatar SDK 自动设置它们。若您选择了自动，Avatar SDK 将在模型骨骼层级中的这些位置为您自动绑定它们：

- Head
- Torso
- Hands L/R
- Feet L/R
- Fingers L/R
  - Index
  - Middle
  - Ring
  - Little
  ::: info 译者注
  这些标准碰撞器从上到下分别对应头部，躯干，左右手，左右脚，左右手指 (可单独设置食指，中指，无名指，小指)
  :::

标准碰撞器主要作为触发器发送端，且可与其他玩家模型所带的触发器产生交互。不过，手指和手掌位置的碰撞器额外具备全局[物理骨骼 (PhysBones)](/creators.vrchat.com/avatars/avatar-dynamics/physbones) 碰撞器的功能，可影响其他玩家模型的物理骨骼 (PhysBones)。

## 接收端：VRCContactReceiver
`VRCContactReceiver` 组件定义了一个空间体积，该体积在与 `VRCContactSender` 接触后将接收到一个触发器信号。

![contacts-6f84ac4-2022-04-19_11-57-25_NVIDIA_Share.png](/creators.vrchat.com/images/avatars/contacts-6f84ac4-2022-04-19_11-57-25_NVIDIA_Share.png)

- `Root Transform` - 放置触点的变换。如果为空，则使用此 GameObject 的变换。

本节包含定义 ContactReceiver 形状的设置。
- `Shape Type` - 该触发器使用的碰撞形状类型。
- `Radius` - 碰撞点从 `Root Transform` 原点开始延伸的尺寸。
- `Height` - 沿所选轴的胶囊形状高度

::: info 译者对`Height`的补充说明
当且仅当 `Shape Type` 定义为胶囊形状时，此项生效。
:::

- `Position` - 从 `Root Transform` 偏移的位置。
- `Rotation` - 从 `Root Transform` 偏移的旋转。
- `Collision Tags` - 一个字符串列表，用于指明什么触发器可影响或被影响。要成功发生碰撞，发送端和接收端都需要至少一对互相匹配的字符串。Collision Tags 区分大小写。

## Filtering
本节包含允许您调整和定义触发器接收端端与[触发器发送端](/creators.vrchat.com/avatars/avatar-dynamics/contacts#VRCContactSender)交互方式的设置。

- `Allow Self` - 允许此触发器受自己影响。
- `Allow Others` - 允许此触发器受其他人影响。
- `Local Only` - 限制此触发器仅在本地客户端工作。
- `Collision Tags` - 一个字符串列表，用于指明什么触发器可影响或被影响。要成功发生碰撞，发送端和接收端都需要至少一对互相匹配的字符串。Collision Tags 区分大小写。

## Receiver
本节包含的设置定义了接收端在接收到信号时的操作。

`Receiver Type` 定义了接收到信号时对参数进行设置的行为。

-  `Constant` - 检测到触发时设置恒定数值。检测不到触发时重置。此处最好使用 bool 参数。float 型参数设置为 1.0，bool 型参数设置为 True，Int 型参数设置为 1。
- `OnEnter` -在检测到触发的当前帧下设置数值。下一帧立即重置。此处最好使用 bool 参数。float 型参数设置为 1.0，bool 型参数设置为 True，Int 型参数设置为 1。可选择定义 `Min Velocity`。
- `Proximity`- 提供一个 0.0-1.0 的浮动值，这个值取决于一个触发位置与触发器中心的距离。计算为发送端离接收端的最近点位置。您必须使用 Float。如果检测到多个触发，它会给出最近的一个。

::: tip note
如果想要更精确地量化 Proximity，就需要将发送端的半径调得很小。
:::

- `Parameter` - 动画控制器上更新的参数。该参数无需在网络同步的形象参数列表中定义。根据所使用的接收端类型，该参数可以是 Float 型、Bool 型或 Int 型。
- `Value` - 当检测到碰撞时，参数将更新为此处定义的值。当没有碰撞出现时，参数将重置为零。
- `Min Velocity` - 影响此接收端所需的来自 Sender 的最小运动速度，仅在 OnEnter 类型中有效。
