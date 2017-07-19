---
title: "Proc&#233;dure : d&#233;terminer le nombre d&#39;entit&#233;s retourn&#233;es par une requ&#234;te WCF Data Services | Microsoft Docs"
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
  - "Services de données WCF, nombre de lignes"
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure : d&#233;terminer le nombre d&#39;entit&#233;s retourn&#233;es par une requ&#234;te WCF Data Services
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez déterminer le nombre d'entités qui sont dans le jeu d'entités spécifié par un URI de requête.  Ce nombre peut être inclus avec le résultat de la requête ou comme une valeur entière.  Pour plus d'informations, consultez [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 Cet exemple exécute une requête après avoir appelé la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A>.  La propriété <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> retourne le nombre d'entités dans le jeu d'entités `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## Exemple  
 Cet exemple appelle la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner uniquement une valeur entière qui correspond au nombre d'entités du jeu d'entités `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## Voir aussi  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)