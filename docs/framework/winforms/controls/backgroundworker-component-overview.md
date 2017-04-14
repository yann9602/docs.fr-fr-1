---
title: "Vue d&#39;ensemble du composant BackgroundWorker | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BackgroundWorker"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "modèle asynchrone"
  - "opérations d'arrière-plan"
  - "tâches en arrière-plan"
  - "BackgroundWorker (composant)"
  - "composants (Windows Forms), asynchrones"
  - "formulaires, opérations d'arrière-plan"
  - "formulaires, multithreading"
  - "threads (Windows Forms), opérations d'arrière-plan"
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble du composant BackgroundWorker
De nombreuses opérations couramment exécutées peuvent être longues à s'éxécuter. Par exemple :  
  
-   Téléchargements d'images  
  
-   Appels de service web  
  
-   Téléchargements et chargements de fichiers \(y compris pour les applications d'égal à égal\)  
  
-   Calculs locaux complexes  
  
-   Transactions de base de données  
  
-   Accès au disque local, compte tenu de sa vitesse lente par rapport à l'accès mémoire  
  
 Les opérations comme celles\-ci peuvent entraîner le blocage de votre interface utilisateur pendant leur exécution. Quand vous souhaitez une interface utilisateur réactive et que vous êtes confronté à de longs délais associés à ce type d'opérations, le composant <xref:System.ComponentModel.BackgroundWorker> fournit une solution commode.  
  
 Le composant <xref:System.ComponentModel.BackgroundWorker> vous donne la possibilité d'exécuter les opérations longues de façon asynchrone \(« en arrière\-plan »\), sur un thread différent du thread d'interface utilisateur principal de votre application. Pour utiliser un <xref:System.ComponentModel.BackgroundWorker>, vous lui indiquez simplement quelle méthode de travail de longue durée exécuter en arrière\-plan, puis vous appelez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. Votre thread d'appel continue de s'exécuter normalement pendant que la méthode de travail s'exécute de façon asynchrone. Une fois la méthode exécutée, le <xref:System.ComponentModel.BackgroundWorker> alerte le thread d'appel en déclenchant l'événement <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, lequel contient éventuellement les résultats de l'opération.  
  
 Le composant <xref:System.ComponentModel.BackgroundWorker> est disponible dans la **Boîte à outils**, sous l'onglet **Composants**. Pour ajouter un <xref:System.ComponentModel.BackgroundWorker> à votre formulaire, faites glisser le composant <xref:System.ComponentModel.BackgroundWorker> dessus. Il apparaît dans la barre d'état des composants et ses propriétés apparaissent dans la fenêtre **Propriétés**.  
  
 Pour démarrer votre opération asynchrone, utilisez la méthode <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> prend un paramètre `object` facultatif qui peut être utilisé pour passer des arguments à votre méthode de travail. La classe <xref:System.ComponentModel.BackgroundWorker> expose l'évenement <xref:System.ComponentModel.BackgroundWorker.DoWork> auquel votre thread de travail est attaché via le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>.  
  
 Le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork> prend un paramètre <xref:System.ComponentModel.DoWorkEventArgs> qui est doté de la propriété <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>. Celle\-ci reçoit le paramètre de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> et peut être passée à votre méthode de travail qui sera appelée dans le gestionnaire d'événements <xref:System.ComponentModel.BackgroundWorker.DoWork>. L'exemple suivant montre comment affecter un résultat depuis une méthode de travail appelée `ComputeFibonacci`. Il fait partie d'un exemple plus étendu que vous pouvez trouver à l'emplacement suivant : [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Pour plus d'informations sur l'utilisation des gestionnaires d'événements, consultez [Événements](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  Quand vous utilisez le multithreading, vous vous exposez potentiellement à des bogues très sérieux et complexes. Consultez [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) avant d'implémenter une solution utilisant le multithreading.  
  
 Pour plus d'informations sur l'utilisation de la classe <xref:System.ComponentModel.BackgroundWorker>, consultez [Comment : exécuter une opération en arrière\-plan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## Voir aussi  
 [NOT IN BUILD: Multithreading in Visual Basic](http://msdn.microsoft.com/fr-fr/c731a50c-09c1-4468-9646-54c86b75d269)   
 [Comment : implémenter un formulaire qui utilise une opération d'arrière\-plan](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)