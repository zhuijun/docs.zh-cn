---
title: 演练：创建加密应用程序
description: 演练如何创建加密应用程序。 了解如何对 Windows 窗体应用程序中的内容进行加密和解密。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 72116227fbec2435d428ad2bbdb4cc74e5c3663f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602175"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="3f7d8-104">演练：创建加密应用程序</span><span class="sxs-lookup"><span data-stu-id="3f7d8-104">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="3f7d8-105">本演练演示如何对内容进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-105">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="3f7d8-106">下面的代码示例是特为 Windows 窗体应用程序设计的。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-106">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="3f7d8-107">此应用程序不演示实际方案，例如使用智能卡。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-107">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="3f7d8-108">而演示加密和解密的基础知识。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-108">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="3f7d8-109">本演练使用以下加密原则：</span><span class="sxs-lookup"><span data-stu-id="3f7d8-109">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="3f7d8-110">使用 <xref:System.Security.Cryptography.RijndaelManaged> 类（一种对称算法），用于通过使用其自动生成的 <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> 和 <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> 来加密和解密数据。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-110">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="3f7d8-111">使用 <xref:System.Security.Cryptography.RSACryptoServiceProvider>（一种非对称算法），对由 <xref:System.Security.Cryptography.RijndaelManaged> 加密的数据的密钥进行加密和解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-111">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="3f7d8-112">非对称算法最适用于较少的数据，如密钥。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-112">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3f7d8-113">如果要保护计算机上的数据（而不是与他人交换加密内容），可考虑使用 <xref:System.Security.Cryptography.ProtectedData> 或 <xref:System.Security.Cryptography.ProtectedMemory> 类。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-113">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="3f7d8-114">下表总结了本主题中的加密任务。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-114">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="3f7d8-115">任务</span><span class="sxs-lookup"><span data-stu-id="3f7d8-115">Task</span></span>|<span data-ttu-id="3f7d8-116">说明</span><span class="sxs-lookup"><span data-stu-id="3f7d8-116">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="3f7d8-117">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="3f7d8-117">Creating a Windows Forms application</span></span>|<span data-ttu-id="3f7d8-118">列出运行该应用程序所需的控件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-118">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="3f7d8-119">声明全局对象</span><span class="sxs-lookup"><span data-stu-id="3f7d8-119">Declaring global objects</span></span>|<span data-ttu-id="3f7d8-120">声明字符串路径变量 <xref:System.Security.Cryptography.CspParameters> 和 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 具有 <xref:System.Windows.Forms.Form> 类的全局上下文。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-120">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="3f7d8-121">创建非对称密钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-121">Creating an asymmetric key</span></span>|<span data-ttu-id="3f7d8-122">创建非对称公钥和私钥值对，并为其分配一个密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-122">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="3f7d8-123">加密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-123">Encrypting a file</span></span>|<span data-ttu-id="3f7d8-124">显示对话框，以便选择供加密的文件，并对该文件进行加密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-124">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="3f7d8-125">解密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-125">Decrypting a file</span></span>|<span data-ttu-id="3f7d8-126">显示对话框，以便选择供解密的已加密文件，并对该文件进行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-126">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="3f7d8-127">获取私钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-127">Getting a private key</span></span>|<span data-ttu-id="3f7d8-128">获取使用密钥容器名称的完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-128">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="3f7d8-129">导出公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-129">Exporting a public key</span></span>|<span data-ttu-id="3f7d8-130">将密钥保存到只带有公共参数的 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-130">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="3f7d8-131">导入公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-131">Importing a public key</span></span>|<span data-ttu-id="3f7d8-132">将密钥从 XML 文件加载到密钥容器中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-132">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="3f7d8-133">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="3f7d8-133">Testing the application</span></span>|<span data-ttu-id="3f7d8-134">列出用于测试此应用程序的步骤。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-134">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="3f7d8-135">必备条件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-135">Prerequisites</span></span>  
 <span data-ttu-id="3f7d8-136">您需要满足以下条件才能完成本演练：</span><span class="sxs-lookup"><span data-stu-id="3f7d8-136">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="3f7d8-137">对 <xref:System.IO> 和 <xref:System.Security.Cryptography> 命名空间的引用。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-137">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="3f7d8-138">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="3f7d8-138">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="3f7d8-139">本演练中的大多数代码示例均设计为按钮控件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-139">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="3f7d8-140">下表列出了示例应用程序所需的控件及其匹配代码示例所需的名称。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-140">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="3f7d8-141">控制</span><span class="sxs-lookup"><span data-stu-id="3f7d8-141">Control</span></span>|<span data-ttu-id="3f7d8-142">名称</span><span class="sxs-lookup"><span data-stu-id="3f7d8-142">Name</span></span>|<span data-ttu-id="3f7d8-143">文本属性（根据需要）</span><span class="sxs-lookup"><span data-stu-id="3f7d8-143">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="3f7d8-144">加密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-144">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="3f7d8-145">解密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-145">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="3f7d8-146">创建密钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-146">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="3f7d8-147">导出公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-147">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="3f7d8-148">导入公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-148">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="3f7d8-149">获取私钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-149">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="3f7d8-150">未设置键</span><span class="sxs-lookup"><span data-stu-id="3f7d8-150">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="3f7d8-151">双击 Visual Studio 设计器中的按钮可创建其事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-151">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="3f7d8-152">声明全局对象</span><span class="sxs-lookup"><span data-stu-id="3f7d8-152">Declaring Global Objects</span></span>  
 <span data-ttu-id="3f7d8-153">将以下代码添加到窗体的构造函数中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-153">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="3f7d8-154">编辑环境和首选项的字符串变量。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-154">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="3f7d8-155">创建非对称密钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-155">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="3f7d8-156">此任务创建可对 <xref:System.Security.Cryptography.RijndaelManaged> 密钥进行加密和解密的非对称密钥。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-156">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="3f7d8-157">此密钥用于加密内容，并且它将显示标签控件上的密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-157">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="3f7d8-158">将以下代码添加为 `Create Keys` 按钮 (`buttonCreateAsmKeys_Click`) 的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-158">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="3f7d8-159">加密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-159">Encrypting a File</span></span>  
 <span data-ttu-id="3f7d8-160">此任务涉及两种方法： `Encrypt File` 按钮（ `buttonEncryptFile_Click` ）和方法的事件处理程序方法 `EncryptFile` 。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-160">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="3f7d8-161">第一种方法显示一个用于选择文件的对话框，并将文件名传递给第二种方法，后者将执行加密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-161">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="3f7d8-162">加密的内容、密钥和 IV 全都保存到一个 <xref:System.IO.FileStream> 中，这被称为加密包。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-162">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="3f7d8-163">`EncryptFile` 方法执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3f7d8-163">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="3f7d8-164">创建 <xref:System.Security.Cryptography.RijndaelManaged> 对称算法，以便对内容进行加密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-164">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="3f7d8-165">创建 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象，以便对 <xref:System.Security.Cryptography.RijndaelManaged> 密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-165">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="3f7d8-166">使用 <xref:System.Security.Cryptography.CryptoStream> 对象读取源文件的 <xref:System.IO.FileStream>，并将其加密到已加密文件的目标 <xref:System.IO.FileStream> 对象中（以字节块为单位）。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-166">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="3f7d8-167">确定加密密钥和 IV 的长度并创建其长度值的字节数组。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-167">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="3f7d8-168">将密钥、IV 及其长度值写入已加密的包。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-168">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="3f7d8-169">加密包使用以下格式：</span><span class="sxs-lookup"><span data-stu-id="3f7d8-169">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="3f7d8-170">密钥长度，字节数 0 - 3</span><span class="sxs-lookup"><span data-stu-id="3f7d8-170">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="3f7d8-171">IV 长度，字节数 4 - 7</span><span class="sxs-lookup"><span data-stu-id="3f7d8-171">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="3f7d8-172">已加密的密钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-172">Encrypted key</span></span>  
  
- <span data-ttu-id="3f7d8-173">IV</span><span class="sxs-lookup"><span data-stu-id="3f7d8-173">IV</span></span>  
  
- <span data-ttu-id="3f7d8-174">密码文本</span><span class="sxs-lookup"><span data-stu-id="3f7d8-174">Cipher text</span></span>  
  
 <span data-ttu-id="3f7d8-175">可使用密钥和 IV 的长度来确定起点和加密包所有部件的长度，然后可使用它们来解密文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-175">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="3f7d8-176">将以下代码添加为 `Encrypt File` 按钮 (`buttonEncryptFile_Click`) 的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-176">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="3f7d8-177">将下面的 `EncryptFile` 方法添加到窗体中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-177">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="3f7d8-178">解密文件</span><span class="sxs-lookup"><span data-stu-id="3f7d8-178">Decrypting a File</span></span>  
 <span data-ttu-id="3f7d8-179">此任务涉及两种方法，即 `Decrypt File` 按钮 (`buttonDecryptFile_Click`) 的事件处理程序方法和 `DecryptFile` 方法。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-179">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="3f7d8-180">第一种方法显示一个用于选择文件的对话框，并将其文件名传递给第二种方法，后者将执行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-180">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="3f7d8-181">`Decrypt` 方法执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3f7d8-181">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="3f7d8-182">创建 <xref:System.Security.Cryptography.RijndaelManaged> 对称算法，以便对内容进行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-182">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="3f7d8-183">将已加密包的 <xref:System.IO.FileStream> 的前八个字节读取到字节数组中，以便获取已加密的密钥和 IV 的长度。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-183">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="3f7d8-184">将密钥和 IV 从加密包提取到字节数组中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-184">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="3f7d8-185">创建 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 对象，以便对 <xref:System.Security.Cryptography.RijndaelManaged> 密钥进行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-185">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="3f7d8-186">使用 <xref:System.Security.Cryptography.CryptoStream> 对象来读取 <xref:System.IO.FileStream> 加密包的密码文本部分，并将其解密到已解密文件的 <xref:System.IO.FileStream> 对象中（以字节块为单位）。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-186">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="3f7d8-187">完成后，解密即完成。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-187">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="3f7d8-188">将以下代码添加为 `Decrypt File` 按钮的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-188">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="3f7d8-189">将下面的 `DecryptFile` 方法添加到窗体中。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-189">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="3f7d8-190">导出公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-190">Exporting a Public Key</span></span>  
 <span data-ttu-id="3f7d8-191">此任务将 `Create Keys` 按钮创建的密钥保存到文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-191">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="3f7d8-192">它仅导出公共参数。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-192">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="3f7d8-193">此任务模拟以下场景：Alice 把她的公钥给 Bob，从而 Bob 可为她加密文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-193">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="3f7d8-194">他和其他具有公钥的人将不能对文件进行解密，因为他们没有带专用参数的完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-194">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="3f7d8-195">将以下代码添加为 `Export Public Key` 按钮 (`buttonExportPublicKey_Click`) 的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-195">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="3f7d8-196">导入公钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-196">Importing a Public Key</span></span>  
 <span data-ttu-id="3f7d8-197">此任务将加载只有公共参数的密钥（由 `Export Public Key` 按钮创建），并将其设置为密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-197">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="3f7d8-198">此任务模拟以下场景：Bob 加载 Alice 的只含公共参数的密钥，从而可以为她加密文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-198">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="3f7d8-199">将以下代码添加为 `Import Public Key` 按钮 (`buttonImportPublicKey_Click`) 的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-199">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="3f7d8-200">获取私钥</span><span class="sxs-lookup"><span data-stu-id="3f7d8-200">Getting a Private Key</span></span>  
 <span data-ttu-id="3f7d8-201">此任务将密钥容器名称设置为使用 `Create Keys` 按钮创建的密钥的名称。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-201">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="3f7d8-202">密钥容器将包含带专用参数的完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-202">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="3f7d8-203">此任务模拟以下场景：Alice 使用她的私钥对由 Bob 加密的文件进行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-203">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="3f7d8-204">将以下代码添加为 `Get Private Key` 按钮 (`buttonGetPrivateKey_Click`) 的 `Click` 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-204">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="3f7d8-205">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="3f7d8-205">Testing the Application</span></span>  
 <span data-ttu-id="3f7d8-206">生成应用程序后，执行以下测试方案。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-206">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="3f7d8-207">创建密钥、加密和解密</span><span class="sxs-lookup"><span data-stu-id="3f7d8-207">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="3f7d8-208">单击“`Create Keys`”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-208">Click the `Create Keys` button.</span></span> <span data-ttu-id="3f7d8-209">标签显示密钥名称，并显示它是完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-209">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="3f7d8-210">单击“`Export Public Key`”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-210">Click the `Export Public Key` button.</span></span> <span data-ttu-id="3f7d8-211">请注意，导出公钥参数并不会更改当前密钥。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-211">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="3f7d8-212">单击 `Encrypt File` 按钮并选择文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-212">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="3f7d8-213">单击 `Decrypt File` 按钮，然后选择刚刚加密的文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-213">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="3f7d8-214">检查刚刚解密的文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-214">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="3f7d8-215">关闭应用程序并重启，以便测试检索下一个方案中保留的密钥容器。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-215">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="3f7d8-216">使用公钥进行加密</span><span class="sxs-lookup"><span data-stu-id="3f7d8-216">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="3f7d8-217">单击“`Import Public Key`”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-217">Click the `Import Public Key` button.</span></span> <span data-ttu-id="3f7d8-218">标签显示密钥名称，并显示它仅是公共的。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-218">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="3f7d8-219">单击 `Encrypt File` 按钮并选择文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-219">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="3f7d8-220">单击 `Decrypt File` 按钮，然后选择刚刚加密的文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-220">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="3f7d8-221">这将失败，因为必须使用私钥进行解密。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-221">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="3f7d8-222">此方案演示了仅使用公钥为他人加密文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-222">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="3f7d8-223">通常这个人只会为你提供公钥，而保留供解密的私钥。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-223">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="3f7d8-224">使用私钥进行解密</span><span class="sxs-lookup"><span data-stu-id="3f7d8-224">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="3f7d8-225">单击“`Get Private Key`”按钮。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-225">Click the `Get Private Key` button.</span></span> <span data-ttu-id="3f7d8-226">标签显示密钥名称，并显示它是否是完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-226">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="3f7d8-227">单击 `Decrypt File` 按钮，然后选择刚刚加密的文件。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-227">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="3f7d8-228">这将会成功，因为你具有用于解密的完整密钥对。</span><span class="sxs-lookup"><span data-stu-id="3f7d8-228">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7d8-229">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f7d8-229">See also</span></span>

- [<span data-ttu-id="3f7d8-230">加密服务</span><span class="sxs-lookup"><span data-stu-id="3f7d8-230">Cryptographic Services</span></span>](cryptographic-services.md)
