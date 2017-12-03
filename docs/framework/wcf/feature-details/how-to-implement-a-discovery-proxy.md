---
title: "Procédure : implémenter un proxy de découverte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90713d1779566448547265d6487c113abdc84e00
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="fe77c-102">Procédure : implémenter un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="fe77c-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="fe77c-103">Cette rubrique explique comment implémenter un proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="fe77c-103">This topic explains how to implement a discovery proxy.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fe77c-104">la fonctionnalité de découverte dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], consultez [vue d’ensemble de la découverte WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe77c-104"> the discovery feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="fe77c-105">Un proxy de découverte peut être implémenté en créant une classe qui étend la classe abstraite <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="fe77c-106">Un certain nombre d'autres classes de prise en charge sont définies et utilisées dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="fe77c-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="fe77c-107">`OnResolveAsyncResult`, `OnFindAsyncResult` et `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="fe77c-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="fe77c-108">Ces classes implémentent l'interface <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fe77c-109"><xref:System.IAsyncResult> consultez [System.IAsyncResult interface](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="fe77c-109"> <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>
  
 <span data-ttu-id="fe77c-110">L'implémentation d'un proxy de découverte est divisée en trois parties principales dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="fe77c-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>  
  
-   <span data-ttu-id="fe77c-111">Définir une classe qui contient une banque de données et étend la classe abstraite <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>  
  
-   <span data-ttu-id="fe77c-112">Implémenter la classe d'assistance `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="fe77c-112">Implement the helper `AsyncResult` class.</span></span>  
  
-   <span data-ttu-id="fe77c-113">Héberger le proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="fe77c-113">Host the Discovery Proxy.</span></span>  
  
### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="fe77c-114">Pour créer un nouveau projet d'application console</span><span class="sxs-lookup"><span data-stu-id="fe77c-114">To create a new console application project</span></span>  
  
1.  <span data-ttu-id="fe77c-115">Démarrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe77c-115">Start [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="fe77c-116">Créez un projet d'application console.</span><span class="sxs-lookup"><span data-stu-id="fe77c-116">Create a new console application project.</span></span> <span data-ttu-id="fe77c-117">Nommez le projet `DiscoveryProxy` et la solution `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="fe77c-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>  
  
3.  <span data-ttu-id="fe77c-118">Ajoutez au projet les références suivantes.</span><span class="sxs-lookup"><span data-stu-id="fe77c-118">Add the following references to the project</span></span>  
  
    1.  <span data-ttu-id="fe77c-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="fe77c-119">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="fe77c-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="fe77c-120">System.Servicemodel.Discovery.dll</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="fe77c-121">Vérifiez que vous référencez la version 4.0 ou supérieure de ces assemblys.</span><span class="sxs-lookup"><span data-stu-id="fe77c-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>  
  
### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="fe77c-122">Pour implémenter la classe ProxyDiscoveryService</span><span class="sxs-lookup"><span data-stu-id="fe77c-122">To implement the ProxyDiscoveryService class</span></span>  
  
1.  <span data-ttu-id="fe77c-123">Ajoutez à votre projet un nouveau fichier de code et nommez-le DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="fe77c-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>  
  
2.  <span data-ttu-id="fe77c-124">Ajoutez les instructions `using` suivantes à DiscoveryProxy.cs.</span><span class="sxs-lookup"><span data-stu-id="fe77c-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using System.Xml;  
    ```  
  
3.  <span data-ttu-id="fe77c-125">Dérivez `DiscoveryProxyService` de <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="fe77c-126">Appliquez l'attribut `ServiceBehavior` à la classe, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fe77c-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>  
  
    ```  
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]  
    public class DiscoveryProxyService : DiscoveryProxy  
    {  
    }  
    ```  
  
4.  <span data-ttu-id="fe77c-127">Dans la classe `DiscoveryProxy`, définissez un dictionnaire qui contiendra les services inscrits.</span><span class="sxs-lookup"><span data-stu-id="fe77c-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>  
  
    ```  
    // Repository to store EndpointDiscoveryMetadata.   
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;  
    ```  
  
5.  <span data-ttu-id="fe77c-128">Définissez un constructeur qui initialise le dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="fe77c-128">Define a constructor that initializes the dictionary.</span></span>  
  
    ```  
    public DiscoveryProxyService()  
            {  
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();  
            }  
    ```  
  
### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="fe77c-129">Pour définir les méthodes utilisées pour mettre à jour le cache du proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="fe77c-129">To define the methods used to update the discovery proxy cache</span></span>  
  
1.  <span data-ttu-id="fe77c-130">Implémentez la méthode `AddOnlineservice` pour ajouter des services au cache.</span><span class="sxs-lookup"><span data-stu-id="fe77c-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="fe77c-131">Cette méthode est appelée à chaque fois que le proxy reçoit un message d'annonce.</span><span class="sxs-lookup"><span data-stu-id="fe77c-131">This is called every time the proxy receives an announcement message.</span></span>  
  
    ```  
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
            {  
                lock (this.onlineServices)  
                {  
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;                  
                }  
  
                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");  
            }  
    ```  
  
2.  <span data-ttu-id="fe77c-132">Implémentez la méthode `RemoveOnlineService` utilisée pour supprimer des services du cache.</span><span class="sxs-lookup"><span data-stu-id="fe77c-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>  
  
    ```  
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
            {  
                if (endpointDiscoveryMetadata != null)  
                {  
                    lock (this.onlineServices)  
                    {  
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);                      
                    }  
  
                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");  
                }      
            }  
    ```  
  
3.  <span data-ttu-id="fe77c-133">Implémentez les méthodes `MatchFromOnlineService` qui tentent de faire correspondre un service à un service du dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="fe77c-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>  
  
    ```  
    void MatchFromOnlineService(FindRequestContext findRequestContext)  
            {  
                lock (this.onlineServices)  
                {  
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                    {  
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))  
                        {  
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);  
                        }  
                    }  
                }  
            }  
    ```  
  
    ```  
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)  
            {  
                EndpointDiscoveryMetadata matchingEndpoint = null;  
                lock (this.onlineServices)  
                {  
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                    {  
                        if (criteria.Address == endpointDiscoveryMetadata.Address)  
                        {  
                            matchingEndpoint = endpointDiscoveryMetadata;  
                        }  
                    }  
                }  
                return matchingEndpoint;  
            }  
    ```  
  
4.  <span data-ttu-id="fe77c-134">Implémentez la méthode `PrintDiscoveryMetadata` qui fournit à l'utilisateur une sortie de texte de console sur ce que le proxy de découverte est en train d'effectuer.</span><span class="sxs-lookup"><span data-stu-id="fe77c-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>  
  
    ```  
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)  
            {  
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");  
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)  
                {  
                    Console.WriteLine("** " + contractName.ToString());  
                    break;  
                }  
                Console.WriteLine("**** Operation Completed");  
            }  
    ```  
  
5.  <span data-ttu-id="fe77c-135">Ajoutez les classes AsyncResult suivantes à DiscoveryProxyService.</span><span class="sxs-lookup"><span data-stu-id="fe77c-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="fe77c-136">Ces classes permettent de faire la distinction entre les différents résultats des opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="fe77c-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>  
  
    ```  
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult  
            {  
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);  
                }  
            }  
  
            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult  
            {  
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);  
                }  
            }  
  
            sealed class OnFindAsyncResult : AsyncResult  
            {  
                public OnFindAsyncResult(AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.Complete(true);  
                }  
  
                public static void End(IAsyncResult result)  
                {  
                    AsyncResult.End<OnFindAsyncResult>(result);  
                }  
            }  
  
            sealed class OnResolveAsyncResult : AsyncResult  
            {  
                EndpointDiscoveryMetadata matchingEndpoint;  
  
                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)  
                    : base(callback, state)  
                {  
                    this.matchingEndpoint = matchingEndpoint;  
                    this.Complete(true);  
                }  
  
                public static EndpointDiscoveryMetadata End(IAsyncResult result)  
                {  
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);  
                    return thisPtr.matchingEndpoint;  
                }  
            }  
    ```  
  
### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="fe77c-137">Pour définir les méthodes qui implémentent les fonctionnalités du proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="fe77c-137">To define the methods that implement the discovery proxy functionality</span></span>  
  
1.  <span data-ttu-id="fe77c-138">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-139">Cette méthode est appelée lorsque le proxy de découverte reçoit un message d'annonce en ligne.</span><span class="sxs-lookup"><span data-stu-id="fe77c-139">This method is called when the discovery proxy receives an online announcement message.</span></span>  
  
    ```  
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy  
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
            {          
                this.AddOnlineService(endpointDiscoveryMetadata);  
                return new OnOnlineAnnouncementAsyncResult(callback, state);  
            }  
    ```  
  
2.  <span data-ttu-id="fe77c-140">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-141">Cette méthode est appelée lorsque le proxy de découverte finit un traitement de message d'annonce.</span><span class="sxs-lookup"><span data-stu-id="fe77c-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>  
  
    ```  
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)  
            {  
                OnOnlineAnnouncementAsyncResult.End(result);  
            }  
    ```  
  
3.  <span data-ttu-id="fe77c-142">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-143">Cette méthode est appelée lorsque le proxy de découverte reçoit un message d'annonce hors connexion.</span><span class="sxs-lookup"><span data-stu-id="fe77c-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>  
  
    ```  
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy  
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
            {  
                this.RemoveOnlineService(endpointDiscoveryMetadata);  
                return new OnOfflineAnnouncementAsyncResult(callback, state);  
            }  
    ```  
  
4.  <span data-ttu-id="fe77c-144">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-145">Cette méthode est appelée lorsque le proxy de découverte finit un traitement de message d'annonce hors connexion.</span><span class="sxs-lookup"><span data-stu-id="fe77c-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>  
  
    ```  
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)  
            {  
                OnOfflineAnnouncementAsyncResult.End(result);  
            }  
    ```  
  
5.  <span data-ttu-id="fe77c-146">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-147">Cette méthode est appelée lorsque le proxy de découverte reçoit une demande de recherche.</span><span class="sxs-lookup"><span data-stu-id="fe77c-147">This method is called when the discovery proxy receives a find request.</span></span>  
  
    ```  
    // OnBeginFind method is called when a Probe request message is received by the Proxy  
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)  
            {  
                this.MatchFromOnlineService(findRequestContext);  
                return new OnFindAsyncResult(callback, state);  
            }  
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)  
    {  
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);  
        return new OnFindAsyncResult(  
                    matchingEndpoints,  
                    callback,  
                    state);  
    }  
    ```  
  
6.  <span data-ttu-id="fe77c-148">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-149">Cette méthode est appelée lorsque le proxy de découverte finit un traitement de demande de recherche.</span><span class="sxs-lookup"><span data-stu-id="fe77c-149">This method is called when the discovery proxy finishes processing a find request.</span></span>  
  
    ```  
    protected override void OnEndFind(IAsyncResult result)  
            {  
                OnFindAsyncResult.End(result);  
            }  
    ```  
  
7.  <span data-ttu-id="fe77c-150">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-151">Cette méthode est appelée lorsque le proxy de découverte reçoit un message de résolution.</span><span class="sxs-lookup"><span data-stu-id="fe77c-151">This method is called when the discovery proxy receives a resolve message.</span></span>  
  
    ```  
    // OnBeginFind method is called when a Resolve request message is received by the Proxy  
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)  
            {  
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);  
            }  
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)  
    {  
        return new OnResolveAsyncResult(  
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),  
            callback,  
            state);  
    }  
    ```  
  
8.  <span data-ttu-id="fe77c-152">Remplacez la méthode <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe77c-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe77c-153">Cette méthode est appelée lorsque le proxy de découverte finit un traitement de message de résolution.</span><span class="sxs-lookup"><span data-stu-id="fe77c-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>  
  
    ```  
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)  
    {  
        return OnResolveAsyncResult.End(result);  
    }  
    ```  
  
 <span data-ttu-id="fe77c-154">Les méthodes OnBegin..</span><span class="sxs-lookup"><span data-stu-id="fe77c-154">The OnBegin..</span></span> <span data-ttu-id="fe77c-155">/ OnEnd..</span><span class="sxs-lookup"><span data-stu-id="fe77c-155">/ OnEnd..</span></span> <span data-ttu-id="fe77c-156">les méthodes fournissent la logique pour les opérations de découverte ultérieures.</span><span class="sxs-lookup"><span data-stu-id="fe77c-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="fe77c-157">Par exemple, les méthodes <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> et <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> implémentent la logique de recherche pour le proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="fe77c-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="fe77c-158">Lorsque le proxy de découverte reçoit un message Probe, ces méthodes sont exécutées pour renvoyer une réponse au client.</span><span class="sxs-lookup"><span data-stu-id="fe77c-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="fe77c-159">Vous pouvez modifier la logique de recherche à votre gré, par exemple, vous pouvez incorporer dans le cadre de votre opération de recherche une étendue personnalisée de correspondance par algorithmes ou une analyse des métadonnées XML spécifiques à une application.</span><span class="sxs-lookup"><span data-stu-id="fe77c-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>  
  
### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="fe77c-160">Pour implémenter la classe AsyncResult</span><span class="sxs-lookup"><span data-stu-id="fe77c-160">To implement the AsyncResult class</span></span>  
  
1.  <span data-ttu-id="fe77c-161">Définissez la classe de base abstraite AsyncResult qui sera utilisée pour dériver les diverses classes de résultats asynchrones.</span><span class="sxs-lookup"><span data-stu-id="fe77c-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>  
  
2.  <span data-ttu-id="fe77c-162">Créez un nouveau fichier de code nommé AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="fe77c-162">Create a new code file called AsyncResult.cs.</span></span>  
  
3.  <span data-ttu-id="fe77c-163">Ajoutez les instructions `using` suivantes à AsyncResult.cs.</span><span class="sxs-lookup"><span data-stu-id="fe77c-163">Add the following `using` statements to AsyncResult.cs.</span></span>  
  
    ```  
    using System;  
    using System.Threading;  
    ```  
  
4.  <span data-ttu-id="fe77c-164">Ajoutez la classe AsyncResult suivante.</span><span class="sxs-lookup"><span data-stu-id="fe77c-164">Add the following AsyncResult class.</span></span>  
  
    ```  
    abstract class AsyncResult : IAsyncResult  
        {  
            AsyncCallback callback;  
            bool completedSynchronously;  
            bool endCalled;  
            Exception exception;  
            bool isCompleted;  
            ManualResetEvent manualResetEvent;  
            object state;  
            object thisLock;  
  
            protected AsyncResult(AsyncCallback callback, object state)  
            {  
                this.callback = callback;  
                this.state = state;  
                this.thisLock = new object();  
            }  
  
            public object AsyncState  
            {  
                get  
                {  
                    return state;  
                }  
            }  
  
            public WaitHandle AsyncWaitHandle  
            {  
                get  
                {  
                    if (manualResetEvent != null)  
                    {  
                        return manualResetEvent;  
                    }  
                    lock (ThisLock)  
                    {  
                        if (manualResetEvent == null)  
                        {  
                            manualResetEvent = new ManualResetEvent(isCompleted);  
                        }  
                    }  
                    return manualResetEvent;  
                }  
            }  
  
            public bool CompletedSynchronously  
            {  
                get  
                {  
                    return completedSynchronously;  
                }  
            }  
  
            public bool IsCompleted  
            {  
                get  
                {  
                    return isCompleted;  
                }  
            }  
  
            object ThisLock  
            {  
                get  
                {  
                    return this.thisLock;  
                }  
            }  
  
            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)  
                where TAsyncResult : AsyncResult  
            {  
                if (result == null)  
                {  
                    throw new ArgumentNullException("result");  
                }  
  
                TAsyncResult asyncResult = result as TAsyncResult;  
  
                if (asyncResult == null)  
                {  
                    throw new ArgumentException("Invalid async result.", "result");  
                }  
  
                if (asyncResult.endCalled)  
                {  
                    throw new InvalidOperationException("Async object already ended.");  
                }  
  
                asyncResult.endCalled = true;  
  
                if (!asyncResult.isCompleted)  
                {  
                    asyncResult.AsyncWaitHandle.WaitOne();  
                }  
  
                if (asyncResult.manualResetEvent != null)  
                {  
                    asyncResult.manualResetEvent.Close();  
                }  
  
                if (asyncResult.exception != null)  
                {  
                    throw asyncResult.exception;  
                }  
  
                return asyncResult;  
            }  
  
            protected void Complete(bool completedSynchronously)  
            {  
                if (isCompleted)  
                {  
                    throw new InvalidOperationException("This async result is already completed.");  
                }  
  
                this.completedSynchronously = completedSynchronously;  
  
                if (completedSynchronously)  
                {  
                    this.isCompleted = true;  
                }  
                else  
                {  
                    lock (ThisLock)  
                    {  
                        this.isCompleted = true;  
                        if (this.manualResetEvent != null)  
                        {  
                            this.manualResetEvent.Set();  
                        }  
                    }  
                }  
  
                if (callback != null)  
                {  
                    callback(this);  
                }  
            }  
  
            protected void Complete(bool completedSynchronously, Exception exception)  
            {  
                this.exception = exception;  
                Complete(completedSynchronously);  
            }  
        }  
    ```  
  
### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="fe77c-165">Pour héberger le DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="fe77c-165">To host the DiscoveryProxy</span></span>  
  
1.  <span data-ttu-id="fe77c-166">Ouvrez le fichier Program.cs dans le projet DiscoveryProxyExample.</span><span class="sxs-lookup"><span data-stu-id="fe77c-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>  
  
2.  <span data-ttu-id="fe77c-167">Ajoutez les instructions `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="fe77c-167">Add the following `using` statements.</span></span>  
  
    ```  
    using System;  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    ```  
  
3.  <span data-ttu-id="fe77c-168">Ajoutez le code suivant dans la méthode `Main()`.</span><span class="sxs-lookup"><span data-stu-id="fe77c-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="fe77c-169">Ce code crée une instance de la classe `DiscoveryProxy`.</span><span class="sxs-lookup"><span data-stu-id="fe77c-169">This creates an instance of the `DiscoveryProxy` class.</span></span>  
  
    ```  
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
                // Host the DiscoveryProxy service  
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());  
    ```  
  
4.  <span data-ttu-id="fe77c-170">Ensuite, ajoutez le code suivant afin d'ajouter un point de terminaison de découverte et un point de terminaison d'annonce.</span><span class="sxs-lookup"><span data-stu-id="fe77c-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>  
  
    ```  
    try  
              {                  
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages  
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
                  discoveryEndpoint.IsSystemEndpoint = false;  
  
                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages  
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));                  
  
                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);  
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);  
  
                  proxyServiceHost.Open();  
  
                  Console.WriteLine("Proxy Service started.");  
                  Console.WriteLine();  
                  Console.WriteLine("Press <ENTER> to terminate the service.");  
                  Console.WriteLine();  
                  Console.ReadLine();  
  
                  proxyServiceHost.Close();  
              }  
              catch (CommunicationException e)  
              {  
                  Console.WriteLine(e.Message);  
              }  
              catch (TimeoutException e)  
              {  
                  Console.WriteLine(e.Message);  
              }     
  
              if (proxyServiceHost.State != CommunicationState.Closed)  
              {  
                  Console.WriteLine("Aborting the service...");  
                  proxyServiceHost.Abort();  
              }  
    ```  
  
 <span data-ttu-id="fe77c-171">Vous avez terminé l'implémentation du proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="fe77c-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="fe77c-172">Continuer à [Comment : implémenter un Service détectable qui s’enregistre avec le Proxy de découverte](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="fe77c-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe77c-173">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe77c-173">Example</span></span>  
 <span data-ttu-id="fe77c-174">Les éléments suivants représentent l'intégralité du code utilisé dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fe77c-174">This is the full listing of the code used in this topic.</span></span>  
  
```  
// DiscoveryProxy.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using System.Xml;  
  
namespace Microsoft.Samples.Discovery  
{  
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]  
    public class DiscoveryProxyService : DiscoveryProxy  
    {  
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.  
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;  
  
        public DiscoveryProxyService()  
        {  
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();  
        }  
  
        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy  
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
        {          
            this.AddOnlineService(endpointDiscoveryMetadata);  
            return new OnOnlineAnnouncementAsyncResult(callback, state);  
        }  
  
        protected override void OnEndOnlineAnnouncement(IAsyncResult result)  
        {  
            OnOnlineAnnouncementAsyncResult.End(result);  
        }  
  
        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy  
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)  
        {  
            this.RemoveOnlineService(endpointDiscoveryMetadata);  
            return new OnOfflineAnnouncementAsyncResult(callback, state);  
        }  
  
        protected override void OnEndOfflineAnnouncement(IAsyncResult result)  
        {  
            OnOfflineAnnouncementAsyncResult.End(result);  
        }  
  
        // OnBeginFind method is called when a Probe request message is received by the Proxy  
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)  
        {  
            this.MatchFromOnlineService(findRequestContext);  
            return new OnFindAsyncResult(callback, state);  
        }  
  
        protected override void OnEndFind(IAsyncResult result)  
        {  
            OnFindAsyncResult.End(result);  
        }  
  
        // OnBeginFind method is called when a Resolve request message is received by the Proxy  
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)  
        {  
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);  
        }  
  
        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)  
        {  
            return OnResolveAsyncResult.End(result);  
        }  
  
        // The following are helper methods required by the Proxy implementation  
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
        {  
            lock (this.onlineServices)  
            {  
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;                  
            }  
  
            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");  
        }  
  
        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)  
        {  
            if (endpointDiscoveryMetadata != null)  
            {  
                lock (this.onlineServices)  
                {  
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);                      
                }  
  
                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");  
            }      
        }  
  
        void MatchFromOnlineService(FindRequestContext findRequestContext)  
        {  
            lock (this.onlineServices)  
            {  
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                {  
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))  
                    {  
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);  
                    }  
                }  
            }  
        }  
  
        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)  
        {  
            EndpointDiscoveryMetadata matchingEndpoint = null;  
            lock (this.onlineServices)  
            {  
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)  
                {  
                    if (criteria.Address == endpointDiscoveryMetadata.Address)  
                    {  
                        matchingEndpoint = endpointDiscoveryMetadata;  
                    }  
                }  
            }  
            return matchingEndpoint;  
        }  
  
        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)  
        {  
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");  
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)  
            {  
                Console.WriteLine("** " + contractName.ToString());  
                break;  
            }  
            Console.WriteLine("**** Operation Completed");  
        }  
  
        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult  
        {  
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);  
            }  
        }  
  
        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult  
        {  
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);  
            }  
        }  
  
        sealed class OnFindAsyncResult : AsyncResult  
        {  
            public OnFindAsyncResult(AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.Complete(true);  
            }  
  
            public static void End(IAsyncResult result)  
            {  
                AsyncResult.End<OnFindAsyncResult>(result);  
            }  
        }  
  
        sealed class OnResolveAsyncResult : AsyncResult  
        {  
            EndpointDiscoveryMetadata matchingEndpoint;  
  
            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)  
                : base(callback, state)  
            {  
                this.matchingEndpoint = matchingEndpoint;  
                this.Complete(true);  
            }  
  
            public static EndpointDiscoveryMetadata End(IAsyncResult result)  
            {  
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);  
                return thisPtr.matchingEndpoint;  
            }  
        }  
    }  
}  
```  
  
```  
// AsyncResult.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Threading;  
  
namespace Microsoft.Samples.Discovery  
{  
    abstract class AsyncResult : IAsyncResult  
    {  
        AsyncCallback callback;  
        bool completedSynchronously;  
        bool endCalled;  
        Exception exception;  
        bool isCompleted;  
        ManualResetEvent manualResetEvent;  
        object state;  
        object thisLock;  
  
        protected AsyncResult(AsyncCallback callback, object state)  
        {  
            this.callback = callback;  
            this.state = state;  
            this.thisLock = new object();  
        }  
  
        public object AsyncState  
        {  
            get  
            {  
                return state;  
            }  
        }  
  
        public WaitHandle AsyncWaitHandle  
        {  
            get  
            {  
                if (manualResetEvent != null)  
                {  
                    return manualResetEvent;  
                }  
                lock (ThisLock)  
                {  
                    if (manualResetEvent == null)  
                    {  
                        manualResetEvent = new ManualResetEvent(isCompleted);  
                    }  
                }  
                return manualResetEvent;  
            }  
        }  
  
        public bool CompletedSynchronously  
        {  
            get  
            {  
                return completedSynchronously;  
            }  
        }  
  
        public bool IsCompleted  
        {  
            get  
            {  
                return isCompleted;  
            }  
        }  
  
        object ThisLock  
        {  
            get  
            {  
                return this.thisLock;  
            }  
        }  
  
        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)  
            where TAsyncResult : AsyncResult  
        {  
            if (result == null)  
            {  
                throw new ArgumentNullException("result");  
            }  
  
            TAsyncResult asyncResult = result as TAsyncResult;  
  
            if (asyncResult == null)  
            {  
                throw new ArgumentException("Invalid async result.", "result");  
            }  
  
            if (asyncResult.endCalled)  
            {  
                throw new InvalidOperationException("Async object already ended.");  
            }  
  
            asyncResult.endCalled = true;  
  
            if (!asyncResult.isCompleted)  
            {  
                asyncResult.AsyncWaitHandle.WaitOne();  
            }  
  
            if (asyncResult.manualResetEvent != null)  
            {  
                asyncResult.manualResetEvent.Close();  
            }  
  
            if (asyncResult.exception != null)  
            {  
                throw asyncResult.exception;  
            }  
  
            return asyncResult;  
        }  
  
        protected void Complete(bool completedSynchronously)  
        {  
            if (isCompleted)  
            {  
                throw new InvalidOperationException("This async result is already completed.");  
            }  
  
            this.completedSynchronously = completedSynchronously;  
  
            if (completedSynchronously)  
            {  
                this.isCompleted = true;  
            }  
            else  
            {  
                lock (ThisLock)  
                {  
                    this.isCompleted = true;  
                    if (this.manualResetEvent != null)  
                    {  
                        this.manualResetEvent.Set();  
                    }  
                }  
            }  
  
            if (callback != null)  
            {  
                callback(this);  
            }  
        }  
  
        protected void Complete(bool completedSynchronously, Exception exception)  
        {  
            this.exception = exception;  
            Complete(completedSynchronously);  
        }  
    }  
}  
```  
  
```  
// program.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Program  
    {  
        public static void Main()  
        {  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");  
  
            // Host the DiscoveryProxy service  
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());  
  
            try  
            {                  
                // Add DiscoveryEndpoint to receive Probe and Resolve messages  
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
                discoveryEndpoint.IsSystemEndpoint = false;  
  
                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages  
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));                  
  
                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);  
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);  
  
                proxyServiceHost.Open();  
  
                Console.WriteLine("Proxy Service started.");  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to terminate the service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                proxyServiceHost.Close();  
            }  
            catch (CommunicationException e)  
            {  
                Console.WriteLine(e.Message);  
            }  
            catch (TimeoutException e)  
            {  
                Console.WriteLine(e.Message);  
            }     
  
            if (proxyServiceHost.State != CommunicationState.Closed)  
            {  
                Console.WriteLine("Aborting the service...");  
                proxyServiceHost.Abort();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe77c-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe77c-175">See Also</span></span>  
 [<span data-ttu-id="fe77c-176">Vue d’ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="fe77c-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="fe77c-177">Comment : implémenter un Service détectable qui s’enregistre avec le Proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="fe77c-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="fe77c-178">Comment : implémenter une Application cliente qui utilise le Proxy de découverte pour rechercher un Service</span><span class="sxs-lookup"><span data-stu-id="fe77c-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 [<span data-ttu-id="fe77c-179">Comment : tester le Proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="fe77c-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)
