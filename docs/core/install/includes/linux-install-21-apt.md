---
ms.openlocfilehash: 164d7a8277cf985735b959c73eb87391944e795b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602674"
---

### <a name="install-the-sdk"></a>安装 SDK

.NET Core SDK 使你可以通过 .NET Core 开发应用。 如果安装 .NET Core SDK，则无需安装相应的运行时。 若要安装 .NET Core SDK，请运行以下命令：

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-2.1
```

> [!IMPORTANT]
> 如果收到类似于“找不到包 dotnet-sdk-2.1”的错误消息，请参阅 [APT 疑难解答](#apt-troubleshooting)部分。

### <a name="install-the-runtime"></a>安装运行时

.NET Core 运行时允许运行使用不随附运行时的 .NET Core 所开发的应用。 以下命令安装 ASP.NET Core 运行时，这是与 .NET Core 最兼容的运行时。 在终端中，运行以下命令。

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-2.1
```

> [!IMPORTANT]
> 如果收到类似于“找不到包 aspnetcore-runtime-2.1”的错误消息，请参阅 [APT 疑难解答](#apt-troubleshooting)部分。

作为 ASP.NET Core 运行时的一种替代方法，你可以安装不包含 ASP.NET Core 支持的 .NET Core 运行时：将上述命令中的 `aspnetcore-runtime-2.1` 替换为 `dotnet-runtime-2.1`。

```bash
sudo apt-get install -y dotnet-runtime-2.1
```
