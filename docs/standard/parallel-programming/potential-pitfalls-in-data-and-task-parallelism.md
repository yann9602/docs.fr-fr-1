---
title: "Potential Pitfalls in Data and Task Parallelism | Microsoft Docs"
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
  - "parallel programming, pitfalls"
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Potential Pitfalls in Data and Task Parallelism
Dans de nombreux cas, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> peuvent améliorer les performances de manière significative sur des boucles séquentielles ordinaires.  Toutefois, la mise en parallèle de la boucle présente une certaine complexité pouvant entraîner des problèmes qui, dans du code séquentiel, ne sont que peu voire jamais rencontrés.  Cette rubrique répertorie les pratiques à éviter lorsque vous écrivez des boucles parallèles.  
  
## Parallèle n'est pas forcément synonyme de rapidité  
 Dans certains cas, une boucle parallèle peut s'exécuter plus lentement que son équivalent séquentiel.  La règle empirique de base est que les boucles parallèles qui ont peu d'itérations et des délégués utilisateurs rapides sont nettement moins susceptibles de s'accélérer.  Toutefois, étant donné que de nombreux facteurs sont impliqués dans la performance, nous vous recommandons de mesurer toujours des résultats réels.  
  
## Éviter d'écrire dans les zones de mémoire partagées  
 Dans du code séquentiel, il n'est pas rare de lire ou d'écrire dans les variables statiques ou les champs de classe.  Toutefois, lorsque plusieurs threads accèdent simultanément à de telles variables, les conditions de concurrence sont favorisées.  Bien qu'il soit possible d'utiliser des verrous pour synchroniser l'accès à la variable, le coût de synchronisation peut réduire les performances.  Par conséquent, il est recommandé d'éviter, ou du moins de limiter autant que possible, l'accès à l'état partagé dans une boucle parallèle.  Pour ce faire, la meilleure méthode consiste à utiliser les surcharges de <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> qui utilisent une variable <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> pour stocker l'état thread local pendant l'exécution de la boucle.  Pour plus d’informations, consultez [How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) et [How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## Éviter la surparallélisation  
 En utilisant les boucles parallèles, vous entraînez des coûts de partitionnement de la collection source et de synchronisation des threads de travail.  Les avantages de la parallélisation sont également limités par le nombre de processeurs de l'ordinateur.  L'exécution de plusieurs threads orientés ordinateur sur un seul processeur n'accélère pas l'exécution.  Par conséquent, veillez à éviter la surparallélisation d'une boucle.  
  
 La surparallélisation se produit le plus souvent dans des boucles imbriquées.  Dans la plupart des cas, il vaut mieux paralléliser uniquement la boucle externe à moins qu'une ou plusieurs des conditions suivantes ne s'appliquent :  
  
-   La boucle interne est réputée pour être très longue.  
  
-   Vous exécutez un calcul coûteux sur chaque ordre \(l'opération affichée dans cet exemple n'est pas coûteuse\)  
  
-   Le système cible est connu pour avoir suffisamment de processeurs pour gérer le nombre de threads qui seront produits en parallélisant la requête sur `cust.Orders`.  
  
 Dans tous les cas, la meilleure méthode pour déterminer la forme de requête optimale est de la tester et la mesurer.  
  
## Éviter les appels à des méthodes non thread\-safe  
 L'écriture dans des méthodes d'instance non thread\-safe depuis une boucle parallèle peut mener à des données endommagées, susceptibles de ne pas être détectées dans votre programme.  Elle peut également provoquer des exceptions.  Dans l'exemple suivant, plusieurs threads essaient d'appeler simultanément la méthode <xref:System.IO.FileStream.WriteByte%2A?displayProperty=fullName>, qui n'est pas prise en charge par la classe.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## Limiter les appels à des méthodes thread\-safe  
 La plupart des méthodes statiques du .NET Framework sont thread\-safe et peuvent être appelées simultanément par plusieurs threads.  Toutefois, même dans ce cas\-là, la synchronisation impliquée peut mener à un ralentissement significatif de la requête.  
  
> [!NOTE]
>  Vous pouvez tester ceci vous\-même en insérant des appels à <xref:System.Console.WriteLine%2A> dans vos requêtes.  Bien que cette méthode soit utilisée à des fins de démonstration dans les exemples de documentation, ne l'utilisez pas dans les boucles parallèles sauf en cas de nécessité.  
  
## Connaître les problèmes d'affinité de thread  
 Certaines technologies, telles que l'interopérabilité COM pour les composants STA, Windows Forms et Windows Presentation Foundation \(WPF\), imposent des restrictions d'affinité de thread qui nécessitent que le code soit exécuté sur un thread spécifique.  Par exemple, un contrôle est accessible uniquement sur le thread sur lequel il a été créé dans Windows Forms et WPF.  Par exemple, cela signifie que vous ne pouvez pas mettre à jour un contrôle de liste à partir d'une boucle parallèle à moins de configurer le planificateur de thread pour qu'il planifie uniquement le travail sur le thread d'interface utilisateur.  Pour plus d'informations, consultez [How to: Schedule Work on the User Interface \(UI\) Thread](../Topic/How%20to:%20Schedule%20Work%20on%20the%20User%20Interface%20\(UI\)%20Thread.md).  
  
## Utiliser l'avertissement lors de l'attente dans les délégués appelés par Parallel.Invoke  
 Dans certaines circonstances, la bibliothèque parallèle de tâches veut inclure une tâche, ce qui signifie qu'elle s'exécute sur la tâche sur le thread en cours d'exécution. \(Pour plus d'informations, consultez [Task Schedulers](../Topic/Task%20Schedulers.md).\) Cette optimisation des performances peut mener à l'interblocage dans certains cas.  Par exemple, deux tâches peuvent exécuter le même code de délégué, qui signale lorsqu'un événement se produit, puis attend que l'autre tâche envoie un signal.  Si la seconde tâche est incluse sur le même thread que la première, et que la première passe à un état d'attente, la seconde tâche ne sera jamais en mesure de signaler son événement.  Pour éviter que cela ne se produise, vous pouvez spécifier un délai d'attente sur l'opération d'attente, ou utilisez des constructeurs de thread explicites pour aider à garantir qu'une tâche ne peut pas bloquer l'autre.  
  
## Les itérations de ForEach, For et ForAll ne s'exécutent pas forcément toujours en parallèle  
 Il est important de ne pas oublier que les itérations individuelles dans une boucle <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> peuvent s'exécuter en parallèle, mais n'ont aucune obligation de le faire.  Par conséquent, vous devez éviter d'écrire du code dont l'exactitude dépend de l'exécution parallèle d'itérations ou de l'exécution d'itérations dans un ordre particulier.  Par exemple, ce code risque l'interblocage :  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Dans cet exemple, une itération définit un événement, et toutes les autres itérations attendent l'événement.  Aucune des itérations en cours d'attente ne peut se terminer tant que l'itération définissant l'événement ne l'est pas elle\-même.  Toutefois, il est possible que les itérations en cours d'attente bloquent tous les threads utilisés pour exécuter la boucle parallèle, avant la fin de l'exécution de l'itération définissant l'événement.  Cela provoque un interblocage, autrement dit, l'itération définissant l'événement ne s'exécutera jamais et les itérations en attente ne se réveilleront jamais.  
  
 En particulier, une itération d'une boucle parallèle ne doit jamais attendre une autre itération de la boucle pour poursuivre sa progression.  Si la boucle parallèle décide de planifier les itérations séquentiellement mais dans l'ordre opposé, un interblocage se produira.  
  
## Comment éviter l'exécution de boucles parallèles sur le thread d'interface utilisateur  
 Il est important que l'interface utilisateur de votre application reste réactive.  Si une opération contient suffisamment de travail pour assurer la parallélisation, elle ne devrait probablement pas être exécutée sur le thread d'interface utilisateur.  À la place, cette opération devrait être déchargée afin d'être exécutée sur un thread d'arrière\-plan.  Par exemple, si vous souhaitez utiliser une boucle parallèle pour calculer certaines données qui doivent être restituées ensuite dans un contrôle d'interface utilisateur, exécutez la boucle dans une instance de tâche plutôt que directement dans un gestionnaire d'événements d'interface utilisateur.  Ce n'est qu'à la fin du calcul principal que vous devez remarshaler la mise à jour de l'interface utilisateur au thread d'interface utilisateur.  
  
 Si vous exécutez des boucles parallèles sur le thread d'interface utilisateur, essayez d'éviter de mettre à jour des contrôles d'interface utilisateur depuis l'intérieur de la boucle.  La tentative de mise à jour des contrôles d'interface utilisateur depuis l'intérieur d'une boucle parallèle qui exécute le thread d'interface utilisateur peut entraîner l'altération de l'état, des exceptions, des mises à jour retardées y compris des interblocages, selon la façon dont la mise à jour de l'interface utilisateur est appelée.  Dans l'exemple suivant, la boucle parallèle bloque le thread d'interface utilisateur sur lequel elle s'exécute jusqu'à ce que toutes les itérations soient terminées.  Toutefois, si une itération de la boucle s'exécute sur un thread d'arrière\-plan \(comme <xref:System.Threading.Tasks.Parallel.For%2A> peut le faire\), l'appel à Invoke entraîne l'envoi d'un message au thread d'interface utilisateur et bloque l'attente pour que ce message soit traité.  Puisque le thread d'interface utilisateur est bloqué lors de l'exécution de <xref:System.Threading.Tasks.Parallel.For%2A>, le message ne peut jamais être traité, et le thread d'interface utilisateur donne lieu à un interblocage.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 L'exemple suivant indique comment éviter l'interblocage, en exécutant la boucle à l'intérieur d'une instance de tâche.  Le thread d'interface utilisateur n'est pas bloqué par la boucle et le message peut être traité.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## Voir aussi  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Potential Pitfalls with PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)   
 [Modèles de programmation parallèle : présentation et application des modèles parallèles avec le .NET Framework 4 \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=185142)