---
title: "Proc&#233;dure&#160;: activer l&#39;acc&#232;s au service de donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, configuration"
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: activer l&#39;acc&#232;s au service de donn&#233;es (WCF Data Services)
Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous devez accorder explicitement l'accès aux ressources exposées par un service de données.  Cela signifie qu'après avoir créé un service de données, vous devez encore fournir explicitement l'accès à des ressources individuelles comme les jeux d'entités.  Cette rubrique indique comment activer l'accès en lecture et en écriture à cinq des jeux d'entités dans le service de données Northwind qui est créé lorsque vous terminez le [démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Étant donné que l'énumération de <xref:System.Data.Services.EntitySetRights> est définie à l'aide de <xref:System.FlagsAttribute>, vous pouvez utiliser un opérateur OR logique pour spécifier plusieurs autorisations pour un jeu d'entités unique.  
  
> [!NOTE]
>  Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données.  Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle\-même.  Pour plus d'informations, consultez [NIB: ASP.NET Security](http://msdn.microsoft.com/fr-fr/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### Pour activer l'accès au service de données  
  
-   Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Cela permet aux clients de disposer d'un accès en lecture et en écriture aux jeux d'entités `Order_Details` et `Orders` et d'un accès en lecture seule aux jeux d'entités `Customers`.  
  
## Voir aussi  
 [Procédure : développer un WCF Data Service qui fonctionne sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)   
 [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)