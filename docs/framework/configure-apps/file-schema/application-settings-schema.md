---
title: 应用程序设置架构
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: fc9cd8ac3819c6a02019c871e7bd45ceb4c2cef7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552305"
---
# <a name="application-settings-schema"></a><span data-ttu-id="d6f8f-102">应用程序设置架构</span><span class="sxs-lookup"><span data-stu-id="d6f8f-102">Application Settings schema</span></span>

<span data-ttu-id="d6f8f-103">应用程序设置允许 Windows 窗体或 ASP.NET 应用程序存储和检索应用程序范围的设置和用户范围的设置。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="d6f8f-104">在此上下文中， *设置* 是指特定于应用程序或特定于当前用户的任何信息，包括从数据库连接字符串到用户首选默认窗口大小的任何信息。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="d6f8f-105">默认情况下，Windows 窗体应用程序中的应用程序设置使用 <xref:System.Configuration.LocalFileSettingsProvider> 类，该类使用 .net 配置系统将设置存储在 XML 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="d6f8f-106">有关应用程序设置使用的文件的详细信息，请参阅 [应用程序设置体系结构](/dotnet/desktop/winforms/advanced/application-settings-architecture)。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-106">For more information about the files used by application settings, see [Application Settings Architecture](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span></span>

<span data-ttu-id="d6f8f-107">应用程序设置将以下元素定义为它所使用的配置文件的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="d6f8f-108">元素</span><span class="sxs-lookup"><span data-stu-id="d6f8f-108">Element</span></span>                    | <span data-ttu-id="d6f8f-109">说明</span><span class="sxs-lookup"><span data-stu-id="d6f8f-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="d6f8f-110">包含 **\<setting>** 应用程序特定的所有标记。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="d6f8f-111">包含 **\<setting>** 特定于当前用户的所有标记。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="d6f8f-112">定义设置。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-112">Defines a setting.</span></span> <span data-ttu-id="d6f8f-113">或的子级 **\<applicationSettings>** **\<userSettings>** 。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="d6f8f-114">定义设置的值。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-114">Defines a setting's value.</span></span> <span data-ttu-id="d6f8f-115">的子项 **\<setting>** 。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="d6f8f-116">\<applicationSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="d6f8f-116">\<applicationSettings> element</span></span>

<span data-ttu-id="d6f8f-117">此元素包含 **\<setting>** 特定于客户端计算机上的应用程序实例的所有标记。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="d6f8f-118">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="d6f8f-119">\<userSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="d6f8f-119">\<userSettings> element</span></span>

<span data-ttu-id="d6f8f-120">此元素包含 **\<setting>** 特定于当前正在使用应用程序的用户的所有标记。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="d6f8f-121">未定义任何属性。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="d6f8f-122">\<setting> 元素</span><span class="sxs-lookup"><span data-stu-id="d6f8f-122">\<setting> element</span></span>

<span data-ttu-id="d6f8f-123">此元素定义一个设置。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-123">This element defines a setting.</span></span> <span data-ttu-id="d6f8f-124">它具有以下属性。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-124">It has the following attributes.</span></span>

| <span data-ttu-id="d6f8f-125">Attribute</span><span class="sxs-lookup"><span data-stu-id="d6f8f-125">Attribute</span></span>        | <span data-ttu-id="d6f8f-126">说明</span><span class="sxs-lookup"><span data-stu-id="d6f8f-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="d6f8f-127">name</span><span class="sxs-lookup"><span data-stu-id="d6f8f-127">**name**</span></span>         | <span data-ttu-id="d6f8f-128">必需。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-128">Required.</span></span> <span data-ttu-id="d6f8f-129">设置的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-129">The unique ID of the setting.</span></span> <span data-ttu-id="d6f8f-130">使用名称保存通过 Visual Studio 创建的设置 `ProjectName.Properties.Settings` 。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="d6f8f-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="d6f8f-131">**serializeAs**</span></span> | <span data-ttu-id="d6f8f-132">必需。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-132">Required.</span></span> <span data-ttu-id="d6f8f-133">将值序列化为文本时要使用的格式。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="d6f8f-134">有效值是：</span><span class="sxs-lookup"><span data-stu-id="d6f8f-134">Valid values are:</span></span><br><br><span data-ttu-id="d6f8f-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="d6f8f-135">- `string`.</span></span> <span data-ttu-id="d6f8f-136">该值使用来序列化为字符串 <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="d6f8f-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="d6f8f-137">- `xml`.</span></span> <span data-ttu-id="d6f8f-138">使用 XML 序列化对值进行序列化。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="d6f8f-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="d6f8f-139">- `binary`.</span></span> <span data-ttu-id="d6f8f-140">使用二进制序列化将值作为文本编码的二进制序列化。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="d6f8f-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="d6f8f-141">- `custom`.</span></span> <span data-ttu-id="d6f8f-142">设置提供程序具有此设置的固有知识，并对其进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="d6f8f-143">\<value> 元素</span><span class="sxs-lookup"><span data-stu-id="d6f8f-143">\<value> element</span></span>

<span data-ttu-id="d6f8f-144">此元素包含设置的值。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="d6f8f-145">示例</span><span class="sxs-lookup"><span data-stu-id="d6f8f-145">Example</span></span>

<span data-ttu-id="d6f8f-146">以下示例显示了一个应用程序设置文件，该文件定义了两个应用程序范围的设置和两个用户范围的设置：</span><span class="sxs-lookup"><span data-stu-id="d6f8f-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d6f8f-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="d6f8f-147">See also</span></span>

- [<span data-ttu-id="d6f8f-148">应用程序设置概述</span><span class="sxs-lookup"><span data-stu-id="d6f8f-148">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="d6f8f-149">应用程序设置体系结构</span><span class="sxs-lookup"><span data-stu-id="d6f8f-149">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
