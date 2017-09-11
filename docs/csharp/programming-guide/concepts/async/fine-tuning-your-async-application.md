---
title: "Réglage de votre application Async (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7afcdb28fbe10d5aa33dd2704d264ffd716af5d6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="9df63-102">Réglage de votre application Async (C#)</span><span class="sxs-lookup"><span data-stu-id="9df63-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="9df63-103">Vous pouvez ajouter de la précision et de la flexibilité à vos applications asynchrones en utilisant les méthodes et les propriétés qui sont mises à disposition par le type <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="9df63-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="9df63-104">Les rubriques de cette section présentent des exemples qui utilisent <xref:System.Threading.CancellationToken> et des méthodes `Task` importantes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="9df63-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="9df63-105">En utilisant `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en ne surveillant qu’une seule tâche.</span><span class="sxs-lookup"><span data-stu-id="9df63-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="9df63-106">`WhenAny` retourne une tâche qui se termine lorsque l’une des tâches d’une collection est terminée.</span><span class="sxs-lookup"><span data-stu-id="9df63-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="9df63-107">Pour obtenir des exemples qui utilisent `WhenAny`, consultez [Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) et [Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="9df63-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="9df63-108">`WhenAll` retourne une tâche qui se termine lorsque toutes les tâches d’une collection sont terminées.</span><span class="sxs-lookup"><span data-stu-id="9df63-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="9df63-109">Pour plus d’informations et pour obtenir un exemple qui utilise `WhenAll`, consultez [Guide pratique pour étendre la procédure pas à pas Async à l’aide de Task.WhenAll](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="9df63-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="9df63-110">Cette section comprend les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="9df63-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="9df63-111">[Annuler une tâche asynchrone ou une liste de tâches (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="9df63-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="9df63-112">Annuler des tâches asynchrones après une période spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="9df63-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="9df63-113">Annuler les tâches asynchrones restantes quand l’une d’elles est terminée (C#)</span><span class="sxs-lookup"><span data-stu-id="9df63-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="9df63-114">Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)</span><span class="sxs-lookup"><span data-stu-id="9df63-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="9df63-115">Pour exécuter les exemples, Visual Studio 2012 ou ultérieur et le .NET Framework 4.5 ou ultérieur doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9df63-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="9df63-116">Les projets créent une interface utilisateur qui contient un bouton permettant de démarrer le processus et un autre permettant de l’annuler, comme dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="9df63-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="9df63-117">Ces boutons se nomment `startButton` et `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="9df63-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="9df63-118">![Fenêtre WPF avec un bouton d'annulation](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Annulation")</span><span class="sxs-lookup"><span data-stu-id="9df63-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="9df63-119">Téléchargez l’intégralité des projets Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="9df63-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df63-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9df63-120">See Also</span></span>  
 [<span data-ttu-id="9df63-121">Programmation asynchrone avec Async et Await (C#)</span><span class="sxs-lookup"><span data-stu-id="9df63-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)

