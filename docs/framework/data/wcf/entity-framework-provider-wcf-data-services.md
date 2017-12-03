---
title: "Fournisseur Entity Framework (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c054e3cc9dbf920ab280df43d97acdb90ca055
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a>Fournisseur Entity Framework (services de données WCF)
Comme [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], ADO.NET Entity Framework est basé sur Entity Data Model qui est un type de modèle de relation d'entité. Entity Framework traduit des opérations par rapport à son implémentation de l’Entity Data Model, qui est appelé le *modèle conceptuel*, en opérations équivalentes sur une source de données. Cela fait d'Entity Framework un fournisseur idéal pour les services de données basés sur les données relationnelles, et toute base de données dont le fournisseur de données prend en charge Entity Framework peut être utilisée avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Pour obtenir la liste des sources de données qui prennent en charge Entity Framework, consultez [des fournisseurs tiers pour Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).  
  
 Dans un modèle conceptuel, le conteneur d'entités est la racine du service. Vous devez définir un modèle conceptuel dans Entity Framework avant que les données puissent être exposées par un service de données. Pour plus d’informations, consultez [procédure : création d’un Service de données à l’aide d’une Source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]prend en charge le modèle d’accès concurrentiel optimiste en vous permettant de définir un jeton d’accès concurrentiel pour une entité. Ce jeton d'accès concurrentiel, qui inclut une ou plusieurs propriétés de l'entité, est utilisé par le service de données pour déterminer si une modification a eu lieu dans les données demandées, mises à jour ou supprimées. Lorsque les valeurs du jeton obtenues de l'eTag dans la demande diffèrent des valeurs actuelles de l'entité, le service de données déclenche une exception. Pour indiquer qu'une propriété fait partie du jeton d'accès concurrentiel, vous devez appliquer l'attribut `ConcurrencyMode="Fixed"` dans le modèle de données défini par le fournisseur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]. Le jeton d'accès concurrentiel ne peut pas inclure une propriété de clé ou de navigation. Pour plus d’informations, consultez [mise à jour du Service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 Pour en savoir plus sur Entity Framework, consultez [présentation d’Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [Fournisseur de réflexion](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
