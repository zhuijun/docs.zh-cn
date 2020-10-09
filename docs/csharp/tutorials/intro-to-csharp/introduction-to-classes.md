---
title: 类和对象 - C# 简介教程
description: 创建首个 C# 程序，并探索面向对象的概念
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 57394ecb02745d69e22f4d9f1dbd4213f290cd5a
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609045"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="85ff6-103">使用类和对象探索面向对象的编程</span><span class="sxs-lookup"><span data-stu-id="85ff6-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="85ff6-104">本教程要求你有一台可用于开发的计算机。</span><span class="sxs-lookup"><span data-stu-id="85ff6-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="85ff6-105">.NET 教程 [Hello World 10 分钟入门](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)介绍了如何在 Windows、Linux 或 macOS 上设置本地开发环境。</span><span class="sxs-lookup"><span data-stu-id="85ff6-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="85ff6-106">[熟悉开发工具](local-environment.md)不仅简要概述了将用到的命令，还收录了详细信息链接。</span><span class="sxs-lookup"><span data-stu-id="85ff6-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="85ff6-107">创建应用程序</span><span class="sxs-lookup"><span data-stu-id="85ff6-107">Create your application</span></span>

<span data-ttu-id="85ff6-108">使用终端窗口，创建名为 classes 的目录。</span><span class="sxs-lookup"><span data-stu-id="85ff6-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="85ff6-109">可以在其中生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="85ff6-109">You'll build your application there.</span></span> <span data-ttu-id="85ff6-110">将此目录更改为当前目录，并在控制台窗口中键入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="85ff6-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="85ff6-111">此命令可创建应用程序。</span><span class="sxs-lookup"><span data-stu-id="85ff6-111">This command creates your application.</span></span> <span data-ttu-id="85ff6-112">打开 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="85ff6-112">Open *Program.cs*.</span></span> <span data-ttu-id="85ff6-113">应如下所示：</span><span class="sxs-lookup"><span data-stu-id="85ff6-113">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="85ff6-114">在本教程中，将要新建表示银行帐户的类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="85ff6-115">通常情况下，开发者都会在不同的文本文件中定义每个类。</span><span class="sxs-lookup"><span data-stu-id="85ff6-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="85ff6-116">这样可以更轻松地管理不断增大的程序。</span><span class="sxs-lookup"><span data-stu-id="85ff6-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="85ff6-117">在 classes 目录中，新建名为 BankAccount.cs 的文件。</span><span class="sxs-lookup"><span data-stu-id="85ff6-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="85ff6-118">此文件包含“银行帐户”定义。</span><span class="sxs-lookup"><span data-stu-id="85ff6-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="85ff6-119">面向对象的编程组织代码的方式为，创建类形式的类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="85ff6-120">这些类包含表示特定实体的代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="85ff6-121">`BankAccount` 类表示银行帐户。</span><span class="sxs-lookup"><span data-stu-id="85ff6-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="85ff6-122">代码通过方法和属性实现特定操作。</span><span class="sxs-lookup"><span data-stu-id="85ff6-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="85ff6-123">在本教程中，银行帐户支持以下行为：</span><span class="sxs-lookup"><span data-stu-id="85ff6-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="85ff6-124">用一个 10 位数唯一标识银行帐户。</span><span class="sxs-lookup"><span data-stu-id="85ff6-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="85ff6-125">用字符串存储一个或多个所有者名称。</span><span class="sxs-lookup"><span data-stu-id="85ff6-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="85ff6-126">可以检索余额。</span><span class="sxs-lookup"><span data-stu-id="85ff6-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="85ff6-127">接受存款。</span><span class="sxs-lookup"><span data-stu-id="85ff6-127">It accepts deposits.</span></span>
1. <span data-ttu-id="85ff6-128">接受取款。</span><span class="sxs-lookup"><span data-stu-id="85ff6-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="85ff6-129">初始余额必须是正数。</span><span class="sxs-lookup"><span data-stu-id="85ff6-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="85ff6-130">取款后的余额不能是负数。</span><span class="sxs-lookup"><span data-stu-id="85ff6-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="85ff6-131">定义银行帐户类型</span><span class="sxs-lookup"><span data-stu-id="85ff6-131">Define the bank account type</span></span>

<span data-ttu-id="85ff6-132">首先，创建定义此行为的类的基本设置。</span><span class="sxs-lookup"><span data-stu-id="85ff6-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="85ff6-133">使用 File:New 命令创建新文件。</span><span class="sxs-lookup"><span data-stu-id="85ff6-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="85ff6-134">将其命名为“BankAccount.cs”。</span><span class="sxs-lookup"><span data-stu-id="85ff6-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="85ff6-135">将以下代码添加到 BankAccount.cs 文件：</span><span class="sxs-lookup"><span data-stu-id="85ff6-135">Add the following code to your *BankAccount.cs* file:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="85ff6-136">继续操作前，先来看看已经生成的内容。</span><span class="sxs-lookup"><span data-stu-id="85ff6-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="85ff6-137">借助 `namespace` 声明，可以按逻辑组织代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="85ff6-138">由于本教程的篇幅较小，因此所有代码都将添加到一个命名空间中。</span><span class="sxs-lookup"><span data-stu-id="85ff6-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="85ff6-139">`public class BankAccount` 定义要创建的类或类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="85ff6-140">类声明后面 `{` 和 `}` 中的所有内容定义了类的状态和行为。</span><span class="sxs-lookup"><span data-stu-id="85ff6-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="85ff6-141">`BankAccount` 类有五个成员。</span><span class="sxs-lookup"><span data-stu-id="85ff6-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="85ff6-142">前三个成员是属性。</span><span class="sxs-lookup"><span data-stu-id="85ff6-142">The first three are ***properties***.</span></span> <span data-ttu-id="85ff6-143">属性是数据元素，可以包含强制执行验证或其他规则的代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="85ff6-144">最后两个成员是方法。</span><span class="sxs-lookup"><span data-stu-id="85ff6-144">The last two are ***methods***.</span></span> <span data-ttu-id="85ff6-145">方法是执行一个函数的代码块。</span><span class="sxs-lookup"><span data-stu-id="85ff6-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="85ff6-146">读取每个成员的名称应该能够为自己或其他开发者提供了解类用途的足够信息。</span><span class="sxs-lookup"><span data-stu-id="85ff6-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="85ff6-147">打开新帐户</span><span class="sxs-lookup"><span data-stu-id="85ff6-147">Open a new account</span></span>

<span data-ttu-id="85ff6-148">要实现的第一个功能是打开银行帐户。</span><span class="sxs-lookup"><span data-stu-id="85ff6-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="85ff6-149">打开帐户时，客户必须提供初始余额，以及此帐户的一个或多个所有者的相关信息。</span><span class="sxs-lookup"><span data-stu-id="85ff6-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="85ff6-150">新建 `BankAccount` 类型的对象意味着，定义可分配这些值的构造函数。</span><span class="sxs-lookup"><span data-stu-id="85ff6-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="85ff6-151">构造函数是与类同名的成员。</span><span class="sxs-lookup"><span data-stu-id="85ff6-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="85ff6-152">用于初始化相应类类型的对象。</span><span class="sxs-lookup"><span data-stu-id="85ff6-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="85ff6-153">将以下构造函数添加到 `BankAccount` 类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="85ff6-154">将下面的代码放在 `MakeDeposit` 声明的上方：</span><span class="sxs-lookup"><span data-stu-id="85ff6-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="85ff6-155">构造函数是在使用 [`new`](../../language-reference/operators/new-operator.md) 创建对象时进行调用。</span><span class="sxs-lookup"><span data-stu-id="85ff6-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="85ff6-156">将 Program.cs 中的代码行 `Console.WriteLine("Hello World!");` 替换为以下代码行（将 `<name>` 替换为自己的名称）：</span><span class="sxs-lookup"><span data-stu-id="85ff6-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="85ff6-157">我们来运行到目前为止已构建的内容。</span><span class="sxs-lookup"><span data-stu-id="85ff6-157">Let's run what you've built so far.</span></span> <span data-ttu-id="85ff6-158">如果使用的是 Visual Studio，请在“运行”菜单中选择“启动而不调试”。</span><span class="sxs-lookup"><span data-stu-id="85ff6-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="85ff6-159">如果使用的是命令行，请在创建项目的目录中键入 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="85ff6-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="85ff6-160">有没有注意到帐号为空？</span><span class="sxs-lookup"><span data-stu-id="85ff6-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="85ff6-161">是时候解决这个问题了。</span><span class="sxs-lookup"><span data-stu-id="85ff6-161">It's time to fix that.</span></span> <span data-ttu-id="85ff6-162">帐号应在构造对象时分配。</span><span class="sxs-lookup"><span data-stu-id="85ff6-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="85ff6-163">但不得由调用方负责创建。</span><span class="sxs-lookup"><span data-stu-id="85ff6-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="85ff6-164">`BankAccount` 类代码应了解如何分配新帐号。</span><span class="sxs-lookup"><span data-stu-id="85ff6-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="85ff6-165">这样做的简单方法是从一个 10 位数开始。</span><span class="sxs-lookup"><span data-stu-id="85ff6-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="85ff6-166">帐号随每个新建的帐户而递增。</span><span class="sxs-lookup"><span data-stu-id="85ff6-166">Increment it when each new account is created.</span></span> <span data-ttu-id="85ff6-167">最后，在构造对象时，存储当前的帐号。</span><span class="sxs-lookup"><span data-stu-id="85ff6-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="85ff6-168">将成员声明添加到 `BankAccount` 类。</span><span class="sxs-lookup"><span data-stu-id="85ff6-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="85ff6-169">将以下代码行放在 `BankAccount` 类开头的左括号 `{` 后面：</span><span class="sxs-lookup"><span data-stu-id="85ff6-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="85ff6-170">此为数据成员。</span><span class="sxs-lookup"><span data-stu-id="85ff6-170">This is a data member.</span></span> <span data-ttu-id="85ff6-171">它是 `private`，这意味着只能通过 `BankAccount` 类中的代码访问它。</span><span class="sxs-lookup"><span data-stu-id="85ff6-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="85ff6-172">这是一种分离公共责任（如拥有帐号）与私有实现（如何生成帐号）的方法。</span><span class="sxs-lookup"><span data-stu-id="85ff6-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="85ff6-173">它也是 `static`，这意味着它由所有 `BankAccount` 对象共享。</span><span class="sxs-lookup"><span data-stu-id="85ff6-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="85ff6-174">非静态变量的值对于 `BankAccount` 对象的每个实例是唯一的。</span><span class="sxs-lookup"><span data-stu-id="85ff6-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="85ff6-175">将下面两行代码添加到构造函数，以分配帐号。</span><span class="sxs-lookup"><span data-stu-id="85ff6-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="85ff6-176">将它们放在 `this.Balance = initialBalance` 行后面：</span><span class="sxs-lookup"><span data-stu-id="85ff6-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="85ff6-177">键入 `dotnet run` 看看结果如何。</span><span class="sxs-lookup"><span data-stu-id="85ff6-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="85ff6-178">创建存款和取款</span><span class="sxs-lookup"><span data-stu-id="85ff6-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="85ff6-179">银行帐户类必须接受存款和取款，才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="85ff6-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="85ff6-180">接下来，将为银行帐户创建每笔交易日记，实现存款和取款。</span><span class="sxs-lookup"><span data-stu-id="85ff6-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="85ff6-181">与仅更新每笔交易余额相比，这样做有一些优点。</span><span class="sxs-lookup"><span data-stu-id="85ff6-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="85ff6-182">历史记录可用于审核所有交易，并管理每日余额。</span><span class="sxs-lookup"><span data-stu-id="85ff6-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="85ff6-183">通过在需要时根据所有交易的历史记录计算余额，单笔交易中修正的任何错误将会在下次计算余额时得到正确体现。</span><span class="sxs-lookup"><span data-stu-id="85ff6-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="85ff6-184">接下来，先新建表示交易的类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="85ff6-185">这是一个没有任何责任的简单类型。</span><span class="sxs-lookup"><span data-stu-id="85ff6-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="85ff6-186">但需要有多个属性。</span><span class="sxs-lookup"><span data-stu-id="85ff6-186">It needs a few properties.</span></span> <span data-ttu-id="85ff6-187">新建名为 Transaction.cs 的文件。</span><span class="sxs-lookup"><span data-stu-id="85ff6-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="85ff6-188">向新文件添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="85ff6-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="85ff6-189">现在，将 `Transaction` 对象的 <xref:System.Collections.Generic.List%601> 添加到 `BankAccount` 类中。</span><span class="sxs-lookup"><span data-stu-id="85ff6-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="85ff6-190">将以下声明放在 BankAccount.cs 文件中的构造函数后面：</span><span class="sxs-lookup"><span data-stu-id="85ff6-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="85ff6-191"><xref:System.Collections.Generic.List%601> 类要求导入不同的命名空间。</span><span class="sxs-lookup"><span data-stu-id="85ff6-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="85ff6-192">在 BankAccount.cs 的开头，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="85ff6-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="85ff6-193">现在，更改 `Balance` 的报告方式。</span><span class="sxs-lookup"><span data-stu-id="85ff6-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="85ff6-194">可以通过对所有交易的值进行求和计算余额。</span><span class="sxs-lookup"><span data-stu-id="85ff6-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="85ff6-195">将 `BankAccount` 类中 `Balance` 的声明修改为如下所示：</span><span class="sxs-lookup"><span data-stu-id="85ff6-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="85ff6-196">此示例反映了属性的一个重要方面。</span><span class="sxs-lookup"><span data-stu-id="85ff6-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="85ff6-197">现在，可以在其他程序员要求获取余额时计算值。</span><span class="sxs-lookup"><span data-stu-id="85ff6-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="85ff6-198">计算会枚举所有交易，总和即为当前余额。</span><span class="sxs-lookup"><span data-stu-id="85ff6-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="85ff6-199">接下来，实现 `MakeDeposit` 和 `MakeWithdrawal` 方法。</span><span class="sxs-lookup"><span data-stu-id="85ff6-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="85ff6-200">这些方法将强制执行最后两条规则：初始余额必须为正数，且取款后的余额不能是负数。</span><span class="sxs-lookup"><span data-stu-id="85ff6-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="85ff6-201">这就引入了异常的概念。</span><span class="sxs-lookup"><span data-stu-id="85ff6-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="85ff6-202">指明方法无法成功完成工作的标准方法是抛出异常。</span><span class="sxs-lookup"><span data-stu-id="85ff6-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="85ff6-203">异常类型及其关联消息描述了错误。</span><span class="sxs-lookup"><span data-stu-id="85ff6-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="85ff6-204">在此示例中，如果存款金额为负数，`MakeDeposit` 方法会抛出异常。</span><span class="sxs-lookup"><span data-stu-id="85ff6-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="85ff6-205">如果取款金额为负数，或取款后的余额为负数，`MakeWithdrawal` 方法会抛出异常。</span><span class="sxs-lookup"><span data-stu-id="85ff6-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="85ff6-206">将以下代码添加到 `allTransactions` 列表的声明后面：</span><span class="sxs-lookup"><span data-stu-id="85ff6-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="85ff6-207">[`throw`](../../language-reference/keywords/throw.md) 语句将引发异常。</span><span class="sxs-lookup"><span data-stu-id="85ff6-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="85ff6-208">当前块执行结束，将控制权移交给在调用堆栈中发现的第一个匹配的 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="85ff6-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="85ff6-209">添加 `catch` 块可以稍后再测试一下此代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="85ff6-210">构造函数应进行一处更改，更改为添加初始交易，而不是直接更新余额。</span><span class="sxs-lookup"><span data-stu-id="85ff6-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="85ff6-211">由于已编写 `MakeDeposit` 方法，因此通过构造函数调用它。</span><span class="sxs-lookup"><span data-stu-id="85ff6-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="85ff6-212">完成的构造函数应如下所示：</span><span class="sxs-lookup"><span data-stu-id="85ff6-212">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="85ff6-213"><xref:System.DateTime.Now?displayProperty=nameWithType> 是返回当前日期和时间的属性。</span><span class="sxs-lookup"><span data-stu-id="85ff6-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="85ff6-214">在创建新 `BankAccount` 的代码后面，在 `Main` 方法中添加几个存款和取款，对此进行测试：</span><span class="sxs-lookup"><span data-stu-id="85ff6-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="85ff6-215">接下来，尝试创建初始余额为负数的帐户，测试能否捕获到错误条件。</span><span class="sxs-lookup"><span data-stu-id="85ff6-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="85ff6-216">在刚刚添加的上述代码后面，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="85ff6-216">Add the following code after the preceding code you just added:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="85ff6-217">使用 [`try` 和 `catch` 语句](../../language-reference/keywords/try-catch.md)，标记可能会引发异常的代码块，并捕获预期错误。</span><span class="sxs-lookup"><span data-stu-id="85ff6-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="85ff6-218">可以使用相同的技术，测试代码能否在取款后余额为负数时引发异常。</span><span class="sxs-lookup"><span data-stu-id="85ff6-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="85ff6-219">在 `Main` 方法的末尾添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="85ff6-219">Add the following code at the end of your `Main` method:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="85ff6-220">保存此文件，并键入 `dotnet run`，试运行看看。</span><span class="sxs-lookup"><span data-stu-id="85ff6-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="85ff6-221">挑战 - 记录所有交易</span><span class="sxs-lookup"><span data-stu-id="85ff6-221">Challenge - log all transactions</span></span>

<span data-ttu-id="85ff6-222">为了完成本教程，可以编写 `GetAccountHistory` 方法，为交易历史记录创建 `string`。</span><span class="sxs-lookup"><span data-stu-id="85ff6-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="85ff6-223">将此方法添加到 `BankAccount` 类型中：</span><span class="sxs-lookup"><span data-stu-id="85ff6-223">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="85ff6-224">上面的代码使用 <xref:System.Text.StringBuilder> 类，设置包含每个交易行的字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="85ff6-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="85ff6-225">在前面的教程中，也遇到过字符串格式设置代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="85ff6-226">新增的一个字符为 `\t`。</span><span class="sxs-lookup"><span data-stu-id="85ff6-226">One new character is `\t`.</span></span> <span data-ttu-id="85ff6-227">这用于插入选项卡，从而设置输出格式。</span><span class="sxs-lookup"><span data-stu-id="85ff6-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="85ff6-228">添加以下代码行，在 Program.cs 中对它进行测试：</span><span class="sxs-lookup"><span data-stu-id="85ff6-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="85ff6-229">运行程序以查看结果。</span><span class="sxs-lookup"><span data-stu-id="85ff6-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85ff6-230">后续步骤</span><span class="sxs-lookup"><span data-stu-id="85ff6-230">Next steps</span></span>

<span data-ttu-id="85ff6-231">如果遇到问题，可以在 [GitHub 存储库](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/)中查看本教程的源代码。</span><span class="sxs-lookup"><span data-stu-id="85ff6-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="85ff6-232">可继续学习[面向对象的编程](object-oriented-programming.md)教程。</span><span class="sxs-lookup"><span data-stu-id="85ff6-232">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="85ff6-233">若要详细了解这些概念，请参阅下列文章：</span><span class="sxs-lookup"><span data-stu-id="85ff6-233">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="85ff6-234">If 和 else 语句</span><span class="sxs-lookup"><span data-stu-id="85ff6-234">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="85ff6-235">While 语句</span><span class="sxs-lookup"><span data-stu-id="85ff6-235">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="85ff6-236">Do 语句</span><span class="sxs-lookup"><span data-stu-id="85ff6-236">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="85ff6-237">For 语句</span><span class="sxs-lookup"><span data-stu-id="85ff6-237">For statement</span></span>](../../language-reference/keywords/for.md)
