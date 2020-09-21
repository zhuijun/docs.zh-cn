---
title: 向 COM 公开 .NET Core 组件
description: 向 COM 公开 .NET 组件。 为互操作限定 .NET 类型。 应用互操作特性。 将 COM 的程序集打包。 从 COM 使用托管类型。
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: dc808f3e8d6bd89ba979d43e5b4ec9d787bd09b1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545254"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="1f23b-107">向 COM 公开 .NET Core 组件</span><span class="sxs-lookup"><span data-stu-id="1f23b-107">Exposing .NET components to COM</span></span>

<span data-ttu-id="1f23b-108">对开发人员而言，编写 .NET 类型以及从非托管代码使用该类型是不同的活动。</span><span class="sxs-lookup"><span data-stu-id="1f23b-108">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="1f23b-109">本部分介绍编写与 COM 客户端互操作的托管代码的几个提示：</span><span class="sxs-lookup"><span data-stu-id="1f23b-109">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="1f23b-110">[为互操作限定 .NET 类型](../../standard/native-interop/qualify-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="1f23b-110">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="1f23b-111">要向 COM 公开的所有托管类型、方法、属性、字段和事件都必须是公开的。</span><span class="sxs-lookup"><span data-stu-id="1f23b-111">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="1f23b-112">各类型必须具有公共无参数默认构造函数，通过 COM 只能调用该构造函数。</span><span class="sxs-lookup"><span data-stu-id="1f23b-112">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="1f23b-113">[应用互操作属性](../../standard/native-interop/apply-interop-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="1f23b-113">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="1f23b-114">托管代码中的自定义属性可增强组件的互操作性。</span><span class="sxs-lookup"><span data-stu-id="1f23b-114">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="1f23b-115">[将 COM 的程序集打包](packaging-an-assembly-for-com.md)。</span><span class="sxs-lookup"><span data-stu-id="1f23b-115">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="1f23b-116">COM 开发人员可能会要求用户总结引用和部署程序集所涉及的步骤。</span><span class="sxs-lookup"><span data-stu-id="1f23b-116">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="1f23b-117">此外，本部分还确定了从 COM 客户端使用托管类型的相关任务。</span><span class="sxs-lookup"><span data-stu-id="1f23b-117">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="1f23b-118">从 COM 使用托管类型</span><span class="sxs-lookup"><span data-stu-id="1f23b-118">To consume a managed type from COM</span></span>

1. <span data-ttu-id="1f23b-119">[向 COM 注册程序集](registering-assemblies-with-com.md)。</span><span class="sxs-lookup"><span data-stu-id="1f23b-119">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="1f23b-120">必须在设计时注册程序集（和类型库）中的类型。</span><span class="sxs-lookup"><span data-stu-id="1f23b-120">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="1f23b-121">如果安装程序未注册程序集，请指示 COM 开发人员使用 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="1f23b-121">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="1f23b-122">[从 COM 引用 .NET 类型](how-to-reference-net-types-from-com.md)。</span><span class="sxs-lookup"><span data-stu-id="1f23b-122">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="1f23b-123">COM 开发人员可使用当前使用的相同工具和技术引用程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="1f23b-123">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="1f23b-124">[调用 .NET 对象](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1f23b-124">[Call a .NET object](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="1f23b-125">COM 开发人员可采用在任何非托管类型上调用方法的方式在 .NET 对象上调用方法。</span><span class="sxs-lookup"><span data-stu-id="1f23b-125">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="1f23b-126">例如，COM CoCreateInstance API 激活 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="1f23b-126">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="1f23b-127">[为 COM 访问部署应用程序](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="1f23b-127">[Deploy an application for COM access](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="1f23b-128">具有强名称的程序集可安装在全局程序集缓存中，并向其发布者请求签名。</span><span class="sxs-lookup"><span data-stu-id="1f23b-128">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="1f23b-129">不具有强名称的程序集必须安装在客户端的应用程序目录中。</span><span class="sxs-lookup"><span data-stu-id="1f23b-129">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f23b-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f23b-130">See also</span></span>

- [<span data-ttu-id="1f23b-131">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="1f23b-131">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="1f23b-132">COM 互操作示例：COM 客户端和 .NET 服务器</span><span class="sxs-lookup"><span data-stu-id="1f23b-132">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)
