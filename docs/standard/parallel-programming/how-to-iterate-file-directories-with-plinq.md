---
title: "Comment : itérer les répertoires de fichiers avec PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Comment : itérer les répertoires de fichiers avec PLINQ
Cet exemple montre comment paralléliser des opérations sur les répertoires de fichiers. La première requête utilise le <xref:System.IO.Directory.GetFiles%2A> méthode pour remplir un tableau de noms de fichiers dans un répertoire et tous les sous-répertoires. Cette méthode ne retourne pas jusqu'à ce que l’intégralité du tableau est rempli, et par conséquent il peut introduire une latence au début de l’opération. Toutefois, une fois que le tableau est rempli, PLINQ peut le traiter en parallèle très rapidement.  
  
 La seconde requête utilise la méthode statique <xref:System.IO.Directory.EnumerateDirectories%2A> et <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> les méthodes qui commencent à retourner des résultats immédiatement. Cette approche peut être plus rapide lorsque vous itérez au sein des arborescences de répertoires importantes, bien que le temps de traitement par rapport au premier exemple peut dépendre de nombreux facteurs.  
  
> [!WARNING]
>  Ces exemples sont destinés à illustrer l’utilisation et peut ne pas fonctionner plus rapidement que la LINQ séquentiel équivalentes à interroger des objets. Pour plus d’informations sur l’accélération, consultez [fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer les répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires dans l’arborescence, les tailles de fichiers ne sont pas très volumineux et les temps d’accès ne sont pas significatifs. Cette approche implique une période de latence au début, tandis que le tableau de noms de fichiers est en cours de construction.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer les répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires dans l’arborescence, les tailles de fichiers ne sont pas très volumineux et les temps d’accès ne sont pas significatifs. Cette méthode commence à produire des résultats plus rapidement que l’exemple précédent.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Lorsque vous utilisez <xref:System.IO.Directory.GetFiles%2A>, assurez-vous que vous disposez des autorisations suffisantes sur tous les répertoires dans l’arborescence. Sinon, une exception est levée et aucun résultat. Lorsque vous utilisez la <xref:System.IO.Directory.EnumerateDirectories%2A> dans une requête PLINQ, il est problématique pour gérer les exceptions de d’e/s de façon normale qui vous permet de poursuivre l’itération. Si votre code doit gérer les e/s ou des exceptions d’accès non autorisé, vous devez envisager l’approche décrite dans [Comment : itérer les répertoires de fichiers avec la classe Parallel](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Si la latence d’e/s est un problème, par exemple d’e/s de fichier sur un réseau, envisagez d’utiliser une des techniques d’e/s asynchrones décrites dans [bibliothèque parallèle de tâches et le Framework programmation asynchrone .NET traditionnelle](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) et dans ce [billet de blog ](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## <a name="see-also"></a>Voir aussi  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
