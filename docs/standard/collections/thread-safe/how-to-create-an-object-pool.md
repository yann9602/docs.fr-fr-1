---
title: "Comment&#160;: cr&#233;er un pool d&#39;objets &#224; l&#39;aide d&#39;un ConcurrentBag | Microsoft Docs"
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
  - "pool d’objets, dans .NET Framework"
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# Comment&#160;: cr&#233;er un pool d&#39;objets &#224; l&#39;aide d&#39;un ConcurrentBag
Cet exemple indique comment utiliser un conteneur simultané pour implémenter un pool d'objet.  Les pools d'objet peuvent améliorer les performances de l'application dans les situations où vous devez avoir plusieurs instances d'une classe et où la création ou la destruction de la classe est coûteuse.  Lorsqu'un programme client demande un nouvel objet, le pool d'objet tente d'abord d'en fournir un qui a été créé et retourné au pool.  Si aucun n'est disponible, et uniquement dans ce cas, un nouvel objet est créé.  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> est utilisé pour stocker les objets parce qu'il prend en charge l'insertion et la suppression rapides, en particulier lorsque le même thread ajoute et supprime des éléments.  Cet exemple peut être encore augmenté pour être généré autour d'un <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que la structure de données de conteneur implémente, à l'instar de <xref:System.Collections.Concurrent.ConcurrentQueue%601> et de <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
## Exemple  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## Voir aussi  
 [Collections thread\-safe](../../../../docs/standard/collections/thread-safe/index.md)