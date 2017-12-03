---
title: "Activation dynamique du traçage analytique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4984cb7fd89b69f0006c5294c24184bd8d1f1d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamically-enabling-analytic-tracing"></a>Activation dynamique du traçage analytique
À l'aide des outils fournis par le système d'exploitation Windows, vous pouvez activer ou désactiver de manière dynamique le suivi d'événements Windows (ETW). Pour tous les services [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] , le traçage analytique peut être activé et désactivé de manière dynamique sans modifier le fichier Web.config de l'application ni redémarrer le service. Cela permet de ne pas perturber l'application qui émet les événements de suivi.  
  
 Les options de suivi[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] peuvent être configurées de manière similaire. Par exemple, vous pouvez modifier le niveau de gravité **Erreur** en **Informations** sans porter atteinte à l'application. Cela peut s'effectuer à l'aide des outils suivants :  
  
-   **Logman** : outil de ligne de commande pour configurer, contrôler et interroger les données de suivi. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Logman Create Trace](http://go.microsoft.com/fwlink/?LinkId=165426) et [Logman Update Trace](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Observateur d'événements** : outil d'administration graphique de Windows pour afficher les résultats du suivi. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Les Services WCF et suivi d’événements pour Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) et [Observateur d’événements](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** : outil d'administration graphique de Windows utilisant des compteurs pour analyser les compteurs de suivi et les effets du suivi sur les performances. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Créer un ensemble de collecteurs de données manuellement](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Mots clés  
 Lors de l'utilisation de la classe <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> , les messages de trace .NET Framework sont généralement filtrés en fonction du niveau de gravité (par exemple, Erreur, Avertissement et Informations). Le suivi ETW prend en charge le concept de niveau de gravité, mais introduit un nouveau mécanisme de filtre souple, utilisant des mots clés. Les mots clés sont des valeurs textuelles arbitraires qui permettent aux événements de suivi de fournir un contexte supplémentaire sur la signification de cet événement.  
  
 Pour le traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , chaque événement de trace possède deux types de mots clés. Tout d'abord, chaque événement possède un ou plusieurs mots clés de scénario. Ces mots clés indiquent les scénarios que cet événement est destiné à prendre en charge. Il y a trois mots clés de scénario, chacun conçu pour un objectif spécifique, comme indiqué dans le tableau suivant. Le filtrage à l'aide de mots clés peut être modifié de manière dynamique sans porter atteinte au service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] . Cela signifie que vous pouvez modifier de manière dynamique votre scénario de suivi actuel et la quantité d'informations de suivi que vous rassemblez. Par exemple, vous pouvez modifier `HealthMonitoring` en `Troubleshooting` et augmenter la granularité de l'événement de suivi.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|`HealthMonitoring`|Suivi très léger, minimal qui vous permet de surveiller l'activité de votre service.|  
|`EndToEndMonitoring`|Événements utilisés pour prendre en charge le suivi du flux des messages.|  
|`Troubleshooting`|Événements plus précis concernant les points d'extensibilité [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
 Le second groupe de mots clés définit quel composant du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] a émis l'événement.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|`UserEvents`|Événements émis par le code utilisateur et non par le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Événements émis par l'exécution [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] .|  
|`ServiceHost`|Événements émis par l'hôte de service.|  
|`WCFMessageLogging`|Événements de journalisation des messages[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] .|  
  
## <a name="see-also"></a>Voir aussi  
 [WCF Services and Event Tracing for Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
