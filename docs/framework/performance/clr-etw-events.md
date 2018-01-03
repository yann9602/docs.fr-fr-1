---
title: "Événements ETW du CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17701ee1ddbb1056c9b06b2467c4ce10b91271ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-events"></a>Événements ETW du CLR
Les rubriques de cette section décrivent le suivi d’événements pour les événements Windows (ETW). Chaque événement est associé à un mot clé et à un niveau, qui sont décrits dans la rubrique [Niveaux et mots clés ETW du CLR](../../../docs/framework/performance/clr-etw-keywords-and-levels.md). Le CLR a deux fournisseurs pour les événements :  
  
-   Le fournisseur de runtime, qui déclenche des événements en fonction des mots clés (catégories d’événements) activés. Le GUID du fournisseur de runtime du CLR est e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   Le fournisseur d’arrêt, qui est réservé à des usages spécifiques. Le GUID du fournisseur d’arrêt du CLR est a669021c-c450-4609-a035-5af59af4df18.  
  
 Pour plus d’informations sur les fournisseurs, consultez [Fournisseurs ETW du CLR](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Événements d’information du runtime](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Capture des informations sur l’exécution, notamment la référence, le numéro de version, le mode d’activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID (le cas échéant) et d’autres informations pertinentes.  
  
 [Événement d’exception Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Capture des informations sur les exceptions levées.  
  
 [Événements de conflit](../../../docs/framework/performance/contention-etw-events.md)  
 Capture des informations sur les conflits de verrous du moniteur ou de verrous natifs utilisés par le runtime.  
  
 [Événements de pool de threads](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Capture des informations sur les pools de threads de travail et les pools de threads d’E/S.  
  
 [Événements de chargeur](../../../docs/framework/performance/loader-etw-events.md)  
 Capture des informations sur le chargement et le déchargement des domaines d’application, des assemblys et des modules.  
  
 [Événements de méthode](../../../docs/framework/performance/method-etw-events.md)  
 Capture des informations sur les méthodes CLR pour la résolution des symboles.  
  
 [Événements de garbage collection](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Capture des informations relatives au garbage collection, pour vous aider lors du diagnostic et du débogage.  
  
 [Événements de traçage JIT](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Capture des informations sur l’incorporation (inlining) juste à temps (JIT) et les appels tail JIT.  
  
 [Événements d’interopérabilité](../../../docs/framework/performance/interop-etw-events.md)  
 Capture des informations sur la mise en cache et la génération du stub MSIL (Microsoft Intermediate Language).  
  
 [Événements ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Capture des informations de diagnostic détaillées sur l’état d’un domaine d’application.  
  
 [Événements de sécurité](../../../docs/framework/performance/security-etw-events.md)  
 Capture des informations sur la vérification de nom fort et la vérification Authenticode.  
  
 [Événement de pile](../../../docs/framework/performance/stack-etw-event.md)  
 Capture des informations utilisées avec d’autres événements pour générer des traces de pile après le déclenchement d’un événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorer le débogage et le réglage des performances avec ETW](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Blog des performances de Windows](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [Contrôle de l’enregistrement .NET Framework](../../../docs/framework/performance/controlling-logging.md)  
 [Fournisseurs ETW du CLR](../../../docs/framework/performance/clr-etw-providers.md)  
 [Niveaux et mots clés ETW du CLR](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Événements ETW dans le Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
