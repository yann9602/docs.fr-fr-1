---
title: "Extension de ServiceHost et de la couche de modèle de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c73af3b9187fa5365d7ea99474ea182d5f5ae86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="f7a47-102">Extension de ServiceHost et de la couche de modèle de service</span><span class="sxs-lookup"><span data-stu-id="f7a47-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="f7a47-103">La couche du modèle de service est chargée de tirer des messages entrants des canaux sous-jacents, de les traduire dans des appels de méthode dans le code d’application et de renvoyer les résultats à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="f7a47-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="f7a47-104">Les extensions de modèle de service modifient ou implémentent le comportement et les fonctionnalités d’exécution ou de communication qui impliquent des fonctionnalités de répartiteur ou client, des comportements personnalisés, l’interception de messages et de paramètres, ainsi que d’autres fonctionnalités d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f7a47-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7a47-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f7a47-105">In This Section</span></span>  
 [<span data-ttu-id="f7a47-106">Extension de clients</span><span class="sxs-lookup"><span data-stu-id="f7a47-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="f7a47-107">Décrit les interfaces qui peuvent intercepter et modifier l’exécution du client, ainsi que les classes dans lesquelles vous pouvez insérer vos extensions personnalisées dans les applications clientes.</span><span class="sxs-lookup"><span data-stu-id="f7a47-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="f7a47-108">Par exemple, vous pouvez exécuter la journalisation des messages client personnalisée, exécuter une sérialisation personnalisée des messages, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f7a47-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="f7a47-109">Extension des répartiteurs</span><span class="sxs-lookup"><span data-stu-id="f7a47-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="f7a47-110">Décrit les interfaces qui peuvent intercepter et modifier l’exécution d’un service, ainsi que les classes dans lesquelles vous pouvez insérer vos extensions personnalisées dans les applications de service.</span><span class="sxs-lookup"><span data-stu-id="f7a47-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="f7a47-111">Par exemple, vous pouvez exécuter la journalisation personnalisée du service, une validation des messages côté service, une répartition personnalisée, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f7a47-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="f7a47-112">Objets extensibles</span><span class="sxs-lookup"><span data-stu-id="f7a47-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="f7a47-113">Décrit les cinq objets extensibles et le modèle <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="f7a47-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="f7a47-114">Le modèle d’objet extensible est utilisé pour étendre des classes d’exécution existantes à l’aide de nouvelles fonctionnalités ou ajouter un nouvel état à un objet.</span><span class="sxs-lookup"><span data-stu-id="f7a47-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="f7a47-115">Les extensions, attachées à l’un des objets extensibles, permettent aux comportements à des étapes différentes du traitement, d’accéder à l’état partagé et aux fonctionnalités attachés à un objet extensible commun qui leur est accessible.</span><span class="sxs-lookup"><span data-stu-id="f7a47-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="f7a47-116">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="f7a47-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="f7a47-117">Pour modifier des paramètres ou insérer des extensions dans l'exécution de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous devez utiliser les comportements.</span><span class="sxs-lookup"><span data-stu-id="f7a47-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="f7a47-118">WCF inclut des comportements implémentés par le système pour contrôler la limitation, l'instanciation et de nombreux autres aspects des services et des opérations.</span><span class="sxs-lookup"><span data-stu-id="f7a47-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="f7a47-119">Cette section décrit comment créer vos propres comportements personnalisés et les rendre disponibles pour les utiliser par programme et à l'aide de fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="f7a47-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="f7a47-120">Extension de l’hébergement à l’aide de ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="f7a47-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="f7a47-121">Décrit comment développer <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> et <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> et comment utiliser les classes <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> pour personnaliser l'environnement hôte.</span><span class="sxs-lookup"><span data-stu-id="f7a47-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f7a47-122">Référence</span><span class="sxs-lookup"><span data-stu-id="f7a47-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7a47-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="f7a47-123">Related Sections</span></span>
