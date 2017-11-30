---
title: "Gestion des exceptions (bibliothèque parallèle de tâches)"
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
helpviewer_keywords: tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e62498376d321d8ff22a53315b9d5f18a8865056
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling-task-parallel-library"></a>Gestion des exceptions (bibliothèque parallèle de tâches)
Les exceptions non gérées levées par le code utilisateur s’exécutant à l’intérieur d’une tâche sont propagées vers le thread appelant, sauf dans certains scénarios décrits plus loin dans cette rubrique. Les exceptions sont propagées lorsque vous utilisez la méthode statique ou d’instance <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` méthodes et que vous les gérez en incluant l’appel dans un `try` / `catch` instruction. Si une tâche est le parent de tâches enfants attachées ou si vous attendez plusieurs tâches, plusieurs exceptions peuvent être levées.  
  
 Pour propager toutes les exceptions vers le thread appelant, l’infrastructure de la tâche les encapsule dans une instance <xref:System.AggregateException> . L’exception <xref:System.AggregateException> possède une propriété <xref:System.AggregateException.InnerExceptions%2A> qu’il est possible d’énumérer pour examiner toutes les exceptions d’origine levées et gérer (ou non) individuellement chacune d’elles. Vous pouvez également gérer les exceptions d’origine à l’aide de la <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> (méthode).  
  
 Même si une seule exception est levée, elle est encapsulée dans une exception <xref:System.AggregateException> , comme le montre l’exemple suivant.  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 Vous pouvez éviter une exception non gérée en interceptant l’exception <xref:System.AggregateException> et en n’observant aucune des exceptions internes. Toutefois, cela n’est pas recommandé car cela revient à intercepter le type <xref:System.Exception> de base dans des scénarios non parallèles. Intercepter une exception sans prendre de mesures spécifiques de récupération peut laisser votre programme dans un état indéterminé.  
  
 Si vous ne voulez pas appeler le <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` méthode pour attendre la fin d’une tâche, vous pouvez également récupérer la <xref:System.AggregateException> exception à partir de la tâche <xref:System.Threading.Tasks.Task.Exception%2A> propriété, comme le montre l’exemple suivant. Pour plus d’informations, consultez la section [Observation d’exceptions à l’aide de la propriété Task.Exception](#ExceptionProp) dans cette rubrique.  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 Si vous n’attendez pas une tâche qui propage une exception ou accédez à sa propriété <xref:System.Threading.Tasks.Task.Exception%2A> , l’exception est transmise d’après la stratégie de l’exception .NET lorsque la tâche est récupérée par le garbage collector.  
  
 Lorsque les exceptions sont autorisées à se propager vers le thread joint, il est possible qu’une tâche continue à traiter des éléments après que l’exception a été levée.  
  
> [!NOTE]
>  Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans ces exemples. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher **Autoriser uniquement mon code** sous **Outils, Options, Débogage, Général**.  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>Tâches enfants attachées et exceptions AggregateException imbriquées  
 Si une tâche a une tâche enfant attachée qui lève une exception, cette exception est encapsulée dans une exception <xref:System.AggregateException> avant d’être propagée vers la tâche parent, qui encapsule cette exception dans sa propre exception <xref:System.AggregateException> avant de la propager vers le thread appelant. Dans ce cas, le <xref:System.AggregateException.InnerExceptions%2A> propriété de la <xref:System.AggregateException> exception interceptée à la <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> ou <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` ou <xref:System.Threading.Tasks.Task.WaitAny%2A> ou <xref:System.Threading.Tasks.Task.WaitAll%2A> méthode contient un ou plusieurs <xref:System.AggregateException> instances, pas le exceptions d’origine ayant provoqué l’erreur. Pour éviter d’avoir à itérer imbriqués <xref:System.AggregateException> des exceptions, vous pouvez utiliser la <xref:System.AggregateException.Flatten%2A> méthode pour supprimer tous les imbriqué <xref:System.AggregateException> des exceptions, afin que le <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> propriété contient les exceptions d’origine. Dans l’exemple suivant, les instances <xref:System.AggregateException> imbriquées sont aplaties et gérées en une seule boucle.  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 Vous pouvez également utiliser le <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> méthode lever les exceptions internes de multiples à <xref:System.AggregateException> levées par plusieurs tâches dans une seule des instances <xref:System.AggregateException> instance, comme le montre l’exemple suivant.  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>Exceptions des tâches enfants détachées  
 Par défaut, les tâches enfants sont créées détachées. Les exceptions levées depuis des tâches détachées doivent être gérées ou levées à nouveau dans la tâche parent immédiate. Elles ne sont pas propagées vers le thread appelant de la même façon que les tâches enfants attachées. Le parent le plus haut peut lever à nouveau manuellement une exception à partir d’un enfant détaché pour l’encapsuler dans une exception <xref:System.AggregateException> et la propager vers le thread appelant.  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 Même si vous utilisez une continuation pour observer une exception dans une tâche enfant, l’exception doit toujours être observée par la tâche parent.  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>Exceptions indiquant une annulation coopérative  
 Lorsque le code utilisateur d’une tâche répond à une demande d’annulation, la procédure correcte consiste à lever une exception <xref:System.OperationCanceledException> qui passe le jeton d’annulation sur lequel la demande a été communiquée. Avant d’essayer de propager l’exception, l’instance de tâche compare le jeton de l’exception à celui qui lui a été passé lors de sa création. S’ils sont identiques, la tâche propage une exception <xref:System.Threading.Tasks.TaskCanceledException> encapsulée dans l’exception <xref:System.AggregateException>, et cette dernière peut être affichée au moment d’examiner les exceptions internes. Toutefois, si le thread appelant n’est pas en attente sur la tâche, cette exception spécifique n’est pas propagée. Pour plus d'informations, consultez [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>Utilisation de la méthode Handle pour filtrer les exceptions internes  
 Vous pouvez utiliser la <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> méthode pour filtrer les exceptions que vous pouvez traiter comme « gérées » sans utiliser d’autre logique. Dans le délégué utilisateur fourni à la <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> (méthode), vous pouvez examiner le type d’exception, son <xref:System.Exception.Message%2A> propriété, ou toute autre information le concernant qui vous permettra de déterminer si elle est sans gravité. Toutes les exceptions pour lesquelles le délégué retourne `false` sont levées dans une nouvelle <xref:System.AggregateException> instance immédiatement après le <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> le retour de méthode.  
  
 L’exemple suivant est fonctionnellement équivalent au premier exemple dans cette rubrique, qui examine chaque exception de la <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> collection.  Au lieu de cela, ce gestionnaire d’exceptions appelle la <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> objet de méthode pour chaque exception et les seules exceptions levées qui ne sont pas `CustomException` instances.  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 Voici un exemple plus complet qui utilise le <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> méthode pour fournir une gestion spéciale pour un <xref:System.UnauthorizedAccessException> exception lors de l’énumération des fichiers.  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Observation d’exceptions à l’aide de la propriété Task.Exception  
 Si une tâche se termine dans le <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> état, son <xref:System.Threading.Tasks.Task.Exception%2A> propriété peut être examinée pour découvrir quelle exception a provoqué l’erreur. Un bon moyen d’observer la propriété <xref:System.Threading.Tasks.Task.Exception%2A> consiste à utiliser une continuation qui s’exécute uniquement en cas d’erreur de la tâche antérieure, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 Dans une application réelle, le délégué de continuation peut consigner des informations détaillées sur l’exception et générer de nouvelles tâches pour se remettre de l’exception.  
  
## <a name="unobservedtaskexception-event"></a>Événement UnobservedTaskException  
 Dans certains scénarios, tels que l’hébergement de plug-ins non approuvés, des exceptions sans gravité sont courantes. Il peut s’avérer trop difficile de toutes les observer manuellement. Dans ce cas, vous pouvez gérer le <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> événement. Le <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> instance qui est passé à votre gestionnaire peut être utilisée pour empêcher l’exception non prise en charge soient propagées vers le thread joint.  
  
## <a name="see-also"></a>Voir aussi  
 [La bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
