---
title: 集成企业服务事务性组件
ms.date: 03/30/2017
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
ms.openlocfilehash: 1c4fabfadb113c79b216fa10ff80b551ba0f9716
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596846"
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="097c6-102">集成企业服务事务性组件</span><span class="sxs-lookup"><span data-stu-id="097c6-102">Integrating Enterprise Services Transactional Components</span></span>

<span data-ttu-id="097c6-103">Windows Communication Foundation （WCF）提供了用于与企业服务集成的自动机制（请参阅[与 COM + 应用程序集成](integrating-with-com-plus-applications.md)）。</span><span class="sxs-lookup"><span data-stu-id="097c6-103">Windows Communication Foundation (WCF) provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="097c6-104">但是，你可能希望灵活地开发可在内部使用承载于企业服务中的事务性组件的服务。</span><span class="sxs-lookup"><span data-stu-id="097c6-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="097c6-105">由于 WCF 事务功能是基于 <xref:System.Transactions> 基础结构构建的，因此将企业服务与 WCF 集成的过程与指定和企业服务之间的互操作性的过程相同 <xref:System.Transactions> ，如[与企业服务和 com + 事务的互操作性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85))中所述。</span><span class="sxs-lookup"><span data-stu-id="097c6-105">Because the WCF Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with WCF is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms229974(v=vs.85)).</span></span>  
  
 <span data-ttu-id="097c6-106">若要在传入的流式事务和 COM+ 上下文事务之间提供所需级别的互操作性，服务实现必须创建一个 <xref:System.Transactions.TransactionScope> 实例并使用 <xref:System.Transactions.EnterpriseServicesInteropOption> 枚举中的适当值。</span><span class="sxs-lookup"><span data-stu-id="097c6-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="097c6-107">使企业服务与服务操作相集成</span><span class="sxs-lookup"><span data-stu-id="097c6-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="097c6-108">下面的代码演示对 Allowed 事务流执行的操作，该操作创建一个具有 <xref:System.Transactions.TransactionScope> 选项的 <xref:System.Transactions.EnterpriseServicesInteropOption.Full>。</span><span class="sxs-lookup"><span data-stu-id="097c6-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="097c6-109">以下条件适用于这种情况：</span><span class="sxs-lookup"><span data-stu-id="097c6-109">The following conditions apply in this scenario:</span></span>  
  
- <span data-ttu-id="097c6-110">如果客户端对事务进行流式处理，则操作（包括调用企业服务组件）将在该事务范围内执行。</span><span class="sxs-lookup"><span data-stu-id="097c6-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="097c6-111">使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 可确保事务与 <xref:System.EnterpriseServices> 上下文同步，这意味着 <xref:System.Transactions> 的环境事务和 <xref:System.EnterpriseServices> 相同。</span><span class="sxs-lookup"><span data-stu-id="097c6-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
- <span data-ttu-id="097c6-112">如果客户端不对事务进行流式处理，则将 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 设置为 `true` 可为操作创建新的事务范围。</span><span class="sxs-lookup"><span data-stu-id="097c6-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="097c6-113">同样，使用 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 可确保操作的事务与 <xref:System.EnterpriseServices> 组件的上下文中使用的事务相同。</span><span class="sxs-lookup"><span data-stu-id="097c6-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="097c6-114">任何其他方法调用也发生在同一个操作的事务范围内。</span><span class="sxs-lookup"><span data-stu-id="097c6-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```csharp
[ServiceContract()]  
public interface ICustomerServiceContract  
{  
   [OperationContract]  
   [TransactionFlow(TransactionFlowOption.Allowed)]  
   void UpdateCustomerNameOperation(int customerID, string newCustomerName);  
}  
  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CustomerService : ICustomerServiceContract  
{  
   [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
   public void UpdateCustomerNameOperation(int customerID, string newCustomerName)  
   {  
   // Create a transaction scope with full ES interop  
      using (TransactionScope ts = new TransactionScope(  
                     TransactionScopeOption.Required,  
                     new TransactionOptions(),  
                     EnterpriseServicesInteropOption.Full))  
      {  
         // Create an Enterprise Services component  
         // Call UpdateCustomer method on an Enterprise Services
         // component
  
         // Call UpdateOtherCustomerData method on an Enterprise
         // Services component
         ts.Complete();  
      }  
  
      // Do UpdateAdditionalData on an non-Enterprise Services  
      // component  
   }  
}  
```  
  
 <span data-ttu-id="097c6-115">如果某一操作的当前事务和对事务性企业服务组件的调用之间不需要同步，则在实例化 <xref:System.Transactions.EnterpriseServicesInteropOption.None> 实例时请使用 <xref:System.Transactions.TransactionScope> 选项。</span><span class="sxs-lookup"><span data-stu-id="097c6-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="097c6-116">使企业服务与客户端相集成</span><span class="sxs-lookup"><span data-stu-id="097c6-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="097c6-117">下面的代码演示使用 <xref:System.Transactions.TransactionScope> 实例的客户端代码，该实例具有 <xref:System.Transactions.EnterpriseServicesInteropOption.Full> 设置。</span><span class="sxs-lookup"><span data-stu-id="097c6-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="097c6-118">在这种情况下，对支持事务流的服务操作的调用与对企业服务组件的调用发生在同一个事务范围内。</span><span class="sxs-lookup"><span data-stu-id="097c6-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```csharp
static void Main()  
{  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
  
    // Create a transaction scope with full ES interop  
    using (TransactionScope ts = new TransactionScope(  
          TransactionScopeOption.Required,  
          new TransactionOptions(),  
          EnterpriseServicesInteropOption.Full))  
    {  
        // Call Add calculator service operation  
  
        // Create an Enterprise Services component  
  
        // Call UpdateCustomer method on an Enterprise Services
        // component
  
        ts.Complete();  
    }  
  
    // Closing the client gracefully closes the connection and
    // cleans up resources  
    client.Close();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="097c6-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="097c6-119">See also</span></span>

- [<span data-ttu-id="097c6-120">与 COM + 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="097c6-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
- [<span data-ttu-id="097c6-121">与 COM 应用程序集成</span><span class="sxs-lookup"><span data-stu-id="097c6-121">Integrating with COM Applications</span></span>](integrating-with-com-applications.md)
