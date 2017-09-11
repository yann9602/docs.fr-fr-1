---
title: "Réglage de votre Application Async (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e031c2e23430a62629424ee57a140a7d8da41777
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="2e76a-102">Réglage de votre Application Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e76a-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="2e76a-103">Vous pouvez ajouter précision et la flexibilité à vos applications asynchrones à l’aide de méthodes et propriétés qui le <xref:System.Threading.Tasks.Task>type rend disponible.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="2e76a-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="2e76a-104">Les rubriques de cette section montrent des exemples qui utilisent <xref:System.Threading.CancellationToken>et important `Task` méthodes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="2e76a-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="2e76a-105">À l’aide de `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en une seule tâche d’analyse.</span><span class="sxs-lookup"><span data-stu-id="2e76a-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="2e76a-106">`WhenAny`Retourne une tâche se termine lorsque toutes les tâches dans une collection sont terminée.</span><span class="sxs-lookup"><span data-stu-id="2e76a-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="2e76a-107">Pour obtenir des exemples qui utilisent `WhenAny`, consultez [annuler les tâches Asynch restantes après une est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)et [démarrer plusieurs tâches d’Async et processus les comme ils complète (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="2e76a-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="2e76a-108">`WhenAll`Retourne une tâche se termine lorsque toutes les tâches d’un regroupement sont terminées.</span><span class="sxs-lookup"><span data-stu-id="2e76a-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="2e76a-109">Pour plus d’informations et un exemple qui utilise `WhenAll`, consultez [Comment : étendre le Walkthrough asynchrone à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="2e76a-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="2e76a-110">Cette section inclut les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="2e76a-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="2e76a-111">[Annuler une tâche asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="2e76a-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="2e76a-112">Annuler des tâches Asynch après une période de temps (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e76a-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="2e76a-113">Annuler les tâches Asynch restantes après une est terminée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e76a-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="2e76a-114">Démarrer plusieurs tâches Asynch et les traiter comme terminées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e76a-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="2e76a-115">Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2e76a-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="2e76a-116">Les projets de créent une interface utilisateur qui contient un bouton qui démarre le processus et un bouton qui annule, comme le montre l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="2e76a-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="2e76a-117">Les boutons sont nommés `startButton` et `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="2e76a-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="2e76a-118">![Fenêtre WPF avec un bouton Annuler](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "l’annulation")</span><span class="sxs-lookup"><span data-stu-id="2e76a-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="2e76a-119">Vous pouvez télécharger les projets Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="2e76a-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e76a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e76a-120">See Also</span></span>  
 [<span data-ttu-id="2e76a-121">Programmation asynchrone avec Async et Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e76a-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
