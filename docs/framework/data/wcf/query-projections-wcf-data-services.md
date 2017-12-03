---
title: "Projections de requête (services de données WCF)"
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
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d14c67daa387f06a3c7d6e43219991950bceb73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="query-projections-wcf-data-services"></a>Projections de requête (services de données WCF)
Projection fournit un mécanisme dans le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] afin de réduire la quantité de données dans le flux retourné par une requête en spécifiant que seules certaines propriétés d’une entité sont retournées dans la réponse. Pour plus d’informations, consultez [OData : sélectionnez une Option de requête système ($select)](http://go.microsoft.com/fwlink/?LinkId=186076).  
  
 Cette rubrique décrit comment définir une projection de requête, quelles sont les exigences pour les types d’entité et de non-entité, la mise à jour des résultats projetés, la création des types projetés et répertorie des considérations relatives à la projection.  
  
## <a name="defining-a-query-projection"></a>Définition d'une projection de requête  
 Vous pouvez ajouter une clause de projection à une requête à l’aide de la `$select` option dans un URI ou à l’aide de requête le [sélectionnez](~/docs/csharp/language-reference/keywords/select-clause.md) clause ([sélectionnez](~/docs/visual-basic/language-reference/queries/select-clause.md) en Visual Basic) dans une requête LINQ. Les données d'entité retournées peuvent être projetées dans des types d'entités ou de non-entités sur le client. Les exemples de cette rubrique montrent comment utiliser la clause `select` dans une requête LINQ.  
  
> [!IMPORTANT]
>  Une perte de données peut survenir dans le service de données lorsque vous enregistrez des mises à jour apportées aux types projetés. Pour plus d’informations, consultez [considérations sur la Projection](#considerations).  
  
## <a name="requirements-for-entity-and-non-entity-types"></a>Exigences pour les types d’entité et de non-entité  
 Les types d'entité doivent avoir une ou plusieurs propriétés d'identité qui composent la clé d'entité. Les types d'entité sont définis sur les clients de l'une des manières suivantes :  
  
-   En appliquant <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> au type.  
  
-   Lorsque le type a une propriété appelée `ID`.  
  
-   Lorsque le type a une propriété nommée *type*`ID`, où *type* est le nom du type.  
  
 Par défaut, lorsque vous projetez des résultats de requête dans un type défini sur le client, les propriétés demandées dans la projection doivent exister dans le type de client. Toutefois, lorsque vous spécifiez une valeur `true` pour la propriété <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> de <xref:System.Data.Services.Client.DataServiceContext>, il n'est pas requis que les propriétés spécifiées dans la projection se produisent dans le type de client.  
  
### <a name="making-updates-to-projected-results"></a>Mise à jour des résultats projetés  
 Lorsque vous projetez des résultats de requête dans des types d'entité sur le client, <xref:System.Data.Services.Client.DataServiceContext> peut suivre ces objets avec les mises à jour à renvoyer au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée. Toutefois, les mises à jour apportées aux données projetées dans des types de non-entité sur le client ne peuvent pas être renvoyées au service de données. La cause est que sans une clé pour identifier l'instance d'entité, le service de données ne peut pas mettre à jour l'entité correcte dans la source de données. Les types de non-entité ne sont pas joints à <xref:System.Data.Services.Client.DataServiceContext>.  
  
 Lorsqu'une ou plusieurs propriétés d'un type d'entité défini dans le service de données ne se produit pas dans le type de client dans lequel l'entité est projetée, les insertions de nouvelles entités ne contiennent pas ces propriétés manquantes. Dans ce cas, les mises à jour apportées aux entités existantes seront **également** n’inclut pas ces propriétés manquantes. Lorsqu'une valeur existe pour une telle propriété, la mise à jour rétablit la valeur par défaut de la propriété, comme défini dans la source de données.  
  
### <a name="creating-projected-types"></a>Création de types projetés  
 L'exemple suivant utilise une requête LINQ anonyme qui projette les propriétés associées à l'adresse du type `Customers` dans un nouveau type `CustomerAddress`, qui est défini sur le client et est attribué comme un type d'entité :  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 Dans cet exemple, le modèle de l'initialiseur d'objet est utilisé pour créer une nouvelle instance de type `CustmerAddress` au lieu d'appeler un constructeur. Les constructeurs ne sont pas pris en charge lors de la projection dans des types d'entité, mais ils peuvent être utilisés pour les projections dans des types de non-entité et anonymes. Étant donné que `CustomerAddress` est un type d'entité, les modifications peuvent être apportées et renvoyées au service de données.  
  
 De même, les données de type `Customer` sont projetées dans une instance du type d'entité `CustomerAddress` au lieu d'un type anonyme. La projection dans des types anonymes est prise en charge, mais les données sont en lecture seule parce que les types anonymes sont traités comme des types de non-entité.  
  
 Les paramètres de <xref:System.Data.Services.Client.MergeOption> de <xref:System.Data.Services.Client.DataServiceContext> sont utilisés pour la résolution de l'identité pendant la projection de la requête. Cela signifie que si une instance de type `Customer` existe déjà dans <xref:System.Data.Services.Client.DataServiceContext>, une instance `CustomerAddress` avec la même identité suit les règles de résolution de l'identité définies par <xref:System.Data.Services.Client.MergeOption>  
  
 Le tableau suivant décrit les comportements lors de la projection de résultats dans les types d'entité et de non-entité :  
  
|Action|Type d'entité|Type de non entité|  
|------------|-----------------|----------------------|  
|Création d'une nouvelle instance projetée à l'aide d'initialiseurs, comme dans l'exemple suivant :<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|Pris en charge|Pris en charge|  
|Création d'une nouvelle instance projetée à l'aide de constructeurs, comme dans l'exemple suivant :<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|<xref:System.NotSupportedException> est levée.|Pris en charge|  
|Utilisation de la projection pour transformer une valeur de propriété, comme dans l'exemple suivant :<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> Cette transformation n'est pas prise en charge pour les types d'entité car cela peut engendrer une confusion et remplacer les données de la source de données qui appartient à une autre entité.|<xref:System.NotSupportedException> est levée.|Pris en charge|  
  
<a name="considerations"></a>   
## <a name="projection-considerations"></a>Considérations sur la projection  
 Les considérations supplémentaires suivantes s'appliquent à la définition d'une projection de requête.  
  
-   Lorsque vous définissez des flux personnalisés au format Atom, vous devez vérifier que toutes les propriétés de l'entité qui ont des mappages personnalisés définis sont incluses dans la projection. Lorsqu'une propriété d'entité mappée n'est pas incluse dans la projection, une perte de données peut se produire. Pour plus d’informations, consultez [personnalisation de flux](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
-   Lorsque des insertions sont apportées à un type projeté qui ne contient pas toutes les propriétés de l'entité du modèle de données du service de données, les propriétés non incluses dans la projection sur le client sont définies sur les valeurs par défaut.  
  
-   Lorsque des mises à jour sont apportées à un type projeté qui ne contient pas toutes les propriétés de l'entité du modèle de données du service de données, les valeurs existantes non incluses dans la projection sur le client sont remplacées par les valeurs par défaut non initialisées.  
  
-   Lorsqu'une projection inclut une propriété complexe, l'objet complexe entier doit être retourné.  
  
-   Lorsqu'une projection inclut une propriété de navigation, les objets connexes sont chargés implicitement sans devoir appeler la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>. La méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> n'est pas prise en charge pour une utilisation dans une requête projetée.  
  
-   Les requêtes de projections de requête sur le client sont traduites pour utiliser l'option de requête `$select` dans l'URI de requête. Lorsqu'une requête avec projection est exécutée sur une version précédente d'[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] qui ne prend pas en charge l'option de requête `$select`, une erreur est retournée. Cela peut également arriver lorsque <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> de <xref:System.Data.Services.DataServiceBehavior> pour le service de données est défini sur une valeur <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>. Pour plus d’informations, consultez [contrôle de version de Service de données](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
 Pour plus d’informations, consultez [Comment : résultats de la requête](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
