---
title: 将可移植类库与模型-视图-视图模型配合使用
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: ff34b295ba443088115d470d8ade0c986ac1d856
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288844"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="8c21d-102">将可移植类库与模型-视图-视图模型配合使用</span><span class="sxs-lookup"><span data-stu-id="8c21d-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="8c21d-103">您可以使用 .NET Framework[可移植类库](cross-platform-development-with-the-portable-class-library.md)来实现模型-视图-视图模型（MVVM）模式并跨多个平台共享程序集。</span><span class="sxs-lookup"><span data-stu-id="8c21d-103">You can use the .NET Framework [Portable Class Library](cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="8c21d-104">MVVM 是将用户界面与基础业务逻辑相隔离的应用程序模式。</span><span class="sxs-lookup"><span data-stu-id="8c21d-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="8c21d-105">你可以在 Visual Studio 2012 中的可移植类库项目内实现模型和视图模型类，然后创建针对不同平台自定义的视图。</span><span class="sxs-lookup"><span data-stu-id="8c21d-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="8c21d-106">此方法使你能够仅编写数据模型和业务逻辑一次，并使用 .NET Framework、Silverlight、Windows Phone 和 Windows 8.x 应用商店应用中的代码，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8c21d-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![显示跨平台跨 MVVM 共享程序集的可移植类库。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="8c21d-108">本主题不提供有关 MVVM 模式的一般信息。</span><span class="sxs-lookup"><span data-stu-id="8c21d-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="8c21d-109">它仅提供有关如何使用可移植类库实现 MVVM 的信息。</span><span class="sxs-lookup"><span data-stu-id="8c21d-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="8c21d-110">有关 MVVM 的详细信息，请参阅[使用适用于 WPF 的 Prism 库5.0 的 Mvvm 快速入门](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。</span><span class="sxs-lookup"><span data-stu-id="8c21d-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="8c21d-111">支持 MVVM 的类</span><span class="sxs-lookup"><span data-stu-id="8c21d-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="8c21d-112">如果面向可移植类库项目的 .NET Framework 4.5、适用于 Windows 8.x 应用商店应用的 .NET 或 Windows Phone 7.5，则可使用以下类实现 MVVM 模式：</span><span class="sxs-lookup"><span data-stu-id="8c21d-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="8c21d-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="8c21d-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="8c21d-123">命名空间中的所有类 <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8c21d-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="8c21d-124">实现 MVVM</span><span class="sxs-lookup"><span data-stu-id="8c21d-124">Implementing MVVM</span></span>
 <span data-ttu-id="8c21d-125">若要实现 MVVM，通常会在可移植类库项目中同时创建模型和视图模型，因为可移植类库项目无法引用不可移植的项目。</span><span class="sxs-lookup"><span data-stu-id="8c21d-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="8c21d-126">模型和视图模型可以位于同一个项目中，也可以位于单独的项目中。</span><span class="sxs-lookup"><span data-stu-id="8c21d-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="8c21d-127">如果使用单独的项目，请从视图模型项目向模型项目添加引用。</span><span class="sxs-lookup"><span data-stu-id="8c21d-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="8c21d-128">编译模型和视图模型项目后，在包含该视图的应用程序中引用这些程序集。</span><span class="sxs-lookup"><span data-stu-id="8c21d-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="8c21d-129">如果视图仅与视图模型交互，则只需引用包含该视图模型的程序集。</span><span class="sxs-lookup"><span data-stu-id="8c21d-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="8c21d-130">型号</span><span class="sxs-lookup"><span data-stu-id="8c21d-130">Model</span></span>
 <span data-ttu-id="8c21d-131">下面的示例演示可在可移植类库项目中驻留的简化模型类。</span><span class="sxs-lookup"><span data-stu-id="8c21d-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="8c21d-132">下面的示例演示了一种简单的方法，用于填充、检索和更新可移植类库项目中的数据。</span><span class="sxs-lookup"><span data-stu-id="8c21d-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="8c21d-133">在实际应用中，你将从 Windows Communication Foundation （WCF）服务等源中检索数据。</span><span class="sxs-lookup"><span data-stu-id="8c21d-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="8c21d-134">查看模型</span><span class="sxs-lookup"><span data-stu-id="8c21d-134">View Model</span></span>
 <span data-ttu-id="8c21d-135">在实现 MVVM 模式时，经常会添加视图模型的基类。</span><span class="sxs-lookup"><span data-stu-id="8c21d-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="8c21d-136">下面的示例演示了一个基类。</span><span class="sxs-lookup"><span data-stu-id="8c21d-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="8c21d-137">接口的实现 <xref:System.Windows.Input.ICommand> 经常与 MVVM 模式一起使用。</span><span class="sxs-lookup"><span data-stu-id="8c21d-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="8c21d-138">下面的示例演示 <xref:System.Windows.Input.ICommand> 接口的实现。</span><span class="sxs-lookup"><span data-stu-id="8c21d-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="8c21d-139">下面的示例显示一个简化的视图模型。</span><span class="sxs-lookup"><span data-stu-id="8c21d-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="8c21d-140">查看</span><span class="sxs-lookup"><span data-stu-id="8c21d-140">View</span></span>  
 <span data-ttu-id="8c21d-141">通过 .NET Framework 4.5 应用、Windows 8.x 应用商店应用、基于 Silverlight 的应用或 Windows Phone 7.5 应用，你可以引用包含模型和视图模型项目的程序集。</span><span class="sxs-lookup"><span data-stu-id="8c21d-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="8c21d-142">然后创建与视图模型交互的视图。</span><span class="sxs-lookup"><span data-stu-id="8c21d-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="8c21d-143">下面的示例演示了一个简化的 Windows Presentation Foundation （WPF）应用，该应用从视图模型检索和更新数据。</span><span class="sxs-lookup"><span data-stu-id="8c21d-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="8c21d-144">可以在 Silverlight、Windows Phone 或 Windows 8.x 应用商店应用中创建类似视图。</span><span class="sxs-lookup"><span data-stu-id="8c21d-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="8c21d-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c21d-145">See also</span></span>

- [<span data-ttu-id="8c21d-146">可移植类库</span><span class="sxs-lookup"><span data-stu-id="8c21d-146">Portable Class Library</span></span>](cross-platform-development-with-the-portable-class-library.md)
