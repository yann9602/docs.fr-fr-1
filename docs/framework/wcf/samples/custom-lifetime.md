---
title: Custom Lifetime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26038aba792d8b5dd51d1b47156adcfe4882121
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-lifetime"></a><span data-ttu-id="4d3f0-102">Custom Lifetime</span><span class="sxs-lookup"><span data-stu-id="4d3f0-102">Custom Lifetime</span></span>
<span data-ttu-id="4d3f0-103">Cet exemple montre comment écrire une extension [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] afin de fournir des services de durée de vie personnalisés pour des instances de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] partagées.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-103">This sample demonstrates how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extension to provide custom lifetime services for shared [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d3f0-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="4d3f0-105">Instanciation partagée</span><span class="sxs-lookup"><span data-stu-id="4d3f0-105">Shared Instancing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4d3f0-106"> propose plusieurs modes d'instanciation pour vos instances de service.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-106"> offers several instancing modes for your service instances.</span></span> <span data-ttu-id="4d3f0-107">Le mode d'instanciation partagée présenté dans cette rubrique offre un moyen de partager une instance du service entre plusieurs canaux.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="4d3f0-108">Le client peut soit résoudre localement l'adresse du point de terminaison de l'instance, soit contacter une méthode de fabrique du service pour obtenir l'adresse du point de terminaison d'une instance en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="4d3f0-109">Une fois qu'il a l'adresse du point de terminaison, il peut créer un canal et démarrer la communication.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="4d3f0-110">L'extrait de code suivant montre comment une application cliente crée un canal vers une instance existante du service.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="4d3f0-111">Contrairement aux autres modes d'instanciation, l'instanciation partagée a une façon unique de libérer des instances de service.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="4d3f0-112">Lorsque tous les canaux sont fermés pour une instance, l'exécution [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] du service démarre un minuteur.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-112">When all the channels are closed for an instance, the service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime starts a timer.</span></span> <span data-ttu-id="4d3f0-113">Si personne n'établit de connexion avant l'expiration du délai d'attente, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] libère l'instance et réclame les ressources.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-113">If nobody makes a connection before the timeout expires, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] releases the instance and claims the resources.</span></span> <span data-ttu-id="4d3f0-114">Dans le cadre de la procédure de démontage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de toutes les implémentations d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> avant de libérer l'instance.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-114">As a part of the teardown procedure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="4d3f0-115">Si toutes retournent la valeur `true`, l'instance est libérée.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="4d3f0-116">Sinon, l'implémentation d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est chargée de notifier l'état inactif au `Dispatcher` à l'aide d'une méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="4d3f0-117">Par défaut, le délai d'inactivité d'<xref:System.ServiceModel.InstanceContext> est d'une minute.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="4d3f0-118">Cependant, cet exemple montre comment étendre ce délai à l'aide d'une extension personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="4d3f0-119">Extension de l'InstanceContext</span><span class="sxs-lookup"><span data-stu-id="4d3f0-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="4d3f0-120">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> est le lien entre l'instance du service et le `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-120">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="4d3f0-121"> vous permet d'étendre ce composant d'exécution en ajoutant un nouvel état ou comportement à l'aide de son modèle d'objet extensible.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-121"> allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="4d3f0-122">Le modèle d'objet extensible est utilisé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour étendre des classes d'exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d'état à un objet.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-122">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="4d3f0-123">Le modèle d'objet extensible contient trois interfaces : `IExtensibleObject<T>`, `IExtension<T>` et `IExtensionCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="4d3f0-124">L'interface `IExtensibleObject<T>` est implémentée par des objets pour autoriser des extensions qui personnalisent leurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="4d3f0-125">L'interface `IExtension<T>` est implémentée par des objets qui peuvent être des extensions de classes de type `T`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="4d3f0-126">Et enfin, l'interface `IExtensionCollection<T>` est une collection d'`IExtensions` qui permet de récupérer les `IExtensions` par leur type.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="4d3f0-127">Par conséquent, pour étendre l'<xref:System.ServiceModel.InstanceContext>, vous devez implémenter l'interface `IExtension`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="4d3f0-128">Dans cet exemple de projet, la classe `CustomLeaseExtension` contient cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="4d3f0-129">L'interface `IExtension` possède deux méthodes : `Attach` et `Detach`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="4d3f0-130">Comme leur nom le laisse supposer, ces deux méthodes sont appelées lorsque le runtime attache l'extension à une instance de la classe <xref:System.ServiceModel.InstanceContext> et l'en détache.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="4d3f0-131">Dans cet exemple, la méthode `Attach` est utilisée pour effectuer le suivi de l'objet <xref:System.ServiceModel.InstanceContext> qui appartient à l'instance actuelle de l'extension.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="4d3f0-132">En outre, vous devez ajouter l'implémentation dont l'extension a besoin pour fournir la prise en charge de la durée de vie étendue.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="4d3f0-133">Par conséquent, l'interface `ICustomLease` est déclarée avec les méthodes voulues et est implémentée dans la classe `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="4d3f0-134">Lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> dans l'implémentation d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, cet appel est routé vers la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> de `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-134">When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="4d3f0-135">`CustomLeaseExtension` vérifie ensuite son état privé pour voir si <xref:System.ServiceModel.InstanceContext> est inactive.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="4d3f0-136">Si elle l'est, elle retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="4d3f0-137">Sinon, elle démarre un minuteur pour l'extension spécifiée de la durée de vie.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 <span data-ttu-id="4d3f0-138">Dans l'événement `Elapsed` du minuteur, la fonction de rappel du répartiteur (Dispatcher) est appelée pour démarrer un autre cycle de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="4d3f0-139">Il n'existe pas de moyen de renouveler le minuteur en cours d'exécution lorsqu'un nouveau message arrive pour l'instance qui passe à l'état inactif.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="4d3f0-140">L'exemple implémente <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> pour intercepter les appels à la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> et les router vers `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="4d3f0-141">L'implémentation d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> est contenue dans la classe `CustomLifetimeLease`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="4d3f0-142">La méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> est appelée lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est sur le point de libérer l'instance du service.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is about to release the service instance.</span></span> <span data-ttu-id="4d3f0-143">Toutefois, il n'existe qu'une instance d'une implémentation d'`ISharedSessionInstance` particulière dans la collection <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> du ServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="4d3f0-144">Cela signifie qu'il n'est pas possible de savoir quel <xref:System.ServiceModel.InstanceContext> est en cours de fermeture au moment où [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vérifie la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="4d3f0-145">Par conséquent, cet exemple utilise le verrouillage de threads pour sérialiser les requêtes adressées à la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d3f0-146">Le recours au verrouillage de threads n'est pas une approche recommandée, car la sérialisation peut considérablement affecter les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="4d3f0-147">Une variable membre privé est utilisée dans la classe `CustomLeaseExtension` pour effectuer le suivi de la valeur `IsIdle`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="4d3f0-148">À chaque récupération de la valeur d'<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>, le membre privé `IsIdle` est retourné et réinitialisé à `false`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="4d3f0-149">L'affectation de `false` à cette valeur est indispensable pour que le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="4d3f0-150">Si la propriété `ISharedSessionLifetime.IsIdle` retourne `false`, le répartiteur inscrit une fonction de rappel à l'aide de la méthode `NotifyIdle`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="4d3f0-151">Cette méthode reçoit une référence à l'<xref:System.ServiceModel.InstanceContext> libéré.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="4d3f0-152">Par conséquent, l'exemple de code peut interroger l'extension de type `ICustomLease` et vérifier la propriété `ICustomLease.IsIdle` dans l'état étendu.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 <span data-ttu-id="4d3f0-153">Avant que la propriété `ICustomLease.IsIdle` ne soit vérifiée, la propriété Callback doit être définie, condition essentielle pour que `CustomLeaseExtension` puisse indiquer au répartiteur le moment où elle devient inactive.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="4d3f0-154">Si `ICustomLease.IsIdle` retourne `true`, le membre privé `isIdle` reçoit simplement dans `CustomLifetimeLease` la valeur `true` et appelle la méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="4d3f0-155">Étant donné que le code maintient un verrou, d'autres threads ne peuvent pas modifier la valeur de ce membre privé.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="4d3f0-156">Et la prochaine fois que le répartiteur vérifie l'`ISharedSessionLifetime.IsIdle`, il retourne `true` et laisse le répartiteur libérer l'instance.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="4d3f0-157">Le travail préparatoire étant à présent terminé, l'extension personnalisée doit être raccordée au modèle de service.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="4d3f0-158">Pour raccorder l'implémentation de `CustomLeaseExtension` au <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit l'interface <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> qui permet d'effectuer le l'initialisation d'<xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="4d3f0-159">Dans l'exemple, la classe `CustomLeaseInitializer` implémente cette interface et ajoute une instance de `CustomLeaseExtension` à la collection <xref:System.ServiceModel.InstanceContext.Extensions%2A> à partir de la seule initialisation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="4d3f0-160">Cette méthode est appelée par le répartiteur en initialisant l'<xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="4d3f0-161">Enfin le `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` et <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implémentations sont raccordés jusqu'à le modèle de service à l’aide de la <xref:System.ServiceModel.Description.IServiceBehavior> implémentation.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="4d3f0-162">Cette implémentation est placée dans la classe `CustomLeaseTimeAttribute` et dérive également de la classe de base `Attribute` pour exposer ce comportement en tant qu'attribut.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="4d3f0-163">Dans la méthode `IServiceBehavior.ApplyBehavior`, les instances d'<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> et les implémentations d'`System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` sont ajoutées respectivement aux collections `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` et <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> du <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime>.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="4d3f0-164">Ce comportement peut être ajouté à une classe de l'exemple de service en l'annotant avec l'attribut `CustomLeaseTime`.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="4d3f0-165">Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4d3f0-166">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d3f0-167">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="4d3f0-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4d3f0-168">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d3f0-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4d3f0-169">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d3f0-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4d3f0-170">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d3f0-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d3f0-171">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d3f0-172">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4d3f0-173">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d3f0-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d3f0-174">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="4d3f0-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="4d3f0-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d3f0-175">See Also</span></span>
