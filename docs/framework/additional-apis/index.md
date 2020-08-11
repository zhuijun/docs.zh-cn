---
title: 其他类库和 API
description: 探索 .NET 中的其他类库和 Api，包括带外 (OOB) 项目、平台特定的库和私有 Api。
ms.date: 08/11/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: c6404df5d4f0be381bc0a9c1924fcf82cf078306
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88075470"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="ec5f1-103">其他类库和 API</span><span class="sxs-lookup"><span data-stu-id="ec5f1-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="ec5f1-104">本文列出了以带外方式发布的 .NET Framework Api，这些 Api 以特定的平台为目标，或者是私有或内部类型。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="ec5f1-105">OOB 项目</span><span class="sxs-lookup"><span data-stu-id="ec5f1-105">OOB projects</span></span>

<span data-ttu-id="ec5f1-106">为了改善跨平台开发并及早引入新功能，一些 .NET Framework 功能已在 (OOB) 中发布。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="ec5f1-107">项目</span><span class="sxs-lookup"><span data-stu-id="ec5f1-107">Project</span></span> | <span data-ttu-id="ec5f1-108">说明</span><span class="sxs-lookup"><span data-stu-id="ec5f1-108">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="ec5f1-109">提供的集合数是线程安全的，并且保证决不会更改该集合的内容。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="ec5f1-110">基于 Windows 的 WinHTTP 接口为 <xref:System.Net.Http.HttpClient> 提供消息处理程序。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="ec5f1-111">提供可利用基于 SIMD 硬件的加速的向量类型库。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="ec5f1-112">TPL 数据流库提供数据流组件以帮助提高启用并发的应用程序的稳健性。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="ec5f1-113">特定于平台的库</span><span class="sxs-lookup"><span data-stu-id="ec5f1-113">Platform-specific libraries</span></span>

<span data-ttu-id="ec5f1-114">某些库面向特定的平台。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="ec5f1-115">例如， <xref:System.Text.CodePagesEncodingProvider> 类使代码页编码可用于使用 .NET Framework 开发的 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>
  
| <span data-ttu-id="ec5f1-116">项目</span><span class="sxs-lookup"><span data-stu-id="ec5f1-116">Project</span></span> | <span data-ttu-id="ec5f1-117">说明</span><span class="sxs-lookup"><span data-stu-id="ec5f1-117">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="ec5f1-118">扩展 <xref:System.Text.EncodingProvider> 类，使代码页编码可用于面向通用 Windows 平台的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="ec5f1-119">私有 API</span><span class="sxs-lookup"><span data-stu-id="ec5f1-119">Private APIs</span></span>  

<span data-ttu-id="ec5f1-120">这些 Api 支持产品基础结构，不应在代码中直接使用。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="ec5f1-121">SmiOrderProperty 属性（& e）</span><span class="sxs-lookup"><span data-stu-id="ec5f1-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="ec5f1-122">PrepForRemoting 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="ec5f1-123">SqlTypes. SqlChars 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="ec5f1-124">SqlTypes. SqlStreamChars 构造函数</span><span class="sxs-lookup"><span data-stu-id="ec5f1-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="ec5f1-125">SqlTypes. SqlStreamChars. CanSeek 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="ec5f1-126">SqlTypes. SqlStreamChars 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="ec5f1-127">SqlTypes. SqlStreamChars 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="ec5f1-128">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="ec5f1-129">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="ec5f1-130">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="ec5f1-131">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="ec5f1-132">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="ec5f1-133">SqlTypes. SqlStreamChars. SetLength 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="ec5f1-134">SqlTypes. SqlStreamChars 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="ec5f1-135">MemoryStream. InternalGetOriginAndLength 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="ec5f1-136">ComNetOS 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="ec5f1-137">系统 .Net. 连接类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="ec5f1-138">系统 \_ WriteList 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="ec5f1-139">ConnectionGroup 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="ec5f1-140">系统 ConnectionGroup \_ ConnectionList 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="ec5f1-141">系统 ConnectStream 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="ec5f1-142">CoreResponseData 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="ec5f1-143">系统 CoreResponseData \_ ResponseHeaders 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="ec5f1-144">系统 CoreResponseData \_ StatusCode 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="ec5f1-145">ExceptionHelper 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="ec5f1-146">HttpStatusDescription 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="ec5f1-147">系统 HttpWebRequest。 \_AutoRedirects 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="ec5f1-148">系统 HttpWebRequest。 \_CoreResponse 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="ec5f1-149">系统 HttpWebRequest。 \_Httpresponse.cache 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="ec5f1-150">系统 .Net. 日志类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="ec5f1-151">系统 MailAddressParser 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="ec5f1-152">系统 QuotedPairReader 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="ec5f1-153">MailBnfHelper 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="ec5f1-154">PooledStream. NetworkStream 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="ec5f1-155">RtcState 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="ec5f1-156">SslState. SslProtocol 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="ec5f1-157">系统 ServicePoint \_ ConnectionGroupList 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="ec5f1-158">ServicePointManager. CloseConnectionGroups 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="ec5f1-159">系统 ServicePointManager \_ ServicePointTable 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="ec5f1-160">系统 m_Worker 字段 TlsStream</span><span class="sxs-lookup"><span data-stu-id="ec5f1-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="ec5f1-161">UnsafeNclNativeMethods 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="ec5f1-162">设置了 webheadercollection. AddInternal 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="ec5f1-163">System.servicemodel. BodyToString 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="ec5f1-164">System.servicemodel. WriteStartHeaders 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="ec5f1-165">ControlBuilderInterceptor 类。</span><span class="sxs-lookup"><span data-stu-id="ec5f1-165">System.Web.Compilation.ControlBuilderInterceptor class</span></span>](controlbuilderinterceptor-class.md)
* [<span data-ttu-id="ec5f1-166">VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes 字段</span><span class="sxs-lookup"><span data-stu-id="ec5f1-166">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="ec5f1-167">"DataMemberFieldEditor" 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-167">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="ec5f1-168">"DataMemberListEditor" 类</span><span class="sxs-lookup"><span data-stu-id="ec5f1-168">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="ec5f1-169">System.Xml.XmlCreateSqlReader 方法</span><span class="sxs-lookup"><span data-stu-id="ec5f1-169">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="ec5f1-170">adodb.recordset.连接接口</span><span class="sxs-lookup"><span data-stu-id="ec5f1-170">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="ec5f1-171">adodb.recordset.EventReason 枚举</span><span class="sxs-lookup"><span data-stu-id="ec5f1-171">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="ec5f1-172">adodb.recordset.EventStatus 枚举</span><span class="sxs-lookup"><span data-stu-id="ec5f1-172">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="ec5f1-173">stdole.DISPPARAMS 结构</span><span class="sxs-lookup"><span data-stu-id="ec5f1-173">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="ec5f1-174">stdole.EXCEPINFO 结构</span><span class="sxs-lookup"><span data-stu-id="ec5f1-174">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="ec5f1-175">stdole.IFont.Name 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-175">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="ec5f1-176">stdole.IFontDisp 接口</span><span class="sxs-lookup"><span data-stu-id="ec5f1-176">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="ec5f1-177">stdole.IPicture 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-177">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="ec5f1-178">stdole.IPictureDisp 属性</span><span class="sxs-lookup"><span data-stu-id="ec5f1-178">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="ec5f1-179">stdole.StdFont 接口</span><span class="sxs-lookup"><span data-stu-id="ec5f1-179">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="ec5f1-180">stdole.StdPicture 接口</span><span class="sxs-lookup"><span data-stu-id="ec5f1-180">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="ec5f1-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec5f1-181">See also</span></span>

* [<span data-ttu-id="ec5f1-182">.NET Framework 和带外版本</span><span class="sxs-lookup"><span data-stu-id="ec5f1-182">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
