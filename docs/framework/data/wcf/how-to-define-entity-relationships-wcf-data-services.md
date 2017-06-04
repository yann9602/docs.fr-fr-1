---
title: "Proc&#233;dure&#160;: d&#233;finir des relations d&#39;entit&#233; (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, changer des données"
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: d&#233;finir des relations d&#39;entit&#233; (WCF Data Services)
Lorsque vous ajoutez une nouvelle entité dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], les relations entre la nouvelle entité et les entités connexes ne sont pas définies automatiquement.  Vous pouvez créer et modifier les relations entre des instances d'entité et faire répercuter par la bibliothèque cliente ces modifications dans le service de données.  Pour plus d'informations, consultez [Mise à jour du service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant crée une nouvelle instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte avec le lien vers l'ordre connexe.  Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## Exemple  
 L'exemple suivant montre comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pour ajouter un objet `Order_Details` à un objet `Orders` connexe avec une référence à un objet `Products` spécifique.  Les méthodes <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> et <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> définissent les relations.  Dans cet exemple, les propriétés de navigation sur l'objet `Order_Details` sont également définies explicitement.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorder)]  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [Procédure : ajouter, modifier et supprimer des entités](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)