---
title: 指定程序集的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646033"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="efad0-102">指定程序集的位置</span><span class="sxs-lookup"><span data-stu-id="efad0-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="efad0-103">可以通过两种方法来指定程序集的位置：</span><span class="sxs-lookup"><span data-stu-id="efad0-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="efad0-104">使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="efad0-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="efad0-105">使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="efad0-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="efad0-106">你还可以使用[.NET Framework 配置工具（mscorcfg.msc）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))来指定程序集位置或指定公共语言运行时用于探测程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="efad0-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="efad0-107">使用 \<codeBase> 元素</span><span class="sxs-lookup"><span data-stu-id="efad0-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="efad0-108">**\<codeBase>** 只能在计算机配置或同时重定向程序集版本的发行者策略文件中使用元素。</span><span class="sxs-lookup"><span data-stu-id="efad0-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="efad0-109">当运行时确定要使用的程序集版本时，它将从确定版本的文件应用基本代码设置。</span><span class="sxs-lookup"><span data-stu-id="efad0-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="efad0-110">如果未指定任何代码库，则运行时以正常方式探测程序集。</span><span class="sxs-lookup"><span data-stu-id="efad0-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="efad0-111">有关详细信息，请参阅[运行时如何定位程序集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="efad0-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="efad0-112">下面的示例演示如何指定程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="efad0-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="efad0-113">对于所有具有强名称的程序集， **version**特性都是必需的，但对于不具有强名称的程序集，应忽略该特性。</span><span class="sxs-lookup"><span data-stu-id="efad0-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="efad0-114">**\<codeBase>** 元素需要**href**特性。</span><span class="sxs-lookup"><span data-stu-id="efad0-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="efad0-115">不能在元素中指定版本范围 **\<codeBase>** 。</span><span class="sxs-lookup"><span data-stu-id="efad0-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efad0-116">如果要为不具有强名称的程序集提供基本代码提示，则提示必须指向应用程序基目录或应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="efad0-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="efad0-117">使用 \<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="efad0-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="efad0-118">运行时通过探测来查找没有代码库的程序集。</span><span class="sxs-lookup"><span data-stu-id="efad0-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="efad0-119">有关探测的详细信息，请参阅[运行时如何定位程序集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="efad0-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="efad0-120">您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 应用程序配置文件中的元素指定运行时在查找程序集时应搜索的子目录。</span><span class="sxs-lookup"><span data-stu-id="efad0-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="efad0-121">下面的示例演示如何指定运行时应搜索的目录。</span><span class="sxs-lookup"><span data-stu-id="efad0-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="efad0-122">**PrivatePath**属性包含运行时应搜索程序集的目录。</span><span class="sxs-lookup"><span data-stu-id="efad0-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="efad0-123">如果应用程序位于 C:\Program Files\MyApp，则运行时将查找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定基本代码的程序集。</span><span class="sxs-lookup"><span data-stu-id="efad0-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="efad0-124">在**privatePath**中指定的目录必须是应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="efad0-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efad0-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="efad0-125">See also</span></span>

- [<span data-ttu-id="efad0-126">.NET 中的程序集</span><span class="sxs-lookup"><span data-stu-id="efad0-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="efad0-127">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="efad0-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="efad0-128">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="efad0-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="efad0-129">使用配置文件配置应用</span><span class="sxs-lookup"><span data-stu-id="efad0-129">Configuring Apps by using Configuration Files</span></span>](index.md)
