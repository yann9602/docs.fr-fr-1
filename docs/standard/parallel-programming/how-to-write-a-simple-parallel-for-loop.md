---
title: "How to: Write a Simple Parallel.For Loop | Microsoft Docs"
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
  - "Parallel.For, How to Write"
  - "for loop, parallel construction in .NET"
  - "parallel for loops, how to use"
ms.assetid: 9029ba7f-a9d1-4526-8c84-c88716dba5d4
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# How to: Write a Simple Parallel.For Loop
Cette rubrique contient deux exemples qui illustrent la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>.  Le premier utilise la surcharge de méthode <xref:System.Threading.Tasks.Parallel.For%28System.Int64%2CSystem.Int64%2CSystem.Action%7BSystem.Int64%7D%29?displayProperty=fullName> et le second utilise la surcharge <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Action%7BSystem.Int32%7D%29?displayProperty=fullName>, les deux surcharges les plus simples de la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>.  Vous pouvez utiliser ces deux surcharges de la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> quand vous n'avez pas besoin d'annuler la boucle, de sortir des itérations de boucle ou de maintenir un état de thread local.  
  
> [!NOTE]
>  Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches.  Si les expressions lambda en C\# ou Visual Basic ne vous sont pas familières, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Le premier exemple calcule la taille des fichiers dans un répertoire unique.  Le deuxième calcule le produit de deux matrices.  
  
## Exemple  
 Cet exemple est un utilitaire en ligne de commande simple qui calcule la taille totale des fichiers d'un répertoire.  Il attend un chemin d'accès de répertoire unique en tant qu'argument et indique le nombre et la taille totale des fichiers contenus dans ce répertoire.  Après avoir vérifié que le répertoire existe, il utilise la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> pour énumérer les fichiers dans le répertoire et déterminer leur taille.  Chaque taille de fichier est ensuite ajoutée à la variable `totalSize`.  Notez que l'addition est effectuée en appelant la méthode <xref:System.Threading.Interlocked.Add%2A?displayProperty=fullName>, pour être exécutée comme une opération atomique.  Dans le cas contraire, plusieurs tâches pourraient essayer de mettre à jour la variable `totalSize` simultanément.  
  
 [!code-csharp[Conceptual.Parallel.For#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.parallel.for/cs/for1.cs#1)]
 [!code-vb[Conceptual.Parallel.For#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.parallel.for/vb/for1.vb#1)]  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> pour calculer le produit de deux matrices.  Il montre également comment utiliser la classe <xref:System.Diagnostics.Stopwatch?displayProperty=fullName> pour comparer les performances d'une boucle parallèle avec une boucle non parallèle.  Étant donné qu'il peut générer un important volume de sortie, l'exemple permet de rediriger la sortie vers un fichier.  
  
 [!code-csharp[TPL_Parallel#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleparallelfor.cs#01)]
 [!code-vb[TPL_Parallel#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleparallelfor.vb#01)]  
  
 Lors de la parallélisation du code, y compris des boucles, un objectif important consiste à utiliser les processeurs le plus possible sans surparalléliser jusqu'au point où la surcharge de traitement en parallèle réduit les performances.  Dans cet exemple, seule la boucle externe est parallélisée, car peu de travail est effectué dans la boucle interne.  La combinaison d'une petite quantité de travail et des effets indésirables du cache peut entraîner une dégradation des performances dans les boucles parallèles imbriquées.  Par conséquent, paralléliser uniquement la boucle externe est la meilleure façon d'optimiser les avantages offerts par l'accès concurrentiel sur la plupart des systèmes.  
  
## Délégué  
 Le troisième paramètre de cette surcharge de <xref:System.Threading.Tasks.Parallel.For%2A> est un délégué de type `Action<int>` en C\# ou `Action(Of Integer)` en Visual Basic.  Un délégué `Action`, qu'il possède zéro, un ou seize paramètres de type, retourne toujours void.  En Visual Basic, le comportement d'une `Action` est défini avec un `Sub`.  L'exemple utilise une expression lambda pour créer le délégué, mais vous pouvez le créer d'autres façons.  Pour plus d'informations, consultez [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## Valeur d'itération  
 Le délégué accepte un seul paramètre d'entrée dont la valeur est l'itération actuelle.  Cette valeur d'itération est fournie par le runtime et sa valeur de départ est l'index du premier élément du segment \(partition\) de la source qui est en cours de traitement sur le thread actuel.  
  
 Si vous souhaitez contrôler plus étroitement le niveau d'accès concurrentiel, utilisez l'une des surcharges qui acceptent un paramètre d'entrée <xref:System.Threading.Tasks.ParallelOptions?displayProperty=fullName>, telles que : <xref:System.Threading.Tasks.Parallel.For%28System.Int32%2CSystem.Int32%2CSystem.Threading.Tasks.ParallelOptions%2CSystem.Action%7BSystem.Int32%2CSystem.Threading.Tasks.ParallelLoopState%7D%29?displayProperty=fullName>.  
  
## Valeur de retour et gestion des exceptions  
 <xref:System.Threading.Tasks.Parallel.For%2A> retourne un objet <xref:System.Threading.Tasks.ParallelLoopResult?displayProperty=fullName> quand tous les threads sont terminés.  Cette valeur de retour est utile quand vous arrêtez ou rompez l'itération de boucle manuellement, car le <xref:System.Threading.Tasks.ParallelLoopResult> stocke des informations telles que la dernière itération qui s'est achevée.  Si une ou plusieurs exceptions se produisent sur l'un des threads, une <xref:System.AggregateException?displayProperty=fullName> est levée.  
  
 Dans le code de cet exemple, la valeur de retour de <xref:System.Threading.Tasks.Parallel.For%2A> n'est pas utilisée.  
  
## Analyse et performances  
 Vous pouvez utiliser l'Assistant Performance pour afficher l'utilisation du processeur sur votre ordinateur.  À des fins de test, augmentez le nombre de colonnes et de lignes des matrices.  Plus les matrices sont grandes, plus la différence de performances est élevée entre les versions parallèles et séquentielles du calcul.  Quand la matrice est petite, la version séquentielle s'exécute plus rapidement en raison de la surcharge liée au paramétrage de la boucle parallèle.  
  
 Les appels synchrones aux ressources partagées, telles que la console ou le système de fichiers, entraînent une dégradation sensible des performances d'une boucle parallèle.  Quand vous mesurez les performances, essayez d'éviter les appels tels que <xref:System.Console.WriteLine%2A?displayProperty=fullName> dans la boucle.  
  
## Compilation du code  
  
-   Coupez et collez ce code dans un projet Visual Studio 2010.  
  
## Voir aussi  
 <xref:System.Threading.Tasks.Parallel.For%2A>   
 <xref:System.Threading.Tasks.Parallel.ForEach%2A>   
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)