---
title: My.WebServices 对象
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 0b63b44c2cd9d55094fb83fed6c04e4de528a25c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867209"
---
# <a name="mywebservices-object"></a><span data-ttu-id="d1dfa-102">My.WebServices 对象</span><span class="sxs-lookup"><span data-stu-id="d1dfa-102">My.WebServices Object</span></span>

<span data-ttu-id="d1dfa-103">提供用于创建和访问当前项目所引用的每个 XML Web service 的单个实例的属性。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1dfa-104">备注</span><span class="sxs-lookup"><span data-stu-id="d1dfa-104">Remarks</span></span>  

 <span data-ttu-id="d1dfa-105">`My.WebServices` 对象提供当前项目所引用的每个 Web 服务的实例。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="d1dfa-106">按需实例化每个实例。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="d1dfa-107">可以通过 `My.WebServices` 对象的属性访问这些 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="d1dfa-108">该属性的名称与该属性所访问的 Web 服务的名称相同。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="d1dfa-109">任何自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 继承的类均为 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="d1dfa-110">有关将 Web 服务添加到项目的信息，请参阅 [访问应用程序 Web 服务](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="d1dfa-111">`My.WebServices`对象只公开与当前项目相关联的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="d1dfa-112">它不提供对引用 Dll 中声明的 Web 服务的访问权限。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="d1dfa-113">若要访问 DLL 提供的 Web 服务，必须使用 Web 服务的限定名称，格式为 *DllName*。*WebServiceName*。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="d1dfa-114">有关详细信息，请参阅 [访问应用程序 Web 服务](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-114">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="d1dfa-115">对象及其属性不适用于 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1dfa-116">属性</span><span class="sxs-lookup"><span data-stu-id="d1dfa-116">Properties</span></span>  

 <span data-ttu-id="d1dfa-117">对象的每个属性都 `My.WebServices` 提供对当前项目所引用的 Web 服务的实例的访问。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="d1dfa-118">属性的名称与属性所访问的 Web 服务的名称相同，属性类型与 Web 服务的类型相同。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1dfa-119">如果存在名称冲突，则用于访问 Web 服务的属性名称为*RootNamespace*_*Namespace* \_ *ServiceName*。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="d1dfa-120">例如，请考虑两个名为 `Service1` 的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="d1dfa-121">如果这些服务之一位于根命名空间 `WindowsApplication1` 和命名空间中 `Namespace1` ，则可以使用来访问该服务 `My.WebServices.WindowsApplication1_Namespace1_Service1` 。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="d1dfa-122">首次访问某个 `My.WebServices` 对象的属性时，它将创建 Web 服务的新实例并将其存储。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="d1dfa-123">此属性的后续访问将返回该 Web 服务的实例。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="d1dfa-124">可以通过 `Nothing` 将分配给 web 服务的属性来释放 web 服务。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="d1dfa-125">属性 setter 分配 `Nothing` 给存储的值。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="d1dfa-126">如果为属性分配除以外的任何值 `Nothing` ，则 setter 会引发 <xref:System.ArgumentException> 异常。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="d1dfa-127">您可以 `My.WebServices` 使用 or 运算符测试对象的属性是否存储了 Web 服务的实例 `Is` `IsNot` 。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="d1dfa-128">您可以使用这些运算符来检查属性的值是否为 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1dfa-129">通常， `Is` 或 `IsNot` 运算符必须读取属性的值才能执行比较。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="d1dfa-130">但是，如果属性当前存储 `Nothing` ，则属性创建 Web 服务的新实例，然后返回该实例。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="d1dfa-131">不过，Visual Basic 编译器会专门处理对象的属性 `My.WebServices` ，并允许 `Is` 或 `IsNot` 运算符检查属性的状态，而无需更改其值。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1dfa-132">示例</span><span class="sxs-lookup"><span data-stu-id="d1dfa-132">Example</span></span>  

 <span data-ttu-id="d1dfa-133">此示例调用 `FahrenheitToCelsius` XML Web service 的方法 `TemperatureConverter` ，并返回结果。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="d1dfa-134">要使此示例正常运行，你的项目必须引用名为的 Web 服务 `Converter` ，并且该 web 服务必须公开 `ConvertTemperature` 方法。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="d1dfa-135">有关详细信息，请参阅 [访问应用程序 Web 服务](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-135">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="d1dfa-136">此代码在 Web 应用程序项目中不起作用。</span><span class="sxs-lookup"><span data-stu-id="d1dfa-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1dfa-137">要求</span><span class="sxs-lookup"><span data-stu-id="d1dfa-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="d1dfa-138">按项目类型的可用性</span><span class="sxs-lookup"><span data-stu-id="d1dfa-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="d1dfa-139">项目类型</span><span class="sxs-lookup"><span data-stu-id="d1dfa-139">Project type</span></span>|<span data-ttu-id="d1dfa-140">可用</span><span class="sxs-lookup"><span data-stu-id="d1dfa-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="d1dfa-141">Windows 应用程序</span><span class="sxs-lookup"><span data-stu-id="d1dfa-141">Windows Application</span></span>|<span data-ttu-id="d1dfa-142">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-142">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-143">类库</span><span class="sxs-lookup"><span data-stu-id="d1dfa-143">Class Library</span></span>|<span data-ttu-id="d1dfa-144">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-144">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-145">控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="d1dfa-145">Console Application</span></span>|<span data-ttu-id="d1dfa-146">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-146">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-147">Windows 控件库</span><span class="sxs-lookup"><span data-stu-id="d1dfa-147">Windows Control Library</span></span>|<span data-ttu-id="d1dfa-148">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-148">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-149">Web 控件库</span><span class="sxs-lookup"><span data-stu-id="d1dfa-149">Web Control Library</span></span>|<span data-ttu-id="d1dfa-150">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-150">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-151">Windows 服务</span><span class="sxs-lookup"><span data-stu-id="d1dfa-151">Windows Service</span></span>|<span data-ttu-id="d1dfa-152">**是**</span><span class="sxs-lookup"><span data-stu-id="d1dfa-152">**Yes**</span></span>|  
|<span data-ttu-id="d1dfa-153">网站</span><span class="sxs-lookup"><span data-stu-id="d1dfa-153">Web Site</span></span>|<span data-ttu-id="d1dfa-154">否</span><span class="sxs-lookup"><span data-stu-id="d1dfa-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1dfa-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d1dfa-155">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="d1dfa-156">访问应用程序 Web 服务</span><span class="sxs-lookup"><span data-stu-id="d1dfa-156">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
