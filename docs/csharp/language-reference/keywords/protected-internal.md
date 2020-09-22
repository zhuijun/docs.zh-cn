---
description: protected internal - C# 参考
title: protected internal - C# 参考
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: f22de104154df74f02c048b1209eeac754a03e64
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536792"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="f2695-103">受保护的内部成员（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f2695-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="f2695-104">`protected internal` 关键字组合是一种成员访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="f2695-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="f2695-105">可从当前程序集或派生自包含类的类型访问受保护的内部成员。</span><span class="sxs-lookup"><span data-stu-id="f2695-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="f2695-106">有关 `protected internal` 和其他访问修饰符的比较，请参阅[可访问性级别](accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="f2695-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2695-107">示例</span><span class="sxs-lookup"><span data-stu-id="f2695-107">Example</span></span>

<span data-ttu-id="f2695-108">可从包含程序集内的任何类型访问基类的受保护的内部成员。</span><span class="sxs-lookup"><span data-stu-id="f2695-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="f2695-109">也可在另一程序集中的派生类中访问它，前提是通过派生类类型的变量进行访问。</span><span class="sxs-lookup"><span data-stu-id="f2695-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="f2695-110">以下面的代码段为例：</span><span class="sxs-lookup"><span data-stu-id="f2695-110">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="f2695-111">此示例包含两个文件，即 `Assembly1.cs` 和 `Assembly2.cs`。</span><span class="sxs-lookup"><span data-stu-id="f2695-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="f2695-112">第一个文件包含公共基类 `BaseClass` 和另一个类 `TestAccess`。</span><span class="sxs-lookup"><span data-stu-id="f2695-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="f2695-113">`BaseClass` 拥有受保护的内部成员 `myValue`，由 `TestAccess` 类型访问。</span><span class="sxs-lookup"><span data-stu-id="f2695-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="f2695-114">在第二个文件中，如果尝试通过 `BaseClass` 的实例访问 `myValue` ，会生成错误，但如果尝试通过一个派生类的实例来访问此成员，`DerivedClass` 会成功。</span><span class="sxs-lookup"><span data-stu-id="f2695-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="f2695-115">结构成员不能为 `protected internal`，因为无法继承结构。</span><span class="sxs-lookup"><span data-stu-id="f2695-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f2695-116">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="f2695-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f2695-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2695-117">See also</span></span>

- [<span data-ttu-id="f2695-118">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f2695-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2695-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f2695-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2695-120">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="f2695-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f2695-121">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="f2695-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="f2695-122">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="f2695-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="f2695-123">修饰符</span><span class="sxs-lookup"><span data-stu-id="f2695-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f2695-124">public</span><span class="sxs-lookup"><span data-stu-id="f2695-124">public</span></span>](public.md)
- [<span data-ttu-id="f2695-125">private</span><span class="sxs-lookup"><span data-stu-id="f2695-125">private</span></span>](private.md)
- [<span data-ttu-id="f2695-126">internal</span><span class="sxs-lookup"><span data-stu-id="f2695-126">internal</span></span>](internal.md)
- <span data-ttu-id="f2695-127">[Internal Virtual 关键字的安全问题](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f2695-127">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
