---
title: "Proc&#233;dure&#160;: cr&#233;er un service de donn&#233;es &#224; l&#39;aide du fournisseur de r&#233;flexion (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, fournisseurs"
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: cr&#233;er un service de donn&#233;es &#224; l&#39;aide du fournisseur de r&#233;flexion (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de définir un modèle de données basé sur les classes arbitraires tant que ces classes sont exposées comme des objets qui implémentent l'interface <xref:System.Linq.IQueryable%601>.  Pour plus d'informations, consultez [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant définit un modèle de données qui inclut `Orders` et `Items`.  La classe de conteneur d'entités  `OrderItemData` a deux méthodes publiques qui retournent des interfaces <xref:System.Linq.IQueryable%601>.  Ces interfaces sont les jeux d'entités des types d'entité `Items` et `Orders`.  Un `Order` peut inclure plusieurs `Items`, donc le type d'entité `Orders` a une propriété de navigation `Items` qui retourne une collection d'objets `Items`.  La classe de conteneur d'entités `OrderItemData` est le type générique de la classe <xref:System.Data.Services.DataService%601> d'où est dérivé le service de données `OrderItems`.  
  
> [!NOTE]
>  Comme cet exemple illustre un fournisseur de données en mémoire et que les modifications ne sont pas persistantes en dehors des instances de l'objet actuelles, l'implémentation de l'interface <xref:System.Data.Services.IUpdatable> n'apporte aucun avantage.  Pour obtenir un exemple qui implémente l'interface <xref:System.Data.Services.IUpdatable>, consultez [Procédure : créer un service de données à l'aide d'une source de données LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## Voir aussi  
 [Procédure : créer un service de données à l'aide d'une source de données LINQ to SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)   
 [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [Procédure : créer un service de données à l'aide d'une source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)