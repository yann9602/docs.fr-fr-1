---
title: "How to: Implement a Client of the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "Asynchronous Pattern"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "components [.NET Framework], asynchronous"
  - "AsyncOperation class"
  - "threading [Windows Forms], asynchronous features"
  - "AsyncCompletedEventArgs class"
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Implement a Client of the Event-based Asynchronous Pattern
L'exemple de code suivant montre comment utiliser un composant obéissant à la [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  Le formulaire pour cet exemple utilise le composant  `PrimeNumberCalculator`  décrit dans [How to: Implement a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Lorsque vous exécutez un projet qui utilise cet exemple, vous voyez un formulaire "Prime Number Calculator" avec une grille et deux boutons : **Start New Task** et **Cancel**.  Vous pouvez cliquer sur le bouton **Start New Task** plusieurs fois à la suite, et à chaque clic, une opération asynchrone commence un calcul pour déterminer si un nombre test généré de façon aléatoire est un nombre premier.  Le formulaire affiche périodiquement la progression et les résultats incrémentiels.  Un identificateur de tâche unique est assigné à chaque opération.  Le résultat du calcul est affiché dans la colonne **Résultat** ; si le numéro de test n'est pas premier, il est étiqueté comme **Composite** et son premier diviseur est affiché.  
  
 Toute opération en attente peut être annulée avec le bouton **Start New Task**.  Plusieurs sélections peuvent être effectuées.  
  
> [!NOTE]
>  La plupart des nombres ne seront pas premiers.  Si vous n'avez pas trouvé de nombre premier après avoir terminé plusieurs opérations, lancez simplement davantage de tâches et vous finirez par en trouver.  
  
## Exemple  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## Voir aussi  
 <xref:System.ComponentModel.AsyncOperation>   
 <xref:System.ComponentModel.AsyncOperationManager>   
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>