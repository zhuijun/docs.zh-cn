---
title: .NET Framework 加密模型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography [.NET Framework], model
- encryption [.NET Framework], model
ms.assetid: 12fecad4-fbab-432a-bade-2f05976a2971
ms.openlocfilehash: c2d28abacd34736764b69be750a850a0f2e8db85
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288376"
---
# <a name="net-framework-cryptography-model"></a><span data-ttu-id="3e1f3-102">.NET Framework 加密模型</span><span class="sxs-lookup"><span data-stu-id="3e1f3-102">.NET Framework Cryptography Model</span></span>

<span data-ttu-id="3e1f3-103">.NET Framework 提供了许多标准加密算法的实现。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-103">The .NET Framework provides implementations of many standard cryptographic algorithms.</span></span> <span data-ttu-id="3e1f3-104">这些算法易于使用且具有最安全的可能默认属性。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-104">These algorithms are easy to use and have the safest possible default properties.</span></span> <span data-ttu-id="3e1f3-105">此外，对象继承、流设计和配置的 .NET Framework 加密模型完全可扩展。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-105">In addition, the .NET Framework cryptography model of object inheritance, stream design, and configuration is extremely extensible.</span></span>

## <a name="object-inheritance"></a><span data-ttu-id="3e1f3-106">对象继承</span><span class="sxs-lookup"><span data-stu-id="3e1f3-106">Object Inheritance</span></span>

<span data-ttu-id="3e1f3-107">.NET Framework 安全系统实现派生类继承的可扩展模式。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-107">The .NET Framework security system implements an extensible pattern of derived class inheritance.</span></span> <span data-ttu-id="3e1f3-108">层次结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-108">The hierarchy is as follows:</span></span>

- <span data-ttu-id="3e1f3-109">算法类型类，如 <xref:System.Security.Cryptography.SymmetricAlgorithm>、<xref:System.Security.Cryptography.AsymmetricAlgorithm> 或 <xref:System.Security.Cryptography.HashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-109">Algorithm type class, such as <xref:System.Security.Cryptography.SymmetricAlgorithm>,  <xref:System.Security.Cryptography.AsymmetricAlgorithm> or <xref:System.Security.Cryptography.HashAlgorithm>.</span></span> <span data-ttu-id="3e1f3-110">此级别是抽象的。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-110">This level is abstract.</span></span>

- <span data-ttu-id="3e1f3-111">从算法类型类继承的算法类；例如，<xref:System.Security.Cryptography.Aes>、<xref:System.Security.Cryptography.RC2> 或 <xref:System.Security.Cryptography.ECDiffieHellman>。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-111">Algorithm class that inherits from an algorithm type class; for example, <xref:System.Security.Cryptography.Aes>, <xref:System.Security.Cryptography.RC2>, or <xref:System.Security.Cryptography.ECDiffieHellman>.</span></span> <span data-ttu-id="3e1f3-112">此级别是抽象的。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-112">This level is abstract.</span></span>

- <span data-ttu-id="3e1f3-113">从算法类继承的算法类实现；例如，<xref:System.Security.Cryptography.AesManaged>、<xref:System.Security.Cryptography.RC2CryptoServiceProvider> 或 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-113">Implementation of an algorithm class that inherits from an algorithm class; for example, <xref:System.Security.Cryptography.AesManaged>, <xref:System.Security.Cryptography.RC2CryptoServiceProvider>, or <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3e1f3-114">此级别已完全实现。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-114">This level is fully implemented.</span></span>

<span data-ttu-id="3e1f3-115">使用此模式派生类，可轻松添加新算法或现有算法的新实现。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-115">Using this pattern of derived classes, it is easy to add a new algorithm or a new implementation of an existing algorithm.</span></span> <span data-ttu-id="3e1f3-116">例如，要创建新的公共密钥算法，你会继承 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 类。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-116">For example, to create a new public-key algorithm, you would inherit from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class.</span></span> <span data-ttu-id="3e1f3-117">要创建特定算法的新实现，将需要创建该算法的非抽象派生类。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-117">To create a new implementation of a specific algorithm, you would create a non-abstract derived class of that algorithm.</span></span>

## <a name="how-algorithms-are-implemented-in-the-net-framework"></a><span data-ttu-id="3e1f3-118">算法在 .NET Framework 中的实现方式</span><span class="sxs-lookup"><span data-stu-id="3e1f3-118">How Algorithms Are Implemented in the .NET Framework</span></span>

<span data-ttu-id="3e1f3-119">作为可用于一种算法的不同实现的示例，请考虑对称算法。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-119">As an example of the different implementations available for an algorithm, consider symmetric algorithms.</span></span> <span data-ttu-id="3e1f3-120">所有对称算法都基于 <xref:System.Security.Cryptography.SymmetricAlgorithm>，它由以下算法继承：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-120">The base for all symmetric algorithms is <xref:System.Security.Cryptography.SymmetricAlgorithm>, which is inherited by the following algorithms:</span></span>

* <xref:System.Security.Cryptography.Aes>
* <xref:System.Security.Cryptography.DES>
* <xref:System.Security.Cryptography.RC2>
* <xref:System.Security.Cryptography.Rijndael>
* <xref:System.Security.Cryptography.TripleDES>

<span data-ttu-id="3e1f3-121"><xref:System.Security.Cryptography.Aes> 由两个类继承：<xref:System.Security.Cryptography.AesCryptoServiceProvider> 和 <xref:System.Security.Cryptography.AesManaged>。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-121"><xref:System.Security.Cryptography.Aes> is inherited by two classes: <xref:System.Security.Cryptography.AesCryptoServiceProvider> and <xref:System.Security.Cryptography.AesManaged>.</span></span> <span data-ttu-id="3e1f3-122"><xref:System.Security.Cryptography.AesCryptoServiceProvider> 类是围绕 Aes 的 Windows 加密 API (CAPI) 实现的包装器，而 <xref:System.Security.Cryptography.AesManaged> 类完全用托管代码编写。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-122">The <xref:System.Security.Cryptography.AesCryptoServiceProvider> class is a wrapper around the Windows Cryptography API (CAPI) implementation of Aes, whereas the <xref:System.Security.Cryptography.AesManaged> class is written entirely in managed code.</span></span> <span data-ttu-id="3e1f3-123">除托管和 CAPI 实现外，还有第三种类型的实现，即下一代加密技术 (CNG)。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-123">There is also a third type of implementation, Cryptography Next Generation (CNG), in addition to the managed and CAPI implementations.</span></span> <span data-ttu-id="3e1f3-124">CNG 算法的一个示例是 <xref:System.Security.Cryptography.ECDiffieHellmanCng>。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-124">An example of a CNG algorithm is <xref:System.Security.Cryptography.ECDiffieHellmanCng>.</span></span> <span data-ttu-id="3e1f3-125">CNG 算法在 Windows Vista 和更高版本中都可用。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-125">CNG algorithms are available on Windows Vista and later.</span></span>

<span data-ttu-id="3e1f3-126">你可以选择最适合自己的实现。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-126">You can choose which implementation is best for you.</span></span> <span data-ttu-id="3e1f3-127">托管实现在支持 .NET Framework 的所有平台上可用。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-127">The managed implementations are available on all platforms that support .NET Framework.</span></span> <span data-ttu-id="3e1f3-128">CAPI 实现在较早版本的操作系统上可用，不再进行开发。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-128">The CAPI implementations are available on older operating systems and are no longer being developed.</span></span> <span data-ttu-id="3e1f3-129">CNG 是要在其中进行新开发的最新实现。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-129">CNG is the latest implementation where new development will take place.</span></span> <span data-ttu-id="3e1f3-130">但是，托管实现未获得美国联邦信息处理标准 (FIPS) 认证，并且可能比包装器类更慢。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-130">However, the managed implementations are not certified by the Federal Information Processing Standards (FIPS), and may be slower than the wrapper classes.</span></span>

## <a name="stream-design"></a><span data-ttu-id="3e1f3-131">流设计</span><span class="sxs-lookup"><span data-stu-id="3e1f3-131">Stream Design</span></span>

<span data-ttu-id="3e1f3-132">公共语言运行时使用面向流的设计实现对称算法和哈希算法。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-132">The common language runtime uses a stream-oriented design for implementing symmetric algorithms and hash algorithms.</span></span> <span data-ttu-id="3e1f3-133">这种设计的核心是 <xref:System.Security.Cryptography.CryptoStream> 类，该类派生自 <xref:System.IO.Stream> 类。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-133">The core of this design is the <xref:System.Security.Cryptography.CryptoStream> class, which derives from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="3e1f3-134">基于流的加密对象支持用于处理对象的数据传输部分的单个标准接口 (`CryptoStream`)。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-134">Stream-based cryptographic objects support a single standard interface (`CryptoStream`) for handling the data transfer portion of the object.</span></span> <span data-ttu-id="3e1f3-135">由于所有对象都基于标准接口，因此可以将多个对象（例如，一个哈希对象后跟一个加密对象）链接起来，且无需任何中间存储来对数据执行多个操作。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-135">Because all the objects are built on a standard interface, you can chain together multiple objects (such as a hash object followed by an encryption object), and you can perform multiple operations on the data without needing any intermediate storage for it.</span></span> <span data-ttu-id="3e1f3-136">使用流模型还可以从更小的对象生成对象。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-136">The streaming model also enables you to build objects from smaller objects.</span></span> <span data-ttu-id="3e1f3-137">例如，尽管该对象可能从一组流对象中生成，组合的加密和哈希算法仍可视为单个流对象。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-137">For example, a combined encryption and hash algorithm can be viewed as a single stream object, although this object might be built from a set of stream objects.</span></span>

## <a name="cryptographic-configuration"></a><span data-ttu-id="3e1f3-138">加密配置</span><span class="sxs-lookup"><span data-stu-id="3e1f3-138">Cryptographic Configuration</span></span>

<span data-ttu-id="3e1f3-139">使用加密配置可将算法的特定实现解析为算法名称，从而允许 .NET Framework 加密类扩展性。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-139">Cryptographic configuration lets you resolve a specific implementation of an algorithm to an algorithm name, allowing extensibility of the .NET Framework cryptography classes.</span></span> <span data-ttu-id="3e1f3-140">可以添加自己算法的硬件或软件实现，并将该实现映射到所选择的算法名称。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-140">You can add your own hardware or software implementation of an algorithm and map the implementation to the algorithm name of your choice.</span></span> <span data-ttu-id="3e1f3-141">如果配置文件中未指定算法，则使用默认设置。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-141">If an algorithm is not specified in the configuration file, the default settings are used.</span></span> <span data-ttu-id="3e1f3-142">有关加密配置的详细信息，请参阅[配置加密类](../../framework/configure-apps/configure-cryptography-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-142">For more information about cryptographic configuration, see [Configuring Cryptography Classes](../../framework/configure-apps/configure-cryptography-classes.md).</span></span>

## <a name="choosing-an-algorithm"></a><span data-ttu-id="3e1f3-143">选择算法</span><span class="sxs-lookup"><span data-stu-id="3e1f3-143">Choosing an Algorithm</span></span>

<span data-ttu-id="3e1f3-144">可以出于各种原因选择一种算法：例如，为了保护数据完整性，为了保护数据隐私或为了生成密钥。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-144">You can select an algorithm for different reasons: for example, for data integrity, for data privacy, or to generate a key.</span></span> <span data-ttu-id="3e1f3-145">为了保护完整性（防止更改）或保护隐私（防止查看），对称算法和哈希算法用于保护数据。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-145">Symmetric and hash algorithms are intended for protecting data for either integrity reasons (protect from change) or privacy reasons (protect from viewing).</span></span> <span data-ttu-id="3e1f3-146">哈希算法主要用于保护数据完整性。</span><span class="sxs-lookup"><span data-stu-id="3e1f3-146">Hash algorithms are used primarily for data integrity.</span></span>

<span data-ttu-id="3e1f3-147">下面是按应用程序分类的建议算法列表：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-147">Here is a list of recommended algorithms by application:</span></span>

- <span data-ttu-id="3e1f3-148">数据隐私：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-148">Data privacy:</span></span>
  - <xref:System.Security.Cryptography.Aes>
- <span data-ttu-id="3e1f3-149">数据完整性：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-149">Data integrity:</span></span>
  - <xref:System.Security.Cryptography.HMACSHA256>
  - <xref:System.Security.Cryptography.HMACSHA512>
- <span data-ttu-id="3e1f3-150">数字签名：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-150">Digital signature:</span></span>
  - <xref:System.Security.Cryptography.ECDsa>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="3e1f3-151">密钥交换：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-151">Key exchange:</span></span>
  - <xref:System.Security.Cryptography.ECDiffieHellman>
  - <xref:System.Security.Cryptography.RSA>
- <span data-ttu-id="3e1f3-152">随机数生成：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-152">Random number generation:</span></span>
  - <xref:System.Security.Cryptography.RNGCryptoServiceProvider>
- <span data-ttu-id="3e1f3-153">从密码生成密钥：</span><span class="sxs-lookup"><span data-stu-id="3e1f3-153">Generating a key from a password:</span></span>
  - <xref:System.Security.Cryptography.Rfc2898DeriveBytes>

## <a name="see-also"></a><span data-ttu-id="3e1f3-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3e1f3-154">See also</span></span>

- [<span data-ttu-id="3e1f3-155">加密服务</span><span class="sxs-lookup"><span data-stu-id="3e1f3-155">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="3e1f3-156">使用 C 中的 Bruce Schneier 应用加密协议、算法和源代码</span><span class="sxs-lookup"><span data-stu-id="3e1f3-156">Applied Cryptography Protocols, Algorithms, and Source Code in C, by Bruce Schneier</span></span>](https://www.schneier.com/books/applied_cryptography/)
