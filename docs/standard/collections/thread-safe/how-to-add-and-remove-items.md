---
title: "Comment&#160;: ajouter et supprimer des &#233;l&#233;ments d&#39;un ConcurrentDictionary | Microsoft Docs"
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
  - "collections thread-safe, dictionnaire simultané"
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter et supprimer des &#233;l&#233;ments d&#39;un ConcurrentDictionary
Cet exemple indique comment ajouter, extraire, mettre à jour et supprimer des éléments à partir d'un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>.  Cette classe de collection est une implémentation thread\-safe.  Nous vous recommandons de l'utiliser chaque fois que plusieurs threads peuvent essayer d'accéder aux éléments de façon simultanée.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> fournit plusieurs méthodes pratiques qui permettent au code de ne plus avoir à vérifier au préalable si une clé existe avant d'essayer d'ajouter ou de supprimer des données.  Le tableau suivant répertorie ces méthodes pratiques et indique quand les utiliser.  
  
|Méthode|À utiliser lorsque...|  
|-------------|---------------------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Vous souhaitez ajouter une nouvelle valeur pour une clé spécifiée et, si la clé existe déjà, vous souhaitez remplacer sa valeur.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Vous souhaitez extraire la valeur existante d'une clé spécifiée et, si la clé n'existe pas, vous souhaitez spécifier une paire clé\/valeur.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Vous souhaitez ajouter, obtenir, mettre à jour ou supprimer une paire clé\/valeur, et, si la clé existe déjà ou si la tentative échoue pour une autre raison, vous souhaitez prendre une autre mesure.|  
  
## Exemple  
 L'exemple suivant utilise deux instances <xref:System.Threading.Tasks.Task> pour ajouter des éléments à un <xref:System.Collections.Concurrent.ConcurrentDictionary%602> simultanément, puis sort tout le contenu pour montrer que les éléments ont été ajoutés avec succès.  L'exemple montre également comment utiliser les méthodes <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> et pour ajouter, mettre à jour, extraire et retirer des éléments à partir de la collection.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> est conçu pour les scénarios multithreads.  Vous n'avez pas besoin d'utiliser des verrous dans votre code pour ajouter ou supprimer des éléments dans la collection.  Toutefois, il est toujours possible pour un thread d'extraire une valeur et pour un autre thread de mettre à jour immédiatement la collection en donnant une nouvelle valeur à la même clé.  
  
 En outre, bien que toutes les méthodes de <xref:System.Collections.Concurrent.ConcurrentDictionary%602> soient thread\-safe, toutes les méthodes sont atomiques, en particulier <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> et <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.  Le délégué utilisateur passé à ces méthodes est appelé en dehors du verrou interne du dictionnaire. \(Cela permet d'empêcher un code inconnu de bloquer tous les threads\). Par conséquent, cette séquence d'événements peut se produire :  
  
 1\) le threadA appelle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, ne trouve pas d'élément et crée un nouvel élément à ajouter en appelant le délégué valueFactory.  
  
 2\) simultanément, le threadB appelle <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, son délégué valueFactory est appelé et atteint le verrou interne avant le threadA. Sa nouvelle paire clé\-valeur est alors ajoutée au dictionnaire.  
  
 3\) le délégué utilisateur du threadA se termine. Le thread atteint le verrou, mais il constate que l'élément existe déjà  
  
 4\) le threadA exécute une commande GET et retourne les données déjà ajoutées par le threadB.  
  
 Par conséquent, il n'est pas garanti que les données retournées par <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> sont les mêmes que celles créées par le valueFactory du thread.  Une séquence d'événements similaire peut se produire lors de l'appel de <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.  
  
## Voir aussi  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Collections thread\-safe](../../../../docs/standard/collections/thread-safe/index.md)