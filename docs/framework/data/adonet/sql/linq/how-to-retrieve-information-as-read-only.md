---
title: "Proc&#233;dure&#160;: r&#233;cup&#233;rer des informations en lecture seule | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: r&#233;cup&#233;rer des informations en lecture seule
Lorsque vous ne projetez pas de modifier les données, vous pouvez augmenter les performances des requêtes en recherchant des résultats en lecture seule.  
  
 Implémentez le traitement en lecture seule en affectant la valeur `false` à <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>.  
  
> [!NOTE]
>  Lorsque la valeur `false` est affectée à <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a implicitement la valeur `false`.  
  
## Exemple  
 Le code suivant récupère une collection en lecture seule de dates d'embauche d'employés.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## Voir aussi  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)   
 [Comparaison entre le chargement différé et le chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)