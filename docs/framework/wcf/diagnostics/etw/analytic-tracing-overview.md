---
title: "Vue d'ensemble du traçage analytique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dd456401073d8c7f3c7bc9fbfbe5c11dbbd4e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-overview"></a>Vue d'ensemble du traçage analytique
Le traçage analytique dans [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] est une fonctionnalité de suivi très performante et à faible niveau de commentaires, définie au-dessus du suivi d'événements Windows (ETW). ETW s'exécute au niveau du noyau pour diminuer considérablement les surcharges des opérations de suivi. Il met efficacement en mémoire tampon les événements en mode utilisateur et noyau, et permet l'activation dynamique de la journalisation, sans que le service ait besoin de redémarrer. Les données de suivi sont disponibles dans les journaux des événements, une fois qu'elles ont été émises et reçues.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] ETW, consultez [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkId=164781)(Améliorer le débogage et le réglage des performances à l’aide d’ETW).  
  
 En plus d'utiliser les journaux d'événements du système Windows, de la sécurité et de l'application pour analyser l'application, [!INCLUDE[wv](../../../../../includes/wv-md.md)] et [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] ont introduit des journaux supplémentaires sous le nœud de niveau supérieur des journaux des applications et des services. L'objectif de ces nouveaux journaux est de stocker les événements d'une application particulière ou d'un composant spécifique, au lieu d'événements globaux qui ont un impact sur l'ensemble du système (tels le type d'événements enregistrés par le journal des événements de sécurité). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] unifie et met en corrélation l'enregistrement des événements de trace [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , des journaux de messages [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] , et les enregistrements de suivi [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] avec les journaux des applications et des services.  
  
## <a name="concepts-and-capabilities"></a>Concepts et fonctions  
 Les concepts et fonctions suivants s'appliquent au traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] .  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Activation des paramètres de diagnostic WCF  
 Les diagnostics WCF sont activés dans le \<system.serviceModel >\<diagnostics > section de configuration.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Les paramètres de diagnostic WCF d'une application virtuelle IIS hébergée sur le Web sont activés dans son fichier Web.config. Une autre option est de créer un Web.config dans un sous-répertoire au sein de l'application.  Ce choix applique les paramètres à tous les services dans un sous-répertoire.  Pour s'assurer que les paramètres de diagnostic sont initialisés de manière cohérente pour tous les services de l'application, les paramètres doivent être configurés dans le fichier Web.config qui se trouve dans le répertoire de l'application et non dans l'un des sous-répertoires individuels de l'application.  
  
### <a name="channels"></a>Canaux  
 ETW permet aux composants logiciels de diriger les événements de suivi vers une audience particulière via les canaux. Par exemple, vous pouvez envoyer des événements aux administrateurs système sur un canal, et les événements qui intéressent les développeurs d'applications sur un autre canal. Les canaux sont nommés et enregistrés par Windows, afin que les utilisateurs puissent consulter les événements d'un canal à l'aide de l'observateur d'événements.  
  
 La fonctionnalité de traçage analytique de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] écrit sur le canal Microsoft-Windows-Serveur d'applications-Applications. Ce canal est spécifiquement conçu pour les utilisateurs qui souhaitent surveiller l'intégrité des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] en production. Il définit un jeu d'événements restreint qui peut être utilisé dans de nombreux scénarios de contrôle d'intégrité et de dépannage.  
  
 Pour activer le suivi d'événements pour le manifeste Windows afin que les messages soient décodés correctement dans le journal des événements, utilisez l'outil ServiceModelReg sur la ligne de commande de la façon suivante :  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Configuration Dynamique  
 L'infrastructure ETW permet d'activer le suivi et de le configurer de manière dynamique, à l'aide d'outils Windows standard. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)(Améliorer le débogage et le réglage des performances à l’aide d’ETW).  
  
### <a name="message-flow-tracing"></a>Suivi de flux de messages  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] la manière d’activer le suivi de flux de messages, consultez [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)(Améliorer le débogage et le réglage des performances à l’aide d’ETW).  
  
### <a name="keywords"></a>Mots clés  
 Les mots clés sont utilisés pour filtrer les messages de trace et définir quel composant du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] a émis l'événement. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)(Améliorer le débogage et le réglage des performances à l’aide d’ETW).
