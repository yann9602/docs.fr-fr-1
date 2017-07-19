---
title: "How to: Implement a Producer-Consumer Dataflow Pattern | Microsoft Docs"
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
  - "TPL dataflow library, implementing producer-consumer pattern"
  - "Task Parallel Library, dataflows"
  - "producer-consumer patterns, implementing [TPL]"
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Implement a Producer-Consumer Dataflow Pattern
Ce document explique comment utiliser la bibliothèque de flux TPL pour implémenter un modèle producteur\- consommateur.  Dans ce modèle, le *producteur* envoie des messages à un bloc de messages et le *consommateur* lit les messages à partir de ce bloc.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Exemple  
 L'exemple suivant illustre un modèle de base producteur\-consommateur qui utilise le flux de données.  La méthode `Produce` écrit les tableaux qui contiennent des octets aléatoires de données sur un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=fullName> et la méthode `Consume` lit les octets depuis un objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=fullName>.  En agissant sur les interfaces <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, au lieu de leurs types dérivés, vous pouvez écrire du code réutilisable qui peut intervenir sur différents types de bloc de flux de données.  Cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>.  Étant donné que la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> agit à la fois comme un bloc de source et comme un bloc cible, le producteur et le consommateur peuvent utiliser un objet partagé pour transférer des données.  
  
 La méthode `Produce` appelle la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> dans une boucle pour écrire de manière synchrone des données sur le bloc cible.  Une fois que la méthode `Produce` ait écrit les données sur bloc cible, elle appelle la méthode <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> pour indiquer que le bloc n'aura jamais d'informations supplémentaires.  La méthode `Consume` utilise les opérateurs [async](../Topic/async%20\(C%23%20Reference\).md) et [await](../Topic/await%20\(C%23%20Reference\).md) \([Async](../Topic/Async%20\(Visual%20Basic\).md) et [await](../Topic/Await%20Operator%20\(Visual%20Basic\).md) dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) pour calculer de manière asynchrone le nombre total d'octets reçus de l'objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>.  Pour agir de manière asynchrone, la méthode `Consume` appelle la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> pour recevoir une notification lorsque le bloc source a des données disponibles ou lorsque le bloc de source n'aura jamais d'informations supplémentaires.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `DataflowProducerConsumer.cs`\(`DataflowProducerConsumer.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## Programmation fiable  
 Cet exemple utilise uniquement un consommateur pour traiter les données sources.  Si vous avez plusieurs consommateurs dans votre application, utilisez la méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pour lire des données dans le bloc source, comme le montre l'exemple suivant.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 La méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> renvoie `False` lorsqu'aucune donnée n'est disponible.  Si plusieurs consommateurs doivent accéder au bloc source simultanément, ce mécanisme garantie que les données reste disponible après l'appel à <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)