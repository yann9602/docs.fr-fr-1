---
title: "Walkthrough: Creating a Custom Dataflow Block Type | Microsoft Docs"
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
  - "TPL dataflow library, creating custom dataflow blocks"
  - "dataflow blocks, creating custom in TPL"
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Creating a Custom Dataflow Block Type
Bien que la bibliothèque TPL de flux fournisse plusieurs types de bloc de flux de données qui permettent à un grand nombre de fonctionnalités, également, créez des types personnalisés de blocs.  Ce document décrit comment créer un type de bloc de flux de données qui implémente un comportement personnalisé.  
  
## Composants requis  
 Lisez [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de lire ce document.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Définition du bloc de flux de données de fenêtre glissante  
 Examinez une application de flux de données qui requiert que les valeurs d'entrée soient mises en mémoires tampon puis sorties d'une manière à fenêtre glissante.  Par exemple, pour les valeurs d'entrée {0, 1, 2, 3, 4, 5} et une taille de la fenêtre de trois, un bloc de flux de données de fenêtre glissante produit des tables de sorties {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, et {3, 4, 5}.  Les sections suivantes décrivent deux méthodes pour créer un type de bloc de flux de données qui implémente ce comportement personnalisé.  La première technique utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pour combiner les fonctionnalités d'un objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et d'un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> dans un bloc propagateur.  La deuxième technique définit une classe qui dérive de <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> et combine les fonctionnalités existantes pour exécuter le comportement personnalisé.  
  
## Utilisation de la méthode d'encapsulation pour définir le bloc de flux de données de fenêtre glissante  
 L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pour créer un bloc propagateur d'une cible et d'une source.  Un bloc propagateur permet à un bloc source et à un bloc cible de servir de récepteur et d'expéditeur des données.  
  
 Cette technique est utile lorsque vous avez besoin des fonctionnalités personnalisées de flux de données, mais vous n'avez pas besoin de type qui fournit des méthodes, des propriétés, ou des champs supplémentaires.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## Dérivation d'IPropagatorBlock pour définir le bloc de flux de données de fenêtre glissante  
 L'exemple suivant présente la classe `SlidingWindowBlock`.  Cette classe provient <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> afin qu'il puisse servir à la fois de source et cible de données.  Comme dans l'exemple précédent, la classe `SlidingWindowBlock` repose sur les types existants du bloc de flux de données.  Toutefois, la classe `SlidingWindowBlock` applique également les méthodes requises par les interfaces <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, et <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>.  Toutes ces méthodes transfèrent toutes du travail aux membres de type de bloc de flux de données prédéfini.  Par exemple, la méthode `Post` diffère le travail au membre de données `m_target`, qui est également un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Cette technique est utile lorsque vous avez besoin des fonctionnalités personnalisées de flux de données, et aussi avez besoin d'un type qui fournit des méthodes, des propriétés, ou des champs supplémentaires.  Par exemple, la classe `SlidingWindowBlock` dérive également de <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> pour qu'elle puisse fournir des méthodes <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> et <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>.  La classe `SlidingWindowBlock` illustre également l'extensibilité en spécifiant la propriété `WindowSize`, qui récupère le nombre d'éléments dans la fenêtre glissante.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## Exemple complet  
 L'exemple suivant présente le code complet pour cette visite  Elle montre également comment utiliser les blocs de fenêtre glissante avec une méthode qui écrit dans le bloc, qui le lit, et affiche les résultats dans la console.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `SlidingWindowBlock.cs`\(`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) et exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## Étapes suivantes  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)