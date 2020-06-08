---
title: 基本序列化技术示例
description: 本示例说明公共语言运行时 (CLR) 将内存中的对象图序列化成流的能力。 此示例可以使用 SoapFormatter 或 BinaryFormatter。
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 3f2273e6afb3a72f9734444ffe92d30871fb762b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "84276564"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="360df-104">基本序列化技术示例</span><span class="sxs-lookup"><span data-stu-id="360df-104">Basic Serialization Technology Sample</span></span>

[<span data-ttu-id="360df-105">下载示例</span><span class="sxs-lookup"><span data-stu-id="360df-105">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)

<span data-ttu-id="360df-106">本示例说明公共语言运行时将内存中的对象图序列化成流的能力。</span><span class="sxs-lookup"><span data-stu-id="360df-106">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="360df-107">此示例可以使用 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 来进行序列化。</span><span class="sxs-lookup"><span data-stu-id="360df-107">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="360df-108">用数据填充的链接列表可以被序列化成文件流，也可以从文件流反序列化该链接列表。</span><span class="sxs-lookup"><span data-stu-id="360df-108">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="360df-109">上述任何一种情况都会显示该列表，这样，您就可以看到相应的结果。</span><span class="sxs-lookup"><span data-stu-id="360df-109">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="360df-110">链接列表的类型为 `LinkedList`，该类型由此示例定义。</span><span class="sxs-lookup"><span data-stu-id="360df-110">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>

<span data-ttu-id="360df-111">有关序列化的更多信息，请查看源代码中的注释以及 build.proj 文件。</span><span class="sxs-lookup"><span data-stu-id="360df-111">Review comments in the source code and build.proj files for more information on serialization.</span></span>

### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="360df-112">使用命令提示生成示例</span><span class="sxs-lookup"><span data-stu-id="360df-112">To build the sample using the Command Prompt</span></span>

1. <span data-ttu-id="360df-113">使用命令提示定位到 Technologies\Serialization\Runtime Serialization\Basic 目录下语言特定的子目录之一。</span><span class="sxs-lookup"><span data-stu-id="360df-113">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>

2. <span data-ttu-id="360df-114">在命令行中键入 msbuild SerializationCS.sln、msbuild SerializationJSL.sln 或 msbuild SerializationVB.sln，具体取决于所选的编程语言  。</span><span class="sxs-lookup"><span data-stu-id="360df-114">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>

### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="360df-115">使用 Visual Studio 生成示例</span><span class="sxs-lookup"><span data-stu-id="360df-115">To build the sample using Visual Studio</span></span>

1. <span data-ttu-id="360df-116">打开文件资源管理器，定位到该示例的语言特定的子目录之一。</span><span class="sxs-lookup"><span data-stu-id="360df-116">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>

2. <span data-ttu-id="360df-117">根据所选的编程语言，双击 SerializationCS.sln、SerializationJSL.sln 或 SerializationVB.sln 文件的图标，在 Visual Studio 中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="360df-117">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="360df-118">在“生成”菜单中选择“生成解决方案” 。</span><span class="sxs-lookup"><span data-stu-id="360df-118">In the **Build** menu, select **Build Solution**.</span></span>

 <span data-ttu-id="360df-119">示例应用程序将在默认的 \bin 或 \bin\Debug 子目录中生成。</span><span class="sxs-lookup"><span data-stu-id="360df-119">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>

### <a name="to-run-the-sample"></a><span data-ttu-id="360df-120">运行示例</span><span class="sxs-lookup"><span data-stu-id="360df-120">To run the sample</span></span>

1. <span data-ttu-id="360df-121">定位到包含生成的可执行文件的目录。</span><span class="sxs-lookup"><span data-stu-id="360df-121">Navigate to the directory containing the built executable.</span></span>

2. <span data-ttu-id="360df-122">在命令行中键入 Serialization.exe 以及所需的参数值。</span><span class="sxs-lookup"><span data-stu-id="360df-122">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>

  > [!NOTE]
  > <span data-ttu-id="360df-123">此示例生成控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="360df-123">This sample builds a console application.</span></span> <span data-ttu-id="360df-124">必须使用命令提示来启动该程序，才能查看相应的输出。</span><span class="sxs-lookup"><span data-stu-id="360df-124">You must launch it using the command prompt in order to view its output.</span></span>

## <a name="remarks"></a><span data-ttu-id="360df-125">备注</span><span class="sxs-lookup"><span data-stu-id="360df-125">Remarks</span></span>

<span data-ttu-id="360df-126">示例应用程序接受指示您要执行何种测试的命令行参数。</span><span class="sxs-lookup"><span data-stu-id="360df-126">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="360df-127">若要使用 SOAP 格式化程序将 10 节点列表序列化成名为 Test.xml 的文件，请使用参数 sx Test.xml 10 。</span><span class="sxs-lookup"><span data-stu-id="360df-127">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>

<span data-ttu-id="360df-128">例如：</span><span class="sxs-lookup"><span data-stu-id="360df-128">For Example:</span></span>

```console
Serialize.exe -sx Test.xml 10
```

<span data-ttu-id="360df-129">若要从先前的示例中反序列化 Test.xml文件，请使用参数 dx Test.xml 。</span><span class="sxs-lookup"><span data-stu-id="360df-129">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>

<span data-ttu-id="360df-130">例如：</span><span class="sxs-lookup"><span data-stu-id="360df-130">For Example:</span></span>

```console
Serialize.exe -dx Test.xml
```

<span data-ttu-id="360df-131">在上面的两个示例中，命令行开关中的“x”指示您需要 XML SOAP 序列化。</span><span class="sxs-lookup"><span data-stu-id="360df-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="360df-132">您可以用“b”来代替它，以使用二进制序列化。</span><span class="sxs-lookup"><span data-stu-id="360df-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="360df-133">如果您想尝试对非常多的节点进行序列化，则可能需要将控制台输出重定向到某个文件。</span><span class="sxs-lookup"><span data-stu-id="360df-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>

<span data-ttu-id="360df-134">例如：</span><span class="sxs-lookup"><span data-stu-id="360df-134">For Example:</span></span>

```console
Serialize.exe -sb Test.bin 10000 >somefile.txt
```

<span data-ttu-id="360df-135">下面的项目符号简要说明了此示例所使用的类和技术。</span><span class="sxs-lookup"><span data-stu-id="360df-135">The following bullets briefly describe the classes and technologies used by this sample.</span></span>

- <span data-ttu-id="360df-136">运行时序列化</span><span class="sxs-lookup"><span data-stu-id="360df-136">Runtime Serialization</span></span>

  - <span data-ttu-id="360df-137"><xref:System.Runtime.Serialization.IFormatter> 用于引用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 对象。</span><span class="sxs-lookup"><span data-stu-id="360df-137"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>

  - <span data-ttu-id="360df-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 用于使用二进制格式将链接列表序列化到流。</span><span class="sxs-lookup"><span data-stu-id="360df-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="360df-139">二进制格式化程序使用了只有 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 类型才理解的格式。</span><span class="sxs-lookup"><span data-stu-id="360df-139">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="360df-140">然而，该数据非常简明。</span><span class="sxs-lookup"><span data-stu-id="360df-140">However, the data is concise.</span></span>

  - <span data-ttu-id="360df-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 用于使用 SOAP 格式将链接列表序列化到流。</span><span class="sxs-lookup"><span data-stu-id="360df-141"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="360df-142">SOAP 是一种标准格式。</span><span class="sxs-lookup"><span data-stu-id="360df-142">SOAP is a standard format.</span></span>

- <span data-ttu-id="360df-143">流 I/O</span><span class="sxs-lookup"><span data-stu-id="360df-143">Stream I/O</span></span>

  - <span data-ttu-id="360df-144"><xref:System.IO.Stream> 可用于序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="360df-144"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="360df-145">此示例中使用的特定流类型是 <xref:System.IO.FileStream> 类型。</span><span class="sxs-lookup"><span data-stu-id="360df-145">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="360df-146">然而，序列化可以用于从 <xref:System.IO.Stream> 派生的任何类型。</span><span class="sxs-lookup"><span data-stu-id="360df-146">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>

  - <span data-ttu-id="360df-147"><xref:System.IO.File> 可用于创建 <xref:System.IO.FileStream> 对象，以便在磁盘上读取和创建文件。</span><span class="sxs-lookup"><span data-stu-id="360df-147"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>

  - <span data-ttu-id="360df-148"><xref:System.IO.FileStream> 可用于对链接列表进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="360df-148"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>

## <a name="see-also"></a><span data-ttu-id="360df-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="360df-149">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="360df-150">基本序列化</span><span class="sxs-lookup"><span data-stu-id="360df-150">Basic Serialization</span></span>](basic-serialization.md)
- [<span data-ttu-id="360df-151">二进制序列化</span><span class="sxs-lookup"><span data-stu-id="360df-151">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="360df-152">使用属性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="360df-152">Controlling XML Serialization Using Attributes</span></span>](controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="360df-153">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="360df-153">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="360df-154">序列化</span><span class="sxs-lookup"><span data-stu-id="360df-154">Serialization</span></span>](index.md)
- [<span data-ttu-id="360df-155">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="360df-155">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
