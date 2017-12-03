---
title: Gestion des erreurs WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26dfea83400b5d601fabc5cfb52bc71a4d5e4f6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-error-handling"></a><span data-ttu-id="3f1c9-102">Gestion des erreurs WCF</span><span class="sxs-lookup"><span data-stu-id="3f1c9-102">WCF Error Handling</span></span>
<span data-ttu-id="3f1c9-103">Les erreurs rencontrées par une application WCF appartiennent à l'un de ces trois groupes :</span><span class="sxs-lookup"><span data-stu-id="3f1c9-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1.  <span data-ttu-id="3f1c9-104">Erreurs de communication</span><span class="sxs-lookup"><span data-stu-id="3f1c9-104">Communication Errors</span></span>  
  
2.  <span data-ttu-id="3f1c9-105">Erreurs de proxy/canal</span><span class="sxs-lookup"><span data-stu-id="3f1c9-105">Proxy/Channel Errors</span></span>  
  
3.  <span data-ttu-id="3f1c9-106">Erreurs d'application</span><span class="sxs-lookup"><span data-stu-id="3f1c9-106">Application Errors</span></span>  
  
 <span data-ttu-id="3f1c9-107">Les erreurs de communication se produisent lorsqu'un réseau n'est pas disponible, lorsqu'un client utilise une adresse incorrecte ou lorsque l'hôte de service n'écoute pas les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="3f1c9-108">Des erreurs de ce type sont retournées au client comme classes dérivées <xref:System.ServiceModel.CommunicationException> ou <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="3f1c9-109">Les erreurs de proxy/canal sont des erreurs qui se produisent dans le canal ou le proxy lui-même.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="3f1c9-110">Les erreurs de ce type incluent : une tentative d'utilisation d'un proxy ou d'un canal qui a été fermé, des contrats qui ne correspondent pas entre le client et le service ou des informations d'identification de client rejetées par le service.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="3f1c9-111">Cette catégorie inclut de nombreux types différents d'erreurs, qu'il serait trop long d'énumérer ici.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="3f1c9-112">Les erreurs de ce type sont retournées au client en l'état (les objets d'exception ne subissent aucune transformation).</span><span class="sxs-lookup"><span data-stu-id="3f1c9-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="3f1c9-113">Les erreurs d'application se produisent au cours de l'exécution d'une opération de service.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="3f1c9-114">Les erreurs se ce genre sont envoyées au client en tant que <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="3f1c9-115">Le traitement des erreurs dans WCF est effectué par un ou plusieurs des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3f1c9-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="3f1c9-116">Traitement direct de l'exception levée.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="3f1c9-117">Uniquement effectué pour les erreurs de communication et de proxy/canal.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="3f1c9-118">Utilisation des contrats d'erreur</span><span class="sxs-lookup"><span data-stu-id="3f1c9-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="3f1c9-119">Implémentation de l'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler></span><span class="sxs-lookup"><span data-stu-id="3f1c9-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="3f1c9-120">Gestion des événements <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="3f1c9-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="3f1c9-121">Contrats d'erreur</span><span class="sxs-lookup"><span data-stu-id="3f1c9-121">Fault Contracts</span></span>  
 <span data-ttu-id="3f1c9-122">Les contrats d'erreur vous permettent de définir les erreurs qui peuvent se produire au cours du fonctionnement du service de façon indépendante de la plate-forme.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="3f1c9-123">Par défaut, toutes les exceptions levées à partir d'une opération de service seront retournées au client en tant qu'objet <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="3f1c9-124">L'objet <xref:System.ServiceModel.FaultException> contiendra très peu d'informations.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="3f1c9-125">Vous pouvez contrôler les informations envoyées au client en définissant un contrat d'erreur et en retournant l'erreur en tant que <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3f1c9-126">[Spécification et gestion des erreurs dans les contrats et les Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="3f1c9-126"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="3f1c9-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="3f1c9-127">IErrorHandler</span></span>  
 <span data-ttu-id="3f1c9-128">L'interface <xref:System.ServiceModel.Dispatcher.IErrorHandler> vous permet de mieux contrôler la façon dont votre application WCF répond aux erreurs.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="3f1c9-129">Elle vous donne le contrôle total sur les messages d'erreur retournés au client et vous permet un traitement d'erreur personnalisé tel que la journalisation.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<span data-ttu-id="3f1c9-130"><xref:System.ServiceModel.Dispatcher.IErrorHandler> et [extension du contrôle à la gestion des erreurs et création de rapports](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="3f1c9-130"> <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="3f1c9-131">Événements ServiceHost</span><span class="sxs-lookup"><span data-stu-id="3f1c9-131">ServiceHost Events</span></span>  
 <span data-ttu-id="3f1c9-132">La classe <xref:System.ServiceModel.ServiceHost> héberge les services et définit plusieurs événements qui peuvent être nécessaires au traitement des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3f1c9-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="3f1c9-133">Exemple :</span><span class="sxs-lookup"><span data-stu-id="3f1c9-133">For example:</span></span>  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3f1c9-134"> <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="3f1c9-134"> <xref:System.ServiceModel.ServiceHost></span></span>
