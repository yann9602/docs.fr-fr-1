---
title: "Proc&#233;dure&#160;: intercepter des messages de service de donn&#233;es (WCF Data Services) | Microsoft Docs"
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
  - "intercepteurs de requêtes [WCF Data Services]"
  - "Services de données WCF, personnalisation"
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: intercepter des messages de service de donn&#233;es (WCF Data Services)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez intercepter des messages de demande afin de pouvoir ajouter la logique personnalisée à une opération.  Pour intercepter un message, vous utilisez des méthodes attribuées spécialement dans le service de données.  Pour plus d'informations, consultez [Intercepteurs](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 L'exemple de cette rubrique utilise l'exemple du service de données Northwind.  Ce service est créé lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### Pour définir un intercepteur de requête pour le jeu d'entités Orders  
  
1.  Dans le projet de service de données Northwind, ouvrez le fichier Northwind.svc.  
  
2.  Dans la page de codes de la classe `Northwind`, ajoutez l'instruction suivante `using` \(`Imports` en Visual Basic\).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  Dans la classe `Northwind`, définissez une méthode d'opération de service nommée `OnQueryOrders` comme suit :  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### Pour définir un intercepteur de modification pour le jeu d'entités Products  
  
1.  Dans le projet de service de données Northwind, ouvrez le fichier Northwind.svc.  
  
2.  Dans la classe `Northwind`, définissez une méthode d'opération de service nommée `OnChangeProducts` comme suit :  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## Exemple  
 Cet exemple définit une méthode d'interception de requête pour le jeu d'entités `Orders` qui retourne une expression lambda.  Cette expression contient un délégué qui filtre le `Orders` demandé en fonction du `Customers` connexe qui a un nom de contact spécifique.  Le nom est déterminé ensuite selon l'utilisateur demandeur.  Cet exemple suppose que le service de données est hébergé dans une application Web ASP.NET qui utilise WCF, et que l'authentification est activée.  La classe <xref:System.Web.HttpContext> est utilisée pour récupérer le principe de la demande actuelle.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## Exemple  
 Cet exemple définit une méthode d'interception de modification pour le jeu d'entités `Products`.  Cette méthode valide l'entrée au service pour une opération <xref:System.Data.Services.UpdateOperations> ou <xref:System.Data.Services.UpdateOperations> et lève une exception si une modification est apportée à un produit de fin de série.  Elle bloque également la suppression de produits comme une opération non prise en charge.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## Voir aussi  
 [Procédure : définir une opération de service](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)   
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)