---
title: "Comment&#160;: utiliser des canaux anonymes pour la communication entre processus en local | Microsoft Docs"
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
  - "canaux anonymes (.NET Framework)"
  - "communication avec l'ordinateur local (.NET Framework), canaux"
  - "communication unidirectionnelle (.NET Framework)"
  - "communication parent-enfant (.NET Framework)"
  - "canaux (.NET Framework)"
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser des canaux anonymes pour la communication entre processus en local
Les canaux anonymes assurent la communication entre processus sur un ordinateur local.  Ils proposent moins de fonctionnalités que les canaux nommés, mais ils nécessitent moins de charge mémoire.  Vous pouvez utiliser des canaux anonymes pour faciliter la communication entre processus sur un ordinateur local.  Vous ne pouvez pas utiliser de canaux anonymes pour la communication sur un réseau.  
  
 Pour implémenter des canaux anonymes, utilisez les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
## Exemple  
 Une méthode permettant d'envoyer une chaîne d'un processus parent à un processus enfant à l'aide de canaux anonymes est illustrée dans l'exemple suivant.  Cet exemple crée un objet <xref:System.IO.Pipes.AnonymousPipeServerStream> dans un processus parent dont un <xref:System.IO.Pipes.PipeDirection> a la valeur <xref:System.IO.Pipes.PipeDirection>.  Le processus parent crée ensuite un processus enfant à l'aide d'un handle client en vue de générer un objet <xref:System.IO.Pipes.AnonymousPipeClientStream>.  Le processus enfant possède un <xref:System.IO.Pipes.PipeDirection> dont la valeur est <xref:System.IO.Pipes.PipeDirection>.  
  
 Le processus parent envoie ensuite une chaîne fournie par utilisateur au processus enfant.  La chaîne s'affiche sur la console dans le processus enfant.  
  
 L'exemple suivant indique le processus serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## Exemple  
 L'exemple suivant indique le processus client.  Le processus serveur démarre le processus client et donne un handle client à ce processus.  Vous devez nommer l'exécutable résultant du code client `pipeClient.exe` et le copier dans le même répertoire que l'exécutable du serveur avant d'exécuter le processus serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## Voir aussi  
 [Canaux](../../../docs/standard/io/pipe-operations.md)   
 [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)