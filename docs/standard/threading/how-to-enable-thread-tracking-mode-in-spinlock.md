---
title: "Comment : activer le mode de suivi des threads dans le verrouillage Spinlock"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="3f0f8-102">Comment : activer le mode de suivi des threads dans le verrouillage Spinlock</span><span class="sxs-lookup"><span data-stu-id="3f0f8-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="3f0f8-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>est un verrou d’exclusion mutuelle de bas niveau que vous pouvez utiliser pour les scénarios qui ont des durées d’attente très courtes.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="3f0f8-104"><xref:System.Threading.SpinLock>n’est pas réentrant.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="3f0f8-105">Après qu’un thread entré le verrou, il doit quitter correctement avant de pouvoir à nouveau entrer.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="3f0f8-106">En règle générale, toute tentative d’entrer à nouveau le verrou provoquerait un interblocage et les interblocages peuvent être très difficiles à déboguer.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="3f0f8-107">Comme une aide au développement, <xref:System.Threading.SpinLock?displayProperty=nameWithType> prend en charge un mode de suivi de thread qui lève une exception levée lorsqu’un thread tente de réentrer un verrou qu’il détient déjà.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="3f0f8-108">Cela vous permet de que retrouver plus facilement le point auquel le verrou a été pas fermé correctement.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="3f0f8-109">Vous pouvez activer le mode de suivi de thread à l’aide de la <xref:System.Threading.SpinLock> constructeur qui accepte une valeur booléenne d’entrée et en passant un argument de `true`.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="3f0f8-110">Après avoir terminé le développement et les phases de test, désactivez le mode de suivi des threads pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f0f8-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f0f8-111">Example</span></span>  
 <span data-ttu-id="3f0f8-112">L’exemple suivant montre le mode de suivi de thread.</span><span class="sxs-lookup"><span data-stu-id="3f0f8-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="3f0f8-113">Les lignes de quitter correctement le verrou sont commentées pour simuler une erreur de codage provoquant l’un des résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="3f0f8-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="3f0f8-114">Une exception est levée si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `true` (`True` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3f0f8-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="3f0f8-115">Interblocage si le <xref:System.Threading.SpinLock> a été créé à l’aide d’un argument de `false` (`False` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3f0f8-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="3f0f8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f0f8-116">See Also</span></span>  
 [<span data-ttu-id="3f0f8-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="3f0f8-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
