---
title: "Comment&#160;: utiliser des canaux nomm&#233;s pour la communication entre processus en r&#233;seau | Microsoft Docs"
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
  - "communication en duplex intégral (.NET Framework), canaux nommés"
  - "emprunt d'identité (.NET Framework), canaux nommés"
  - "communication basée sur des messages (.NET Framework), canaux nommés"
  - "connexion multiples via des canaux nommés"
  - "canaux nommés (.NET Framework)"
  - "communications réseau (.NET Framework), canaux nommés"
  - "canaux (.NET Framework)"
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: utiliser des canaux nomm&#233;s pour la communication entre processus en r&#233;seau
Les canaux nommés assurent la communication entre processus entre un serveur de canal et un ou plusieurs clients de canaux.  Ils proposent davantage de fonctionnalités que les canaux anonymes, qui assurent la communication entre processus sur un ordinateur local.  Parmi ces fonctionnalités figurent la communication en full duplex sur un réseau et entre plusieurs instances de serveur, la communication par messagerie et l'emprunt d'identité client, qui permet aux processus de connexion d'utiliser leur propre ensemble d'autorisations sur des serveurs distants.  
  
 Pour implémenter des canaux nommés, utilisez <xref:System.IO.Pipes.NamedPipeServerStream> et les classes <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
## Exemple  
 L'exemple suivant montre comment créer un canal nommé à l'aide de la classe <xref:System.IO.Pipes.NamedPipeServerStream>.  Dans cet exemple, le processus serveur crée quatre threads.  Chaque thread peut accepter une connexion cliente.  Le processus client connecté fournit ensuite le serveur avec un nom de fichier.  Si le client possède les autorisations suffisantes, le processus serveur ouvre le fichier et renvoie son contenu au client.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## Exemple  
 L'exemple suivant indique le processus client qui utilise la classe <xref:System.IO.Pipes.NamedPipeClientStream>.  Le client se connecte au processus serveur et envoie un nom de fichier au serveur.  L'exemple utilise l'emprunt d'identité, donc l'identité qui exécute l'application cliente doit avoir l'autorisation d'accéder au fichier.  Le serveur renvoie ensuite le contenu du fichier au client.  Le contenu du fichier est alors affiché dans la console.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## Programmation fiable  
 Comme les processus client et serveur sont, dans cet exemple, censés être exécutés sur le même ordinateur, le nom du serveur fourni à l'objet <xref:System.IO.Pipes.NamedPipeClientStream> est `"."`.  Si les processus client et serveur étaient sur des ordinateurs séparés, `"."` serait alors remplacé par le nom de réseau de l'ordinateur qui exécute le processus serveur.  
  
## Voir aussi  
 <xref:System.Security.Principal.TokenImpersonationLevel>   
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>   
 [Canaux](../../../docs/standard/io/pipe-operations.md)   
 [Comment : utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)