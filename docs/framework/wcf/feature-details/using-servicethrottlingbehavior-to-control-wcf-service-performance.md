---
title: "Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01f3815c095012d10fdfd56893125135c35f8009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="bc469-102">Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF</span><span class="sxs-lookup"><span data-stu-id="bc469-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="bc469-103">La classe <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> expose les propriétés que vous pouvez utiliser pour limiter le nombre d'instances ou de sessions créées au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="bc469-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="bc469-104">À l'aide de ce comportement, vous pouvez ajuster avec précision les performances de votre application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc469-104">Using this behavior, you can fine-tune the performance of your [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="bc469-105">Contrôle des instances de service et des appels simultanés</span><span class="sxs-lookup"><span data-stu-id="bc469-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="bc469-106">Utilisez la propriété <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> pour spécifier le nombre maximal des messages en cours de traitement actif dans une classe <xref:System.ServiceModel.ServiceHost>, et la propriété <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> pour spécifier le nombre maximal d'objets <xref:System.ServiceModel.InstanceContext> dans le service.</span><span class="sxs-lookup"><span data-stu-id="bc469-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="bc469-107">Car généralement à déterminer les paramètres de ces propriétés a lieu après l’exécution de l’application par rapport à l’expérience réelle charge, les paramètres pour le <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> propriétés est généralement spécifié dans un fichier de configuration d’application à l’aide du [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) élément.</span><span class="sxs-lookup"><span data-stu-id="bc469-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="bc469-108">L'exemple de code suivant illustre l'utilisation de la classe <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> à partir d'un fichier de configuration de l'application qui affecte aux propriétés <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> et <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> la valeur 1 en guise d'exemple simple.</span><span class="sxs-lookup"><span data-stu-id="bc469-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="bc469-109">L'expérience détermine les paramètres optimaux pour toute application particulière.</span><span class="sxs-lookup"><span data-stu-id="bc469-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="bc469-110">Le comportement exact au moment de l'exécution dépend des valeurs des propriétés <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> et <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> qui contrôlent le nombre de messages pouvant s'exécuter simultanément dans une opération et les durées de vie du service <xref:System.ServiceModel.InstanceContext> en fonction des sessions de canal entrantes, respectivement.</span><span class="sxs-lookup"><span data-stu-id="bc469-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="bc469-111">Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> et <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc469-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc469-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc469-112">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
