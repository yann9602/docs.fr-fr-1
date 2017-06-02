---
title: "How to: Use JoinBlock to Read Data From Multiple Sources | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, joining blocks in"
  - "dataflow blocks, joining in TPL"
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Use JoinBlock to Read Data From Multiple Sources
Ce document explique comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> pour effectuer une opération lorsque des données sont disponibles à partir de plusieurs sources.  Cela montre aussi comment utiliser le mode non gourmand pour permettre à plusieurs blocs de jointure de partager une source de données plus efficacement.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Exemple  
 L'exemple suivant définit trois types de ressources, `NetworkResource`, `FileResource`, et `MemoryResource`, et effectue des opérations lorsque les ressources sont disponibles.  Cet exemple nécessite une paire `NetworkResource` et `MemoryResource` pour effectuer la première opération et une paire `FileResource` et `MemoryResource` pour effectuer la seconde opération.  Pour permettre aux opérations de se produire lorsque toutes les ressources requises sont disponibles, cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>.  Lorsqu'un objet <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> reçoit les données de toutes les sources, il envoie ces données à la cible, qui dans cet exemple est un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.  Les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> lisent d'un pool partagé d'objets `MemoryResource`.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Pour permettre l'utilisation efficace du pool partagé des objets `MemoryResource`, cet exemple spécifie un objet <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> qui contient le jeu de propriétés <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> à `False` pour créer les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> qui agissent en mode non gourmand.  Un bloc joint non\-gourmand remet les messages entrants jusqu'à ce qu'il y en est un disponible sur chaque source.  Si n'importe quel message remis plus tard a été reçu par un autre bloc, le bloc joint redémarre le processus.  Le mode non gourmand permet aux blocs joints qui partagent un ou plusieurs blocs sources d'avancer quand les autres blocs attendent des données.  Dans cet exemple, si un objet `MemoryResource` est ajouté au pool `memoryResources`, le premier bloc joint peut progresser pour recevoir sa deuxième source de données.  Si cet exemple était d'utiliser le mode gourmand, qui est la valeur par défaut, un bloc joint peut prendre l'objet `MemoryResource` et attendre que la deuxième ressource soit disponible.  Toutefois, si l'autre bloc joint a sa deuxième source de données disponible, il ne peut pas avancer car l'objet `MemoryResource` a été pris par l'autre bloc joint.  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `DataflowNonGreedyJoin.cs`\(`DataflowNonGreedyJoin.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## Programmation fiable  
 L'utilisation de jointures non gourmandes peut également vous aider à empêcher tout interblocage dans votre application.  Dans une application, l'*interblocage* se produit lorsque plusieurs processus détiennent chacun une ressource et attendent mutuellement qu'un autre processus libère une autre ressource.  Examinez la requête qui définit deux objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>.  Les deux objets lisent chacun des données de deux blocs sources partagés .  En mode gourmand, si un bloc joint lit depuis la première source et le deuxième bloc joint lit depuis la seconde source, l'application peut être interbloquée car les deux blocs joints attendent l'autre pour libérer sa ressource.  En mode non gourmand, chaque bloc joint lit depuis ses sources uniquement lorsque toutes les données sont disponibles et, par conséquent, il élimine le risque d'interblocage.  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)