---
title: 反射和 .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
ms.openlocfilehash: 65921377be9b8bf1c2d147b384c85cbd037d15f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128182"
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="3d014-102">反射和 .NET Native</span><span class="sxs-lookup"><span data-stu-id="3d014-102">Reflection and .NET Native</span></span>
<span data-ttu-id="3d014-103">在 .NET Framework 中，托管开发通过反射 API 支持元编程。</span><span class="sxs-lookup"><span data-stu-id="3d014-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="3d014-104">反射允许你检查应用中的对象，调用通过检查发现的对象上的方法，在运行时间生成性类型，并支持所有其他动态代码方案。</span><span class="sxs-lookup"><span data-stu-id="3d014-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="3d014-105">它还支持序列化和反序列化，这允许一个对象的字段值被持久化并在后来得到还原。</span><span class="sxs-lookup"><span data-stu-id="3d014-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="3d014-106">这些方案都要求 .NET Framework 及时生成 (JIT) 编译器以可用的元数据为基础生成本机代码。</span><span class="sxs-lookup"><span data-stu-id="3d014-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="3d014-107">.NET Native 运行时不包括 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="3d014-107">The .NET Native runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="3d014-108">因此，所有所需的本机代码必需提前生成。</span><span class="sxs-lookup"><span data-stu-id="3d014-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="3d014-109">一组启发可用于确定应生成哪些代码，但是这些启发不能涵盖所有可能的元编程方案。</span><span class="sxs-lookup"><span data-stu-id="3d014-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="3d014-110">因此，必须通过使用[运行时指令](runtime-directives-rd-xml-configuration-file-reference.md)向这些元编程方案提供提示。</span><span class="sxs-lookup"><span data-stu-id="3d014-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="3d014-111">如果所需的元数据或实现代码在运行时不可用，应用将引发 [MissingMetadataException](missingmetadataexception-class-net-native.md)、[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 或 [MissingInteropDataException](missinginteropdataexception-class-net-native.md) 异常。</span><span class="sxs-lookup"><span data-stu-id="3d014-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="3d014-112">有两个疑难解答程序可用于为运行时指令文件提供合适的条目，指令文件将消除以下异常：</span><span class="sxs-lookup"><span data-stu-id="3d014-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
- <span data-ttu-id="3d014-113">类型的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="3d014-113">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
- <span data-ttu-id="3d014-114">方法的 [MissingMetadataException 故障排除程序](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="3d014-114">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d014-115">有关提供为何需要运行时指令文件的背景的 .NET 本机编译过程的概述，请参阅 [.NET 本机和编译](net-native-and-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="3d014-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="3d014-116">此外，.NET Native 不允许反映 .NET Framework 类库的私有成员。</span><span class="sxs-lookup"><span data-stu-id="3d014-116">In addition, .NET Native doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="3d014-117">例如，调用 <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> 属性来检索一个 .NET Framework 类库类型的字段仅返回公共或受保护的字段。</span><span class="sxs-lookup"><span data-stu-id="3d014-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="3d014-118">以下主题提供了你需要在自己的应用中支持反射和序列化的概念和引用文档：</span><span class="sxs-lookup"><span data-stu-id="3d014-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
- [<span data-ttu-id="3d014-119">利用反射的 API</span><span class="sxs-lookup"><span data-stu-id="3d014-119">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)  
  
- [<span data-ttu-id="3d014-120">反射 API 引用</span><span class="sxs-lookup"><span data-stu-id="3d014-120">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)  
  
- [<span data-ttu-id="3d014-121">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="3d014-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d014-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d014-122">See also</span></span>

- [<span data-ttu-id="3d014-123">使用 .NET Native 编译应用程序</span><span class="sxs-lookup"><span data-stu-id="3d014-123">Compiling Apps with .NET Native</span></span>](index.md)
- [<span data-ttu-id="3d014-124">.NET Native 和编译</span><span class="sxs-lookup"><span data-stu-id="3d014-124">.NET Native and Compilation</span></span>](net-native-and-compilation.md)
