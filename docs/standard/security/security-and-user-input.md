---
title: 安全性和用户输入
description: 你的代码可能会将用户输入的数据作为参数传递给其他代码，这可能会影响安全性。 可以执行范围检查以拒绝出现问题的输入。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 995af30385790a88718193e7abad1db7bc4b56c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275940"
---
# <a name="security-and-user-input"></a><span data-ttu-id="7cfc6-104">安全性和用户输入</span><span class="sxs-lookup"><span data-stu-id="7cfc6-104">Security and User Input</span></span>

<span data-ttu-id="7cfc6-105">用户数据是指任何种类的输入（来自 Web 请求或 URL 的数据、对 Microsoft Windows 窗体应用程序控件输入的数据等等），它可能会对代码产生负面影响，因为这些数据通常直接用作参数来调用其他代码。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="7cfc6-106">这种情况类似于恶意代码使用奇特参数调用你的代码，因而必须采取同样的防范措施。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="7cfc6-107">用户输入实际上更难以保证安全性，因为没有堆栈帧来跟踪可能不受信任的数据的存在。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="7cfc6-108">它们属于最为微妙、最难发现的安全性 bug，因为虽然它们位于表面上与安全性不相关的代码中，但它们是将有害数据传递到其他代码的通道。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="7cfc6-109">若要查找这些 bug，请跟随任意一种输入数据，设想可能的值的范围，并考虑看到这一数据的代码是否能够处理所有这些情形。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="7cfc6-110">通过范围检查和拒绝任何无法由代码处理的输入，可以修复这些 bug。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="7cfc6-111">涉及用户数据的重要注意事项包括以下几个方面：</span><span class="sxs-lookup"><span data-stu-id="7cfc6-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="7cfc6-112">服务器响应中的任何用户数据在客户端上的服务器站点的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="7cfc6-113">例如，如果 Web 服务器接收用户数据并将其插入到返回的网页中，则可能会包含一个 **\<script>** 标记，并在服务器上运行。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="7cfc6-114">请记住，客户端可以请求任何 URL。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="7cfc6-115">考虑欺骗性的或无效的路径：</span><span class="sxs-lookup"><span data-stu-id="7cfc6-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="7cfc6-116">..\ ，非常长的路径。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="7cfc6-117">使用通配符 (\*)。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="7cfc6-118">标记展开 (%token%)。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="7cfc6-119">具有特殊意义的奇特路径形式。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="7cfc6-120">备用文件系统流名称，例如 `filename::$DATA`。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="7cfc6-121">文件名的简称，例如 `longfilename` 简称为 `longfi~1`。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="7cfc6-122">请记住，Eval(userdata) 可以执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="7cfc6-123">在后期绑定到包含某些用户数据的名称时要多加小心。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="7cfc6-124">如果正在处理 Web 数据，请考虑所允许的各种转义形式，包括：</span><span class="sxs-lookup"><span data-stu-id="7cfc6-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="7cfc6-125">十六进制转义 (%nn)。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="7cfc6-126">Unicode 转义 (%nnn)。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="7cfc6-127">超长 UTF-8 转义 (%nn%nn)。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="7cfc6-128">双转义（%nn 成为 %mmnn，其中 %mm 是 '%' 的转义）。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="7cfc6-129">请注意，用户名可能不止有一种规范格式。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="7cfc6-130">例如，经常可以使用 MYDOMAIN\\*username* 形式或 *username*@mydomain.example.com 形式。</span><span class="sxs-lookup"><span data-stu-id="7cfc6-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cfc6-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cfc6-131">See also</span></span>

- [<span data-ttu-id="7cfc6-132">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="7cfc6-132">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
