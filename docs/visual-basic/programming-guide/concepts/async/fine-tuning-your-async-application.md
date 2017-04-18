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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d0cac2fe7305031b93a375a08e785285a291320
ms.lasthandoff: 03/13/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Réglage de votre Application Async (Visual Basic)
Vous pouvez ajouter précision et la flexibilité à vos applications asynchrones à l’aide de méthodes et propriétés qui le <xref:System.Threading.Tasks.Task>type rend disponible.</xref:System.Threading.Tasks.Task> Les rubriques de cette section montrent des exemples qui utilisent <xref:System.Threading.CancellationToken>et important `Task` méthodes telles que <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken>  
  
 À l’aide de `WhenAny` et `WhenAll`, vous pouvez plus facilement démarrer plusieurs tâches et attendre leur achèvement en une seule tâche d’analyse.  
  
-   `WhenAny`Retourne une tâche se termine lorsque toutes les tâches dans une collection sont terminée.  
  
     Pour obtenir des exemples qui utilisent `WhenAny`, consultez [annuler les tâches Asynch restantes après une est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)et [démarrer plusieurs tâches d’Async et processus les comme ils complète (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll`Retourne une tâche se termine lorsque toutes les tâches d’un regroupement sont terminées.  
  
     Pour plus d’informations et un exemple qui utilise `WhenAll`, consultez [Comment : étendre le Walkthrough asynchrone à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Cette section inclut les exemples suivants.  
  
-   [Annuler une tâche asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Annuler des tâches Asynch après une période de temps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Annuler les tâches Asynch restantes après une est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Démarrer plusieurs tâches Asynch et les traiter comme terminées (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Pour exécuter les exemples, vous devez disposer de Visual Studio 2012 ou plus récent et le .NET Framework 4.5 ou ultérieure, installé sur votre ordinateur.  
  
 Les projets de créent une interface utilisateur qui contient un bouton qui démarre le processus et un bouton qui annule, comme le montre l’image suivante. Les boutons sont nommés `startButton` et `cancelButton`.  
  
 ![Fenêtre WPF avec un bouton Annuler](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "l’annulation")  
  
 Vous pouvez télécharger les projets Windows Presentation Foundation (WPF) complète de [exemple Async : Fine réglage de votre Application](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
