---
title: "Procédure : activer l'accès au service de données (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b41de296143d325ba0e1932831d4a3ef1bd7dc80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Procédure : activer l'accès au service de données (WCF Data Services)
Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous devez accorder explicitement l'accès aux ressources exposées par un service de données. Cela signifie qu'après avoir créé un service de données, vous devez encore fournir explicitement l'accès à des ressources individuelles comme les jeux d'entités. Cette rubrique montre comment activer la lecture et écriture aux cinq de l’entité définit dans le service de données Northwind est créé lorsque vous complétez le [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Puisque l'énumération <xref:System.Data.Services.EntitySetRights> est définie à l'aide de l'objet <xref:System.FlagsAttribute>, vous pouvez utiliser un opérateur OR logique pour spécifier plusieurs autorisations pour un jeu d'entités unique.  
  
> [!NOTE]
>  Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données. Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même. Pour plus d’informations, consultez [NIB : sécurité ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Pour activer l'accès au service de données  
  
-   Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     Cela permet aux clients de disposer d'un accès en lecture et en écriture aux jeux d'entités `Orders` et `Order_Details` et d'un accès en lecture seule aux jeux d'entités `Customers`.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : développer un Service de données WCF en cours d’exécution sur IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
