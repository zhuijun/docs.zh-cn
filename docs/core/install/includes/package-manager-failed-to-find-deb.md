---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132934"
---

如果收到类似于“找不到包 {netcore-package}”或“无法安装某些包”的错误消息，请运行以下命令 。

以下命令组中有两个占位符。

- `{dotnet-package}`\
此项表示要安装的 .NET Core 包，如 `aspnetcore-runtime-3.1`。 此项在以下 `sudo apt-get install` 命令中使用。

- `{os-version}`\
此项表示你所使用的 Linux 版本。 此项在以下 `wget` 命令中使用。

首先，尝试清除包列表：

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

然后，再次尝试安装 .NET Core。 如果这不起作用，可使用以下命令运行手动安装：
