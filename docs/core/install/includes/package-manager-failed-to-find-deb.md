---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602746"
---

如果收到类似于“找不到包 {netcore-package}”的错误消息，请运行以下命令。

以下命令组中有两个占位符。

- `{dotnet-package}`\
此项表示要安装的 .NET Core 包，如 `aspnetcore-runtime-3.1`。 此项在以下 `sudo apt-get install` 命令中使用。

- `{os-version}`\
此项表示你所使用的 Linux 版本。 此项在以下 `wget` 命令中使用。

尝试清除包列表：

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

如果这不起作用，可使用以下命令运行手动安装：
