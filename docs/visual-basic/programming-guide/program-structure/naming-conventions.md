---
title: 命名约定
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: b25d246bd31147b7a9ba2c72214926fdb5ca8895
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072140"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="27902-102">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="27902-102">Visual Basic Naming Conventions</span></span>

<span data-ttu-id="27902-103">在 Visual Basic 应用程序中为某个元素命名时，该名称的第一个字符必须是字母字符或下划线。</span><span class="sxs-lookup"><span data-stu-id="27902-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="27902-104">但请注意，以下划线开头的名称不符合 [语言独立性和与语言无关的组件](../../../standard/language-independence-and-language-independent-components.md) (CLS) 。</span><span class="sxs-lookup"><span data-stu-id="27902-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="27902-105">以下建议适用于命名。</span><span class="sxs-lookup"><span data-stu-id="27902-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="27902-106">以大写字母开头每个单独的单词，如和中所示 `FindLastRecord` `RedrawMyForm` 。</span><span class="sxs-lookup"><span data-stu-id="27902-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="27902-107">使用谓词作为函数和方法名称的开头，如或中所示 `InitNameArray` `CloseDialog` 。</span><span class="sxs-lookup"><span data-stu-id="27902-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="27902-108">以名词开头的类、结构、模块和属性名称，如 `EmployeeName` 或 `CarAccessory` 。</span><span class="sxs-lookup"><span data-stu-id="27902-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="27902-109">以前缀 "I" 开始接口名称，后跟名词或名词短语，如 `IComponent` ，或带有描述接口行为的形容词（如） `IPersistable` 。</span><span class="sxs-lookup"><span data-stu-id="27902-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="27902-110">不要使用下划线，并慎用缩写，因为缩写会导致混淆。</span><span class="sxs-lookup"><span data-stu-id="27902-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="27902-111">用名词开始事件处理程序名称，该名称描述后跟 "" 后缀的事件类型 `EventHandler` ，如 " `MouseEventHandler` "。</span><span class="sxs-lookup"><span data-stu-id="27902-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="27902-112">在事件参数类的名称中，包含 " `EventArgs` " 后缀。</span><span class="sxs-lookup"><span data-stu-id="27902-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="27902-113">如果某个事件具有 "before" 或 "after" 这一概念，则使用现在时或过去时形式的后缀，如 " `ControlAdd` " 或 " `ControlAdded` "。</span><span class="sxs-lookup"><span data-stu-id="27902-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="27902-114">对于长或频繁使用的术语，请使用缩写使名称长度合理，例如 "HTML"，而不是 "超文本标记语言"。</span><span class="sxs-lookup"><span data-stu-id="27902-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="27902-115">通常，超过32个字符的变量名称在设置为低分辨率的监视器上难以读取。</span><span class="sxs-lookup"><span data-stu-id="27902-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="27902-116">此外，请确保缩写在整个应用程序中保持一致。</span><span class="sxs-lookup"><span data-stu-id="27902-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="27902-117">在 "HTML" 和 "超文本标记语言" 之间随机切换项目可能会导致混淆。</span><span class="sxs-lookup"><span data-stu-id="27902-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="27902-118">避免使用与外部作用域中的名称相同的内部作用域中的名称。</span><span class="sxs-lookup"><span data-stu-id="27902-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="27902-119">如果访问错误的变量，则会导致错误。</span><span class="sxs-lookup"><span data-stu-id="27902-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="27902-120">如果变量与同名的关键字之间发生冲突，则必须通过在其前面加上适当的类型库来标识关键字。</span><span class="sxs-lookup"><span data-stu-id="27902-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="27902-121">例如，如果你有一个名为的变量 `Date` ，则只能通过调用来使用内部 `Date` 函数 <xref:System.DateTime.Date%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="27902-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27902-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="27902-122">See also</span></span>

- [<span data-ttu-id="27902-123">代码中用作元素名称的关键字</span><span class="sxs-lookup"><span data-stu-id="27902-123">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="27902-124">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="27902-124">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="27902-125">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="27902-125">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="27902-126">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="27902-126">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="27902-127">Visual Basic 语言参考</span><span class="sxs-lookup"><span data-stu-id="27902-127">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
