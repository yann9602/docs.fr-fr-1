---
title: "Implémentation du modèle asynchrone basé sur des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b4df5e4df914d932c7413e9330e8663753456c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="8237f-102">Implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="8237f-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="8237f-103">Si vous écrivez une classe avec certaines opérations pouvant entraîner d’importants retards, pensez à lui affecter des fonctionnalités asynchrones en implémentant [Vue d’ensemble du modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="8237f-104">Le modèle asynchrone basé sur des événements fournit une méthode standardisée pour empaqueter une classe incluant des fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="8237f-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="8237f-105">Si implémenté avec des classes d’assistance telles que <xref:System.ComponentModel.AsyncOperationManager>, votre classe fonctionnera correctement sous tout modèle d’application, y compris [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], des applications Windows Forms et des applications Console.</span><span class="sxs-lookup"><span data-stu-id="8237f-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="8237f-106">Pour obtenir un exemple qui implémente le modèle asynchrone basé sur des événements, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="8237f-107">Pour les opérations asynchrones simples, vous trouverez peut-être la <xref:System.ComponentModel.BackgroundWorker> composant approprié.</span><span class="sxs-lookup"><span data-stu-id="8237f-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="8237f-108">Pour plus d’informations sur <xref:System.ComponentModel.BackgroundWorker>, consultez [Comment : exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="8237f-109">La liste suivante décrit les fonctionnalités du modèle asynchrone basé sur des événements décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8237f-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="8237f-110">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="8237f-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="8237f-111">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="8237f-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="8237f-112">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="8237f-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="8237f-113">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="8237f-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="8237f-114">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="8237f-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="8237f-115">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="8237f-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="8237f-116">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="8237f-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="8237f-117">Possibilités d’implémentation du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="8237f-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="8237f-118">Envisagez d’implémenter le modèle asynchrone basé sur des événements quand :</span><span class="sxs-lookup"><span data-stu-id="8237f-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="8237f-119">Les clients de votre classe n’est pas nécessitent <xref:System.Threading.WaitHandle> et <xref:System.IAsyncResult> objets disponibles pour les opérations asynchrones, ce qui signifie que l’interrogation et <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> devrez être développés par le client.</span><span class="sxs-lookup"><span data-stu-id="8237f-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="8237f-120">Vous souhaitez que les opérations asynchrones soient gérées par le client avec le modèle d’événement/de délégué familier.</span><span class="sxs-lookup"><span data-stu-id="8237f-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="8237f-121">Une opération est un candidat pour une implémentation asynchrone, mais vous devez prendre en compte celles impliquant des latences importantes.</span><span class="sxs-lookup"><span data-stu-id="8237f-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="8237f-122">Les opérations tout particulièrement appropriées sont celles dans lesquelles les clients appellent une méthode et sont informés de l’achèvement, sans autre intervention nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8237f-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="8237f-123">Sont également appropriées des opérations exécutées en continu et qui informent régulièrement les clients de la progression, des résultats incrémentiels ou des changements d’état.</span><span class="sxs-lookup"><span data-stu-id="8237f-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="8237f-124">Pour plus d’informations sur le choix du moment auquel prendre en charge le modèle asynchrone basé sur des événements, consultez [Choix du moment auquel implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="8237f-125">Attribution des noms de méthodes asynchrones</span><span class="sxs-lookup"><span data-stu-id="8237f-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="8237f-126">Pour chaque méthode synchrone *MethodName* pour laquelle vous souhaitez fournir un équivalent asynchrone :</span><span class="sxs-lookup"><span data-stu-id="8237f-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="8237f-127">Définissez une méthode *MethodName*`Async` qui :</span><span class="sxs-lookup"><span data-stu-id="8237f-127">Define a *MethodName*`Async` method that:</span></span>  
  
-   <span data-ttu-id="8237f-128">Retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="8237f-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="8237f-129">Accepte les mêmes paramètres que la méthode *MethodName*.</span><span class="sxs-lookup"><span data-stu-id="8237f-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="8237f-130">Accepte plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="8237f-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="8237f-131">Définissez éventuellement une surcharge *MethodName*`Async`, identique à *MethodName*`Async`, mais avec un paramètre objet supplémentaire appelé `userState`.</span><span class="sxs-lookup"><span data-stu-id="8237f-131">Optionally define a *MethodName*`Async` overload, identical to *MethodName*`Async`, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="8237f-132">Procédez ainsi si vous êtes prêt à gérer plusieurs appels simultanés de votre méthode, auquel cas la valeur `userState` est remise à tous les gestionnaires d’événements pour distinguer les appels de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8237f-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="8237f-133">Vous pouvez également choisir d’en faire un emplacement de stockage de l’état utilisateur pour une récupération ultérieure.</span><span class="sxs-lookup"><span data-stu-id="8237f-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="8237f-134">Pour chaque signature de méthode distincte pour *MethodName*`Async` :</span><span class="sxs-lookup"><span data-stu-id="8237f-134">For each separate *MethodName*`Async` method signature:</span></span>  
  
1.  <span data-ttu-id="8237f-135">Définissez l’événement suivant dans la même classe que la méthode :</span><span class="sxs-lookup"><span data-stu-id="8237f-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="8237f-136">Définissez le délégué suivant et <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="8237f-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="8237f-137">Ils seront probablement définis en dehors de la classe, mais dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8237f-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   <span data-ttu-id="8237f-138">Assurez-vous que la classe *MethodName*`CompletedEventArgs` expose ses membres en tant que propriétés en lecture seule et non en tant que champs, car les champs empêchent la liaison des données.</span><span class="sxs-lookup"><span data-stu-id="8237f-138">Ensure that the *MethodName*`CompletedEventArgs` class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="8237f-139">Ne définissez aucune <xref:System.ComponentModel.AsyncCompletedEventArgs>-dérivées des classes pour les méthodes qui ne produisent pas de résultats.</span><span class="sxs-lookup"><span data-stu-id="8237f-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="8237f-140">Utilisez simplement une instance de <xref:System.ComponentModel.AsyncCompletedEventArgs> lui-même.</span><span class="sxs-lookup"><span data-stu-id="8237f-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8237f-141">Il est parfaitement acceptable, lorsque cela est possible et approprié, de réutiliser le délégué et <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span><span class="sxs-lookup"><span data-stu-id="8237f-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="8237f-142">Dans ce cas, l’attribution de noms pas sera aussi cohérente avec le nom de la méthode, depuis un délégué donné et <xref:System.ComponentModel.AsyncCompletedEventArgs> ne seront pas liés à une méthode unique.</span><span class="sxs-lookup"><span data-stu-id="8237f-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="8237f-143">Annulation facultative de prise en charge</span><span class="sxs-lookup"><span data-stu-id="8237f-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="8237f-144">Si votre classe prend en charge l’annulation des opérations asynchrones, l’annulation doit être présentée au client comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8237f-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="8237f-145">Notez que deux décisions importantes doivent être prises avant de définir l’annulation de la prise en charge :</span><span class="sxs-lookup"><span data-stu-id="8237f-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="8237f-146">Votre classe, y compris ses ajouts futurs, comprend-elle une seule opération asynchrone prenant en charge l’annulation ?</span><span class="sxs-lookup"><span data-stu-id="8237f-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="8237f-147">Les opérations asynchrones prenant en charge l’annulation de prise en charge peuvent-elles prendre en charge plusieurs opérations en attente ?</span><span class="sxs-lookup"><span data-stu-id="8237f-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="8237f-148">Autrement dit, la méthode *MethodName*`Async` accepte-t-elle un paramètre `userState` et autorise-t-elle les appels multiples avant d’attendre que l’un d’eux se termine ?</span><span class="sxs-lookup"><span data-stu-id="8237f-148">That is, does the *MethodName*`Async` method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="8237f-149">Utilisez les réponses à ces deux questions dans le tableau ci-dessous pour déterminer la signature de votre méthode d’annulation.</span><span class="sxs-lookup"><span data-stu-id="8237f-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="8237f-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8237f-150">Visual Basic</span></span>  
  
||<span data-ttu-id="8237f-151">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="8237f-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="8237f-152">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="8237f-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="8237f-153">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="8237f-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="8237f-154">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="8237f-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="8237f-155">C#</span><span class="sxs-lookup"><span data-stu-id="8237f-155">C#</span></span>  
  
||<span data-ttu-id="8237f-156">Plusieurs opérations simultanées prises en charge</span><span class="sxs-lookup"><span data-stu-id="8237f-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="8237f-157">Une seule opération à la fois</span><span class="sxs-lookup"><span data-stu-id="8237f-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="8237f-158">Une opération Async dans la classe entière</span><span class="sxs-lookup"><span data-stu-id="8237f-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="8237f-159">Plusieurs opérations Async dans la classe</span><span class="sxs-lookup"><span data-stu-id="8237f-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="8237f-160">Si vous définissez la méthode `CancelAsync(object userState)`, les clients doivent être prudents lorsqu’ils choisissent leurs valeurs d’état afin qu’elles soient capables de distinguer toutes les méthodes asynchrones appelées sur l’objet, et pas seulement tous les appels d’une seule méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8237f-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="8237f-161">La décision de nommer la version de l’opération asynchrone simple *MethodName*`AsyncCancel` est motivée par la capacité à découvrir plus facilement la méthode dans un environnement de conception comme IntelliSense de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8237f-161">The decision to name the single-async-operation version *MethodName*`AsyncCancel` is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="8237f-162">Il regroupe les membres associés et les distingue des autres membres qui n’ont rien à voir avec les fonctionnalités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="8237f-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="8237f-163">Si vous pensez que d’autres opérations asynchrones peuvent être ajoutées dans les versions ultérieures, il est préférable de définir `CancelAsync`.</span><span class="sxs-lookup"><span data-stu-id="8237f-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="8237f-164">Ne définissez pas plusieurs méthodes du tableau ci-dessus dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="8237f-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="8237f-165">Ceci sera inutile ou risquera d’encombrer l’interface de classe d’un trop grand nombre de méthodes.</span><span class="sxs-lookup"><span data-stu-id="8237f-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="8237f-166">Ces méthodes retournent généralement immédiatement et l’opération peut ou non être réellement annulée.</span><span class="sxs-lookup"><span data-stu-id="8237f-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="8237f-167">Dans le gestionnaire d’événements de l’événement *MethodName*`Completed`, l’objet *MethodName*`CompletedEventArgs` contient un champ `Cancelled` que les clients peuvent utiliser pour déterminer si l’annulation a eu lieu.</span><span class="sxs-lookup"><span data-stu-id="8237f-167">In the event handler for the *MethodName*`Completed` event, the *MethodName*`CompletedEventArgs` object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="8237f-168">Respectez la sémantique d’annulation décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="8237f-169">Prise en charge facultative de la propriété IsBusy</span><span class="sxs-lookup"><span data-stu-id="8237f-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="8237f-170">Si votre classe ne prend pas en charge plusieurs appels simultanés, envisagez d’exposer une propriété `IsBusy`.</span><span class="sxs-lookup"><span data-stu-id="8237f-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="8237f-171">Cela permet aux développeurs de déterminer si une méthode *MethodName*`Async` s’exécute sans intercepter d’exception de la méthode *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="8237f-171">This allows developers to determine whether a *MethodName*`Async` method is running without catching an exception from the *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="8237f-172">Respectez la sémantique `IsBusy` décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="8237f-173">Prise en charge facultative du rapport de progression</span><span class="sxs-lookup"><span data-stu-id="8237f-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="8237f-174">Il est généralement souhaitable qu’une opération asynchrone indique sa progression pendant son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="8237f-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="8237f-175">Le modèle asynchrone basé sur des événements fournit des instructions pour le faire.</span><span class="sxs-lookup"><span data-stu-id="8237f-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="8237f-176">Définissez éventuellement un événement déclenché par l’opération asynchrone et appelé sur le thread approprié.</span><span class="sxs-lookup"><span data-stu-id="8237f-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="8237f-177">Le <xref:System.ComponentModel.ProgressChangedEventArgs> objet comporte un indicateur de progression de valeurs entières qui doit être comprise entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="8237f-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="8237f-178">Nommez cet événement de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="8237f-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="8237f-179">`ProgressChanged` si la classe comporte plusieurs opérations asynchrones (ou est censée se développer pour inclure plusieurs opérations asynchrones dans les versions ultérieures) ;</span><span class="sxs-lookup"><span data-stu-id="8237f-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="8237f-180">*MethodName* `ProgressChanged` si la classe comporte une seule opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8237f-180">*MethodName* `ProgressChanged` if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="8237f-181">Ce choix de désignation correspond à celui effectué pour la méthode d’annulation, comme décrit dans la section Annulation facultative de la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8237f-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="8237f-182">Cet événement doit utiliser la <xref:System.ComponentModel.ProgressChangedEventHandler> signature du délégué et la <xref:System.ComponentModel.ProgressChangedEventArgs> classe.</span><span class="sxs-lookup"><span data-stu-id="8237f-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="8237f-183">Vous pouvez également, si un indicateur de progression plus spécifique au domaine peut être fourni (par instance, les octets lus et nombre total d’octets pour une opération de téléchargement), vous devez définir une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="8237f-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="8237f-184">Notez qu’il existe un seul événement `ProgressChanged` ou *MethodName*`ProgressChanged` pour la classe, quel que soit le nombre de méthodes asynchrones qu’elle prend en charge.</span><span class="sxs-lookup"><span data-stu-id="8237f-184">Note that there is only one `ProgressChanged` or *MethodName*`ProgressChanged` event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="8237f-185">Les clients sont censés utiliser l’objet `userState` qui est passé aux méthodes *MethodName*`Async` pour distinguer les mises à jour de progression sur les opérations simultanées multiples.</span><span class="sxs-lookup"><span data-stu-id="8237f-185">Clients are expected to use the `userState` object that is passed to the *MethodName*`Async` methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="8237f-186">Dans certaines situations, plusieurs opérations prennent en charge la progression et chacune renvoie un indicateur de progression différent.</span><span class="sxs-lookup"><span data-stu-id="8237f-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="8237f-187">Dans ce cas, un seul événement `ProgressChanged` n’est pas approprié, et vous pouvez envisager la prise en charge de plusieurs événements `ProgressChanged`.</span><span class="sxs-lookup"><span data-stu-id="8237f-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="8237f-188">Utilisez dans ce cas un modèle de nom *MethodName*`ProgressChanged` pour chaque méthode *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="8237f-188">In this case use a naming pattern of *MethodName*`ProgressChanged` for each *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="8237f-189">Respectez la sémantique de rapport de progression décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="8237f-190">Prise en charge facultative du renvoi des résultats incrémentiels</span><span class="sxs-lookup"><span data-stu-id="8237f-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="8237f-191">Parfois, une opération asynchrone peut retourner des résultats incrémentiels avant la fin.</span><span class="sxs-lookup"><span data-stu-id="8237f-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="8237f-192">Un certain nombre d’options peuvent être utilisées pour prendre en charge ce scénario.</span><span class="sxs-lookup"><span data-stu-id="8237f-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="8237f-193">En voici quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="8237f-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="8237f-194">Classe à une opération</span><span class="sxs-lookup"><span data-stu-id="8237f-194">Single-operation Class</span></span>  
 <span data-ttu-id="8237f-195">Si votre classe ne prend en charge qu’une seule opération asynchrone et que celle-ci peut retourner des résultats incrémentiels :</span><span class="sxs-lookup"><span data-stu-id="8237f-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="8237f-196">Étendre la <xref:System.ComponentModel.ProgressChangedEventArgs> tapez pour intégrer les données de résultat incrémentiel et définissez un *MethodName* `ProgressChanged` événements avec ces données étendues.</span><span class="sxs-lookup"><span data-stu-id="8237f-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName*`ProgressChanged` event with this extended data.</span></span>  
  
-   <span data-ttu-id="8237f-197">Déclenchez cet événement *MethodName*`ProgressChanged` lorsqu’un résultat incrémentiel doit être signalé.</span><span class="sxs-lookup"><span data-stu-id="8237f-197">Raise this *MethodName*`ProgressChanged` event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="8237f-198">Cette solution s’applique tout particulièrement à une classe d’opération asynchrone simple, car le fait que le même événement retourne des résultats incrémentiels sur « toutes les opérations », comme c’est le cas pour l’événement *MethodName*`ProgressChanged`, ne pose aucun problème.</span><span class="sxs-lookup"><span data-stu-id="8237f-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName*`ProgressChanged` event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="8237f-199">Classe à plusieurs opérations avec des résultats incrémentiels homogènes</span><span class="sxs-lookup"><span data-stu-id="8237f-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="8237f-200">Dans ce cas, votre classe prend en charge plusieurs méthodes asynchrones, chacune capable de retourner des résultats incrémentiels, et ces résultats incrémentiels possèdent tous le même type de données.</span><span class="sxs-lookup"><span data-stu-id="8237f-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="8237f-201">Suivre le modèle décrit ci-dessus pour les classes de l’opération simple, comme le même <xref:System.EventArgs> structure fonctionne pour tous les résultats incrémentiels.</span><span class="sxs-lookup"><span data-stu-id="8237f-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="8237f-202">Définissez un événement `ProgressChanged` à la place d’un événement *MethodName*`ProgressChanged` étant donné qu’il s’applique à plusieurs méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="8237f-202">Define a `ProgressChanged` event instead of a *MethodName*`ProgressChanged` event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="8237f-203">Classe à plusieurs opérations avec des résultats incrémentiels hétérogènes</span><span class="sxs-lookup"><span data-stu-id="8237f-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="8237f-204">Si votre classe prend en charge plusieurs méthodes asynchrones, chacune retournant un type de données différent :</span><span class="sxs-lookup"><span data-stu-id="8237f-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="8237f-205">Séparez votre rapport de résultat incrémentiel de votre rapport de progression.</span><span class="sxs-lookup"><span data-stu-id="8237f-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="8237f-206">Définir un distinct *MethodName* `ProgressChanged` événement avec approprié <xref:System.EventArgs> pour chaque méthode asynchrone gérer les données de résultat incrémentiel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8237f-206">Define a separate *MethodName*`ProgressChanged` event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="8237f-207">Appelez ce gestionnaire d’événements sur le thread approprié comme décrit dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="8237f-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="8237f-208">Gestion des paramètres Out et Ref dans les méthodes</span><span class="sxs-lookup"><span data-stu-id="8237f-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="8237f-209">Bien que l’utilisation de `out` et `ref` soit en règle générale déconseillée dans le .NET Framework, voici les règles à suivre lorsqu’ils sont présents :</span><span class="sxs-lookup"><span data-stu-id="8237f-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="8237f-210">Soit une méthode synchrone *MethodName* :</span><span class="sxs-lookup"><span data-stu-id="8237f-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="8237f-211">Les paramètres `out` passés à *MethodName* ne doivent pas faire partie de *MethodName*`Async`.</span><span class="sxs-lookup"><span data-stu-id="8237f-211">`out` parameters to *MethodName* should not be part of *MethodName*`Async`.</span></span> <span data-ttu-id="8237f-212">Ils doivent plutôt faire partie de *MethodName*`CompletedEventArgs` avec le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="8237f-212">Instead, they should be part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="8237f-213">Les paramètres `ref` passés à *MethodName* doivent faire partie de *MethodName*`Async`, et faire partie de *MethodName*`CompletedEventArgs` avec le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).</span><span class="sxs-lookup"><span data-stu-id="8237f-213">`ref` parameters to *MethodName* should appear as part of *MethodName*`Async`, and as part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="8237f-214">Par exemple, soit :</span><span class="sxs-lookup"><span data-stu-id="8237f-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="8237f-215">Votre méthode asynchrone et sa <xref:System.ComponentModel.AsyncCompletedEventArgs> classe ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="8237f-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8237f-216">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8237f-216">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="8237f-217">Guide pratique pour implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="8237f-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="8237f-218">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="8237f-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="8237f-219">Comment : implémenter un formulaire qui utilise une opération d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="8237f-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="8237f-220">Choix du moment auquel implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="8237f-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="8237f-221">Programmation multithread avec le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="8237f-221">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="8237f-222">Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="8237f-222">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
