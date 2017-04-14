---
title: "Op&#233;rations de canal dans le .NET Framework | Microsoft Docs"
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
  - "canaux (.NET Framework)"
  - "opérations de canal (.NET Framework)"
  - "communication entre processus (.NET Framework), canaux"
  - "E/S (.NET Framework), canaux"
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Op&#233;rations de canal dans le .NET Framework
Les canaux assurent la communication entre processus.  Il existe deux types de canaux :  
  
-   Les canaux anonymes  
  
     Les canaux anonymes assurent la communication entre processus sur un ordinateur local.  Les canaux anonymes nécessitent moins de charge mémoire que les canaux nommés, mais les services qu'ils proposent sont limités.  Les canaux anonymes sont unidirectionnels et ne peuvent pas être utilisés sur un réseau.  Ils ne prennent en charge qu'une seule instance de serveur.  Les canaux anonymes sont utiles dans le cadre de la communication entre threads ou entre processus parent et enfant lorsque les handles de canaux peuvent être facilement passés au processus enfant au moment de sa création.  
  
     Dans le Framework .NET, vous pouvez implémenter des canaux anonymes à l'aide des classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
     Consultez [Comment : utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Les canaux nommés  
  
     Les canaux nommés assurent la communication entre processus entre un serveur de canal et un ou plusieurs clients de canaux.  Les canaux nommés peuvent être unidirectionnels ou en duplex.  Ils prennent en charge la communication par messagerie et permettent à plusieurs clients de se connecter simultanément au processus serveur avec le même nom de canal.  Les canaux nommés prennent également en charge l'emprunt d'identité, qui permet aux processus de connexion d'utiliser leurs propres autorisations sur des serveurs distants.  
  
     Dans le Framework .NET, vous pouvez implémenter des canaux nommés à l'aide des classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
     Consultez [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## Voir aussi  
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [Comment : utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)   
 [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)