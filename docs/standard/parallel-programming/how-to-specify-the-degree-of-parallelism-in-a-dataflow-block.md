---
title: "Comment : spécifier le degré de parallélisme dans un bloc de flux de données"
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
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ccd64a9acbc75a30984719671af2dc7dda6922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Comment : spécifier le degré de parallélisme dans un bloc de flux de données
Ce document décrit comment définir la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> pour permettre à un bloc de flux de données d'exécution de traiter plusieurs messages à la fois. Cela est utile quand vous avez un bloc de flux de données qui effectue un calcul de longue durée et qui peut tirer parti du traitement des messages en parallèle. Cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> pour effectuer plusieurs opérations de flux de données simultanément ; toutefois, vous pouvez spécifier le degré maximum de parallélisme dans les types de bloc d'exécution prédéfinis fournis par la bibliothèque de flux de données TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue deux calculs de flux de données et affiche la durée calendaire nécessaire pour chaque calcul. Le premier calcul spécifie un degré maximum de parallélisme de 1, qui est la valeur par défaut. Un degré maximum de parallélisme égal à 1 amène le bloc de flux de données à traiter les messages en série. Le deuxième calcul ressemble à la première, à ceci près qu'il spécifie un degré maximum de parallélisme égal au nombre de processeurs disponibles. Cela permet au bloc de flux de données d'effectuer plusieurs opérations en parallèle.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
 Par défaut, chaque bloc de flux de données prédéfini propage les messages dans l'ordre dans lequel ils sont reçus.  Bien que plusieurs messages soient traités simultanément quand vous spécifiez un degré maximum de parallélisme supérieur 1, ils sont toujours propagés dans l'ordre dans lequel ils sont reçus.  
  
 Étant donné que la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> représente le degré maximal de parallélisme, le bloc de flux de données peut s'exécuter avec un degré de parallélisme moindre spécifié par vos soins. Le bloc de flux de données peut utiliser un degré de parallélisme moindre pour satisfaire ses exigences fonctionnelles ou pour prendre en compte un manque de ressources système disponibles. Un bloc de flux de données ne choisit jamais un degré de parallélisme supérieur à celui que vous spécifiez.  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
