---
title: "Proc&#233;dure&#160;: charger des r&#233;sultats pagin&#233;s (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, contenu différé"
  - "Services de données WCF, chargement de données"
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: charger des r&#233;sultats pagin&#233;s (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permet au service de données de limiter le nombre des entités retournées dans un flux de réponse unique.  Lorsque cela arrive, la dernière entrée dans le flux contient un lien vers la page suivante de données.  L'URI de la page de données suivante est obtenu en appelant la méthode <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> de <xref:System.Data.Services.Client.QueryOperationResponse%601>, qui est retournée lorsque <xref:System.Data.Services.Client.DataServiceQuery%601> est exécuté. L'URI représenté par cet objet est ensuite utilisé pour charger la page des résultats suivante.  Pour plus d'informations, consultez [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 Cet exemple utilise une boucle `do…while` pour charger des entités `Customers` à partir de résultats paginés du service de données.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## Exemple  
 Cet exemple retourne des entités `Orders` connexes avec chaque entité `Customers` et utilise une boucle `do…while` pour charger des pages d'entités `Customers` et une boucle `while` imbriquée pour charger des pages d'entités `Orders` connexes à partir du service de données.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## Voir aussi  
 [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)   
 [Procédure : charger des entités connexes](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)