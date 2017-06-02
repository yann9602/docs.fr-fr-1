---
title: "Service Application Programming Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ServiceController components, programming architecture"
  - "ServiceBase class, service states"
  - "Windows Service applications, code model"
  - "services, programming architecture"
  - "ServiceController class"
  - "services, states"
  - "ServiceProcessInstaller class, service application code model"
  - "Windows Service applications, states"
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# Service Application Programming Architecture
Les applications de service Windows reposent sur une classe qui hérite de la classe <xref:System.ServiceProcess.ServiceBase?displayProperty=fullName>.  Vous substituez les méthodes de cette classe et définissez pour elles des fonctionnalités pour déterminer le comportement de votre service.  
  
 Les principales classes intervenant dans la création des services sont les suivantes :  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=fullName> — Vous substituez les méthodes de la classe <xref:System.ServiceProcess.ServiceBase> lorsque vous créez un service et créez le code qui déterminera le fonctionnement de votre service dans cette classe héritée.  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=fullName> et <xref:System.ServiceProcess.ServiceInstaller?displayProperty=fullName> —Vous utilisez ces classes pour installer et désinstaller votre service.  
  
 En outre, il est possible d'utiliser une classe appelée <xref:System.ServiceProcess.ServiceController> pour manipuler le service.  Cette classe n'intervient pas dans la création d'un service, mais elle peut être utilisée pour le démarrer et l'arrêter, lui passer des commandes et retourner une série d'énumérations.  
  
## Définition du comportement de votre service  
 Dans la classe de votre service, vous substituez les fonctions de classe de base déterminant ce qui se produit quand l'état de votre service est modifié dans le Gestionnaire de contrôle des services.  La classe <xref:System.ServiceProcess.ServiceBase> expose les méthodes suivantes que vous pouvez substituer pour ajouter un comportement personnalisé.  
  
|Méthode|À substituer pour|  
|-------------|-----------------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Indiquer quelles actions doivent être accomplies au démarrage de votre service.  Vous devez écrire du code dans cette procédure pour que votre service accomplisse un travail utile.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Indiquer ce qui se passe lorsque votre service est suspendu.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Indiquer ce qui se passe lorsque votre service est arrêté.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Indiquer ce qui se passe lorsque votre service redémarre après une suspension.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Indiquer ce qui doit se passer juste avant l'arrêt de votre service si celui\-ci est à ce moment\-là en cours d'exécution.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Indiquer ce qui se passe lorsque votre service reçoit une commande personnalisée.  Pour plus d'informations sur les commandes personnalisées, consultez MSDN Online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Indiquer comment le service doit répondre lorsqu'il reçoit un événement de gestion de l'alimentation \(batterie faible ou opération suspendue, par exemple\)|  
  
> [!NOTE]
>  Ces méthodes représentent les états par lesquels passe votre service durant sa vie ; le service passe successivement par ces différents états.  Par exemple, un service ne doit jamais répondre à une commande <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> avant que la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ne soit appelée.  
  
 D'autres propriétés et méthodes présentent un intérêt.  Ces niveaux sont les suivants :  
  
-   Appelez la méthode <xref:System.ServiceProcess.ServiceBase.Run%2A> sur la classe <xref:System.ServiceProcess.ServiceBase>.  Il s'agit du point d'entrée principal du service.  Lorsque vous créez un service en vous servant du modèle de service Windows, du code est inséré dans la méthode `Main` de votre application pour exécuter le service.  Le code présente l'aspect suivant :  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  Ces deux exemples font appel à un tableau de type <xref:System.ServiceProcess.ServiceBase>, auquel chaque service que contient votre application peut être ajouté, après quoi tous les services peuvent s'exécuter ensemble.  Toutefois, si vous ne créez qu'un seul service, vous pouvez choisir de ne pas utiliser le tableau et de simplement déclarer un nouvel objet héritant de la classe <xref:System.ServiceProcess.ServiceBase>, puis de l'exécuter.  Pour un exemple, consultez [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).  
  
-   Une série de propriétés de la classe <xref:System.ServiceProcess.ServiceBase>.  Elles déterminent quelles méthodes peuvent être appelées pour votre service.  Par exemple, lorsque la propriété <xref:System.ServiceProcess.ServiceBase.CanStop%2A> a la valeur `true`, la méthode <xref:System.ServiceProcess.ServiceBase.OnStop%2A> de votre service peut être appelée.  Par exemple, lorsque la propriété <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> a la valeur `true`, les méthodes <xref:System.ServiceProcess.ServiceBase.OnPause%2A> et <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> peuvent être appelées.  Lorsque vous attribuez la valeur `true` à l'une ou l'autre de ces propriétés, vous devez ensuite substituer puis définir le traitement des méthodes associées.  
  
    > [!NOTE]
    >  Votre service doit substituer au moins <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour être utile.  
  
 Vous pouvez également utiliser un composant appelé <xref:System.ServiceProcess.ServiceController> pour communiquer avec un service existant et contrôler son comportement.  
  
## Voir aussi  
 [Introduction to Windows Service Applications](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [How to: Create Windows Services](../../../docs/framework/windows-services/how-to-create-windows-services.md)