---
title: "Comment : utiliser des canaux nommés pour la communication entre processus en réseau"
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
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 952600e71311184c4a4f906734addbf335d0358a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Comment : utiliser des canaux nommés pour la communication entre processus en réseau
Canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canal. Ils offrent plus de fonctionnalités que les canaux anonymes, qui fournissent la communication entre processus sur un ordinateur local. Canaux nommés prennent en charge la communication en duplex intégral sur un réseau et plusieurs instances de serveur, communication basée sur le message et emprunt d’identité du client, ce qui permet le processus de connexion d’utiliser leur propre jeu d’autorisations sur des serveurs distants.  
  
 Pour implémenter des canaux nommés, utilisez le <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream> classes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un canal nommé à l’aide de la <xref:System.IO.Pipes.NamedPipeServerStream> classe. Dans cet exemple, le processus serveur crée quatre threads. Chaque thread peut accepter une connexion cliente. Le processus client connecté fournit ensuite le serveur avec un nom de fichier. Si le client dispose des autorisations suffisantes, le processus serveur ouvre le fichier et renvoie son contenu au client.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre le processus client qui utilise le <xref:System.IO.Pipes.NamedPipeClientStream> classe. Le client se connecte au processus serveur et envoie un nom de fichier sur le serveur. L’exemple utilise l’emprunt d’identité, l’identité de l’application cliente est en cours d’exécution doit avoir l’autorisation d’accès au fichier. Le serveur envoie ensuite le contenu du fichier vers le client. Le contenu du fichier est ensuite affiché sur la console.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les processus client et serveur dans cet exemple sont censés être exécutés sur le même ordinateur, le nom du serveur fourni à la <xref:System.IO.Pipes.NamedPipeClientStream> objet est `"."`. Si les processus client et serveur étaient sur des ordinateurs distincts, `"."` aurait été remplacé par le nom réseau de l’ordinateur qui exécute le processus serveur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [Canaux](../../../docs/standard/io/pipe-operations.md)  
 [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
