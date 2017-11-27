---
title: "Hébergement de services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0d3cd2f53b81ae6114baa3c7eedd899126ed579
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-services"></a>Hébergement de services
Pour devenir actif, un service doit être hébergé dans un environnement d'exécution qui le crée et contrôle son contexte et sa durée de vie. Les services[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] sont conçus pour s'exécuter dans tout processus Windows qui prend en charge le code managé.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est le modèle de programmation unifié de Microsoft permettant de générer des applications orientées service. Ce modèle de programmation reste cohérent et est indépendant de l'environnement d'exécution dans lequel le service est déployé. En pratique, cela signifie que le code de vos services est essentiellement le même quelle que soit l'option d'hébergement.  
  
 Ces options d'hébergement vont de l'exécution dans une application console à une exécution dans des environnements serveur tels qu'un service Windows dans un processus de travail managé par les services IIS (Internet Information Services) ou WAS (Windows Process Activation Services). Les développeurs choisissent l'environnement d'hébergement qui répond aux spécifications de déploiement du service. Ces spécifications peuvent dériver de la plateforme sur laquelle l'application est déployée, du transport sur lequel envoyer et recevoir des messages ou du type de recyclage de processus et tout autre gestion de processus indispensable pour garantir la disponibilité adéquate, ou d'autres impératifs de gestion ou de fiabilité. La section suivante fournit des informations et des instructions sur les options d'hébergement.  
  
## <a name="hosting-options"></a>Options d'hébergement  
  
#### <a name="self-hosting-in-a-managed-application"></a>Auto-hébergement dans une application managée  
 Les services[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peuvent être hébergés dans toute application managée. Il s'agit de l'option la plus souple car l'infrastructure à déployer est la plus faible. Vous incorporez le code pour le service à l'intérieur du code d'application managée, puis créez et ouvrez une instance de <xref:System.ServiceModel.ServiceHost> pour rendre le service disponible. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Comment : héberger un Service WCF dans une Application managée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Cette option active deux scénarios courants : les services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui s'exécutent à l'intérieur d'applications console et des applications clientes élaborées telles que celles basées sur [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] ou Windows Forms (WinForms). L'hébergement d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] à l'intérieur d'une application console est en général utile pendant la phase de développement de l'application. Cela simplifie son débogage, l'obtention des informations de suivi pour déterminer ce qui se passe à l'intérieur de l'application, et son déplacement en la copiant vers un nouvel emplacement. Cette option d'hébergement permet aux applications clientes complexes, comme [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] et WinForms, de communiquer facilement avec le monde extérieur. Il peut s'agit par exemple, d'un client de collaboration pair à pair qui utilise [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] pour son interface utilisateur et héberge également un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui permet à d'autres clients de se connecter à lui et de partager des informations.  
  
#### <a name="managed-windows-services"></a>Services Windows managés  
 Cette option d'hébergement consiste à enregistrer le domaine d'application (AppDomain) qui héberge un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comme un service Windows managé (autrefois appelé un service NT) afin que la durée de vie de processus du service soit contrôlée par le Gestionnaire de contrôle des services (SCM) pour les services Windows. Comme l'option d'auto-hébergement, ce type d'environnement d'hébergement requiert que du code d'hébergement soit écrit dans le cadre de l'application. Le service est implémenté comme un service Windows et comme un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] en lui faisant hériter de la classe <xref:System.ServiceProcess.ServiceBase> ainsi que d'une interface de contrat de service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] . Le <xref:System.ServiceModel.ServiceHost> est ensuite créé et ouvert dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> substituée et fermée dans une méthode <xref:System.ServiceProcess.ServiceBase.OnStop> substituée. Une classe Installer qui hérite de <xref:System.Configuration.Install.Installer> doit également être implémentée pour permettre au programme d'être installé comme un service Windows par l'outil Installutil.exe. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Comment : héberger un Service WCF dans un Service Windows managé](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). Le scénario activé par l'option d'hébergement du service Windows managé est celui d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de longue durée hébergé en dehors d'IIS dans un environnement sécurisé qui n'est pas activé par message. La durée de vie du service est contrôlée par le système d'exploitation. Cette option d'hébergement est disponible dans toutes les versions de Windows.  
  
#### <a name="internet-information-services-iis"></a>Services IIS (Internet Information Services)  
 L'option d'hébergement IIS est intégrée à [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] et utilise les fonctionnalités offertes par ces technologies, telles que le recyclage de processus, l'arrêt inactif, le contrôle d'état de processus et l'activation basée sur des messages. Sur les systèmes d'exploitation [!INCLUDE[wxp](../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] , il s'agit de la solution par défaut pour héberger les applications de service Web qui sont fortement sollicitées et doivent être très évolutives. Les services IIS offrent également la facilité de gestion intégrée que les clients attendent d'un produit serveur de classe d'entreprise. Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. [!INCLUDE[crabout](../../../includes/crabout-md.md)] la configuration de l’hébergement IIS pour un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] , consultez [How to: Host a WCF Service in IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Notez que les services hébergés par IIS peuvent utiliser uniquement le transport HTTP. Son implémentation dans IIS 5.1 a introduit des limitations dans [!INCLUDE[wxp](../../../includes/wxp-md.md)]. L'activation basée sur des messages fournie pour un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] par IIS 5.1 sur [!INCLUDE[wxp](../../../includes/wxp-md.md)] empêche tout autre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] auto-hébergé sur le même ordinateur d'utiliser le port 80 pour communiquer. Les services[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peuvent s'exécuter dans le même domaine d'applicatisur AppDomain/pool d'applicatisurs/processus de travail que d'autres applicatisurs une fois hébergés par [!INCLUDE[iis601](../../../includes/iis601-md.md)] sur [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Cependant, dans la mesure où [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et [!INCLUDE[iis601](../../../includes/iis601-md.md)] utilisent la pile HTTP en mode noyau (HTTP.sys), [!INCLUDE[iis601](../../../includes/iis601-md.md)] peut partager le port 80 avec d'autres services [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] auto-hébergés qui s'exécutent sur le même ordinateur, contrairement à IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Windows Process Activation Service (WAS)  
 Le service WAS (Windows Process Activation Service) est le nouveau mécanisme d'activation de processus pour [!INCLUDE[lserver](../../../includes/lserver-md.md)] , également disponible sur [!INCLUDE[wv](../../../includes/wv-md.md)]. Il conserve le modèle de processus [!INCLUDE[iis601](../../../includes/iis601-md.md)] classique (pools d'applications et activation de processus basée sur des messages) et les fonctionnalités d'hébergement (telles que la protection rapide contre les pannes, le contrôle d'état et le recyclage), mais il supprime la dépendance sur HTTP de l'architecture d'activation. [!INCLUDE[iisver](../../../includes/iisver-md.md)] utilise le service WAS pour accomplir l'activation basée sur des messages via HTTP. Les composants [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] supplémentaires s'intègrent aussi dans le service WAS pour assurer l'activation basée sur des messages via les autres protocoles que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] prend en charge, tels que TCP, MSMQ et les canaux nommés. Cela permet aux applications qui utilisent des protocoles de communication d'utiliser les fonctionnalités IIS (telles que le recyclage de processus, la protection rapide contre les pannes et le système de configuration commun) qui étaient réservées exclusivement aux applications basées sur HTTP.  
  
 Cette option d'hébergement requiert que les services WAS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. [!INCLUDE[crabout](../../../includes/crabout-md.md)] la configuration de l’hébergement WAS, consultez [How to: Host a WCF Service in WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Choix d'un environnement d'hébergement  
 Le tableau suivant résume certains avantages et scénarios clés associés à chacune des options d'hébergement.  
  
|Environnement d'hébergement|Scénarios courants|Avantages et limitations clés|  
|-------------------------|----------------------|----------------------------------|  
|Application managée (« auto-hébergée »)|-Utilisées pendant le développement des applications de la console.<br />-WinForm élaborées et [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] applications client accédant aux services.|-Flexible.<br />-Facile à déployer.<br />-N’est pas une solution d’entreprise pour les services.|  
|Services Windows (autrefois appelés services NT)|-Longue [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service hébergé en dehors d’IIS.|-Durée de vie de processus de Service contrôlée par le système d’exploitation, ne pas compatibles avec les messages.<br />-Prise en charge par toutes les versions de Windows.<br />-Environnement sécurisé.|  
|IIS 5.1, [!INCLUDE[iis601](../../../includes/iis601-md.md)]|-En cours d’exécution un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service côte à côte avec [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] de contenu sur Internet à l’aide du protocole HTTP.|-Le recyclage de processus.<br />-Arrêt inactif.<br />-Traiter le contrôle d’intégrité.<br />-Activation basée sur message.<br />-HTTP uniquement.|  
|Windows Process Activation Service (WAS)|-En cours d’exécution un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service sans avoir à installer IIS sur Internet à l’aide de différents protocoles de transport.|-IIS n’est pas nécessaire.<br />-Le recyclage de processus.<br />-Arrêt inactif.<br />-Traiter le contrôle d’intégrité.<br />-Activation basée sur message.<br />-Fonctionne avec HTTP, TCP, canaux nommés et MSMQ.|  
|IIS 7,0|-En cours d’exécution un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] contenu.<br />-En cours d’exécution un [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service sur Internet à l’aide de différents protocoles de transport.|-A été avantages.<br />-Intégré avec [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] et le contenu d’IIS.|  
  
 Le choix d'un environnement d'hébergement dépend de la version de Windows sur lequel il est déployé, des transports requis pour envoyer les messages et du type de recyclage de processus et de domaine d'application requis. Le tableau suivant résume les données liées à ces spécifications.  
  
|Environnement d'hébergement|Disponibilité de plateforme|Transports pris en charge|Recyclage de processus et AppDomain|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Applications managées (« auto-hébergées »)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Non|  
|Services Windows (autrefois appelés services NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Non|  
|IIS 5,1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Oui|  
|[!INCLUDE[iis601](../../../includes/iis601-md.md)]|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Oui|  
|Windows Process Activation Service (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> net.pipe,<br /><br /> net.msmq|Oui|  
  
 Il est important de noter que l'exécution d'un service ou d'une extension à partir d'un hôte non fiable compromet la sécurité. Notez aussi que lors de l'ouverture d'un <xref:System.ServiceModel.ServiceHost> lorsque l'emprunt d'identité est activé, une application doit garantir que l'utilisateur n'est pas déconnecté, par exemple en mettant en cache le <xref:System.Security.Principal.WindowsIdentity> de l'utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration système requise](../../../docs/framework/wcf/wcf-system-requirements.md)  
 [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)  
 [How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [How to: Host a WCF Service in WAS (Comment : héberger un service WCF dans WAS)](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Comment : héberger un Service WCF dans un Service Windows managé](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Guide pratique pour héberger un service WCF dans une application managée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
