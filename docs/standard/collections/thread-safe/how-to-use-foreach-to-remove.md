---
title: "Comment&#160;: utiliser la boucle ForEach pour supprimer les &#233;l&#233;ments d&#39;un BlockingCollection | Microsoft Docs"
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
  - "collections thread-safe, comment énumérer une collection de blocage"
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: utiliser la boucle ForEach pour supprimer les &#233;l&#233;ments d&#39;un BlockingCollection
Outre l'extraction d'éléments à partir d'une <xref:System.Collections.Concurrent.BlockingCollection%601> à l'aide des méthodes <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, vous pouvez également utiliser une instruction [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) \([For Each](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md) en Visual Basic\) pour supprimer des éléments jusqu'à ce que l'ajout soit terminé et la collection vide.  Cela s'appelle une *énumération de mutation* ou *énumération de consommation* car, contrairement à une boucle `foreach``For Each`\) typique, cet énumérateur modifie la collection source en supprimant ses éléments.  
  
## Exemple  
 L'exemple suivant indique comment supprimer tous les éléments d'une <xref:System.Collections.Concurrent.BlockingCollection%601> à l'aide d'une boucle `foreach``For Each`\).  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Cet exemple utilise une boucle `foreach` avec la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> dans le thread consommateur, ce qui provoque la suppression de chaque élément de la collection pendant son énumération.  <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> limite le nombre maximal d'éléments présents dans la collection à tout moment.  Cette façon d'énumérer la collection bloque le thread consommateur si aucun élément n'est disponible ou si la collection est vide.  Dans cet exemple, le blocage n'est pas un problème car le thread producteur ajoute des éléments plus vite qu'ils peuvent être consommés.  
  
 Il n'y a aucune garantie que les éléments soient énumérés dans le même ordre que celui dans lequel ils ont été ajoutés par les threads producteurs.  
  
 Pour énumérer la collection sans la modifier, utilisez seulement la boucle `foreach` \(`For Each`\) sans la méthode <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>.  Toutefois, il est important de comprendre que ce genre d'énumération représente un instantané de la collection à un moment donné.  Si d'autres threads ajoutent ou suppriment des éléments simultanément pendant l'exécution de la boucle, la boucle peut ne pas représenter l'état réel de la collection.  
  
## Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)