---
title: "Opérations de canal dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a>Opérations de canal dans le .NET Framework
Les canaux fournissent un moyen de communication entre processus. Il existe deux types de canaux :  
  
-   Canaux anonymes.  
  
     Les canaux anonymes fournissent une communication interprocessuse sur un ordinateur local. Les canaux anonymes nécessitent moins de traitement que les canaux nommés, mais ils offrent des services limités. Les canaux anonymes sont unidirectionnels et ne peut pas être utilisés sur un réseau. Ils prennent en charge uniquement une seule instance de serveur. Les canaux anonymes sont utiles pour la communication entre les threads ou entre processus parent et enfant où les handles de canaux peuvent être facilement passés au processus enfant lors de sa création.  
  
     Dans le .NET Framework, vous implémentez les canaux anonymes à l’aide de la <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.  
  
     Consultez [Comment : utiliser des canaux anonymes pour la Communication interprocessus Local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Canaux nommés.  
  
     Canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canal. Canaux nommés peuvent être unidirectionnels ou en duplex. Ils prennent en charge la communication basée sur le message et permettent à plusieurs clients à se connecter simultanément au processus serveur à l’aide du même nom de canal. Canaux nommés prennent également en charge l’emprunt d’identité, ce qui permet le processus de connexion d’utiliser leurs propres autorisations sur des serveurs distants.  
  
     Dans le .NET Framework, vous implémentez des canaux nommés à l’aide de la <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream> classes.  
  
     Consultez [Comment : utiliser des canaux nommés pour la Communication de réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)  
 [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [Guide pratique pour utiliser des canaux nommés pour la communication entre processus en réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
