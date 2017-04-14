---
title: "Proc&#233;dure&#160;: projeter des r&#233;sultats de requ&#234;te (WCF Data Services) | Microsoft Docs"
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
  - "projection [WCF Data Services]"
  - "projection de requête [WCF Data Services]"
  - "Services de données WCF, projection"
  - "Services de données WCF, interroger"
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: projeter des r&#233;sultats de requ&#234;te (WCF Data Services)
La projection fournit un mécanisme permettant de réduire la quantité de données retournées par une requête en spécifiant que seules certaines propriétés d'une entité doivent être retournées dans la réponse.  Vous pouvez effectuer des projections sur les résultats d'une requête [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] en utilisant l'option de requête `$select` ou en utilisant la clause [select](../Topic/select%20clause%20\(C%23%20Reference\).md) \([Select](../Topic/Select%20Clause%20\(Visual%20Basic\).md) dans Visual Basic\) dans une requête LINQ.  Pour plus d'informations, consultez [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant montre une requête LINQ qui projette des entités Customers dans un nouveau type CustomerAddress, qui contient uniquement des propriétés spécifiques à l'adresse ainsi que la propriété d'identité.  Cette classe `CustomerAddress` est définie sur le client et est attribuée de sorte que la bibliothèque cliente puisse le reconnaître comme un type d'entité.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## Exemple  
 L'exemple suivant montre une requête LINQ qui projette les entités Customers renvoyées dans un nouveau type CustomerAddressNonEntity, qui contient uniquement des propriétés spécifiques à l'adresse et aucune propriété d'identité.  Cette classe `CustomerAddressNonEntity` est définie sur le client et n'est pas attribuée comme un type d'entité.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## Exemple  
 L'exemple suivant affiche les définitions des types `CustomerAddress``CustomerAddressNonEntity` utilisés dans les exemples précédents.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]