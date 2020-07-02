---
title: 如何：配置网络跟踪
description: 了解如何在计算机配置文件或应用程序配置文件中配置网络跟踪。 应用程序配置文件优先。
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502556"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="06aff-104">如何：配置网络跟踪</span><span class="sxs-lookup"><span data-stu-id="06aff-104">How to: Configure network tracing</span></span>

<span data-ttu-id="06aff-105">应用程序或计算机配置文件可保存用于确定网络跟踪的格式和内容的设置。</span><span class="sxs-lookup"><span data-stu-id="06aff-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="06aff-106">在执行此过程之前，请确保启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="06aff-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="06aff-107">有关详细信息，请参阅[启用网络跟踪](enabling-network-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="06aff-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="06aff-108">计算机配置文件 machine.config 存储在 %windir%\Microsoft.NET\Framework 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="06aff-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="06aff-109">安装在计算机上的每个版本的 .NET Framework，在 %windir%\Microsoft.NET\Framework 下的文件夹中分别有一个单独的 machine.config 文件，例如：</span><span class="sxs-lookup"><span data-stu-id="06aff-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="06aff-110">C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config</span><span class="sxs-lookup"><span data-stu-id="06aff-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="06aff-111">C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config</span><span class="sxs-lookup"><span data-stu-id="06aff-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="06aff-112">也可以在应用程序的配置文件中做出这些设置，其优先级别高于计算机配置文件。</span><span class="sxs-lookup"><span data-stu-id="06aff-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="06aff-113">配置网络跟踪</span><span class="sxs-lookup"><span data-stu-id="06aff-113">Configure network tracing</span></span>

<span data-ttu-id="06aff-114">要配置网络跟踪，请将下面的行添加到相应的配置文件。</span><span class="sxs-lookup"><span data-stu-id="06aff-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="06aff-115">这些设置的值和选项已在下表中予以说明。</span><span class="sxs-lookup"><span data-stu-id="06aff-115">The values and options for these settings are described in the tables below.</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a><span data-ttu-id="06aff-116">跟踪方法的输出</span><span class="sxs-lookup"><span data-stu-id="06aff-116">Trace output from methods</span></span>

<span data-ttu-id="06aff-117">当你将一个名称添加到 `<switches>` 块后，跟踪输出中将包括来自与该名称相关的一些方法的信息。</span><span class="sxs-lookup"><span data-stu-id="06aff-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="06aff-118">下表对输出进行了说明：</span><span class="sxs-lookup"><span data-stu-id="06aff-118">The following table describes the output:</span></span>

|<span data-ttu-id="06aff-119">“属性”</span><span class="sxs-lookup"><span data-stu-id="06aff-119">Name</span></span>|<span data-ttu-id="06aff-120">输出来自</span><span class="sxs-lookup"><span data-stu-id="06aff-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="06aff-121"><xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient> 和 <xref:System.Net.Dns> 类的一些公共方法。</span><span class="sxs-lookup"><span data-stu-id="06aff-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="06aff-122"><xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 类的一些公共方法，以及 SSL 调试信息（证书无效、缺少颁发机构列表以及客户端证书错误）。</span><span class="sxs-lookup"><span data-stu-id="06aff-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="06aff-123"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 类的一些公共方法。</span><span class="sxs-lookup"><span data-stu-id="06aff-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="06aff-124">`System.Net.Cache` 中的一些私有方法和内部方法。</span><span class="sxs-lookup"><span data-stu-id="06aff-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="06aff-125"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 类的一些公共方法。</span><span class="sxs-lookup"><span data-stu-id="06aff-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="06aff-126"><xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 类的一些公共方法。</span><span class="sxs-lookup"><span data-stu-id="06aff-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="06aff-127">跟踪输出属性</span><span class="sxs-lookup"><span data-stu-id="06aff-127">Trace output attributes</span></span>

<span data-ttu-id="06aff-128">下表中列出的属性用于配置跟踪输出：</span><span class="sxs-lookup"><span data-stu-id="06aff-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="06aff-129">特性名</span><span class="sxs-lookup"><span data-stu-id="06aff-129">Attribute name</span></span>|<span data-ttu-id="06aff-130">特性值</span><span class="sxs-lookup"><span data-stu-id="06aff-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="06aff-131">必选的 <xref:System.String> 特性。</span><span class="sxs-lookup"><span data-stu-id="06aff-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="06aff-132">设置输出的详细程度。</span><span class="sxs-lookup"><span data-stu-id="06aff-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="06aff-133">合法值为 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。</span><span class="sxs-lookup"><span data-stu-id="06aff-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="06aff-134">必须在 switches 元素的 add 元素上设置此属性 。</span><span class="sxs-lookup"><span data-stu-id="06aff-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="06aff-135">如果在 source 元素上设置此属性，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="06aff-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="06aff-136">示例：`<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="06aff-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="06aff-137">可选的 <xref:System.Int32> 特性。</span><span class="sxs-lookup"><span data-stu-id="06aff-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="06aff-138">设置每行跟踪中包含的最大网络数据字节数。</span><span class="sxs-lookup"><span data-stu-id="06aff-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="06aff-139">默认值为 1024。</span><span class="sxs-lookup"><span data-stu-id="06aff-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="06aff-140">必须在 source 元素上设置此属性。</span><span class="sxs-lookup"><span data-stu-id="06aff-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="06aff-141">如果在 switches 元素下的一个元素上设置此属性，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="06aff-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="06aff-142">示例：`<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="06aff-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="06aff-143">可选的 <xref:System.String> 特性。</span><span class="sxs-lookup"><span data-stu-id="06aff-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="06aff-144">设置为 `includehex` 将会以十六进制和文本格式显示协议跟踪。</span><span class="sxs-lookup"><span data-stu-id="06aff-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="06aff-145">设置为 `protocolonly` 将会仅显示文本。</span><span class="sxs-lookup"><span data-stu-id="06aff-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="06aff-146">默认值为 `includehex`。</span><span class="sxs-lookup"><span data-stu-id="06aff-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="06aff-147">必须在 source 元素上设置此属性。</span><span class="sxs-lookup"><span data-stu-id="06aff-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="06aff-148">如果在 switches 元素下的一个元素上设置此属性，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="06aff-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="06aff-149">示例：`<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="06aff-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="06aff-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="06aff-150">See also</span></span>

- [<span data-ttu-id="06aff-151">解释网络跟踪</span><span class="sxs-lookup"><span data-stu-id="06aff-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="06aff-152">.NET Framework 中的网络跟踪</span><span class="sxs-lookup"><span data-stu-id="06aff-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="06aff-153">启用网络跟踪</span><span class="sxs-lookup"><span data-stu-id="06aff-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="06aff-154">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="06aff-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
