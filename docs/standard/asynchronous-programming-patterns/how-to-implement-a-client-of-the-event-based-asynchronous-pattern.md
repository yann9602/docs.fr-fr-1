---
title: "Comment : implémenter un client du modèle asynchrone basé sur des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Comment : implémenter un client du modèle asynchrone basé sur des événements
L’exemple de code suivant montre comment utiliser un composant conforme à la [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). Le formulaire pour cet exemple utilise le `PrimeNumberCalculator` composant décrit dans [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Lorsque vous exécutez un projet qui utilise cet exemple, vous verrez un formulaire « Calculatrice de nombres premiers » avec une grille et deux boutons : **démarrer une nouvelle tâche** et **Annuler**. Vous pouvez cliquer sur le **démarrer une nouvelle tâche** bouton plusieurs fois de suite, et à chaque clic, une opération asynchrone commence un calcul pour déterminer si un nombre test généré de manière aléatoire est un nombre premier. Le formulaire affiche périodiquement progression et des résultats incrémentiels. Chaque opération est attribuée à un ID de tâche unique. Le résultat du calcul est affiché dans le **résultat** colonne ; si le numéro de test n’est pas premier, il est étiqueté comme **Composite,** et son premier diviseur est affiché.  
  
 Toute opération en attente peut être annulée avec le **Annuler** bouton. Sélections peuvent être effectuées.  
  
> [!NOTE]
>  La plupart des nombres ne seront pas premiers. Si vous ne trouvez pas un nombre premier après plusieurs opérations terminées, démarrez simplement davantage de tâches, et par la suite, vous trouverez des nombres premiers.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
