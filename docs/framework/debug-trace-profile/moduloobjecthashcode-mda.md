---
title: moduloObjectHashcode MDA
description: 查看 moduloObjectHashcode 托管调试助手（MDA），这会更改对象类，以获取 GetHashCode 方法结果的余数。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052060"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="c9b7e-103">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="c9b7e-103">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="c9b7e-104">`moduloObjectHashcode` 托管调试助手 (MDA) 更改 <xref:System.Object> 类的行为，以便对 <xref:System.Object.GetHashCode%2A> 方法返回的哈希代码执行取模运算。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c9b7e-105">此 MDA 的模数默认为 1，这将导致 <xref:System.Object.GetHashCode%2A> 对所有对象都返回 0。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c9b7e-106">症状</span><span class="sxs-lookup"><span data-stu-id="c9b7e-106">Symptoms</span></span>  
 <span data-ttu-id="c9b7e-107">在迁移到公共语言运行时 (CLR) 的新版本后，程序将不再正确执行：</span><span class="sxs-lookup"><span data-stu-id="c9b7e-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="c9b7e-108">程序从 <xref:System.Collections.Hashtable> 获得错误的对象。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="c9b7e-109"><xref:System.Collections.Hashtable> 中的枚举顺序发生了一项变化，导致程序中断。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="c9b7e-110">以前相等的两个对象不再相等。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="c9b7e-111">以前不相等的两个对象现在相等。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c9b7e-112">原因</span><span class="sxs-lookup"><span data-stu-id="c9b7e-112">Cause</span></span>  
 <span data-ttu-id="c9b7e-113">由于在 <xref:System.Collections.Hashtable> 中的键的类上，<xref:System.Object.Equals%2A> 方法实现通过比较 <xref:System.Object.GetHashCode%2A> 方法调用的结果测试对象是否相等，因此程序可能从 <xref:System.Collections.Hashtable> 中得到错误的对象。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="c9b7e-114">不应该使用哈希代码测试对象是否相等，因为即使两个对象各自的字段具有不同的值，它们也可能具有相同的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="c9b7e-115">虽然在实践中很罕见，但的确可能会发生这些哈希代码冲突。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="c9b7e-116">这对 <xref:System.Collections.Hashtable> 查找的影响是两个不相等的键似乎相等，并从 <xref:System.Collections.Hashtable> 返回错误的对象。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="c9b7e-117">出于性能的考虑，<xref:System.Object.GetHashCode%2A> 的实现在运行时的两个版本之间可能改变，因此在一个版本中可能不会出现的冲突可能会在随后的版本中出现。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="c9b7e-118">启用此 MDA 测试代码在哈希代码冲突时是否有 bug。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="c9b7e-119">启用后，此 MDA 将导致 <xref:System.Object.GetHashCode%2A> 方法返回 0，造成所有哈希代码冲突。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="c9b7e-120">启用此 MDA 对程序的唯一影响是程序将会运行得更慢。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="c9b7e-121">如果用于计算键的哈希代码的算法改变，则 <xref:System.Collections.Hashtable> 中的枚举顺序可能随运行时版本而改变。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="c9b7e-122">要测试程序是否依赖键的枚举顺序或哈希表的值，可启用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c9b7e-123">解决方法</span><span class="sxs-lookup"><span data-stu-id="c9b7e-123">Resolution</span></span>  
 <span data-ttu-id="c9b7e-124">从不使用哈希代码替换对象标识。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="c9b7e-125">实现 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 方法的重写，以便不比较哈希代码。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="c9b7e-126">不要创建依赖哈希表中的键或值的枚举顺序的依赖项。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c9b7e-127">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="c9b7e-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="c9b7e-128">启用了此 MDA 时，应用程序的运行速度更慢。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="c9b7e-129">此 MDA 只取得原本应该返回的哈希代码，改为返回除以某个模数之后得到的余数。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c9b7e-130">输出</span><span class="sxs-lookup"><span data-stu-id="c9b7e-130">Output</span></span>  
 <span data-ttu-id="c9b7e-131">此 MDA 没有输出。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c9b7e-132">配置</span><span class="sxs-lookup"><span data-stu-id="c9b7e-132">Configuration</span></span>  
 <span data-ttu-id="c9b7e-133">`modulus` 属性指定用于哈希代码的模数。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="c9b7e-134">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="c9b7e-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9b7e-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="c9b7e-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c9b7e-136">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="c9b7e-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
