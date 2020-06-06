---
title: 如何：使用 DEVPATH 查找程序集
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913002"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="3e56d-102">如何：使用 DEVPATH 查找程序集</span><span class="sxs-lookup"><span data-stu-id="3e56d-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="3e56d-103">开发人员可能希望确保它们所构建的共享程序集在多个应用程序中正常工作。</span><span class="sxs-lookup"><span data-stu-id="3e56d-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="3e56d-104">开发人员可以创建一个 DEVPATH 环境变量，该变量指向程序集的生成输出目录，而不是在开发周期期间将程序集不断置于全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="3e56d-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="3e56d-105">例如，假设要生成一个名为 MySharedAssembly 的共享程序集，并且输出目录为 C:\MySharedAssembly\Debug。</span><span class="sxs-lookup"><span data-stu-id="3e56d-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="3e56d-106">可以将 C:\MySharedAssembly\Debug 放在 DEVPATH 变量中。</span><span class="sxs-lookup"><span data-stu-id="3e56d-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="3e56d-107">然后必须 [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) 在计算机配置文件中指定元素。</span><span class="sxs-lookup"><span data-stu-id="3e56d-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="3e56d-108">此元素告知公共语言运行时使用 DEVPATH 来定位程序集。</span><span class="sxs-lookup"><span data-stu-id="3e56d-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="3e56d-109">共享程序集必须可由运行时发现。</span><span class="sxs-lookup"><span data-stu-id="3e56d-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="3e56d-110">若要为解析程序集引用指定一个专用目录，请使用配置文件中的[ \<codeBase> 元素](./file-schema/runtime/codebase-element.md)或[ \<probing> 元素](./file-schema/runtime/probing-element.md)，如[指定程序集的位置](specify-assembly-location.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="3e56d-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="3e56d-111">你还可以将程序集放在应用程序目录的子目录中。</span><span class="sxs-lookup"><span data-stu-id="3e56d-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="3e56d-112">有关详细信息，请参阅[运行时如何定位程序集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="3e56d-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e56d-113">这是一项高级功能，仅用于开发。</span><span class="sxs-lookup"><span data-stu-id="3e56d-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="3e56d-114">下面的示例演示如何使运行时在由 DEVPATH 环境变量指定的目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="3e56d-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e56d-115">示例</span><span class="sxs-lookup"><span data-stu-id="3e56d-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="3e56d-116">此设置默认为 false。</span><span class="sxs-lookup"><span data-stu-id="3e56d-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e56d-117">仅在开发时使用此设置。</span><span class="sxs-lookup"><span data-stu-id="3e56d-117">Use this setting only at development time.</span></span> <span data-ttu-id="3e56d-118">运行时不检查在 DEVPATH 中找到的具有强名称的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="3e56d-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="3e56d-119">它只使用它找到的第一个程序集。</span><span class="sxs-lookup"><span data-stu-id="3e56d-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e56d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e56d-120">See also</span></span>

- [<span data-ttu-id="3e56d-121">使用配置文件配置应用</span><span class="sxs-lookup"><span data-stu-id="3e56d-121">Configuring Apps by using Configuration Files</span></span>](index.md)
