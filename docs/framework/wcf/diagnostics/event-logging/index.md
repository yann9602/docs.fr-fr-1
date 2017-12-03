---
title: "Journalisation des événements dans WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: event logging [WCF]
ms.assetid: aac0530d-f44c-45a1-bada-e30e0677b41f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a2d856aad069a5e532ba893185b6222ee1db0f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="event-logging-in-wcf"></a>Journalisation des événements dans WCF
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] effectue le suivi des événements internes dans le journal des événements Windows.  
  
## <a name="viewing-event-logs"></a>Consultation des journaux des événements  
 La journalisation des événements est activée automatiquement par défaut et il n'existe aucun mécanisme pour la désactiver. Les événements journalisés par [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] peuvent être consultés à l'aide de l'Observateur d'événements. Pour lancer cet outil, cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, double-cliquez sur **outils d’administration**, puis double-cliquez sur **Observateur d’événements**.  
  
### <a name="application-event-log"></a>Journal des événements de l'application  
 Le **journal des événements Application** contient la plupart des événements générés par [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. La plupart des entrées indiquent qu’une fonctionnalité particulière n’a pas réussi à démarrer pour une application. Voici quelques exemples :  
  
-   Journalisation/Suivi des messages : [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] écrit un événement dans le journal des événements lorsque la journalisation du suivi et des messages échoue. Toutefois, tous les échecs de suivi ne déclenchent pas un événement. Pour empêcher le journal des événements de regorger d'échecs de suivi, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] implémente une période d'indisponibilité de 10 minutes pour un tel événement. Cela signifie que si [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] écrit un échec de suivi dans le journal des événements, aucun autre échec de suivi ne sera écrit pendant au moins 10 minutes.  
  
-   Écouteur partagé : le service de partage de ports TCP WCF journalise un événement lorsqu'il ne réussit pas à démarrer.  
  
-   [!INCLUDE[infocard](../../../../../includes/infocard-md.md)] : journalise des événements lorsque le service ne réussit pas à démarrer.  
  
-   Événements critiques et erreurs, tels que les échecs de démarrage ou les blocages  
  
-   Journalisation des messages activée : journalise des événements lorsque la journalisation des messages est activée. L'objectif consiste à avertir l'administrateur que des informations sensibles et spécifiques à l'application peuvent être journalisées dans les en-têtes et les corps des messages.  
  
-   Un événement est journalisé lorsque l'attribut `enableLoggingKnownPII` de l'élément `machineSettings` du fichier `machine.config` est défini. Cet attribut indique si toute application qui s'exécute sur l'ordinateur est autorisée à journaliser des informations d'identification personnelle connues.  
  
-   Si l'attribut `logKnownPii` dans le fichier `app.config` ou `web.config` a la valeur `true` pour qu'une application spécifique active la journalisation des informations d'identification personnelle, mais que l'attribut `enableLoggingKnownPII` dans l'élément `machineSettings` du fichier `machine.config` a la valeur `false`, un événement est journalisé. En outre, si `logKnownPii` et `enableLoggingKnownPII` ont la valeur `true`, un événement est journalisé. Pour plus d’informations sur ces paramètres de configuration, consultez la section sécurité de la [configuration de la journalisation du Message](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) rubrique.  
  
### <a name="security-event-log"></a>Journal des événements de sécurité  
 Le **des événements de sécurité** contient des événements d’audit de sécurité qui sont enregistrés par WCF.  
  
### <a name="system-event-log"></a>Journal des événements système  
 WCF n’enregistre rien le **journal des événements système**.  
  
### <a name="event-log-entries"></a>Entrées de journal des événements  
 Le **source** d’un événement est le nom de l’assembly qui génère l’entrée de journal.  
  
 Le type d'une entrée de journal des événements est utilisé pour indiquer la gravité d'un événement. Chaque événement doit posséder un type unique indiqué par l'application lorsqu'elle signale l'événement. L'observateur d'événements utilise ce type pour déterminer l'icône à afficher dans la vue Liste du journal. Pour connaître les différents types d'événements d'une entrée de journal des événements, consultez <xref:System.Diagnostics.EventLogEntryType>.  
  
 Lorsque vous cliquez sur « plus d’informations » lors de l’affichage d’un événement dans l’Observateur d’événements, l’Observateur d’événements peut envoyer des informations sur Internet. Pour plus d'informations, consultez l'aide de l'Observateur d'événements.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Référence générale des événements](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
