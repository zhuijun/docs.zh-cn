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
# <a name="using-portable-class-library-with-model-view-view-model"></a>将可移植类库与模型-视图-视图模型配合使用
您可以使用 .NET Framework[可移植类库](cross-platform-development-with-the-portable-class-library.md)来实现模型-视图-视图模型（MVVM）模式并跨多个平台共享程序集。

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM 是将用户界面与基础业务逻辑相隔离的应用程序模式。 你可以在 Visual Studio 2012 中的可移植类库项目内实现模型和视图模型类，然后创建针对不同平台自定义的视图。 此方法使你能够仅编写数据模型和业务逻辑一次，并使用 .NET Framework、Silverlight、Windows Phone 和 Windows 8.x 应用商店应用中的代码，如下图所示。

 ![显示跨平台跨 MVVM 共享程序集的可移植类库。](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 本主题不提供有关 MVVM 模式的一般信息。 它仅提供有关如何使用可移植类库实现 MVVM 的信息。 有关 MVVM 的详细信息，请参阅[使用适用于 WPF 的 Prism 库5.0 的 Mvvm 快速入门](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40))。

## <a name="classes-that-support-mvvm"></a>支持 MVVM 的类
 如果面向可移植类库项目的 .NET Framework 4.5、适用于 Windows 8.x 应用商店应用的 .NET 或 Windows Phone 7.5，则可使用以下类实现 MVVM 模式：

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> 类

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> 类

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> 类

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> 类

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> 类

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> 类

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> 类

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> 类

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> 类

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> 类

- 命名空间中的所有类 <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>实现 MVVM
 若要实现 MVVM，通常会在可移植类库项目中同时创建模型和视图模型，因为可移植类库项目无法引用不可移植的项目。 模型和视图模型可以位于同一个项目中，也可以位于单独的项目中。 如果使用单独的项目，请从视图模型项目向模型项目添加引用。

 编译模型和视图模型项目后，在包含该视图的应用程序中引用这些程序集。 如果视图仅与视图模型交互，则只需引用包含该视图模型的程序集。

### <a name="model"></a>型号
 下面的示例演示可在可移植类库项目中驻留的简化模型类。

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 下面的示例演示了一种简单的方法，用于填充、检索和更新可移植类库项目中的数据。 在实际应用中，你将从 Windows Communication Foundation （WCF）服务等源中检索数据。

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>查看模型
 在实现 MVVM 模式时，经常会添加视图模型的基类。 下面的示例演示了一个基类。

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 接口的实现 <xref:System.Windows.Input.ICommand> 经常与 MVVM 模式一起使用。 下面的示例演示 <xref:System.Windows.Input.ICommand> 接口的实现。

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 下面的示例显示一个简化的视图模型。

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>查看  
 通过 .NET Framework 4.5 应用、Windows 8.x 应用商店应用、基于 Silverlight 的应用或 Windows Phone 7.5 应用，你可以引用包含模型和视图模型项目的程序集。  然后创建与视图模型交互的视图。 下面的示例演示了一个简化的 Windows Presentation Foundation （WPF）应用，该应用从视图模型检索和更新数据。 可以在 Silverlight、Windows Phone 或 Windows 8.x 应用商店应用中创建类似视图。  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>另请参阅

- [可移植类库](cross-platform-development-with-the-portable-class-library.md)
