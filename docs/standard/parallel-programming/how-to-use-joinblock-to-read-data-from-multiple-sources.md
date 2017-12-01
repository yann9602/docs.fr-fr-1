---
title: "Comment : utiliser JoinBlock pour lire des données issues de plusieurs sources"
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
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41445e4874b94809840ecf9ebda6f27ccc955c9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Comment : utiliser JoinBlock pour lire des données issues de plusieurs sources
Ce document explique comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> pour effectuer une opération lorsque des données sont disponibles à partir de plusieurs sources. Il présente aussi comment utiliser le mode non gourmand pour permettre à plusieurs blocs de jointure de partager plus efficacement une source de données.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant définit trois types de ressources, `NetworkResource`, `FileResource` et `MemoryResource`, et effectue des opérations lorsque les ressources sont disponibles. Cet exemple nécessite une paire `NetworkResource` et `MemoryResource` pour effectuer la première opération et une paire `FileResource` et `MemoryResource` pour effectuer la seconde opération. Pour permettre aux opérations de se produire lorsque toutes les ressources requises sont disponibles, cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Lorsqu'un objet <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> reçoit les données de toutes les sources, il envoie ces données à la cible, qui dans cet exemple est un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> lisent à partir d'un pool partagé d'objets `MemoryResource`.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Pour permettre l'utilisation efficace du pool partagé des objets `MemoryResource`, cet exemple spécifie un objet <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> qui contient le jeu de propriétés <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> à `False` pour créer les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> qui agissent en mode non gourmand. Un bloc de jointure non-gourmand remet les messages entrants jusqu'à ce qu'il y en ait un disponible à partir de chaque source. Si n'importe quel message remis à plus tard a été reçu par un autre bloc, le bloc de jointure redémarre le processus. Le mode non gourmand permet aux blocs de jointure qui partagent un ou plusieurs blocs sources d'avancer quand les autres blocs attendent des données. Dans cet exemple, si un objet `MemoryResource` est ajouté au pool `memoryResources`, le premier bloc de jointure peut progresser pour recevoir sa deuxième source de données. Si cet exemple visait à utiliser le mode gourmand, qui est la valeur par défaut, un bloc de jointure peut prendre l'objet `MemoryResource` et attendre que la deuxième ressource soit disponible. Toutefois, si l'autre bloc de jointure a sa deuxième source de données disponible, il ne peut pas avancer car l'objet `MemoryResource` a été pris par l'autre bloc de jointure.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
 L'utilisation de jointures non gourmandes peut également vous aider à empêcher tout interblocage dans votre application. Dans une application, *blocage* se produit lorsque deux ou plusieurs processus détiennent chacun une ressource et attendent mutuellement qu’un autre processus libère une autre ressource. Examinez la requête qui définit deux objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Les deux objets lisent chacun des données de deux blocs sources partagés. En mode gourmand, si un bloc de jointure lit depuis la première source et le deuxième bloc de jointure lit depuis la seconde source, l'application peut être interbloquée car les deux blocs de jointure attendent mutuellement l'autre pour libérer sa ressource. En mode non gourmand, chaque bloc de jointure lit uniquement à partir de ses sources lorsque toutes les données sont disponibles, éliminant par conséquent, le risque d'interblocage.  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
