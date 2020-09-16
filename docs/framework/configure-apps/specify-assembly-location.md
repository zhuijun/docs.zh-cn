---
title: 指定程序集的位置
description: 请参阅如何通过在 XML 配置文件中使用 codeBase 元素或探测元素，在 .NET 中指定程序集的位置。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 3b24ff99eee9027d507ef89ca855162f221f826a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555115"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="d0fbe-103">指定程序集的位置</span><span class="sxs-lookup"><span data-stu-id="d0fbe-103">Specifying an Assembly's Location</span></span>
<span data-ttu-id="d0fbe-104">可以通过两种方法来指定程序集的位置：</span><span class="sxs-lookup"><span data-stu-id="d0fbe-104">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="d0fbe-105">使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-105">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="d0fbe-106">使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-106">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="d0fbe-107">你还可以使用 [.NET Framework 配置工具 (mscorcfg.msc) ](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) 指定程序集位置，或指定公共语言运行时用于探测程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-107">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="d0fbe-108">使用 \<codeBase> 元素</span><span class="sxs-lookup"><span data-stu-id="d0fbe-108">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="d0fbe-109">**\<codeBase>** 只能在计算机配置或同时重定向程序集版本的发行者策略文件中使用元素。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-109">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="d0fbe-110">当运行时确定要使用的程序集版本时，它将从确定版本的文件应用基本代码设置。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-110">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="d0fbe-111">如果未指定任何代码库，则运行时以正常方式探测程序集。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-111">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="d0fbe-112">有关详细信息，请参阅 [运行时如何定位程序集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-112">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d0fbe-113">下面的示例演示如何指定程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-113">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d0fbe-114">对于所有具有强名称的程序集， **version** 特性都是必需的，但对于不具有强名称的程序集，应忽略该特性。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-114">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="d0fbe-115">**\<codeBase>** 元素需要**href**特性。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-115">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="d0fbe-116">不能在元素中指定版本范围 **\<codeBase>** 。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-116">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0fbe-117">如果要为不具有强名称的程序集提供基本代码提示，则提示必须指向应用程序基目录或应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-117">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="d0fbe-118">使用 \<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="d0fbe-118">Using the \<probing> Element</span></span>  
 <span data-ttu-id="d0fbe-119">运行时通过探测来查找没有代码库的程序集。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-119">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="d0fbe-120">有关探测的详细信息，请参阅 [运行时如何定位程序集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-120">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d0fbe-121">您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 应用程序配置文件中的元素指定运行时在查找程序集时应搜索的子目录。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-121">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="d0fbe-122">下面的示例演示如何指定运行时应搜索的目录。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-122">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d0fbe-123">**PrivatePath**属性包含运行时应搜索程序集的目录。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-123">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="d0fbe-124">如果应用程序位于 C:\Program Files\MyApp，则运行时将查找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定基本代码的程序集。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-124">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="d0fbe-125">在 **privatePath** 中指定的目录必须是应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="d0fbe-125">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0fbe-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="d0fbe-126">See also</span></span>

- [<span data-ttu-id="d0fbe-127">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="d0fbe-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="d0fbe-128">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="d0fbe-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="d0fbe-129">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="d0fbe-129">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d0fbe-130">使用配置文件配置应用</span><span class="sxs-lookup"><span data-stu-id="d0fbe-130">Configuring Apps by using Configuration Files</span></span>](index.md)
