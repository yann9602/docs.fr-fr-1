---
title: "Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="2f6fb-102">Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases</span><span class="sxs-lookup"><span data-stu-id="2f6fb-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="2f6fb-103">L’exemple suivant montre comment utiliser un <xref:System.Threading.SpinWait?displayProperty=nameWithType> objet pour implémenter une opération d’attente en deux phases.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="2f6fb-104">Dans la première phase, l’objet de synchronisation, un `Latch`, tourne pendant quelques cycles pendant qu’il vérifie si le verrou est devenu disponible.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="2f6fb-105">Dans la deuxième phase, si le verrou devienne disponible, le `Wait` méthode est retournée sans utiliser le <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> à exécuter son attente ; sinon, `Wait` exécute l’attente.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f6fb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f6fb-106">Example</span></span>  
 <span data-ttu-id="2f6fb-107">Cet exemple montre une implémentation de base d’une synchronisation de verrou primitive.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="2f6fb-108">Vous pouvez utiliser cette structure de données lorsque le temps d’attente sont supposés être très courts.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="2f6fb-109">Cet exemple est uniquement à des fins de démonstration.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="2f6fb-110">Si vous avez besoin des fonctionnalités de type de verrou dans votre programme, envisagez d’utiliser <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="2f6fb-111">Le verrou utilise le <xref:System.Threading.SpinWait> objet à mettre en place uniquement jusqu’au prochain appel à `SpinOnce` provoque le <xref:System.Threading.SpinWait> à générer la tranche horaire du thread.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="2f6fb-112">À ce stade, le verrou provoque son propre changement de contexte en appelant <xref:System.Threading.WaitHandle.WaitOne%2A> sur la <xref:System.Threading.ManualResetEvent> et en passant le reste de la valeur de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="2f6fb-113">La sortie d’enregistrement indique la fréquence à laquelle le verrou n’a pu augmenter les performances en acquérir le verrou sans utiliser le <xref:System.Threading.ManualResetEvent>.</span><span class="sxs-lookup"><span data-stu-id="2f6fb-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f6fb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f6fb-114">See Also</span></span>  
 [<span data-ttu-id="2f6fb-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="2f6fb-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="2f6fb-116">Fonctionnalités et objets de threading</span><span class="sxs-lookup"><span data-stu-id="2f6fb-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
