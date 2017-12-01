---
title: "Comment : utiliser des canaux anonymes pour la communication entre processus en local"
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
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Comment : utiliser des canaux anonymes pour la communication entre processus en local
Les canaux anonymes fournissent une communication interprocessuse sur un ordinateur local. Ils offrent moins de fonctionnalités que les canaux nommés, mais également nécessitent moins de surcharge. Vous pouvez utiliser des canaux anonymes pour faciliter la communication entre processus sur un ordinateur local. Vous ne pouvez pas utiliser des canaux anonymes pour la communication sur un réseau.  
  
 Pour implémenter des canaux anonymes, utilisez le <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une façon de pour envoyer une chaîne à partir d’un processus parent à un processus enfant à l’aide de canaux anonymes. Cet exemple crée un <xref:System.IO.Pipes.AnonymousPipeServerStream> objet dans un processus parent avec un <xref:System.IO.Pipes.PipeDirection> valeur <xref:System.IO.Pipes.PipeDirection.Out>. Le processus parent crée ensuite un processus enfant à l’aide d’un handle de client pour créer un <xref:System.IO.Pipes.AnonymousPipeClientStream> objet. Le processus enfant a un <xref:System.IO.Pipes.PipeDirection> valeur <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Le processus parent envoie ensuite une chaîne fournie par l’utilisateur au processus enfant. La chaîne est affichée sur la console dans le processus enfant.  
  
 L’exemple suivant montre le processus du serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le processus client. Le processus serveur démarre le processus client ainsi que ce processus un handle de client. Le fichier exécutable obtenu à partir du code client doit être nommé `pipeClient.exe` et être copié dans le même répertoire que l’exécutable avant d’exécuter le processus du serveur du serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Voir aussi  
 [Canaux](../../../docs/standard/io/pipe-operations.md)  
 [Guide pratique pour utiliser des canaux nommés pour la communication entre processus en réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
