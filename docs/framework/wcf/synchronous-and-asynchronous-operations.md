---
title: "Opérations synchrones et asynchrones"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 106a3faf11c1568f144d42514b64f4d336cf447c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="b5f3d-102">Opérations synchrones et asynchrones</span><span class="sxs-lookup"><span data-stu-id="b5f3d-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="b5f3d-103">Cette rubrique traite de l'implémentation et de l'appel des opérations de service asynchrones.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="b5f3d-104">De nombreuses applications appellent des méthodes de façon asynchrone, car elles peuvent ainsi continuer à effectuer un travail utile pendant que l'appel de méthode s'exécute.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="b5f3d-105">Les services et les clients [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] peuvent participer à des appels d'opération asynchrones à deux niveaux distincts de l'application, qui procurent aux applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] plus de souplesse pour optimiser le débit en fonction de l'interactivité.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-105">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="b5f3d-106">Types d'opérations asynchrones</span><span class="sxs-lookup"><span data-stu-id="b5f3d-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="b5f3d-107">Tous les contrats de service dans [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], indépendamment des types de paramètres et des valeurs de retour, utilisent des attributs [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour spécifier un modèle d'échange de messages particulier entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-107">All service contracts in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], no matter the parameters types and return values, use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] attributes to specify a particular message exchange pattern between client and service.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="b5f3d-108"> route automatiquement les messages SOAP entrants et sortants vers l'opération de service appropriée ou le code client exécuté.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-108"> automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="b5f3d-109">Le client possède uniquement le contrat de service qui spécifie le modèle d'échange de messages pour une opération particulière.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="b5f3d-110">Les clients peuvent offrir au développeur un modèle de programmation de leur choix, tant que le modèle d'échange de messages sous-jacent est respecté.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="b5f3d-111">De même, les services peuvent implémenter des opérations de quelque manière que ce soit, à condition que le modèle de message spécifié soit respecté.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="b5f3d-112">L'indépendance du contrat de service vis à vis de l'implémentation du service ou du client autorise les types d'exécutions asynchrones suivants dans les applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="b5f3d-113">Les clients peuvent appeler de façon asynchrone des opérations de demande/réponse à l'aide d'un échange de messages synchrone.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="b5f3d-114">Les services peuvent implémenter de façon asynchrone une opération de demande/réponse à l'aide d'un échange de messages synchrone.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="b5f3d-115">Les échanges de messages peuvent être unidirectionnels, indépendamment de l'implémentation du client ou service.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="b5f3d-116">Scénarios asynchrones suggérés</span><span class="sxs-lookup"><span data-stu-id="b5f3d-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="b5f3d-117">Utilisez une approche asynchrone dans une implémentation de l'opération de service si celle-ci passe un appel bloquant, par exemple une tâche en E/S.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="b5f3d-118">Lorsque vous êtes dans une implémentation d'opération asynchrone, essayez d'appeler des méthodes et des opérations asynchrones pour étendre le chemin d'appel asynchrone aussi loin que possible.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="b5f3d-119">Par exemple, appelez `BeginOperationTwo()` à partir d'un `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="b5f3d-120">Utilisez une approche asynchrone dans une application cliente ou appelante dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="b5f3d-121">Si vous appelez des opérations à partir d'une application intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="b5f3d-122">([!INCLUDE[crabout](../../../includes/crabout-md.md)] de ces scénarios, consultez [Applications clientes de niveau intermédiaire](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="b5f3d-122">([!INCLUDE[crabout](../../../includes/crabout-md.md)] such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="b5f3d-123">Si vous appelez des opérations à partir d'une page ASP.NET, utiliser des pages asynchrones.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="b5f3d-124">Si vous appelez des opérations à partir de n'importe quelle application monothread, telle que Windows Forms ou [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f3d-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="b5f3d-125">Lorsque vous utilisez le modèle d'appel asynchrone basé sur des événements, l'événement résultant est déclenché sur le thread d'interface utilisateur, ce qui accroît la réactivité de l'application sans exiger la gestion de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="b5f3d-126">En général, si vous avez le choix entre un appel synchrone et asynchrone, choisissez l'appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="b5f3d-127">Implémentation d'une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="b5f3d-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="b5f3d-128">Les opérations asynchrones peuvent être implémentées à l'aide d'une des trois méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="b5f3d-129">Modèle asynchrone basé sur des tâches</span><span class="sxs-lookup"><span data-stu-id="b5f3d-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="b5f3d-130">Modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="b5f3d-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="b5f3d-131">Modèle asynchrone IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="b5f3d-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="b5f3d-132">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="b5f3d-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="b5f3d-133">Le modèle asynchrone basé sur des tâches constitue le meilleur moyen d’implémenter des opérations asynchrones, car il est le plus facile et le plus simple.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="b5f3d-134">Pour utiliser cette méthode, implémentez votre opération de service simplement et spécifiez un type de retour de tâche\<T >, où T est le type retourné par l’opération logique.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="b5f3d-135">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="b5f3d-136">L’opération SampleMethodTaskAsync retourne Task\<chaîne >, car l’opération logique retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="b5f3d-137">Pour plus d’informations sur le modèle asynchrone basé sur des tâches, consultez [les modèle asynchrone basé sur les tâches](http://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="b5f3d-138">Lorsque vous utilisez le modèle asynchrone basé sur des tâches, une exception T:System.AggregateException peut être levée si une exception se produit lors de l’attente de la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="b5f3d-139">Cette exception peut se produire sur le client ou les services.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="b5f3d-140">Modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="b5f3d-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="b5f3d-141">Un service prenant en charge le modèle asynchrone basé sur des événements possédera une ou plusieurs opérations nommées MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="b5f3d-142">Ces méthodes peuvent refléter des versions synchrones qui exécutent la même opération sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="b5f3d-143">La classe peut également posséder un événement MethodNameCompleted et une méthode MethodNameAsyncCancel (ou simplement CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="b5f3d-144">Un client souhaitant appeler l'opération définira un gestionnaire d'événements à appeler lorsque l'opération se termine.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="b5f3d-145">L’extrait de code suivant montre comment déclarer des opérations asynchrones à l’aide du modèle asynchrone basé sur des événements.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="b5f3d-146">Pour plus d’informations sur le modèle asynchrone basé sur des événements, consultez [les modèle asynchrone basé sur les événements](http://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="b5f3d-147">Modèle asynchrone IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="b5f3d-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="b5f3d-148">Une opération de service peut être implémentée de manière asynchrone à l'aide du modèle de programmation asynchrone [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] et en marquant la méthode `<Begin>` avec la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> ayant la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="b5f3d-149">Dans ce cas, l'opération asynchrone est exposée dans les métadonnées sous la forme d'une opération synchrone: Elle est exposée comme une seule opération avec un message de demande et un message de réponse corrélé.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="b5f3d-150">Les modèles de programmation clients doivent ensuite choisir entre deux options.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-150">Client programming models then have a choice.</span></span> <span data-ttu-id="b5f3d-151">Ils peuvent représenter ce modèle comme une opération synchrone ou asynchrone, tant qu'un échange de messages de réponse-demande a lieu lorsque le service est appelé.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="b5f3d-152">En général, avec la nature asynchrone des systèmes, vous ne devez pas exploiter de dépendance sur les threads.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="b5f3d-153">La méthode la plus fiable pour transmettre des données à différentes étapes du traitement de la distribution des opérations consiste à utiliser les extensions.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="b5f3d-154">Pour obtenir un exemple, consultez [Comment : implémenter une opération de Service asynchrone](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="b5f3d-155">Pour définir une opération de contrat `X` exécutée de façon asynchrone quelle que soit la manière dont elle est appelée dans l'application cliente :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="b5f3d-156">Définissez deux méthodes à l'aide du modèle `BeginOperation` et `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="b5f3d-157">La méthode `BeginOperation` inclut les paramètres `in` et `ref` pour l'opération et retourne un type <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="b5f3d-158">La méthode `EndOperation` inclut un paramètre <xref:System.IAsyncResult> ainsi que les paramètres `out` et `ref` et elle retourne le type de retour des opérations.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="b5f3d-159">Par exemple, reportez-vous à la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="b5f3d-160">Voici les deux méthodes pour créer une opération asynchrone :</span><span class="sxs-lookup"><span data-stu-id="b5f3d-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="b5f3d-161">L'attribut <xref:System.ServiceModel.OperationContractAttribute> est appliqué uniquement à la méthode `BeginDoWork`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="b5f3d-162">Le contrat obtenu a une opération WSDL nommée `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="b5f3d-163">Appels asynchrones côté client</span><span class="sxs-lookup"><span data-stu-id="b5f3d-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="b5f3d-164">Une application cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut utiliser un des modèles d'appel asynchrone décrits précédemment.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-164">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="b5f3d-165">Lors de l'utilisation du modèle basé sur des tâches, appelez simplement l'opération en utilisant le mot clé await comme indiqué dans l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="b5f3d-166">L’utilisation du modèle asynchrone basé sur des événements ne nécessite que l’ajout d’un gestionnaire d’événements pour recevoir une notification de la réponse, et l’événement résultant est déclenché automatiquement sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="b5f3d-167">Pour utiliser cette approche, spécifiez à la fois le **/async** et **/tcv:Version35** commande options avec les [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), comme dans les éléments suivants exemple.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="b5f3d-168">Au terme de cette opération, l'outil Svcutil.exe génère une classe cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] avec l'infrastructure d'événement qui permet à l'application appelante d'implémenter et d'affecter un gestionnaire d'événements de recevoir la réponse et prendre la mesure appropriée.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-168">When this is done, Svcutil.exe generates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="b5f3d-169">Pour obtenir un exemple complet, consultez [Comment : appeler les opérations de Service asynchrone](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="b5f3d-170">Cependant, le modèle asynchrone basé sur les événements n'est disponible que dans le [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5f3d-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="b5f3d-171">De plus, il n'est pas pris en charge dans le [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] lorsqu'un canal client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est créé à l'aide d'un <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b5f3d-172">Avec les objets de canal client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], vous devez utiliser des objets <xref:System.IAsyncResult?displayProperty=nameWithType> pour appeler vos opérations de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-172">With [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="b5f3d-173">Pour utiliser cette approche, vous devez spécifier le **/async** commande option avec la [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="b5f3d-174">Vous générez ainsi un contrat de service dans lequel chaque opération est modelée comme une méthode `<Begin>` et où la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> a la valeur `true` et une méthode correspondante `<End>`.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="b5f3d-175">Pour un exemple complet utilisant un <xref:System.ServiceModel.ChannelFactory%601>, consultez [Comment : appeler opérations de façon asynchrone en utilisant une fabrique de canaux](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="b5f3d-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="b5f3d-176">Dans l’un ou l’autre cas, les applications peuvent appeler une opération de façon asynchrone même si le service est implémenté de façon synchrone, de la même façon qu’une application peut utiliser le même modèle pour appeler une méthode synchrone locale de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="b5f3d-177">La méthode d'implémentation de l'opération n'a pas d'importance pour le client. Quand le message de réponse arrive, son contenu est distribué à la méthode <`End`> asynchrone du client et ce dernier récupère les informations.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="b5f3d-178">Modèles d'échange de messages unidirectionnels</span><span class="sxs-lookup"><span data-stu-id="b5f3d-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="b5f3d-179">Vous pouvez également créer un modèle d'échange de messages asynchrone dans lequel les opérations unidirectionnelles (les opérations pour lesquelles <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> a la valeur `true` n'ont aucune réponse corrélée) peuvent être envoyées dans chaque direction par le client ou le service, indépendamment du côté opposé.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="b5f3d-180">(Cette méthode utilise le modèle d'échange de messages duplex avec des messages unidirectionnels.) Ainsi, le contrat de service spécifie un échange de messages unidirectionnels que chaque côté peut mettre en œuvre comme des appels ou implémentations asynchrones, ou synchrones, selon le cas.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="b5f3d-181">En général, lorsque le contrat est un échange de messages unidirectionnels, les implémentations sont en grande partie asynchrones car, après l'envoi d'un message, l'application n'attend pas de réponse et peut continuer à effectuer d'autres tâches.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="b5f3d-182">Contrats de message et clients asynchrones basés sur les événements</span><span class="sxs-lookup"><span data-stu-id="b5f3d-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="b5f3d-183">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="b5f3d-184">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="b5f3d-185">Si vous souhaitez recevoir l’objet de message en tant que le `Result` propriété et ont les valeurs retournées comme propriétés sur cet objet, utilisez le **/messageContract** option de commande.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="b5f3d-186">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="b5f3d-187">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="b5f3d-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f3d-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5f3d-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
