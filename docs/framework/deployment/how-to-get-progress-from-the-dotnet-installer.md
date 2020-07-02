---
title: 如何：获取 .NET Framework 4.5 安装程序的进度
description: 了解如何获取 .NET 4.5 安装程序的进度。 如果要针对此 .NET 版本开发应用，则可以在应用的安装程序中包含（链接）.NET 4.5 安装程序。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
ms.openlocfilehash: 501fcaa7636d586ddfff8606768d4639fdc010d7
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904255"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="e8178-104">如何：获取 .NET Framework 4.5 安装程序的进度</span><span class="sxs-lookup"><span data-stu-id="e8178-104">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>

<span data-ttu-id="e8178-105">.NET Framework 4.5 是可再发行运行时。</span><span class="sxs-lookup"><span data-stu-id="e8178-105">The .NET Framework 4.5 is a redistributable runtime.</span></span> <span data-ttu-id="e8178-106">如果开发基于此 .NET framework 版本的应用，则可以将 .NET Framework 4.5 安装程序作为必备组件包括（链接）在应用的安装程序中。</span><span class="sxs-lookup"><span data-stu-id="e8178-106">If you develop apps for this version of the .NET Framework, you can include (chain) .NET Framework 4.5 setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="e8178-107">若要提供自定义或统一的安装体验，可能需要以无提示方式启动 .NET Framework 4.5 安装程序并跟踪其进度，同时显示应用的安装进度。</span><span class="sxs-lookup"><span data-stu-id="e8178-107">To present a customized or unified setup experience, you may want to silently launch .NET Framework 4.5 setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="e8178-108">若要启用无提示跟踪，.NET Framework 4.5 安装程序（可观察）通过使用内存映射 I/O (MMIO) 段来定义协议，以便与安装程序（观察程序或链接器）进行通信。</span><span class="sxs-lookup"><span data-stu-id="e8178-108">To enable silent tracking, .NET Framework 4.5 setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="e8178-109">此协议定义链接器获取进度信息、详细结果，响应消息和取消 .NET Framework 4.5 安装的方式。</span><span class="sxs-lookup"><span data-stu-id="e8178-109">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the .NET Framework 4.5 setup.</span></span>

- <span data-ttu-id="e8178-110">**调用**。</span><span class="sxs-lookup"><span data-stu-id="e8178-110">**Invocation**.</span></span> <span data-ttu-id="e8178-111">若要调用 .NET Framework 4.5 安装程序并接收来自 MMIO 节的进度信息，安装程序必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e8178-111">To call .NET Framework 4.5 setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>

    1. <span data-ttu-id="e8178-112">调用 .NET Framework 4.5 可再发行程序：</span><span class="sxs-lookup"><span data-stu-id="e8178-112">Call the .NET Framework 4.5 redistributable program:</span></span>

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        <span data-ttu-id="e8178-113">其中“section name”是要用来标识应用的任意名称。</span><span class="sxs-lookup"><span data-stu-id="e8178-113">Where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="e8178-114">.NET Framework 安装程序以异步方式在 MMIO 节进行读写，因此可能会发现在此期间使用事件和消息很方便。</span><span class="sxs-lookup"><span data-stu-id="e8178-114">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="e8178-115">在示例中，.NET Framework 安装进程由分配 MMIO 节 (`TheSectionName`) 和定义事件 (`TheEventName`) 的构造函数创建：</span><span class="sxs-lookup"><span data-stu-id="e8178-115">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        <span data-ttu-id="e8178-116">请使用对于安装程序唯一的名称替换这些名称。</span><span class="sxs-lookup"><span data-stu-id="e8178-116">Please replace those names with names that are unique to your setup program.</span></span>

    2. <span data-ttu-id="e8178-117">从 MMIO 节读取。</span><span class="sxs-lookup"><span data-stu-id="e8178-117">Read from the MMIO section.</span></span> <span data-ttu-id="e8178-118">在 .NET Framework 4.5 中，下载和安装操作是同时进行的：下载 .NET Framework 一部分的同时，可能正在安装另一部分。</span><span class="sxs-lookup"><span data-stu-id="e8178-118">In the .NET Framework 4.5, the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="e8178-119">因此，进度会以从 0 到 255 递增的两个数字（`m_downloadSoFar` 和 `m_installSoFar`）形式发送回（即写入）MMIO 节。</span><span class="sxs-lookup"><span data-stu-id="e8178-119">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="e8178-120">如果写入 255 且 .NET Framework 存在，则表示安装完成。</span><span class="sxs-lookup"><span data-stu-id="e8178-120">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>

- <span data-ttu-id="e8178-121">退出代码。</span><span class="sxs-lookup"><span data-stu-id="e8178-121">**Exit codes**.</span></span> <span data-ttu-id="e8178-122">以下命令中的退出代码用于调用 .NET Framework 4.5 可再发行程序，指示安装是成功还是失败：</span><span class="sxs-lookup"><span data-stu-id="e8178-122">The following exit codes from the command to call the .NET Framework 4.5 redistributable program indicate whether setup has succeeded or failed:</span></span>

  - <span data-ttu-id="e8178-123">0 - 安装已成功完成。</span><span class="sxs-lookup"><span data-stu-id="e8178-123">0 - Setup completed successfully.</span></span>

  - <span data-ttu-id="e8178-124">3010 - 安装已成功完成；需要重启系统。</span><span class="sxs-lookup"><span data-stu-id="e8178-124">3010 – Setup completed successfully; a system restart is required.</span></span>

  - <span data-ttu-id="e8178-125">1602 - 安装已取消。</span><span class="sxs-lookup"><span data-stu-id="e8178-125">1602 – Setup has been canceled.</span></span>

  - <span data-ttu-id="e8178-126">所有其他代码 - 安装过程中出现错误；请检查 %temp% 中创建的日志文件，了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="e8178-126">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>

- <span data-ttu-id="e8178-127">取消安装。</span><span class="sxs-lookup"><span data-stu-id="e8178-127">**Canceling setup**.</span></span> <span data-ttu-id="e8178-128">可随时通过使用 `Abort` 方法在 MMIO 节中设置 `m_downloadAbort` 和 `m_ installAbort` 标志来取消安装。</span><span class="sxs-lookup"><span data-stu-id="e8178-128">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>

## <a name="chainer-sample"></a><span data-ttu-id="e8178-129">链接器示例</span><span class="sxs-lookup"><span data-stu-id="e8178-129">Chainer Sample</span></span>

<span data-ttu-id="e8178-130">链接器示例以无提示方式启动并跟踪 .NET Framework 4.5 安装程序，同时显示进度。</span><span class="sxs-lookup"><span data-stu-id="e8178-130">The Chainer sample silently launches and tracks .NET Framework 4.5 setup while showing progress.</span></span> <span data-ttu-id="e8178-131">此示例类似于为 .NET Framework 4 提供的链接器示例。</span><span class="sxs-lookup"><span data-stu-id="e8178-131">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="e8178-132">但是，它还可以通过处理用于关闭 .NET framework 4 应用的消息框来避免系统重启。</span><span class="sxs-lookup"><span data-stu-id="e8178-132">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="e8178-133">有关此消息框的信息，请参阅[在 .NET Framework 4.5 安装期间减少系统重启](reducing-system-restarts.md)。</span><span class="sxs-lookup"><span data-stu-id="e8178-133">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](reducing-system-restarts.md).</span></span> <span data-ttu-id="e8178-134">可以将此示例与 .NET Framework 4 安装程序结合使用；在这种情况下，不会发送消息。</span><span class="sxs-lookup"><span data-stu-id="e8178-134">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>

> [!WARNING]
> <span data-ttu-id="e8178-135">必须以管理员身份运行此示例。</span><span class="sxs-lookup"><span data-stu-id="e8178-135">You must run the example as an administrator.</span></span>

<span data-ttu-id="e8178-136">可从 MSDN 示例库下载针对 [.NET Framework 4.5 链接器示例](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba)的完整 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="e8178-136">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba) from the MSDN Samples Gallery.</span></span>

<span data-ttu-id="e8178-137">以下章节对此示例中的重要文件进行了介绍：MMIOChainer.h、ChainingdotNet4.cpp 和 IProgressObserver.h。</span><span class="sxs-lookup"><span data-stu-id="e8178-137">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>

#### <a name="mmiochainerh"></a><span data-ttu-id="e8178-138">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="e8178-138">MMIOChainer.h</span></span>

- <span data-ttu-id="e8178-139">MMIOChainer.h 文件（请参阅[完整代码](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)）包含数据结构定义和链接器类应派生自的基类。</span><span class="sxs-lookup"><span data-stu-id="e8178-139">The MMIOChainer.h file (see [complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=663039622)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="e8178-140">.NET Framework 4.5 扩展 MMIO 数据结构，处理 .NET Framework 4.5 安装程序需要的数据。</span><span class="sxs-lookup"><span data-stu-id="e8178-140">The .NET Framework 4.5 extends the MMIO data structure to handle data that the .NET Framework 4.5 installer needs.</span></span> <span data-ttu-id="e8178-141">对 MMIO 结构的更改为后向兼容，因此 .NET Framework 4 链接器可在无需重新编译的情况下与 .NET Framework 4.5 安装程序结合使用。</span><span class="sxs-lookup"><span data-stu-id="e8178-141">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="e8178-142">但是，此方案不支持用于减少系统重启的功能。</span><span class="sxs-lookup"><span data-stu-id="e8178-142">However, this scenario does not support the feature for reducing system restarts.</span></span>

    <span data-ttu-id="e8178-143">版本字段提供标识结构和消息格式的修订的方法。</span><span class="sxs-lookup"><span data-stu-id="e8178-143">A version field provides a means of identifying revisions to the structure and message format.</span></span> <span data-ttu-id="e8178-144">.NET Framework 安装程序通过调用 `VirtualQuery` 函数来确定文件映射的大小，从而确定链接器接口的版本。</span><span class="sxs-lookup"><span data-stu-id="e8178-144">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span> <span data-ttu-id="e8178-145">如果大小足以容纳版本字段，则 .NET framework 安装程序将使用该指定值。</span><span class="sxs-lookup"><span data-stu-id="e8178-145">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="e8178-146">如果文件映射因过小而无法包含版本字段（.NET framework 4 即是这种情况），则安装过程假定为版本 0 (4)。</span><span class="sxs-lookup"><span data-stu-id="e8178-146">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="e8178-147">如果链接器不支持 .NET framework 安装程序希望发送的消息版本，则 .NET framework 安装程序会假定一个忽略响应。</span><span class="sxs-lookup"><span data-stu-id="e8178-147">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>

    <span data-ttu-id="e8178-148">按以下方式定义 MMIO 数据结构：</span><span class="sxs-lookup"><span data-stu-id="e8178-148">The MMIO data structure is defined as follows:</span></span>

    ```cpp
    // MMIO data structure for interprocess communication
        struct MmioDataStructure
        {
            bool m_downloadFinished;               // Is download complete?
            bool m_installFinished;                // Is installation complete?
            bool m_downloadAbort;                  // Set to cause downloader to abort.
            bool m_installAbort;                   // Set to cause installer to abort.
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.
            HRESULT m_hrInternalError;
            WCHAR m_szCurrentItemStep[MAX_PATH];
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.

            BYTE m_version;                        // Version of the data structure, set by chainer:
                                                   // 0x0: .NET Framework 4
                                                   // 0x1: .NET Framework 4.5

            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.
        };
    ```

- <span data-ttu-id="e8178-149">不应直接使用 `MmioDataStructure` 数据结构；而应改用 `MmioChainer` 类以实现链接器。</span><span class="sxs-lookup"><span data-stu-id="e8178-149">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="e8178-150">派生自 `MmioChainer` 类，链接 .NET Framework 4.5 可再发行组件。</span><span class="sxs-lookup"><span data-stu-id="e8178-150">Derive from the `MmioChainer` class to chain the .NET Framework 4.5 redistributable.</span></span>

#### <a name="iprogressobserverh"></a><span data-ttu-id="e8178-151">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="e8178-151">IProgressObserver.h</span></span>

- <span data-ttu-id="e8178-152">IProgressObserver.h 文件实现进度观察器（[请参阅完整代码](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)）。</span><span class="sxs-lookup"><span data-stu-id="e8178-152">The IProgressObserver.h file implements a progress observer ([see complete code](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1263700592)).</span></span> <span data-ttu-id="e8178-153">此观察程序会获得下载和安装进度通知（指定为无符号 `char`，0-255，指示 1%-100% 完成进度）。</span><span class="sxs-lookup"><span data-stu-id="e8178-153">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="e8178-154">链接发送消息时，观察程序也会得到通知，并且观察程序应该发送一个答复。</span><span class="sxs-lookup"><span data-stu-id="e8178-154">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="e8178-155">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="e8178-155">ChainingdotNet4.5.cpp</span></span>

- <span data-ttu-id="e8178-156">[ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) 文件实现从 `MmioChainer` 派生的 `Server` 类，并重写了相应方法以显示进度信息。</span><span class="sxs-lookup"><span data-stu-id="e8178-156">The [ChainingdotNet4.5.cpp](https://code.msdn.microsoft.com/NET-Framework-45-Developer-e416a0ba/sourcecode?fileId=47345&pathId=1757268882) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="e8178-157">MmioChainer 使用指定的节名称创建一节并使用指定的事件名称初始化链接器。</span><span class="sxs-lookup"><span data-stu-id="e8178-157">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="e8178-158">事件名称会保存在映射数据结构中。</span><span class="sxs-lookup"><span data-stu-id="e8178-158">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="e8178-159">应确保节和事件名称的唯一性。</span><span class="sxs-lookup"><span data-stu-id="e8178-159">You should make the section and event names unique.</span></span> <span data-ttu-id="e8178-160">以下代码中的 `Server` 类会启动指定的安装程序，监视其进度并返回退出代码。</span><span class="sxs-lookup"><span data-stu-id="e8178-160">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    <span data-ttu-id="e8178-161">在 Main 方法中开始安装。</span><span class="sxs-lookup"><span data-stu-id="e8178-161">The installation is started in the Main method.</span></span>

    ```cpp
    // Main entry point for program
    int __cdecl main(int argc, _In_count_(argc) char **_argv)
    {
        int result = 0;
        CString args;
        if (argc > 1)
        {
            args = CString(_argv[1]);
        }

        if (IsNetFx4Present(NETFX45_RC_REVISION))
        {
            printf(".NET Framework 4.5 is already installed");
        }
        else
        {
            result = Server().Launch(args);
        }

        return result;
    }
    ```

- <span data-ttu-id="e8178-162">启动安装之前，链接器会先进行检查，查看是否已通过调用 `IsNetFx4Present` 安装 .NET Framework 4.5：</span><span class="sxs-lookup"><span data-stu-id="e8178-162">Before launching the installation, the chainer checks to see if the .NET Framework 4.5 is already installed by calling `IsNetFx4Present`:</span></span>

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- <span data-ttu-id="e8178-163">可以更改 `Launch` 方法中可执行组件（在此示例中为 Setup.exe）的路径以指向其正确位置，或者自定义代码以确定位置。</span><span class="sxs-lookup"><span data-stu-id="e8178-163">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="e8178-164">`MmioChainer` 基类提供派生类调用的阻止 `Run()` 方法。</span><span class="sxs-lookup"><span data-stu-id="e8178-164">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- <span data-ttu-id="e8178-165">`Send` 方法截获并处理消息。</span><span class="sxs-lookup"><span data-stu-id="e8178-165">The `Send` method intercepts and processes the messages.</span></span> <span data-ttu-id="e8178-166">在此版本的 .NET Framework 中，唯一支持的消息是关闭应用程序消息。</span><span class="sxs-lookup"><span data-stu-id="e8178-166">In this version of the .NET Framework, the only supported message is the close application message.</span></span>

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- <span data-ttu-id="e8178-167">进度数据是 0 (0%) 到 255 (100%) 之间的无符号 `char`。</span><span class="sxs-lookup"><span data-stu-id="e8178-167">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- <span data-ttu-id="e8178-168">将 HRESULT 传递给 `Finished` 方法。</span><span class="sxs-lookup"><span data-stu-id="e8178-168">The HRESULT is passed to the `Finished` method.</span></span>

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="e8178-169">.NET Framework 4.5 可再发行组件通常会写入多条进度消息和一条指示完成的消息（在链接器端）。</span><span class="sxs-lookup"><span data-stu-id="e8178-169">The .NET Framework 4.5 redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="e8178-170">它还会以异步方式进行读取，查找 `Abort` 记录。</span><span class="sxs-lookup"><span data-stu-id="e8178-170">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="e8178-171">如果接收到 `Abort` 记录，则会取消安装，并在安装中止和安装操作回退后，使用 E ABORT 作为其数据编写已完成记录。</span><span class="sxs-lookup"><span data-stu-id="e8178-171">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>

<span data-ttu-id="e8178-172">典型的服务器会创建随机 MMIO 文件名、创建文件（如上一个代码示例 `Server::CreateSection` 中所示），并通过使用 `CreateProcess` 和借助 `-pipe someFileSectionName` 选项传递管道名称来启动可再发行组件。</span><span class="sxs-lookup"><span data-stu-id="e8178-172">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="e8178-173">服务器应使用特定于应用程序 UI 的代码来实现 `OnProgress`、`Send` 和 `Finished` 方法。</span><span class="sxs-lookup"><span data-stu-id="e8178-173">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8178-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8178-174">See also</span></span>

- [<span data-ttu-id="e8178-175">面向开发人员的部署指南</span><span class="sxs-lookup"><span data-stu-id="e8178-175">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)
- [<span data-ttu-id="e8178-176">部署</span><span class="sxs-lookup"><span data-stu-id="e8178-176">Deployment</span></span>](index.md)
