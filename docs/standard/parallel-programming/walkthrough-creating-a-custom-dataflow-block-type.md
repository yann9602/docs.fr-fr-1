---
title: "Procédure pas à pas : création d'un type de bloc de flux de données personnalisé"
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
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Procédure pas à pas : création d'un type de bloc de flux de données personnalisé
Bien que la bibliothèque de flux de données TPL fournit plusieurs types de blocs de flux de données qui permettent une gamme de fonctionnalités, vous pouvez également créer des types de blocs personnalisé. Ce document décrit comment créer un type de bloc de flux de données qui implémente un comportement personnalisé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Lecture [flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de lire ce document.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Définition du bloc de flux de données de fenêtre glissante  
 Imaginez une application de flux de données qui exige que les valeurs d’entrée est mis en mémoire tampon, puis de sortie d’une manière de fenêtre glissante. Par exemple, pour les valeurs d’entrée {0, 1, 2, 3, 4, 5} et une taille de fenêtre de trois, un bloc de flux de données de fenêtre glissante génère les tableaux de sortie {0, 1, 2}, {1, 2, 3}, {2, 3, 4,} et {3, 4, 5}. Les sections suivantes décrivent deux façons de créer un type de bloc de flux de données qui implémente ce comportement personnalisé. La première technique utilise le <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> méthode pour combiner les fonctionnalités d’un <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objet et un <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> bloc un propagateur objet. La seconde technique définit une classe qui dérive de <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> et combine les fonctionnalités existantes pour exécuter le comportement personnalisé.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>À l’aide de l’encapsuler la méthode pour définir le bloc de flux de fenêtre glissante  
 L’exemple suivant utilise la <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> méthode pour créer un bloc propagateur à partir d’une source et une cible. Un bloc propagateur permet à un bloc source et un bloc cible pour agir en tant que destinataire et expéditeur des données.  
  
 Cette technique est utile lorsque vous avez besoin des fonctionnalités de flux de données personnalisé, mais vous ne nécessitent pas de type qui fournit d’autres méthodes, propriétés ou champs.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Dérivation à partir de IPropagatorBlock pour définir le bloc de flux de données de fenêtre glissante  
 L’exemple suivant illustre la `SlidingWindowBlock` classe. Cette classe dérive <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> afin qu’il puisse agir comme une source et une cible de données. Comme dans l’exemple précédent, la `SlidingWindowBlock` classe repose sur les types de blocs de flux de données existants. Toutefois, le `SlidingWindowBlock` classe implémente également les méthodes qui sont requis par le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, et <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces. Tous les transférer ces méthodes fonctionnent pour les membres de type de bloc de flux de données prédéfinis. Par exemple, le `Post` méthode diffère le travail à la `m_target` membre de données, qui est également un <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> objet.  
  
 Cette technique est utile lorsque vous nécessitent les fonctionnalités de flux de données personnalisé et également exiger un type qui fournit d’autres méthodes, propriétés ou champs. Par exemple, le `SlidingWindowBlock` classe dérive également de <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> afin qu’il puisse fournir le <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> et <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> méthodes. Le `SlidingWindowBlock` classe illustre également d’extensibilité en fournissant le `WindowSize` propriété, qui Récupère le nombre d’éléments dans la fenêtre glissante.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Exemple complet  
 L'exemple suivant présente le code complet pour cette visite. Il montre également comment utiliser les deux blocs de fenêtre glissante dans une méthode qui écrit dans le bloc, lit à partir de celui-ci et imprime les résultats dans la console.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**  
  
## <a name="next-steps"></a>Étapes suivantes  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
