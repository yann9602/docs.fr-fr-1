---
title: "How to: Write Messages to and Read Messages from a Dataflow Block | Microsoft Docs"
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
  - "TPL dataflow library, reading and writing messages"
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Write Messages to and Read Messages from a Dataflow Block
Ce document explique comment utiliser la bibliothèque de flux TPL pour écrire des messages sur et lire les messages d'un bloc de flux de données.  La bibliothèque de flux TPL fournit à la fois des méthodes synchrones et asynchrones lire les messages et pour écrire des messages sur un bloc de flux de données.  Ce document utilise la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=fullName>.  La classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> met en mémoire tampon des messages et fonctionne à la fois comme source du message et comme cible de message.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Écriture et lecture d'un bloc de flux de données de façon synchrone  
 L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> pour écrire sur un bloc de flux de données <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> lire à partir du même objet.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pour lire d'un bloc de flux de données, comme illustré dans l'exemple suivant.  La méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ne bloque pas le thread actuel et est utile lorsque vous interroger occasionnellement les données.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Comme la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> agit de manière synchrone, l'objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans les exemples précédents reçoit toutes les données avant que le deuxième anneau lise les données.  L'exemple suivant étend le premier exemple en utilisant <xref:System.Threading.Tasks.Parallel.Invoke%2A> pour lire et écrire sur le bloc de messages simultanément.  Comme <xref:System.Threading.Tasks.Parallel.Invoke%2A> effectue des actions simultanément, les valeurs ne sont pas écrites dans l'objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans un ordre spécifique.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## Écriture et lecture d'un bloc de flux de données de façon asynchrone  
 L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> pour l'écriture asynchrone sur un objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> pour lire de façon asynchrone depuis la même objet.  Cet exemple utilise des opérateurs [async](../Topic/async%20\(C%23%20Reference\).md) et [attendez](../Topic/await%20\(C%23%20Reference\).md) \([Async](../Topic/Async%20\(Visual%20Basic\).md) et [Attendez](../Topic/Await%20Operator%20\(Visual%20Basic\).md) en Visual Basic\) pour envoyer façon asynchrone des données et pour lire des données dans le bloc cible.  La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> est utile lorsque vous devez autoriser un bloc de flux de données à transmettre des messages ultérieurs.  La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> est utile lorsque vous souhaitez traiter des données lorsque ces données deviennent disponibles.  Pour plus d'informations sur la façon dont la propagation des messages entre le message se bloque, consultez la section Transmission des Messages dans [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## Un exemple complet  
 L'exemple suivant présente le code complet pour ce document.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `DataflowReadWrite.cs` \(`DataflowReadWrite.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## Étapes suivantes  
 Cet exemple montre comment lire et écrire directement sur un bloc de messages.  Vous pouvez aussi connecter des blocs de flux de données pour former des *pipelines*, qui sont des séquences linéaires de blocs de flux de données, ou *les réseaux*, qui sont des graphiques des blocs de flux de données.  Dans un pipeline ou un réseau, les sources propagent de façon asynchrone des données aux cibles comme ces données deviennent disponibles.  Pour obtenir un exemple qui crée un pipeline de flux de données, consultez [Walkthrough: Creating a Dataflow Pipeline](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md).  Pour obtenir un exemple qui crée un réseau plus complexe de flux de données, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)