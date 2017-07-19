---
title: "How to: Iterate File Directories with PLINQ | Microsoft Docs"
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
  - "PLINQ queries, how to iterate directories"
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Iterate File Directories with PLINQ
Cet exemple indique comment paralléliser des opérations sur des répertoires de fichiers.  La première requête utilise la méthode <xref:System.IO.Directory.GetFiles%2A> pour remplir un tableau de noms de fichiers dans un répertoire et tous les sous\-répertoires.  Cette méthode ne retourne aucun résultat avant que le tableau entier ne soit rempli, et par conséquent il peut introduire un problème de latence au début de l'opération.  Cependant, une fois que le tableau est rempli, PLINQ peut le traiter en parallèle très rapidement.  
  
 La deuxième requête utilise les méthodes statiques <xref:System.IO.Directory.EnumerateDirectories%2A> et <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> qui démarrent en retournant les résultats immédiatement.  Cette méthode peut être plus rapide lorsque vous itérez au sein d'arborescences de répertoires importantes, même si la durée de traitement comparée au premier exemple peut dépendre de nombreux facteurs.  
  
> [!WARNING]
>  Ces exemples sont destinés à montrer l'utilisation et peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente.  Pour plus d'informations sur l'accélération, consultez [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## Exemple  
 L'exemple suivant indique comment itérer au sein de répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l'arborescence, que la taille des fichiers n'est pas très volumineuse et que les temps d'accès ne sont pas significatifs.  Cette méthode implique une période de latence au début lorsque le tableau des noms de fichiers est en cours de création.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## Exemple  
 L'exemple suivant indique comment itérer au sein de répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l'arborescence, que la taille des fichiers n'est pas très volumineuse et que les temps d'accès ne sont pas significatifs.  Cette méthode commence à produire des résultats plus rapidement que dans l'exemple précédent.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Si vous utilisez <xref:System.IO.Directory.GetFiles%2A>, assurez\-vous de disposer des autorisations suffisantes sur tous les répertoires de l'arborescence.  Sinon, une exception est levée et aucun résultat n'est retourné.  Si vous utilisez <xref:System.IO.Directory.EnumerateDirectories%2A> dans une requête PLINQ, cela devient un problème de traiter les exceptions d'E\/S de manière appropriée pour vous permettre de continuer les itérations.  Si votre code doit traiter des exceptions d'E\/S ou d'accès non autorisé, considérez la méthode décrite dans [Comment : itérer les répertoires de fichiers avec la classe parallèle](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Si la latence d'E\/S est un problème, par exemple avec l'E\/S de fichier sur un réseau, envisagez d'utiliser l'une des techniques d'E\/S asynchrone décrites dans [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) et dans cette [publication de blog](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## Voir aussi  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)