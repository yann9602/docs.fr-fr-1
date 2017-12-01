---
title: "Comment : implémenter un modèle de flux de données producteur-consommateur"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Comment : implémenter un modèle de flux de données producteur-consommateur
Ce document décrit comment utiliser la bibliothèque de flux de données TPL pour implémenter un modèle producteur-consommateur. Dans ce modèle, le *producteur* envoie des messages à un bloc de message et le *consommateur* lit les messages de ce bloc.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un modèle producteur-consommateur de base qui utilise des flux de données. Le `Produce` méthode écrit des tableaux qui contiennent les octets aléatoires de données à un <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> objet et la `Consume` méthode lit les octets à partir d’un <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> objet. En agissant sur les <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, et non de leurs types dérivés, vous pouvez écrire du code réutilisable qui peut agir sur une variété de types de blocs de flux de données. Cet exemple utilise la <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> classe. Étant donné que le <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> bloquer de classe agit à la fois en tant que source et comme un bloc cible, le producteur et le consommateur peuvent utiliser un objet partagé pour transférer des données.  
  
 Le `Produce` les appels de méthode le <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> méthode dans une boucle pour écrire des données vers le bloc cible de façon synchrone. Après le `Produce` méthode écrit toutes les données dans le bloc cible, il appelle la <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> méthode pour indiquer que le bloc n’aura jamais des données supplémentaires disponibles. Le `Consume` utilise le [async](~/docs/csharp/language-reference/keywords/async.md) et [await](~/docs/csharp/language-reference/keywords/await.md) opérateurs ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) et [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) à calculer le nombre total d’octets reçus à partir de façon asynchrone le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objet. D’agir de façon asynchrone, le `Consume` les appels de méthode le <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> méthode pour recevoir une notification lorsque le bloc source comporte des données disponibles et lorsque le bloc source n’aura jamais des données supplémentaires disponibles.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
 Cet exemple utilise un seul consommateur pour traiter les données source. Si vous avez plusieurs consommateurs dans votre application, utilisez la <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> méthode pour lire des données à partir du bloc de code source, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Le <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> méthode retourne `False` lorsqu’aucune donnée n’est disponible. Lorsque le bloc source doivent accéder simultanément à plusieurs consommateurs, ce mécanisme garantit que les données sont toujours disponibles après l’appel à <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
