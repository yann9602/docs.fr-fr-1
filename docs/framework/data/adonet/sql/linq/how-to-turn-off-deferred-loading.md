---
title: "Proc&#233;dure&#160;: d&#233;sactiver le chargement diff&#233;r&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: d&#233;sactiver le chargement diff&#233;r&#233;
Vous pouvez désactiver le chargement différé en affectant la valeur `false` à <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A>.  Pour plus d'informations, consultez [Comparaison entre le chargement différé et le chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Le chargement différé est désactivé lorsque le suivi d'objet est désactivé.  Pour plus d'informations, consultez [Procédure : récupérer des informations en lecture seule](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## Exemple  
 L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur `false` à <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A>.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## Voir aussi  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)