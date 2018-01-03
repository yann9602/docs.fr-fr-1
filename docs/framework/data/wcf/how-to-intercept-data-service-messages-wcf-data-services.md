---
title: "Comment : intercepter les messages des services de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28f69bb7f584c8d9e7031d969dce0052b1541aad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>Comment : intercepter les messages des services de données (services de données WCF)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez intercepter des messages de demande afin de pouvoir ajouter la logique personnalisée à une opération. Pour intercepter un message, vous utilisez les méthodes attribuées spécialement dans le service de données. Pour plus d’informations, consultez [intercepteurs](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
 L'exemple de cette rubrique utilise l'exemple du service de données Northwind. Ce service est créé lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Pour définir un intercepteur de requête pour le jeu d'entités Orders  
  
1.  Dans le projet de service de données Northwind, ouvrez le fichier Northwind.svc.  
  
2.  Dans la page de codes de la classe `Northwind`, ajoutez l'instruction suivante `using` (`Imports` en Visual Basic).  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  Dans la classe `Northwind`, définissez une méthode d'opération de service nommée `OnQueryOrders` comme suit :  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Pour définir un intercepteur de modification pour le jeu d'entités Products  
  
1.  Dans le projet de service de données Northwind, ouvrez le fichier Northwind.svc.  
  
2.  Dans la classe `Northwind`, définissez une méthode d'opération de service nommée `OnChangeProducts` comme suit :  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit une méthode d'interception de requête pour le jeu d'entités `Orders` qui retourne une expression lambda. Cette expression contient un délégué qui filtre le `Orders` demandé en fonction du `Customers` connexe qui a un nom de contact spécifique. Le nom est déterminé ensuite selon l'utilisateur demandeur. Cet exemple suppose que le service de données est hébergé dans une application Web ASP.NET qui utilise WCF, et que l'authentification est activée. La classe <xref:System.Web.HttpContext> est utilisée pour récupérer le principe de la demande actuelle.  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>Exemple  
 Cet exemple définit une méthode d'interception de modification pour le jeu d'entités `Products`. Cette méthode valide l'entrée au service pour une opération <xref:System.Data.Services.UpdateOperations.Add> ou <xref:System.Data.Services.UpdateOperations.Change> et lève une exception si une modification est apportée à un produit de fin de série. Elle bloque également la suppression de produits comme une opération non prise en charge.  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir une opération de service](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
