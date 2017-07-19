---
title: "Proc&#233;dure&#160;: charger des entit&#233;s connexes (WCF Data Services) | Microsoft Docs"
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
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: charger des entit&#233;s connexes (WCF Data Services)
Lorsque vous devez charger des entités connexes dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> sur la classe <xref:System.Data.Services.Client.DataServiceContext>.  Vous pouvez également utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> sur <xref:System.Data.Services.Client.DataServiceQuery%601> pour exiger un chargement anticipé des entités connexes dans la même réponse à la requête.  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre comment charger explicitement le `Customer` associé à chaque instance `Orders` retournée.  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## Exemple  
 L'exemple ci\-dessous montre comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> pour retourner `Order Details` qui appartient au `Orders` retourné par la requête.  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## Voir aussi  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)