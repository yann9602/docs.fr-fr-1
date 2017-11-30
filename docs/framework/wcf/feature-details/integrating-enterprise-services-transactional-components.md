---
title: "Intégration de composants transactionnels Enterprise Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05dab277-b8b2-48cf-b40c-826be128b175
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c2420c700d893e6c2c19b72beed0e605ffd4853
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="integrating-enterprise-services-transactional-components"></a><span data-ttu-id="b14fe-102">Intégration de composants transactionnels Enterprise Services</span><span class="sxs-lookup"><span data-stu-id="b14fe-102">Integrating Enterprise Services Transactional Components</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="b14fe-103">fournit un mécanisme automatique pour l’intégration avec les Services d’entreprise (voir [intégration à des Applications COM +](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span><span class="sxs-lookup"><span data-stu-id="b14fe-103"> provides an automatic mechanism for integrating with Enterprise Services (see [Integrating with COM+ Applications](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)).</span></span> <span data-ttu-id="b14fe-104">Cependant, vous préférez peut-être pouvoir développer des services utilisant en interne des composants transactionnels hébergés par Enterprise Services.</span><span class="sxs-lookup"><span data-stu-id="b14fe-104">However, you may want the flexibility to develop services that internally use transactional components hosted within Enterprise Services.</span></span> <span data-ttu-id="b14fe-105">Étant donné que la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonctionnalité de Transactions s’appuie sur le <xref:System.Transactions> infrastructure, le processus d’intégration des Services d’entreprise avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est identique à celle permettant de spécifier l’interopérabilité entre <xref:System.Transactions> et Enterprise Services, comme indiqué dans [l’interopérabilité avec les Services d’entreprise et les Transactions COM +](http://go.microsoft.com/fwlink/?LinkId=94949).</span><span class="sxs-lookup"><span data-stu-id="b14fe-105">Because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Transactions feature is built on the <xref:System.Transactions> infrastructure, the process for integrating Enterprise Services with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is identical to that for specifying interoperability between <xref:System.Transactions> and Enterprise Services, as outlined in [Interoperability with Enterprise Services and COM+ Transactions](http://go.microsoft.com/fwlink/?LinkId=94949).</span></span>  
  
 <span data-ttu-id="b14fe-106">Afin d'offrir un niveau d'interopérabilité suffisant entre les transactions entrantes et les transactions de contexte COM+, l'implémentation de service doit créer une instance <xref:System.Transactions.TransactionScope> et utiliser la valeur appropriée de l'énumération <xref:System.Transactions.EnterpriseServicesInteropOption>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-106">To provide the desired level of interoperability between the incoming flowed transaction and the COM+ context transaction, the service implementation must create a <xref:System.Transactions.TransactionScope> instance and use the appropriate value from the <xref:System.Transactions.EnterpriseServicesInteropOption> enumeration.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-service-operation"></a><span data-ttu-id="b14fe-107">Intégration des composants Enterprise Services à une opération de service</span><span class="sxs-lookup"><span data-stu-id="b14fe-107">Integrating Enterprise Services with a Service Operation</span></span>  
 <span data-ttu-id="b14fe-108">L'exemple de code suivant contient une opération (autorisant le transfert des transactions) qui crée une étendue <xref:System.Transactions.TransactionScope> à l'aide de l'option <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-108">The following code demonstrates an operation, with Allowed transaction flow, that creates a <xref:System.Transactions.TransactionScope> with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> option.</span></span> <span data-ttu-id="b14fe-109">Les conditions suivantes s'appliquent à notre exemple :</span><span class="sxs-lookup"><span data-stu-id="b14fe-109">The following conditions apply in this scenario:</span></span>  
  
-   <span data-ttu-id="b14fe-110">Si le client transfère une transaction, l'opération, y compris l'appel au composant Enterprise Services, est exécutée dans les limites de portée de cette transaction.</span><span class="sxs-lookup"><span data-stu-id="b14fe-110">If the client flows a transaction, the operation, including the call to the Enterprise Services component, is executed within the scope of that transaction.</span></span> <span data-ttu-id="b14fe-111">L'utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> assure la synchronisation de la transaction avec le contexte <xref:System.EnterpriseServices>, ce qui signifie que la transaction ambiante de <xref:System.Transactions> correspond à celle de <xref:System.EnterpriseServices>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-111">Using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the transaction is synchronized with the <xref:System.EnterpriseServices> context, which means that the ambient transaction for <xref:System.Transactions> and the <xref:System.EnterpriseServices> is the same.</span></span>  
  
-   <span data-ttu-id="b14fe-112">Si le client ne transfère pas de transaction, affecter la valeur <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> à`true` attribue une nouvelle portée de transaction à l'opération.</span><span class="sxs-lookup"><span data-stu-id="b14fe-112">If the client does not flow a transaction, setting <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> to `true` creates a new transaction scope for the operation.</span></span> <span data-ttu-id="b14fe-113">De la même façon, l'utilisation de <xref:System.Transactions.EnterpriseServicesInteropOption.Full> garantit que la transaction de l'opération correspond à la transaction utilisée dans le contexte du composant <xref:System.EnterpriseServices>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-113">Similarly, using <xref:System.Transactions.EnterpriseServicesInteropOption.Full> ensures that the operation’s transaction is the same as the transaction used inside the <xref:System.EnterpriseServices> component's context.</span></span>  
  
 <span data-ttu-id="b14fe-114">Tous les appels de méthode supplémentaires se produisent également dans les limites de portée de transaction de la même opération.</span><span class="sxs-lookup"><span data-stu-id="b14fe-114">Any additional method calls also occur within the scope of the same operation’s transaction.</span></span>  
  
```  
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
  
 <span data-ttu-id="b14fe-115">Si aucune synchronisation n'est requise entre la transaction en cours d'une opération et les appels aux composants transactionnels Enterprise Services, utilisez l'option <xref:System.Transactions.EnterpriseServicesInteropOption.None> lorsque vous instanciez l'instance <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-115">If no synchronization is required between an operation’s current transaction and calls to transactional Enterprise Services components, then use the <xref:System.Transactions.EnterpriseServicesInteropOption.None> option when instantiating the <xref:System.Transactions.TransactionScope> instance.</span></span>  
  
## <a name="integrating-enterprise-services-with-a-client"></a><span data-ttu-id="b14fe-116">Intégration des composants Enterprise Services à un client</span><span class="sxs-lookup"><span data-stu-id="b14fe-116">Integrating Enterprise Services with a Client</span></span>  
 <span data-ttu-id="b14fe-117">L'exemple de code suivant contient un code client qui utilise une instance <xref:System.Transactions.TransactionScope> avec le paramètre <xref:System.Transactions.EnterpriseServicesInteropOption.Full>.</span><span class="sxs-lookup"><span data-stu-id="b14fe-117">The following code demonstrates client code using a <xref:System.Transactions.TransactionScope> instance with the <xref:System.Transactions.EnterpriseServicesInteropOption.Full> setting.</span></span> <span data-ttu-id="b14fe-118">Dans cet exemple de code, les appels aux opérations de service qui prennent en charge le transfert des transactions se produisent dans les mêmes limites de portée de transaction que les appels aux composants Enterprise Services, leurs transactions étant identiques.</span><span class="sxs-lookup"><span data-stu-id="b14fe-118">In this scenario, calls to service operations that support transaction flow occur within the scope of the same transaction as the calls to Enterprise Services components.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="b14fe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b14fe-119">See Also</span></span>  
 [<span data-ttu-id="b14fe-120">Intégration à des Applications COM +</span><span class="sxs-lookup"><span data-stu-id="b14fe-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="b14fe-121">Intégration à des Applications COM</span><span class="sxs-lookup"><span data-stu-id="b14fe-121">Integrating with COM Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications.md)
