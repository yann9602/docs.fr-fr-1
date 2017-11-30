---
title: Architecture de programmation d'une application de service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a>Architecture de programmation d'une application de service
Applications de Service Windows sont basées sur une classe qui hérite de la <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> classe. Vous substituez les méthodes de cette classe et définissez des fonctionnalités pour pouvoir déterminer le comporte de votre service.  
  
 Les principales classes impliquées dans la création du service sont :  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— Vous substituez les méthodes de la <xref:System.ServiceProcess.ServiceBase> classe lors de la création d’un service et de définir le code pour déterminer le fonctionnement de votre service dans cette classe héritée.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>et <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> , vous utilisez ces classes pour installer et désinstaller votre service.  
  
 En outre, une classe nommée <xref:System.ServiceProcess.ServiceController> peut être utilisé pour manipuler le service. Cette classe n’est pas impliquée dans la création d’un service, mais il peut être utilisée pour démarrer et arrêter le service, passer des commandes et retourner une série d’énumérations.  
  
## <a name="defining-your-services-behavior"></a>Définition du comportement de votre Service  
 Dans votre classe de service, vous substituez les fonctions de classe de base qui déterminent ce qui se produit lorsque l’état de votre service est modifié dans le Gestionnaire de contrôle des Services. La <xref:System.ServiceProcess.ServiceBase> classe expose les méthodes suivantes, que vous pouvez substituer pour ajouter un comportement personnalisé.  
  
|Méthode|Substituer pour|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Indiquer les actions à effectuer au démarrage de votre service en cours d’exécution. Vous devez écrire du code dans cette procédure pour votre service effectuer des tâches utiles.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Indiquez ce qui doit se produire lorsque votre service est en pause.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Indiquez ce qui doit se produire lorsque votre service s’arrête en cours d’exécution.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Indiquez ce qui doit se produire lorsque votre service reprend un fonctionnement normal après avoir été suspendu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Indiquez ce qui doit se produire juste avant l’arrêt, votre système si votre service est en cours d’exécution à ce moment-là.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Indiquez ce qui doit se produire lorsque votre service reçoit une commande personnalisée. Pour plus d’informations sur les commandes personnalisées, consultez MSDN en ligne.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Indiquer comment le service doit répondre lors de la réception d’un événement de gestion d’alimentation, telle qu’une batterie faible ou suspendu.|  
  
> [!NOTE]
>  Ces méthodes représentent les États par lesquels passe le service dans sa durée de vie ; les transitions de service à partir d’un état à l’autre. Par exemple, vous n’obtiendrez jamais le service pour répondre à une <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> commande avant <xref:System.ServiceProcess.ServiceBase.OnStart%2A> a été appelée.  
  
 Il existe plusieurs autres propriétés et méthodes qui présentent un intérêt. Elles incluent notamment :  
  
-   Le <xref:System.ServiceProcess.ServiceBase.Run%2A> méthode sur la <xref:System.ServiceProcess.ServiceBase> classe. Il s’agit du point d’entrée principal pour le service. Lorsque vous créez un service à l’aide du modèle Service Windows, le code est inséré dans votre application `Main` méthode pour exécuter le service. Ce code ressemble à ceci :  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Ces exemples utilisent un tableau de type <xref:System.ServiceProcess.ServiceBase>, dans lequel chaque service de votre application peut être ajouté, puis tous les services peuvent être exécutés ensemble. Si vous créez qu’un seul service, toutefois, vous pouvez choisir pas à utiliser le tableau et de simplement déclarer un nouvel objet héritant de <xref:System.ServiceProcess.ServiceBase> et exécutez-le. Pour obtenir un exemple, consultez [Comment : écrire des Services par programmation](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Une série de propriétés de la <xref:System.ServiceProcess.ServiceBase> classe. Elles déterminent quelles méthodes peuvent être appelées sur votre service. Par exemple, lorsque le <xref:System.ServiceProcess.ServiceBase.CanStop%2A> est définie sur `true`, le <xref:System.ServiceProcess.ServiceBase.OnStop%2A> méthode sur votre service peut être appelée. Lorsque le <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> est définie sur `true`, le <xref:System.ServiceProcess.ServiceBase.OnPause%2A> et <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> méthodes peuvent être appelées. Lorsque vous définissez une de ces propriétés à `true`, vous devez ensuite remplacer et définir le traitement des méthodes associées.  
  
    > [!NOTE]
    >  Votre service doit substituer au moins <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour être utile.  
  
 Vous pouvez également utiliser un composant appelé le <xref:System.ServiceProcess.ServiceController> de communiquer avec et contrôler le comportement d’un service existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux Applications de Service Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Comment : créer des Services Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
