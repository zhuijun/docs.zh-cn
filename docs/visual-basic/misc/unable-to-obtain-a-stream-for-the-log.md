---
title: 无法获取日志的流
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 887356fac3abe5c9d28751f7c4d3b1908ed35acb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078380"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="e2faf-102">无法获取日志的流</span><span class="sxs-lookup"><span data-stu-id="e2faf-102">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="e2faf-103">无法获取日志的流。</span><span class="sxs-lookup"><span data-stu-id="e2faf-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="e2faf-104">可能的基于的文件名 \<name> 已在使用中。</span><span class="sxs-lookup"><span data-stu-id="e2faf-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="e2faf-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>类无法创建新的日志文件，因为基于的所有潜在日志文件名 \<name> 都已在使用中。</span><span class="sxs-lookup"><span data-stu-id="e2faf-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="e2faf-106">具有过多的日志文件可能表明应用程序存在结构问题。</span><span class="sxs-lookup"><span data-stu-id="e2faf-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="e2faf-107">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 类的文档。</span><span class="sxs-lookup"><span data-stu-id="e2faf-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2faf-108">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e2faf-108">To correct this error</span></span>  
  
1. <span data-ttu-id="e2faf-109">将 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> 属性设置为 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> 或 <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> ，以便在日志文件名中包含日期戳。</span><span class="sxs-lookup"><span data-stu-id="e2faf-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="e2faf-110">将现有日志存档后将其从计算机中删除，以允许 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 对象创建新日志。</span><span class="sxs-lookup"><span data-stu-id="e2faf-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2faf-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2faf-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="e2faf-112">My. .Log</span><span class="sxs-lookup"><span data-stu-id="e2faf-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="e2faf-113">DirectoryPath。</span><span class="sxs-lookup"><span data-stu-id="e2faf-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
