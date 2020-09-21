---
title: 创建和使用组件
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: e4d4fa092363a5e76658f2770c0d655bb225f3f3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544578"
---
# <a name="creating-and-using-components-in-visual-basic"></a><span data-ttu-id="f5b48-102">创建和使用组件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5b48-102">Creating and Using Components in Visual Basic</span></span>

<span data-ttu-id="f5b48-103">组件  是一个类，该类实现 <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> 接口或直接/间接派生自实现 <xref:System.ComponentModel.IComponent> 的类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-103">A *component* is a class that implements the <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> interface or that derives directly or indirectly from a class that implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="f5b48-104">.NET Framework 组件是可重复使用的对象，可以和其他对象进行交互，并提供对外部资源和设计时支持的控制。</span><span class="sxs-lookup"><span data-stu-id="f5b48-104">A .NET Framework component is an object that is reusable, can interact with other objects, and provides control over external resources and design-time support.</span></span>  
  
 <span data-ttu-id="f5b48-105">组件的一个重要特性在于它们是可设计的，这意味着可在 Visual Studio 集成开发环境中使用作为组件的类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-105">An important feature of components is that they are designable, which means that a class that is a component can be used in the Visual Studio Integrated Development Environment.</span></span> <span data-ttu-id="f5b48-106">可以将组件添加到“工具箱”、拖放到窗体以及在设计图面上操作。</span><span class="sxs-lookup"><span data-stu-id="f5b48-106">A component can be added to the Toolbox, dragged and dropped onto a form, and manipulated on a design surface.</span></span> <span data-ttu-id="f5b48-107">请注意，对组件的基本设计时支持已内置于 .NET Framework 中；组件开发人员不必执行任何附加工作便可利用基本设计时功能。</span><span class="sxs-lookup"><span data-stu-id="f5b48-107">Notice that base design-time support for components is built into the .NET Framework; a component developer does not have to do any additional work to take advantage of the base design-time functionality.</span></span>  
  
 <span data-ttu-id="f5b48-108">控件与组件类似，二者都是可设计的。 </span><span class="sxs-lookup"><span data-stu-id="f5b48-108">A *control* is similar to a component, as both are designable.</span></span> <span data-ttu-id="f5b48-109">不过，控件提供用户界面，而组件不提供。</span><span class="sxs-lookup"><span data-stu-id="f5b48-109">However, a control provides a user interface, while a component does not.</span></span> <span data-ttu-id="f5b48-110">控件必须派生自基控件类之一：<xref:System.Windows.Forms.Control> 或 <xref:System.Web.UI.Control>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-110">A control must derive from one of the base control classes: <xref:System.Windows.Forms.Control> or <xref:System.Web.UI.Control>.</span></span>  
  
## <a name="when-to-create-a-component"></a><span data-ttu-id="f5b48-111">创建组件的时间</span><span class="sxs-lookup"><span data-stu-id="f5b48-111">When to Create a Component</span></span>  

 <span data-ttu-id="f5b48-112">如果类将在设计图面（如 Windows 窗体设计器或 Web 窗体设计器）上使用，但没有用户界面，此类应该是一个组件并实现 <xref:System.ComponentModel.IComponent>，或者是从直接或间接实现 <xref:System.ComponentModel.IComponent> 的类派生的。</span><span class="sxs-lookup"><span data-stu-id="f5b48-112">If your class will be used on a design surface (such as the Windows Forms or Web Forms Designer) but has no user interface, it should be a component and implement <xref:System.ComponentModel.IComponent>, or derive from a class that directly or indirectly implements <xref:System.ComponentModel.IComponent>.</span></span>  
  
 <span data-ttu-id="f5b48-113"><xref:System.ComponentModel.Component> 和 <xref:System.ComponentModel.MarshalByValueComponent> 类是 <xref:System.ComponentModel.IComponent> 接口的基实现。</span><span class="sxs-lookup"><span data-stu-id="f5b48-113">The <xref:System.ComponentModel.Component> and <xref:System.ComponentModel.MarshalByValueComponent> classes are base implementations of the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="f5b48-114">这些类之间的主要区别在于 <xref:System.ComponentModel.Component> 类由引用封送，而 <xref:System.ComponentModel.IComponent> 由值封送。</span><span class="sxs-lookup"><span data-stu-id="f5b48-114">The main difference between these classes is that the <xref:System.ComponentModel.Component> class is marshaled by reference, while <xref:System.ComponentModel.IComponent> is marshaled by value.</span></span> <span data-ttu-id="f5b48-115">以下列表为实施者提供了全面的指南。</span><span class="sxs-lookup"><span data-stu-id="f5b48-115">The following list provides broad guidelines for implementers.</span></span>  
  
- <span data-ttu-id="f5b48-116">如果组件需要由引用封送，请从 <xref:System.ComponentModel.Component> 派生。</span><span class="sxs-lookup"><span data-stu-id="f5b48-116">If your component needs to be marshaled by reference, derive from <xref:System.ComponentModel.Component>.</span></span>  
  
- <span data-ttu-id="f5b48-117">如果组件需要由值封送，请从 <xref:System.ComponentModel.MarshalByValueComponent> 派生。</span><span class="sxs-lookup"><span data-stu-id="f5b48-117">If your component needs to be marshaled by value, derive from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
- <span data-ttu-id="f5b48-118">如果因单一继承导致无法从其中一个基实现派生组件，则请实现 <xref:System.ComponentModel.IComponent>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-118">If your component cannot derive from one of the base implementations due to single inheritance, implement <xref:System.ComponentModel.IComponent>.</span></span>  
  
## <a name="component-classes"></a><span data-ttu-id="f5b48-119">组件类</span><span class="sxs-lookup"><span data-stu-id="f5b48-119">Component Classes</span></span>  

 <span data-ttu-id="f5b48-120"><xref:System.ComponentModel> 命名空间提供用于实现组件和控件的运行时和设计时行为的类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-120">The <xref:System.ComponentModel> namespace provides classes that are used to implement the run-time and design-time behavior of components and controls.</span></span> <span data-ttu-id="f5b48-121">此命名空间包括用于特性和类型转换器的实现、数据源绑定和组件授权的基类和接口。</span><span class="sxs-lookup"><span data-stu-id="f5b48-121">This namespace includes the base classes and interfaces for implementing attributes and type converters, binding to data sources, and licensing components.</span></span>  
  
 <span data-ttu-id="f5b48-122">核心组件类包括：</span><span class="sxs-lookup"><span data-stu-id="f5b48-122">The core component classes are:</span></span>  
  
- <span data-ttu-id="f5b48-123"><xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-123"><xref:System.ComponentModel.Component>.</span></span> <span data-ttu-id="f5b48-124"><xref:System.ComponentModel.IComponent> 接口的基实现。</span><span class="sxs-lookup"><span data-stu-id="f5b48-124">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span> <span data-ttu-id="f5b48-125">此类可以实现在应用程序之间共享对象。</span><span class="sxs-lookup"><span data-stu-id="f5b48-125">This class enables object sharing between applications.</span></span>  
  
- <span data-ttu-id="f5b48-126"><xref:System.ComponentModel.MarshalByValueComponent>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-126"><xref:System.ComponentModel.MarshalByValueComponent>.</span></span> <span data-ttu-id="f5b48-127"><xref:System.ComponentModel.IComponent> 接口的基实现。</span><span class="sxs-lookup"><span data-stu-id="f5b48-127">A base implementation for the <xref:System.ComponentModel.IComponent> interface.</span></span>  
  
- <span data-ttu-id="f5b48-128"><xref:System.ComponentModel.Container>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-128"><xref:System.ComponentModel.Container>.</span></span> <span data-ttu-id="f5b48-129"><xref:System.ComponentModel.IContainer> 接口的基实现。</span><span class="sxs-lookup"><span data-stu-id="f5b48-129">The base implementation for the <xref:System.ComponentModel.IContainer> interface.</span></span> <span data-ttu-id="f5b48-130">此类封装零个或多个组件。</span><span class="sxs-lookup"><span data-stu-id="f5b48-130">This class encapsulates zero or more components.</span></span>  
  
 <span data-ttu-id="f5b48-131">部分用于组件授权的类包括：</span><span class="sxs-lookup"><span data-stu-id="f5b48-131">Some of the classes used for component licensing are:</span></span>  
  
- <span data-ttu-id="f5b48-132"><xref:System.ComponentModel.License>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-132"><xref:System.ComponentModel.License>.</span></span> <span data-ttu-id="f5b48-133">所有许可证的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-133">The abstract base class for all licenses.</span></span> <span data-ttu-id="f5b48-134">对组件的特定实例授予许可证。</span><span class="sxs-lookup"><span data-stu-id="f5b48-134">A license is granted to a specific instance of a component.</span></span>  
  
- <span data-ttu-id="f5b48-135"><xref:System.ComponentModel.LicenseManager>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-135"><xref:System.ComponentModel.LicenseManager>.</span></span> <span data-ttu-id="f5b48-136">提供属性和方法，用以将许可证添加到组件和管理 <xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-136">Provides properties and methods to add a license to a component and to manage a <xref:System.ComponentModel.LicenseProvider>.</span></span>  
  
- <span data-ttu-id="f5b48-137"><xref:System.ComponentModel.LicenseProvider>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-137"><xref:System.ComponentModel.LicenseProvider>.</span></span> <span data-ttu-id="f5b48-138">实现许可证提供程序的抽象基类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-138">The abstract base class for implementing a license provider.</span></span>  
  
- <span data-ttu-id="f5b48-139"><xref:System.ComponentModel.LicenseProviderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-139"><xref:System.ComponentModel.LicenseProviderAttribute>.</span></span> <span data-ttu-id="f5b48-140">指定要与某个类一起使用的 <xref:System.ComponentModel.LicenseProvider> 类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-140">Specifies the <xref:System.ComponentModel.LicenseProvider> class to use with a class.</span></span>  
  
 <span data-ttu-id="f5b48-141">常用于描述和保存组件的类。</span><span class="sxs-lookup"><span data-stu-id="f5b48-141">Classes commonly used for describing and persisting components.</span></span>  
  
- <span data-ttu-id="f5b48-142"><xref:System.ComponentModel.TypeDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-142"><xref:System.ComponentModel.TypeDescriptor>.</span></span> <span data-ttu-id="f5b48-143">提供有关组件特征的信息，如组件的特性、属性和事件。</span><span class="sxs-lookup"><span data-stu-id="f5b48-143">Provides information about the characteristics for a component, such as its attributes, properties, and events.</span></span>  
  
- <span data-ttu-id="f5b48-144"><xref:System.ComponentModel.EventDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-144"><xref:System.ComponentModel.EventDescriptor>.</span></span> <span data-ttu-id="f5b48-145">提供有关事件的信息。</span><span class="sxs-lookup"><span data-stu-id="f5b48-145">Provides information about an event.</span></span>  
  
- <span data-ttu-id="f5b48-146"><xref:System.ComponentModel.PropertyDescriptor>。</span><span class="sxs-lookup"><span data-stu-id="f5b48-146"><xref:System.ComponentModel.PropertyDescriptor>.</span></span> <span data-ttu-id="f5b48-147">提供有关属性的信息。</span><span class="sxs-lookup"><span data-stu-id="f5b48-147">Provides information about a property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5b48-148">相关章节</span><span class="sxs-lookup"><span data-stu-id="f5b48-148">Related Sections</span></span>  

 [<span data-ttu-id="f5b48-149">控件和组件创作疑难解答</span><span class="sxs-lookup"><span data-stu-id="f5b48-149">Troubleshooting Control and Component Authoring</span></span>](/dotnet/desktop/winforms/controls/troubleshooting-control-and-component-authoring)  
 <span data-ttu-id="f5b48-150">解释如何解决常见问题。</span><span class="sxs-lookup"><span data-stu-id="f5b48-150">Explains how to fix common problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b48-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5b48-151">See also</span></span>

- [<span data-ttu-id="f5b48-152">如何：在 Windows 窗体中访问设计时支持</span><span class="sxs-lookup"><span data-stu-id="f5b48-152">How to: Access Design-Time Support in Windows Forms</span></span>](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)
