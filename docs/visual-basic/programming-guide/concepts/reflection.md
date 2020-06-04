---
title: 反射
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 43c05a0b3bbfc3dfc304b1aed3f689625a40229a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413175"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="f0a09-102">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0a09-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="f0a09-103">反射提供描述程序集、模块和类型的对象（<xref:System.Type> 类型）。</span><span class="sxs-lookup"><span data-stu-id="f0a09-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="f0a09-104">可以使用反射动态地创建类型的实例，将类型绑定到现有对象，或从现有对象中获取类型，然后调用其方法或访问器字段和属性。</span><span class="sxs-lookup"><span data-stu-id="f0a09-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="f0a09-105">如果代码中使用了特性，可以利用反射来访问它们。</span><span class="sxs-lookup"><span data-stu-id="f0a09-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="f0a09-106">有关更多信息，请参阅[特性](../../../standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f0a09-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="f0a09-107">下面一个简单的反射示例，使用静态方法 `GetType`被 `Object` 基类的所有类型继承）以获取变量类型：</span><span class="sxs-lookup"><span data-stu-id="f0a09-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="f0a09-108">输出为：</span><span class="sxs-lookup"><span data-stu-id="f0a09-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="f0a09-109">下面的示例使用反射获取已加载的程序集的完整名称。</span><span class="sxs-lookup"><span data-stu-id="f0a09-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="f0a09-110">输出为：</span><span class="sxs-lookup"><span data-stu-id="f0a09-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="f0a09-111">反射概述</span><span class="sxs-lookup"><span data-stu-id="f0a09-111">Reflection Overview</span></span>  
 <span data-ttu-id="f0a09-112">反射在以下情况下很有用：</span><span class="sxs-lookup"><span data-stu-id="f0a09-112">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="f0a09-113">需要访问程序元数据中的特性时。</span><span class="sxs-lookup"><span data-stu-id="f0a09-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="f0a09-114">有关详细信息，请参阅[检索存储在特性中的信息](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="f0a09-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="f0a09-115">检查和实例化程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="f0a09-115">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="f0a09-116">在运行时构建新类型。</span><span class="sxs-lookup"><span data-stu-id="f0a09-116">For building new types at runtime.</span></span> <span data-ttu-id="f0a09-117">使用 <xref:System.Reflection.Emit> 中的类。</span><span class="sxs-lookup"><span data-stu-id="f0a09-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="f0a09-118">执行后期绑定，访问在运行时创建的类型上的方法。</span><span class="sxs-lookup"><span data-stu-id="f0a09-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="f0a09-119">请参阅主题 “[动态加载和使用类型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)”。</span><span class="sxs-lookup"><span data-stu-id="f0a09-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0a09-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="f0a09-120">Related Sections</span></span>  
 <span data-ttu-id="f0a09-121">参考信息：</span><span class="sxs-lookup"><span data-stu-id="f0a09-121">For more information:</span></span>  
  
- [<span data-ttu-id="f0a09-122">反射</span><span class="sxs-lookup"><span data-stu-id="f0a09-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="f0a09-123">查看类型信息</span><span class="sxs-lookup"><span data-stu-id="f0a09-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="f0a09-124">反射类型和泛型类型</span><span class="sxs-lookup"><span data-stu-id="f0a09-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="f0a09-125">检索存储在特性中的信息</span><span class="sxs-lookup"><span data-stu-id="f0a09-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="f0a09-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0a09-126">See also</span></span>

- [<span data-ttu-id="f0a09-127">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="f0a09-127">Visual Basic Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f0a09-128">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="f0a09-128">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
