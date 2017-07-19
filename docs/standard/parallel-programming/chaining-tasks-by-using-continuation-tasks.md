---
title: "Chaining Tasks by Using Continuation Tasks | Microsoft Docs"
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
  - "tasks, continuations"
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
caps.latest.revision: 30
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 30
---
# Chaining Tasks by Using Continuation Tasks
En programmation asynchrone, il est très courant pour une opération asynchrone, une fois terminée, d'appeler une deuxième opération et de lui passer des données. Habituellement, cela se fait à l'aide des méthodes de rappel. Dans la bibliothèque parallèle de tâches, les mêmes fonctionnalités sont fournies par les *tâches de continuation*. Une tâche de continuation \(également appelée continuation\) est une tâche asynchrone appelée par une autre tâche, appelée *antécédent*, quand ce dernier est terminé.  
  
 Les continuations sont relativement faciles à utiliser, mais sont néanmoins très puissantes et souples. Par exemple, vous pouvez :  
  
-   passer des données de l'antécédent à la continuation ;  
  
-   spécifier les conditions précises sous lesquelles la continuation doit être ou non appelée ;  
  
-   annuler une continuation avant qu'elle ne soit lancée ou pendant son exécution de manière coopérative ;  
  
-   fournir des conseils sur la manière de planifier la continuation ;  
  
-   appeler plusieurs continuations depuis le même antécédent ;  
  
-   appeler une continuation quand certains ou tous les antécédents se terminent ;  
  
-   chaîner des continuations les unes à la suite des autres à une longueur arbitraire ;  
  
-   utiliser une continuation pour gérer des exceptions levées par l'antécédent.  
  
## À propos des continuations  
 Une continuation est une tâche qui est créée dans l'état <xref:System.Threading.Tasks.TaskStatus>. Elle est automatiquement activée à la fin de la tâche ou des tâches de son antécédent. Appeler <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=fullName> sur une continuation dans le code utilisateur lève une exception <xref:System.InvalidOperationException?displayProperty=fullName>.  
  
 Une continuation est un <xref:System.Threading.Tasks.Task> et ne bloque pas le thread sur lequel elle a démarré. Appelez la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> pour bloquer jusqu'à ce que la tâche de continuation se termine.  
  
## Création d'une continuation pour un seul antécédent  
 Vous créez une continuation qui s'exécute quand son antécédent est terminé en appelant la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName>. L'exemple suivant montre le modèle de base \(pour plus de clarté, la gestion des exceptions a été omise\). Il exécute une tâche d'antécédent, `taskA`, qui retourne un objet <xref:System.DayOfWeek> indiquant le jour actuel de la semaine. Quand l'antécédent termine, la tâche de continuation, `taskB`, le récupère et affiche une chaîne qui comprend son résultat.  
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## Création d'une continuation pour plusieurs antécédents  
 Vous pouvez également créer une continuation qui s'exécute quand tout ou partie d'un groupe de tâches est terminé. Pour exécuter une continuation quand toutes les tâches d'antécédent sont terminées, vous appelez la méthode statique <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> \(`Shared` en Visual Basic\) ou la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=fullName> d'instance. Pour exécuter une continuation quand n'importe quelle tâche d'antécédent est terminée, vous appelez la méthode statique <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> \(`Shared` en Visual Basic\) ou la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=fullName> d'instance.  
  
 Notez que les appels aux surcharges <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> ne bloquent pas le thread appelant.  Cependant, vous appelez généralement toutes les méthodes, sauf <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName> et [Task.WhenAll\(Task\<xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=fullName>, pour extraire la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> retournée, ce qui bloque le thread appelant.  
  
 L'exemple suivant appelle la méthode <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName> pour créer une tâche de continuation qui reflète les résultats de ses dix tâches d'antécédent. Chaque tâche d'antécédent élève au carré une valeur d'index allant de 1 à 10. Si les antécédents se terminent correctement \(leur propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> vaut <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>\), la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> de la continuation est un tableau de valeurs <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> retournées par chaque antécédent. L'exemple les ajoute pour calculer la somme des carrés de tous les nombres compris entre 1 et 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## Options de continuation  
 Quand vous créez une continuation de tâche unique, vous pouvez utiliser une surcharge <xref:System.Threading.Tasks.Task.ContinueWith%2A> qui prend une valeur d'énumération <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> pour spécifier les conditions sous lesquelles la continuation doit se lancer. Par exemple, vous pouvez spécifier que la continuation doit être exécutée uniquement si l'antécédent se termine correctement ou uniquement s'il se termine avec un état d'erreur. Si cette condition n'est pas remplie quand l'antécédent est prêt à appeler la continuation, la continuation passe directement à l'état <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> et ne peut plus être lancée.  
  
 Plusieurs méthodes de continuation multitâche, telles que les surcharges de la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=fullName>, incluent également un paramètre <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName>. Seul un sous\-ensemble des membres de l'énumération <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> est valide, toutefois. Vous pouvez spécifier des valeurs <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> qui ont des équivalents dans l'énumération <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName>, telles que <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName>, <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> et <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName>. Si vous spécifiez n'importe laquelle des options `NotOn` ou `OnlyOn` avec une continuation multitâche, une exception <xref:System.ArgumentOutOfRangeException> est levée au moment de l'exécution.  
  
 Pour plus d'informations sur les options de continuation de tâche, consultez la rubrique <xref:System.Threading.Tasks.TaskContinuationOptions>.  
  
## Passage de données à une continuation  
 La méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName> passe une référence à l'antécédent au délégué d'utilisateur de la continuation en tant qu'argument. Si l'antécédent est un objet <xref:System.Threading.Tasks.Task%601?displayProperty=fullName> et que la tâche s'est exécutée normalement jusqu'à son terme, la continuation peut accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> de la tâche.  
  
 La propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> se bloque jusqu'à ce que la tâche soit terminée. Toutefois, si la tâche a été annulée ou a rencontré une erreur, toute tentative d'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> lève une exception <xref:System.AggregateException>. Vous pouvez éviter ce problème à l'aide de l'option <xref:System.Threading.Tasks.TaskContinuationOptions>, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Si vous voulez que la continuation s'exécute même si l'exécution de l'antécédent n'est pas correctement terminée, vous devez vous attendre à des exceptions. Une approche consiste à tester la propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> de l'antécédent et à n'essayer d'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> que si l'état n'est pas <xref:System.Threading.Tasks.TaskStatus> ou <xref:System.Threading.Tasks.TaskStatus>. Vous pouvez également examiner la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent. Pour plus d'informations, consultez [Gestion des exceptions](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md). L'exemple suivant modifie l'exemple précédent de manière à n'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=fullName> de l'antécédent que si son état est <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## Annulation d'une continuation  
 La propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> d'une continuation est définie sur <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> dans les situations suivantes :  
  
-   Elle lève une exception <xref:System.OperationCanceledException> en réponse à une demande d'annulation. Comme pour toute tâche, si l'exception contient le même jeton qui a été passé à la continuation, il est traité comme un accusé de réception de l'annulation coopérative.  
  
-   La continuation récupère un <xref:System.Threading.CancellationToken?displayProperty=fullName> dont la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> a pour valeur `true`. Dans ce cas, la continuation ne démarre pas, et elle passe à l'état <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
-   La continuation ne s'exécute jamais, car la condition définie par son argument <xref:System.Threading.Tasks.TaskContinuationOptions> n'a pas été remplie. Par exemple, si un antécédent passe à l'état <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>, sa continuation qui a reçu l'option <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> ne s'exécute pas, mais passe à l'état <xref:System.Threading.Tasks.TaskStatus>.  
  
 Si une tâche et sa continuation représentent deux parties de la même opération logique, vous pouvez passer le même jeton d'annulation aux deux tâches, comme illustré dans l'exemple suivant. Ce dernier comprend un antécédent qui génère une liste d'entiers divisibles par 33, transmise ensuite à la continuation. À son tour, la continuation affiche la liste. L'antécédent et la continuation marquent régulièrement des pauses de durée aléatoire. En outre, un objet <xref:System.Threading.Timer?displayProperty=fullName> est utilisé pour exécuter la méthode `Elapsed` après un délai de cinq secondes. Celle\-ci appelle la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>, ce qui amène la tâche en cours d'exécution à appeler la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=fullName>. La durée des pauses générées de manière aléatoire détermine si la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> est appelée pendant l'exécution de l'antécédent ou de sa continuation. Si l'antécédent est annulé, la continuation ne démarre pas. Si l'antécédent n'est pas annulé, le jeton peut toujours être utilisé pour annuler la continuation.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Vous pouvez également empêcher une continuation de s'exécuter si son antécédent est annulé en spécifiant l'option <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName> quand vous créez la continuation, ce qui vous évite de lui fournir un jeton d'annulation. Voici un exemple simple.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Une fois la continuation à l'état <xref:System.Threading.Tasks.TaskStatus>, elle peut affecter les continuations suivantes, selon les <xref:System.Threading.Tasks.TaskContinuationOptions> spécifiés pour ces continuations.  
  
 Les continuations supprimées ne seront pas lancées.  
  
## Continuations et tâches enfants  
 Une continuation ne s'exécute pas tant que l'antécédent et toutes ses tâches enfants attachées ne sont pas terminés. La continuation n'attend pas la fin des tâches enfants détachées. Les deux exemples suivants illustrent des tâches enfants attachées à un antécédent qui crée une continuation, et détachées de celui\-ci. Dans l'exemple suivant, la continuation ne s'exécute qu'une fois toutes les tâches enfants terminées. L'exécution de l'exemple à plusieurs reprise génère systématiquement la même sortie. Notez que l'exemple lance l'antécédent en appelant la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=fullName>, car par défaut la méthode <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=fullName> crée une tâche parente dont l'option de création de tâche par défaut est <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Toutefois, si des tâches enfants sont détachées de l'antécédent, la continuation s'exécute dès que l'antécédent a terminé, indépendamment de l'état des tâches enfants. Ainsi, différentes exécutions de l'exemple suivant peuvent générer différentes sorties en fonction de la façon dont le Planificateur de tâches a géré chaque tâche enfant.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 L'état final de la tâche d'antécédent dépend de l'état final des tâches enfants attachées. L'état des tâches enfants détachées n'affecte pas le parent. Pour plus d'informations, consultez [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## Association d'un état à une continuation  
 Vous pouvez associer un état arbitraire à une continuation de tâche. La méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A> fournit des versions surchargées prenant chacune une valeur <xref:System.Object> qui représente l'état de la continuation. Vous pouvez ensuite accéder à cet objet d'état à l'aide de la propriété <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName>. Cet objet d'état est `null` si vous ne fournissez pas de valeur.  
  
 L'état de continuation est utile quand vous convertissez du code existant qui recourt au [modèle de programmation asynchrone \(APM\)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pour utiliser la bibliothèque parallèle de tâches. Dans l'APM, vous fournissez généralement l'état de l'objet dans la méthode **Begin*Method***, puis vous accédez à l'état à l'aide de la propriété <xref:System.IAsyncResult.AsyncState%2A?displayProperty=fullName>. À l'aide de la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A>, vous pouvez conserver cet état quand vous convertissez du code qui recourt à l'APM pour utiliser la bibliothèque parallèle de tâches.  
  
 L'état de continuation peut également être utile si vous employez des objets <xref:System.Threading.Tasks.Task> dans le débogueur [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Par exemple, dans la fenêtre **Tâches parallèles**, la colonne **Tâche** affiche la représentation sous forme de chaîne de l'objet d'état pour chaque tâche. Pour plus d’informations sur la fenêtre **Tâches parallèles**, consultez [Utilisation de la fenêtre Tâches](../Topic/Using%20the%20Tasks%20Window.md).  
  
 L'exemple suivant montre comment utiliser l'état de continuation. Il crée une chaîne de tâches de continuation. Chaque tâche fournit l'heure actuelle, sous la forme d'un objet <xref:System.DateTime>, pour le paramètre `state` de la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A>. Chaque objet <xref:System.DateTime> représente l'heure de création de la tâche de continuation. Chaque tâche génère un deuxième objet <xref:System.DateTime> qui représente l'heure à laquelle la tâche se termine. Une fois toutes les tâches terminées, cet exemple affiche les heures de création et de fin de chaque tâche de continuation.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## Gestion d'exceptions levées par des continuations  
 Une relation antécédent\-continuation n'est pas une relation parent\-enfant. Les exceptions levées par les continuations ne sont pas propagées à l'antécédent. Vous pouvez ainsi gérer les exceptions levées par les continuations de la même manière qu'avec une autre tâche, comme suit :  
  
-   Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, ou <xref:System.Threading.Tasks.Task.WaitAny%2A>, ou son équivalent générique, pour attendre la continuation. Vous pouvez attendre un antécédent et ses continuations dans la même instruction `try`, comme indiqué dans l'exemple suivant.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
-   Vous pouvez utiliser une deuxième continuation pour observer la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de la première continuation. Dans l'exemple suivant, une tâche tente de lire un fichier inexistant. La continuation affiche ensuite des informations sur l'exception dans la tâche d'antécédent.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ayant été lancée avec l'option <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName>, la continuation ne s'exécute que si une exception se produit dans l'antécédent et peut donc supposer que la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent n'a pas pour valeur `null`. Si la continuation s'exécute indépendamment du fait qu'une exception soit levée ou non dans l'antécédent, elle doit vérifier si la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent n'est pas définie sur `null` avant de gérer l'exception, comme le montre le fragment de code suivant.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Pour plus d’informations, consultez [Gestion des exceptions](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) et [NIB: How to: Handle Exceptions Thrown by Tasks](http://msdn.microsoft.com/fr-fr/d6c47ec8-9de9-4880-beb3-ff19ae51565d).  
  
-   Si la continuation est une tâche enfant attachée qui a été créée à l'aide de l'option <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=fullName>, ses exceptions sont de nouveau propagées par le parent au thread appelant, comme dans le cas de tout autre enfant attaché. Pour plus d'informations, consultez [Attached and Detached Child Tasks](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).  
  
## Voir aussi  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)