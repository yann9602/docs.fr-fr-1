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
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="1eff7-102">Comment : implémenter un client du modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="1eff7-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="1eff7-103">L’exemple de code suivant montre comment utiliser un composant conforme à la [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1eff7-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="1eff7-104">Le formulaire pour cet exemple utilise le `PrimeNumberCalculator` composant décrit dans [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="1eff7-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="1eff7-105">Lorsque vous exécutez un projet qui utilise cet exemple, vous verrez un formulaire « Calculatrice de nombres premiers » avec une grille et deux boutons : **démarrer une nouvelle tâche** et **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="1eff7-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel**.</span></span> <span data-ttu-id="1eff7-106">Vous pouvez cliquer sur le **démarrer une nouvelle tâche** bouton plusieurs fois de suite, et à chaque clic, une opération asynchrone commence un calcul pour déterminer si un nombre test généré de manière aléatoire est un nombre premier.</span><span class="sxs-lookup"><span data-stu-id="1eff7-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="1eff7-107">Le formulaire affiche périodiquement progression et des résultats incrémentiels.</span><span class="sxs-lookup"><span data-stu-id="1eff7-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="1eff7-108">Chaque opération est attribuée à un ID de tâche unique.</span><span class="sxs-lookup"><span data-stu-id="1eff7-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="1eff7-109">Le résultat du calcul est affiché dans le **résultat** colonne ; si le numéro de test n’est pas premier, il est étiqueté comme **Composite,** et son premier diviseur est affiché.</span><span class="sxs-lookup"><span data-stu-id="1eff7-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="1eff7-110">Toute opération en attente peut être annulée avec le **Annuler** bouton.</span><span class="sxs-lookup"><span data-stu-id="1eff7-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="1eff7-111">Sélections peuvent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="1eff7-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1eff7-112">La plupart des nombres ne seront pas premiers.</span><span class="sxs-lookup"><span data-stu-id="1eff7-112">Most numbers will not be prime.</span></span> <span data-ttu-id="1eff7-113">Si vous ne trouvez pas un nombre premier après plusieurs opérations terminées, démarrez simplement davantage de tâches, et par la suite, vous trouverez des nombres premiers.</span><span class="sxs-lookup"><span data-stu-id="1eff7-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eff7-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1eff7-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="1eff7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1eff7-115">See Also</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
