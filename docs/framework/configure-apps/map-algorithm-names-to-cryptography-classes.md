---
title: 将算法名称映射到加密类
description: 在 .NET 中将算法名称映射到加密类。 开发人员有四个选项用于创建加密对象。
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: b67db612496e56a341dab2e5fc4b52c954ff02b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183385"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="7f755-104">将算法名称映射到加密类</span><span class="sxs-lookup"><span data-stu-id="7f755-104">Mapping Algorithm Names to Cryptography Classes</span></span>

<span data-ttu-id="7f755-105">开发人员可通过以下四种方式使用 Windows SDK 创建加密对象：</span><span class="sxs-lookup"><span data-stu-id="7f755-105">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="7f755-106">使用 **new** 运算符创建对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-106">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="7f755-107">通过对该算法的抽象类调用 **create** 方法，创建实现特定加密算法的对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-107">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="7f755-108">通过调用方法，创建实现特定加密算法的对象 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7f755-108">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="7f755-109">创建一个对象，该对象实现一类加密算法 (如对称块加密) 方法是在该类型算法的抽象类上调用 **Create** 方法 (例如 <xref:System.Security.Cryptography.SymmetricAlgorithm>) 。</span><span class="sxs-lookup"><span data-stu-id="7f755-109">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="7f755-110">例如，假设开发人员想要计算一组字节的 SHA1 哈希。</span><span class="sxs-lookup"><span data-stu-id="7f755-110">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="7f755-111"><xref:System.Security.Cryptography>命名空间包含 SHA1 算法的两个实现，一个纯粹的托管实现，另一个包装 CryptoAPI。</span><span class="sxs-lookup"><span data-stu-id="7f755-111">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="7f755-112">开发人员可以选择实例化特定的 SHA1 实现 (如 <xref:System.Security.Cryptography.SHA1Managed>) 通过调用 **new** 运算符来实现）。</span><span class="sxs-lookup"><span data-stu-id="7f755-112">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="7f755-113">但是，如果公共语言运行时加载哪个类（只要类实现 SHA1 哈希算法），开发人员就可以通过调用方法来创建对象 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7f755-113">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f755-114">此方法调用 \*\*CryptoConfig. cryptoconfig.createfromname ( "" \*\*，该 ) 必须返回 SHA1 哈希算法的实现。）。</span><span class="sxs-lookup"><span data-stu-id="7f755-114">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="7f755-115">开发人员还可以调用 \*\*CryptoConfig. cryptoconfig.createfromname ( "SHA1" ) \*\* ，因为在默认情况下，加密配置包括 .NET Framework 附带的算法的短名称。</span><span class="sxs-lookup"><span data-stu-id="7f755-115">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="7f755-116">如果使用的哈希算法并不重要，开发人员可以调用 <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> 方法，这将返回实现哈希转换的对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-116">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="7f755-117">在配置文件中映射算法名称</span><span class="sxs-lookup"><span data-stu-id="7f755-117">Mapping Algorithm Names in Configuration Files</span></span>  

 <span data-ttu-id="7f755-118">默认情况下，运行时 <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> 为所有四个方案返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-118">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="7f755-119">但是，计算机管理员可以更改最后两个方案中的方法返回的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="7f755-119">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="7f755-120">为此，必须将友好算法名称映射到要在计算机配置文件中使用的类 ( # A0) 。</span><span class="sxs-lookup"><span data-stu-id="7f755-120">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="7f755-121">下面的示例演示如何配置运行时，使**CryptoConfig，cryptoconfig.createfromname ( "SHA1" ) **，以及**HashAlgorithm**返回对象**的类型为**""，然后返回一个 `MySHA1HashClass` 对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-121">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="7f755-122">您可以在 [<的 cryptoClass \> 元素](./file-schema/cryptography/cryptoclass-element.md) 中指定属性的名称 (上一个示例将该属性命名 `MySHA1Hash`) 。</span><span class="sxs-lookup"><span data-stu-id="7f755-122">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="7f755-123">元素中的属性的值 **\<cryptoClass>** 是公共语言运行时用来查找类的字符串。</span><span class="sxs-lookup"><span data-stu-id="7f755-123">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="7f755-124">您可以使用满足指定 [完全限定的类型名称](../reflection-and-codedom/specifying-fully-qualified-type-names.md)中指定的要求的任何字符串。</span><span class="sxs-lookup"><span data-stu-id="7f755-124">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="7f755-125">许多算法名称可以映射到同一个类。</span><span class="sxs-lookup"><span data-stu-id="7f755-125">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="7f755-126">[ \<nameEntry> 元素](./file-schema/cryptography/nameentry-element.md)将类映射到一个友好算法名称。</span><span class="sxs-lookup"><span data-stu-id="7f755-126">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="7f755-127">**Name**属性可以是在调用**CryptoConfig. cryptoconfig.createfromname**方法时使用的字符串，也可以是命名空间中抽象加密类的名称 <xref:System.Security.Cryptography> 。</span><span class="sxs-lookup"><span data-stu-id="7f755-127">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="7f755-128">**Class**特性的值是元素中的特性的名称 **\<cryptoClass>** 。</span><span class="sxs-lookup"><span data-stu-id="7f755-128">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f755-129">可以通过调用 <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> 或 \*\*CryptoConfig. cryptoconfig.createfromname ( "sha1" ) \*\* 方法来获取 SHA1 算法。</span><span class="sxs-lookup"><span data-stu-id="7f755-129">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="7f755-130">每个方法仅保证返回实现 SHA1 算法的对象。</span><span class="sxs-lookup"><span data-stu-id="7f755-130">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="7f755-131">不需要将算法的每个友好名称映射到配置文件中的相同类。</span><span class="sxs-lookup"><span data-stu-id="7f755-131">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="7f755-132">有关默认名称及其映射到的类的列表，请参阅 <xref:System.Security.Cryptography.CryptoConfig> 。</span><span class="sxs-lookup"><span data-stu-id="7f755-132">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f755-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f755-133">See also</span></span>

- [<span data-ttu-id="7f755-134">加密服务</span><span class="sxs-lookup"><span data-stu-id="7f755-134">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="7f755-135">配置加密类</span><span class="sxs-lookup"><span data-stu-id="7f755-135">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
