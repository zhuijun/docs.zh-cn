---
title: 示例 COM 类 - C# 编程指南
description: 了解如何在 C# 中将类公开为 COM 对象。 此示例将 .cs 文件中的代码添加到项目中，并设置“注册 COM 互操作”属性。
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 4ea66ba26595c5bae2e579d1cc85c4b0d58616df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303031"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="abbc4-104">COM 类示例（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="abbc4-104">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="abbc4-105">下面是将公开为 COM 对象的类的示例。</span><span class="sxs-lookup"><span data-stu-id="abbc4-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="abbc4-106">在将此代码放置在 .cs 文件中并添加到项目后，将“注册 COM 互操作”属性设置为“True”。</span><span class="sxs-lookup"><span data-stu-id="abbc4-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="abbc4-107">有关详细信息，请参阅[如何：注册 COM 互操作组件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="abbc4-107">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="abbc4-108">对 COM 公开 Visual C# 对象需要声明类接口、事件接口（如有必要）和类本身。</span><span class="sxs-lookup"><span data-stu-id="abbc4-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="abbc4-109">类成员必须遵循这些规则才能显示在 COM 中：</span><span class="sxs-lookup"><span data-stu-id="abbc4-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="abbc4-110">类必须是公开的。</span><span class="sxs-lookup"><span data-stu-id="abbc4-110">The class must be public.</span></span>  
  
- <span data-ttu-id="abbc4-111">属性、方法和事件必须是公开的。</span><span class="sxs-lookup"><span data-stu-id="abbc4-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="abbc4-112">必须在类接口上声明属性和方法。</span><span class="sxs-lookup"><span data-stu-id="abbc4-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="abbc4-113">必须在事件接口中声明事件。</span><span class="sxs-lookup"><span data-stu-id="abbc4-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="abbc4-114">该类中未在这些接口中声明的其他公共成员将对 COM 不可见，但它们对其他 .NET 对象可见。</span><span class="sxs-lookup"><span data-stu-id="abbc4-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="abbc4-115">若要对 COM 公开属性和方法，则必须在类接口上声明这些属性和方法，将它们标记为 `DispId` 属性，并在类中实现它们。</span><span class="sxs-lookup"><span data-stu-id="abbc4-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="abbc4-116">在接口中声明成员的顺序是用于 COM vtable 的顺序。</span><span class="sxs-lookup"><span data-stu-id="abbc4-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="abbc4-117">若要从类中公开事件，则必须在事件接口上声明这些事件并将其标记为 `DispId` 属性。</span><span class="sxs-lookup"><span data-stu-id="abbc4-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="abbc4-118">此类不应实现此接口。</span><span class="sxs-lookup"><span data-stu-id="abbc4-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="abbc4-119">此类实现此类接口；它可以实现多个接口，但第一个实现将为默认类接口。</span><span class="sxs-lookup"><span data-stu-id="abbc4-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="abbc4-120">在此处实现向 COM 公开的方法和属性。</span><span class="sxs-lookup"><span data-stu-id="abbc4-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="abbc4-121">它们必须标记为公共，并且必须匹配类接口中的声明。</span><span class="sxs-lookup"><span data-stu-id="abbc4-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="abbc4-122">此外，在此处声明此类引发的事件。</span><span class="sxs-lookup"><span data-stu-id="abbc4-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="abbc4-123">它们必须标记为公共，并且必须匹配事件接口中的声明。</span><span class="sxs-lookup"><span data-stu-id="abbc4-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abbc4-124">示例</span><span class="sxs-lookup"><span data-stu-id="abbc4-124">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="abbc4-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abbc4-125">See also</span></span>

- [<span data-ttu-id="abbc4-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="abbc4-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="abbc4-127">互操作性</span><span class="sxs-lookup"><span data-stu-id="abbc4-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="abbc4-128">“项目设计器”->“生成”页 (C#)</span><span class="sxs-lookup"><span data-stu-id="abbc4-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
