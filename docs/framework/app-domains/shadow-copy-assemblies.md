---
title: 卷影复制程序集
description: 探索 .NET 中程序集的卷影复制，以便无需卸载应用程序域即可更新在此应用程序域中使用的程序集。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], shadow copying
- application domains, shadow copying assemblies
- shadow copying assemblies
ms.assetid: de8b8759-fca7-4260-896b-5a4973157672
ms.openlocfilehash: a7ff72763dd26dbc50cd37e070c2d25ababa00f3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104556"
---
# <a name="shadow-copying-assemblies"></a><span data-ttu-id="b8460-103">卷影复制程序集</span><span class="sxs-lookup"><span data-stu-id="b8460-103">Shadow Copying Assemblies</span></span>

<span data-ttu-id="b8460-104">借助卷影复制，无需卸载应用程序域就可更新用于此应用程序域的程序集。</span><span class="sxs-lookup"><span data-stu-id="b8460-104">Shadow copying enables assemblies that are used in an application domain to be updated without unloading the application domain.</span></span> <span data-ttu-id="b8460-105">这对必须连续可用的应用程序（如 ASP.NET 网站）特别有用。</span><span class="sxs-lookup"><span data-stu-id="b8460-105">This is particularly useful for applications that must be available continuously, such as ASP.NET sites.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8460-106">卷影复制在 Windows 8.x Store 应用中不受支持。</span><span class="sxs-lookup"><span data-stu-id="b8460-106">Shadow copying is not supported in Windows 8.x Store apps.</span></span>

<span data-ttu-id="b8460-107">公共语言运行时会在加载程序集时锁定程序集文件，因此只有卸载此程序集才能更新此文件。</span><span class="sxs-lookup"><span data-stu-id="b8460-107">The common language runtime locks an assembly file when the assembly is loaded, so the file cannot be updated until the assembly is unloaded.</span></span> <span data-ttu-id="b8460-108">从应用程序域中卸载程序集的唯一方法是卸载应用程序域，因此在正常情况下，只有卸载了正在使用程序集的所有应用程序域才能在磁盘中更新此程序集。</span><span class="sxs-lookup"><span data-stu-id="b8460-108">The only way to unload an assembly from an application domain is by unloading the application domain, so under normal circumstances, an assembly cannot be updated on disk until all the application domains that are using it have been unloaded.</span></span>

<span data-ttu-id="b8460-109">应用程序域配置为卷影复制文件时，应用程序路径中的程序集复制到了另一个位置，并从此位置加载。</span><span class="sxs-lookup"><span data-stu-id="b8460-109">When an application domain is configured to shadow copy files, assemblies from the application path are copied to another location and loaded from that location.</span></span> <span data-ttu-id="b8460-110">此副本处于锁定状态，但原始程序集文件已解锁并可进行更新。</span><span class="sxs-lookup"><span data-stu-id="b8460-110">The copy is locked, but the original assembly file is unlocked and can be updated.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b8460-111">只有存储在应用程序目录或其子目录中的程序集才可进行卷影复制，这些程序集在配置应用程序域时由 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 指定。</span><span class="sxs-lookup"><span data-stu-id="b8460-111">The only assemblies that can be shadow copied are those stored in the application directory or its subdirectories, specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties when the application domain is configured.</span></span> <span data-ttu-id="b8460-112">存储在全局程序集缓存中的程序集不可进行卷影复制。</span><span class="sxs-lookup"><span data-stu-id="b8460-112">Assemblies stored in the global assembly cache are not shadow copied.</span></span>

<span data-ttu-id="b8460-113">本文包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="b8460-113">This article contains the following sections:</span></span>

- <span data-ttu-id="b8460-114">[启用和使用卷影复制](#EnablingAndUsing)描述了卷影复制的基本用法和可用选项。</span><span class="sxs-lookup"><span data-stu-id="b8460-114">[Enabling and Using Shadow Copying](#EnablingAndUsing) describes the basic use and the options that are available for shadow copying.</span></span>

- <span data-ttu-id="b8460-115">[启动性能](#StartupPerformance)描述了为提高启动性能对 .NET Framework 4 中的卷影复制进行的更改，以及还原到早期版本的行为的方法。</span><span class="sxs-lookup"><span data-stu-id="b8460-115">[Startup Performance](#StartupPerformance) describes the changes that are made to shadow copying in the .NET Framework 4 to improve startup performance, and how to revert to the behavior of earlier versions.</span></span>

- <span data-ttu-id="b8460-116">[已过时的方法](#ObsoleteMethods)描述了对控制 .NET Framework 2.0 中卷影复制的属性和方法进行的更改。</span><span class="sxs-lookup"><span data-stu-id="b8460-116">[Obsolete Methods](#ObsoleteMethods) describes the changes that were made to the properties and methods that control shadow copying in the .NET Framework 2.0.</span></span>

<a name="EnablingAndUsing"></a>

## <a name="enabling-and-using-shadow-copying"></a><span data-ttu-id="b8460-117">启用和使用卷影复制</span><span class="sxs-lookup"><span data-stu-id="b8460-117">Enabling and Using Shadow Copying</span></span>

<span data-ttu-id="b8460-118">若要配置卷影复制的应用程序域，可使用 <xref:System.AppDomainSetup> 类的属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b8460-118">You can use the properties of the <xref:System.AppDomainSetup> class as follows to configure an application domain for shadow copying:</span></span>

- <span data-ttu-id="b8460-119">通过将 <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 属性设置为字符串值 `"true"` 来启用卷影复制。</span><span class="sxs-lookup"><span data-stu-id="b8460-119">Enable shadow copying by setting the <xref:System.AppDomainSetup.ShadowCopyFiles%2A> property to the string value `"true"`.</span></span>

  <span data-ttu-id="b8460-120">默认情况下，此设置会导致在加载程序集之前，将应用程序路径中的所有程序集复制到下载缓存。</span><span class="sxs-lookup"><span data-stu-id="b8460-120">By default, this setting causes all assemblies in the application path to be copied to a download cache before they are loaded.</span></span> <span data-ttu-id="b8460-121">此缓存即是公共语言运行时为了存储从其他计算机中下载的文件而维护的缓存，并且公共语言运行时自动删除不再需要的文件。</span><span class="sxs-lookup"><span data-stu-id="b8460-121">This is the same cache maintained by the common language runtime to store files downloaded from other computers, and the common language runtime automatically deletes the files when they are no longer needed.</span></span>

- <span data-ttu-id="b8460-122">或者，可通过使用 <xref:System.AppDomainSetup.CachePath%2A> 属性和 <xref:System.AppDomainSetup.ApplicationName%2A> 属性设置卷影复制文件的自定义位置。</span><span class="sxs-lookup"><span data-stu-id="b8460-122">Optionally set a custom location for shadow copied files by using the <xref:System.AppDomainSetup.CachePath%2A> property and the <xref:System.AppDomainSetup.ApplicationName%2A> property.</span></span>

  <span data-ttu-id="b8460-123">可通过将 <xref:System.AppDomainSetup.ApplicationName%2A> 属性和 <xref:System.AppDomainSetup.CachePath%2A> 属性串联为子目录，形成位置的基路径。</span><span class="sxs-lookup"><span data-stu-id="b8460-123">The base path for the location is formed by concatenating the <xref:System.AppDomainSetup.ApplicationName%2A> property to the <xref:System.AppDomainSetup.CachePath%2A> property as a subdirectory.</span></span> <span data-ttu-id="b8460-124">将程序集卷影复制到此路径的子目录，而不是复制到基路径本身。</span><span class="sxs-lookup"><span data-stu-id="b8460-124">Assemblies are shadow copied to subdirectories of this path, not to the base path itself.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b8460-125">如果未设置 <xref:System.AppDomainSetup.ApplicationName%2A> 属性，则忽略 <xref:System.AppDomainSetup.CachePath%2A> 属性并使用下载缓存。</span><span class="sxs-lookup"><span data-stu-id="b8460-125">If the <xref:System.AppDomainSetup.ApplicationName%2A> property is not set, the <xref:System.AppDomainSetup.CachePath%2A> property is ignored and the download cache is used.</span></span> <span data-ttu-id="b8460-126">不引发异常。</span><span class="sxs-lookup"><span data-stu-id="b8460-126">No exception is thrown.</span></span>

  <span data-ttu-id="b8460-127">如果指定自定义位置，则应负责清理不再需要的目录和复制的文件。</span><span class="sxs-lookup"><span data-stu-id="b8460-127">If you specify a custom location, you are responsible for cleaning up the directories and copied files when they are no longer needed.</span></span> <span data-ttu-id="b8460-128">它们不会自动删除。</span><span class="sxs-lookup"><span data-stu-id="b8460-128">They are not deleted automatically.</span></span>

  <span data-ttu-id="b8460-129">为卷影复制文件设置自定义位置还存在以下几个原因。</span><span class="sxs-lookup"><span data-stu-id="b8460-129">There are a few reasons why you might want to set a custom location for shadow copied files.</span></span> <span data-ttu-id="b8460-130">如果应用程序生成了大量副本，则可能希望为卷影复制文件设置自定义位置。</span><span class="sxs-lookup"><span data-stu-id="b8460-130">You might want to set a custom location for shadow copied files if your application generates a large number of copies.</span></span> <span data-ttu-id="b8460-131">由于下载缓存受到大小（而非生存期）的限制，所以公共语言运行时可能将尝试删除仍在使用的文件。</span><span class="sxs-lookup"><span data-stu-id="b8460-131">The download cache is limited by size, not by lifetime, so it is possible that the common language runtime will attempt to delete a file that is still in use.</span></span> <span data-ttu-id="b8460-132">设置自定义位置的另一个原因是运行应用程序的用户对公共语言运行时用于下载缓存的目录位置不具备写入权限。</span><span class="sxs-lookup"><span data-stu-id="b8460-132">Another reason to set a custom location is when users running your application do not have write access to the directory location the common language runtime uses for the download cache.</span></span>

- <span data-ttu-id="b8460-133">或者，使用 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 属性限制卷影复制的程序集。</span><span class="sxs-lookup"><span data-stu-id="b8460-133">Optionally limit the assemblies that are shadow copied by using the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property.</span></span>

  <span data-ttu-id="b8460-134">启用应用程序域的卷影复制时，默认复制应用程序路径（即 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 属性指定的目录）中的所有程序集。</span><span class="sxs-lookup"><span data-stu-id="b8460-134">When you enable shadow copying for an application domain, the default is to copy all assemblies in the application path — that is, in the directories specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties.</span></span> <span data-ttu-id="b8460-135">可以通过创建仅包含想要卷影复制的目录的字符串并将此字符串分配至 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 属性来限制复制到选定目录。</span><span class="sxs-lookup"><span data-stu-id="b8460-135">You can limit the copying to selected directories by creating a string that contains only those directories you want to shadow copy, and assigning the string to the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property.</span></span> <span data-ttu-id="b8460-136">目录用分号分隔。</span><span class="sxs-lookup"><span data-stu-id="b8460-136">Separate the directories with semicolons.</span></span> <span data-ttu-id="b8460-137">只有选定目录中的程序集才进行卷影复制。</span><span class="sxs-lookup"><span data-stu-id="b8460-137">The only assemblies that are shadow copied are the ones in the selected directories.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b8460-138">如果未将字符串分配至 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 属性或者将此属性设置为 `null`，则 <xref:System.AppDomainSetup.ApplicationBase%2A> 和 <xref:System.AppDomainSetup.PrivateBinPath%2A> 属性指定的目录中的所有程序集均进行卷影复制。</span><span class="sxs-lookup"><span data-stu-id="b8460-138">If you don’t assign a string to the <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> property, or if you set this property to `null`, all assemblies in the directories specified by the <xref:System.AppDomainSetup.ApplicationBase%2A> and <xref:System.AppDomainSetup.PrivateBinPath%2A> properties are shadow copied.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b8460-139">目录路径不能包含分号，因为分号是分隔符。</span><span class="sxs-lookup"><span data-stu-id="b8460-139">Directory paths must not contain semicolons, because the semicolon is the delimiter character.</span></span> <span data-ttu-id="b8460-140">分号没有转义符。</span><span class="sxs-lookup"><span data-stu-id="b8460-140">There is no escape character for semicolons.</span></span>

<a name="StartupPerformance"></a>

## <a name="startup-performance"></a><span data-ttu-id="b8460-141">启动性能</span><span class="sxs-lookup"><span data-stu-id="b8460-141">Startup Performance</span></span>

<span data-ttu-id="b8460-142">如果启动使用卷影复制的应用程序域，在将应用程序目录中的程序集复制到卷影复制目录或验证程序集是否已经位于此位置时，会出现延迟。</span><span class="sxs-lookup"><span data-stu-id="b8460-142">When an application domain that uses shadow copying starts, there is a delay while assemblies in the application directory are copied to the shadow copy directory, or verified if they are already in that location.</span></span> <span data-ttu-id="b8460-143">在 .NET Framework 4 之前，所有程序集均复制到临时目录。</span><span class="sxs-lookup"><span data-stu-id="b8460-143">Before the .NET Framework 4, all assemblies were copied to a temporary directory.</span></span> <span data-ttu-id="b8460-144">已打开每个程序集以验证程序集名称，并验证了强名称。</span><span class="sxs-lookup"><span data-stu-id="b8460-144">Each assembly was opened to verify the assembly name, and the strong name was validated.</span></span> <span data-ttu-id="b8460-145">已检查每个程序集以查看其更新到的版本是否比卷影复制目录中的副本新。</span><span class="sxs-lookup"><span data-stu-id="b8460-145">Each assembly was checked to see whether it had been updated more recently than the copy in the shadow copy directory.</span></span> <span data-ttu-id="b8460-146">如果是，则将它复制到卷影复制目录。</span><span class="sxs-lookup"><span data-stu-id="b8460-146">If so, it was copied to the shadow copy directory.</span></span> <span data-ttu-id="b8460-147">最后，删除临时副本。</span><span class="sxs-lookup"><span data-stu-id="b8460-147">Finally, the temporary copies were discarded.</span></span>

<span data-ttu-id="b8460-148">自 .NET Framework 4 以来，默认启动行为就是直接将应用程序目录中每个程序集的文件日期和时间与影子副本目录中副本的文件日期和时间进行比较。</span><span class="sxs-lookup"><span data-stu-id="b8460-148">Beginning with the .NET Framework 4, the default startup behavior is to directly compare the file date and time of each assembly in the application directory with the file date and time of the copy in the shadow copy directory.</span></span> <span data-ttu-id="b8460-149">如果程序集已更新，则使用 .NET Framework 早期版本中的相同过程进行复制；否则，将加载卷影复制目录中的副本。</span><span class="sxs-lookup"><span data-stu-id="b8460-149">If the assembly has been updated, it is copied by using the same procedure as in earlier versions of the .NET Framework; otherwise, the copy in the shadow copy directory is loaded.</span></span>

<span data-ttu-id="b8460-150">对于其中程序集未频繁更改且通常程序集的较小子集发生更改的应用程序，产生的性能提升最大。</span><span class="sxs-lookup"><span data-stu-id="b8460-150">The resulting performance improvement is largest for applications in which assemblies do not change frequently and changes usually occur in a small subset of assemblies.</span></span> <span data-ttu-id="b8460-151">如果应用程序中的大部分程序集频繁发生更改，则新的默认行为可能导致性能退化。</span><span class="sxs-lookup"><span data-stu-id="b8460-151">If a majority of assemblies in an application change frequently, the new default behavior might cause a performance regression.</span></span> <span data-ttu-id="b8460-152">可以通过向配置文件添加 [\<shadowCopyVerifyByTimestamp> 元素](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)来还原早期版本的 .NET Framework 的启动行为，其中 `enabled="false"`。</span><span class="sxs-lookup"><span data-stu-id="b8460-152">You can restore the startup behavior of previous versions of the .NET Framework by adding the [\<shadowCopyVerifyByTimestamp> element](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md) to the configuration file, with `enabled="false"`.</span></span>

<a name="ObsoleteMethods"></a>

## <a name="obsolete-methods"></a><span data-ttu-id="b8460-153">已过时的方法</span><span class="sxs-lookup"><span data-stu-id="b8460-153">Obsolete Methods</span></span>

<span data-ttu-id="b8460-154"><xref:System.AppDomain> 类具有几种可用来控制应用程序域中卷影复制的方法（如 <xref:System.AppDomain.SetShadowCopyFiles%2A> 和 <xref:System.AppDomain.ClearShadowCopyPath%2A>），但这些方法在 .NET Framework 2.0 版本中已标记为过时。</span><span class="sxs-lookup"><span data-stu-id="b8460-154">The <xref:System.AppDomain> class has several methods, such as <xref:System.AppDomain.SetShadowCopyFiles%2A> and <xref:System.AppDomain.ClearShadowCopyPath%2A>, that can be used to control shadow copying on an application domain, but these have been marked obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b8460-155">若要配置进行卷影复制的应用程序域，推荐使用 <xref:System.AppDomainSetup> 类的属性。</span><span class="sxs-lookup"><span data-stu-id="b8460-155">The recommended way to configure an application domain for shadow copying is to use the properties of the <xref:System.AppDomainSetup> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8460-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="b8460-156">See also</span></span>

- <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ApplicationName%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b8460-157">\<shadowCopyVerifyByTimestamp> 元素</span><span class="sxs-lookup"><span data-stu-id="b8460-157">\<shadowCopyVerifyByTimestamp> Element</span></span>](../configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)
