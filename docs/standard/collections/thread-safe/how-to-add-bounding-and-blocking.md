---
title: "Comment&#160;: ajouter des fonctionnalit&#233;s de liaison et de blocage &#224; une collection | Microsoft Docs"
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
  - "collections thread-safe, collections de blocage personnalisées"
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter des fonctionnalit&#233;s de liaison et de blocage &#224; une collection
Cet exemple indique comment ajouter des fonctionnalités de liaison et de blocage à une classe de collection personnalisée en implémentant l'interface <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> dans la classe, puis en utilisant une instance de classe en tant que mécanisme de stockage interne pour une <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>.  Pour plus d'informations sur la liaison et le bocage, consultez [Vue d'ensemble de BlockingCollection](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## Exemple  
 La classe de collection personnalisée est une file d'attente de priorité de base dans laquelle les niveaux de priorité sont représentés sous la forme d'un tableau d'objets <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>.  Aucun classement supplémentaire n'est exécuté au sein de chaque file d'attente.  
  
 Dans le code client, trois tâches sont démarrées.  La première tâche demande juste aux touches du clavier de permettre l'annulation à tout moment pendant l'exécution.  La deuxième tâche est le thread producteur. Elle ajoute de nouveaux éléments à la collection bloquante et donne une priorité à chaque élément selon une valeur aléatoire.  La troisième tâche supprime des éléments de la collection à mesure qu'ils deviennent disponibles.  
  
 Vous pouvez ajuster le comportement de l'application en rendant un thread plus rapide qu'un autre.  Si le thread producteur est plus rapide, vous remarquerez les fonctionnalités de liaison lorsque la collection bloquante empêche l'ajout d'éléments si elle contient déjà le nombre d'éléments spécifié dans le constructeur.  Si le thread consommateur s'exécute plus vite, vous remarquerez les fonctionnalités de blocage lorsque le consommateur attend l'ajout d'un nouvel élément.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Par défaut, le stockage d'une <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> est <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>.  
  
## Voir aussi  
 [Collections thread\-safe](../../../../docs/standard/collections/thread-safe/index.md)