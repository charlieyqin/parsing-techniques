# 3.3 非确定型自动机

上述两个例子都表征了两个组成部分：一个可以进行替换和记录解析树的机器，以及一个决定机器该做那些动作的控制机器。这个机器相对简单，因为其替换仅允许语法所允许的那些，但是控制机制可以是任意复杂的，并且可能包含语法的广泛的知识。

这种结构可以在所有解析方法中看出：总是有一个替换和保持记录的机器，以及一个指导性的控制机器：

![图1](../../img/3.3_1.png)

替换的机器被称为*非确定型自动机*或NDA；被称为“非确定型”是因为经常有几个可能的行动，并且特殊选择没有预先决定，而“自动”是因为会自动执行应激的操作。它管理三个组件：输入字符串（实际上是它的副本），部分解析树和一些内部的管理工作。NDA的每一个行动都转换来自输入字符串的一些信息到部分解析树中，通过管理工作。三个组件可能在过程中进行修改：

![图2](../../img/3.3_2.png)

NDA的强大力量，以及它实用性的主要来源，就是它可以被轻松的构建，以便它能只做“正确”的行为，也就是说，保持系统部分处理输入，内部控制和部分解析树一致的行为。这有可能导致我们按照选择的任何方式移动NDA的结局：它可能在圈中运动，甚至它可能困住，但是如果它能给我们一个答案，以一个完成的解析树的形式，那这个答案就将是正确的。NDA可以做所有正确的行为也是有必要的，以便它能生成所有解析，如果控制机制足够聪明能指导NDA。NDA的这个属性也很容易安排。

NDA固有的正确性给控制机制带来了极大的自由，简称“控制”。它可能是幼稚的又或成熟的，它可能是麻烦的又或是有效的，它甚至可能是错的，但它绝不可能会使NDA生成一个不正确的解析；而这是一个令人欣慰的想法。然而，如果它是错误的，那可能会是NDA错失一个正确的鸡西，导致无限循环，或在不应该的地方被卡住。