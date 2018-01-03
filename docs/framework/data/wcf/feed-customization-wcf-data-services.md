---
title: "Personnalisation des flux (services de données WCF)"
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
- WCF Data Services, feeds
- WCF Data Services, Atom protocol
- Atom Publishing Protocol [WCF Data Services]
- WCF Data Services, customizing feeds
ms.assetid: 0d1a39bc-6462-4683-bd7d-e74e0fd28a85
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1ada694ed8bdb8aea4551a24f423f896ba1bd61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="feed-customization-wcf-data-services"></a>Personnalisation des flux (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]utilise le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer des données en tant que flux. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]prend en charge les formats Atom et JavaScript Objet Notation (JSON) pour les flux de données. Lorsque vous utilisez un flux Atom, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fournit une méthode standard pour sérialiser les données, telles que les entités et les relations, dans un format XML qui peut être inclus dans le corps du message HTTP. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]définit un mappage de propriété d’entité par défaut entre les données contenues dans les entités et les éléments Atom. Pour plus d’informations, consultez [OData : Format Atom](http://go.microsoft.com/fwlink/?LinkID=185794).  
  
 Vous pouvez avoir un scénario d'application qui requiert que les données de propriété retournées par le service des données soient sérialisées de façon personnalisée plutôt qu'au format de flux standard. Avec [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous pouvez personnaliser la sérialisation dans un flux de données afin que les propriétés d’une entité peuvent être mappées aux éléments inutilisés et les attributs d’une entrée ou pour des éléments personnalisés d’une entrée dans le flux.  
  
> [!NOTE]
>  La personnalisation de flux est prise en charge uniquement pour les flux Atom. Les flux personnalisés ne sont pas retournés lorsque le format JSON est demandé pour le flux retourné.  
  
 Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez définir un autre mappage de propriété pour les charges utiles Atom en appliquant manuellement des attributs aux types d'entité dans le modèle de données. Le fournisseur de sources de données du service de données détermine le mode d'application de ces attributs.  
  
> [!IMPORTANT]
>  Lorsque vous définissez des flux personnalisés, vous devez vérifier que toutes les propriétés de l'entité qui ont des mappages personnalisés définis sont incluses dans la projection. Lorsqu'une propriété d'entité mappée n'est pas incluse dans la projection, une perte de données peut se produire. Pour plus d’informations, consultez [des Projections de requête](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-the-entity-framework-provider"></a>Personnalisation de flux avec le fournisseur Entity Framework  
 Le modèle de données utilisé avec le fournisseur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] est représenté sous la forme de code XML dans le fichier .edmx. Dans ce cas, les attributs qui définissent des flux personnalisés sont ajoutés aux éléments `EntityType` et `Property` qui représentent des types et des propriétés d'entité dans le modèle de données. Ces attributs de personnalisation de flux ne sont pas définies dans [ \[MC-CSDL\]: Format de fichier de définition de schéma conceptuel](http://go.microsoft.com/fwlink/?LinkId=159072), qui est le format qui le [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] fournisseur utilise pour définir le modèle de données. Par conséquent, vous devez déclarer les attributs de personnalisation de flux dans un espace de noms de schéma spécifique défini sous la forme `m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"`. Le fragment XML suivant affiche des attributs de personnalisation de flux appliqués aux éléments `Property` du type d'entité `Products` qui définissent les propriétés `ProductName`, `ReorderLevel` et `UnitsInStock`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedAttributes](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedattributes)]  
  
 Ces attributs produisent le flux de données personnalisé suivant pour le jeu d'entités `Products`. Dans le flux de données personnalisé, la valeur de la propriété `ProductName` s'affiche à la fois dans l'élément `author` et comme élément de propriété `ProductName`, et la propriété `UnitsInStock` s'affiche dans un élément personnalisé possédant son propre espace de noms unique et avec la propriété `ReorderLevel` comme attribut :  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResultProduct](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresultproduct)]  
  
 Pour plus d’informations, consultez [Comment : personnaliser des flux avec le fournisseur Entity Framework](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-ef-provider-wcf-data-services.md).  
  
> [!NOTE]
>  Étant donné que les extensions au modèle de données ne sont pas prises en charge par le Concepteur d’entités, vous devez modifier manuellement le fichier XML qui contient le modèle de données. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]le fichier .edmx généré par le [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] outils, consultez [présentation d’un fichier .edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### <a name="custom-feed-attributes"></a>Attributs de flux personnalisés  
 La table suivante affiche les attributs XML qui personnalisent les flux que vous pouvez ajouter au CSDL (Conceptual Schema Definition Language) qui définit le modèle de données. Ces attributs sont équivalents aux propriétés de <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> utilisées avec le fournisseur de réflexion.  
  
|Nom d'attribut|Description|  
|--------------------|-----------------|  
|`FC_ContentKind`|Indique le type de contenu. Les mots clés suivants définissent des types de contenu de syndication.<br /><br /> `text:`La valeur de propriété est affichée dans le flux sous forme de texte.<br /><br /> `html:`La valeur de propriété est affichée dans le flux au format HTML.<br /><br /> `xhtml:`La valeur de propriété est affichée dans le flux en tant que code HTML au format XML.<br /><br /> Ces mots clés sont équivalents aux valeurs de l'énumération <xref:System.Data.Services.Common.SyndicationTextContentKind> utilisées avec le fournisseur de réflexion.<br /><br /> Cet attribut n'est pas pris en charge lorsque les attributs `FC_NsPrefix` et `FC_NsUri` sont utilisés.<br /><br /> Lorsque vous spécifiez une valeur de `xhtml` pour l'attribut `FC_ContentKind`, vous devez vérifier que la valeur de propriété contient le formatage XML approprié. Le service de données retourne la valeur sans effectuer de transformations. Vous devez également vérifier que tous les préfixes d'élément XML dans le XML retourné ont un URI d'espace de noms et le préfixe défini dans le flux mappé.|  
|`FC_KeepInContent`|Indique que la valeur de propriété référencée doit être incluse à la fois dans la section de contenu du flux et dans l'emplacement mappé. Les valeurs valides sont `true` et `false`. Pour rendre le flux résultant à compatibilité descendante avec les versions antérieures de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], spécifiez la valeur `true` pour vous assurer que la valeur est incluse dans la section de contenu du flux de données.|  
|`FC_NsPrefix`|Préfixe d'espace de noms de l'élément XML dans un mappage de non-syndication. Cet attribut doit être utilisé avec l'attribut `FC_NsUri` et ne peut pas être utilisé avec l'attribut `FC_ContentKind`.|  
|`FC_NsUri`|URI d'espace de noms de l'élément XML dans un mappage de non-syndication. Cet attribut doit être utilisé avec l'attribut `FC_NsPrefix` et ne peut pas être utilisé avec l'attribut `FC_ContentKind`.|  
|`FC_SourcePath`|Chemin d'accès de la propriété de l'entité à laquelle s'applique cette règle de mappage de flux. Cet attribut est pris en charge uniquement lorsqu'il est utilisé dans un élément `EntityType`.<br /><br /> La propriété <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> ne peut pas référencer directement de type complexe. Pour les types complexes, vous devez utiliser une expression de chemin d'accès où les noms de propriété sont séparés par une barre oblique inverse (`/`). Par exemple, les valeurs suivantes sont autorisées pour un type d’entité `Person` avec une propriété entière `Age` et une propriété complexe<br /><br /> `Address`:<br /><br /> `Age`<br /><br /> `Address/Street`<br /><br /> La propriété <xref:System.Data.Services.Common.EntityPropertyMappingAttribute.SourcePath%2A> ne peut pas avoir une valeur qui contient un espace ou un autre caractère qui n'est pas valide dans un nom de propriété.|  
|`FC_TargetPath`|Nom de l'élément cible du flux résultant pour mapper la propriété. Cet élément peut être un élément défini par la spécification Atom ou un élément personnalisé.<br /><br /> Les mots clés suivants sont des valeurs cible-chemin d'accès de syndication prédéfinies qui pointent vers un emplacement spécifique dans un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].<br /><br /> `SyndicationAuthorEmail:`Le `atom:email` élément enfant de le `atom:author` élément.<br /><br /> `SyndicationAuthorName:`Le `atom:name` élément enfant de le `atom:author` élément.<br /><br /> `SyndicationAuthorUri:`Le `atom:uri` élément enfant de le `atom:author` élément.<br /><br /> `SyndicationContributorEmail:`Le `atom:email` élément enfant de le `atom:contributor` élément.<br /><br /> `SyndicationContributorName:`Le `atom:name` élément enfant de le `atom:contributor` élément.<br /><br /> `SyndicationContributorUri:`Le `atom:uri` élément enfant de le `atom:contributor` élément.<br /><br /> `SyndicationCustomProperty:`Un élément de la propriété personnalisée. Lors du mappage à un élément personnalisé, la cible doit être une expression de chemin d'accès où les éléments imbriqués sont séparés par une barre oblique inverse (`/`) et les attributs sont spécifiés par une esperluette (`@`). Dans l'exemple suivant, la chaîne `UnitsInStock/@ReorderLevel` mappe une valeur de propriété à un attribut nommé `ReorderLevel` sur un élément enfant nommé `UnitsInStock` de l'élément d'entrée racine.<br /><br /> `<Property Name="ReorderLevel" Type="Int16"               m:FC_TargetPath="UnitsInStock/@ReorderLevel"               m:FC_NsPrefix="Northwind"               m:FC_NsUri="http://schemas.examples.microsoft.com/dataservices"               m:FC_KeepInContent="false"               />`<br /><br /> Lorsque la cible est un nom d'élément personnalisé, les attributs `FC_NsPrefix` et `FC_NsUri` doivent également être spécifiés.<br /><br /> `SyndicationPublished:`Le `atom:published` élément.<br /><br /> `SyndicationRights:`Le `atom:rights` élément.<br /><br /> `SyndicationSummary:`Le `atom:summary` élément.<br /><br /> `SyndicationTitle:`Le `atom:title` élément.<br /><br /> `SyndicationUpdated:`Le `atom:updated` élément.<br /><br /> Ces mots clés sont équivalents aux valeurs de l'énumération <xref:System.Data.Services.Common.SyndicationItemProperty> utilisées avec le fournisseur de réflexion.|  
  
> [!NOTE]
>  Les noms et valeurs d'attributs respectent la casse. Les attributs peuvent être appliqués à l'élément `EntityType` ou à un ou plusieurs éléments `Property`, mais pas aux deux.  
  
## <a name="customizing-feeds-with-the-reflection-provider"></a>Personnalisation des flux avec le fournisseur de réflexion  
 Pour personnaliser des flux pour un modèle de données ayant été implémenté à l'aide du fournisseur de réflexion, ajoutez une ou plusieurs instances de l'attribut <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> aux classes qui représentent des types d'entité dans le modèle de données. Les propriétés de la classe <xref:System.Data.Services.Common.EntityPropertyMappingAttribute> correspondent aux attributs de personnalisation du flux décrits dans la section précédente. Voici un exemple de la déclaration du type `Order` avec le mappage de flux personnalisé défini pour les deux propriétés.  
  
> [!NOTE]
>  Le modèle de données pour cet exemple est défini dans la rubrique [Comment : créer un Service de données à l’aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
 [!code-csharp[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customorderfeed)]
 [!code-vb[Astoria Custom Feeds#CustomOrderFeed](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customorderfeed)]  
  
 Ces attributs produisent le flux de données personnalisé suivant pour le jeu d'entités `Orders`. Dans ce personnalisé de flux, le `OrderId` valeur de propriété s’affiche uniquement dans le `title` élément de la `entry` et le `Customer` valeur de propriété s’affiche à la fois dans le `author` élément et en tant que le `Customer` élément de propriété :  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresult.xml#iqueryablefeedresult)]  
  
 Pour plus d’informations, consultez [Comment : personnaliser des flux avec le fournisseur de réflexion](../../../../docs/framework/data/wcf/how-to-customize-feeds-with-the-reflection-provider-wcf-data-services.md).  
  
## <a name="customizing-feeds-with-a-custom-data-service-provider"></a>Personnalisation de flux avec un fournisseur de services de données personnalisé  
 La personnalisation de flux pour un modèle de données défini à l'aide d'un fournisseur de services de données personnalisé est définie pour un type de ressource en appelant le <xref:System.Data.Services.Providers.ResourceType.AddEntityPropertyMappingAttribute%2A> sur l'objet <xref:System.Data.Services.Providers.ResourceType> qui représente un type d'entité dans le modèle de données. Pour plus d’informations, consultez [fournisseurs de services de données personnalisé](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
## <a name="consuming-custom-feeds"></a>Consommation de flux personnalisés  
 Lorsque votre application consomme directement un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux, il doit être en mesure de traiter les éléments personnalisés et les attributs dans le flux retourné. Lorsque vous avez implémenté des flux personnalisés dans votre modèle de données, indépendamment du fournisseur de services de données, le point de terminaison `$metadata` retourne des informations de flux personnalisées sous la forme d'attributs de flux personnalisés dans le CSDL retourné par le service de données. Lorsque vous utilisez la **ajouter une référence de Service** boîte de dialogue ou le [datasvcutil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) outil pour générer des classes de service de données client, le flux personnalisé attributs sont utilisés pour garantir que les demandes et des réponses le service de données sont traitées correctement.  
  
## <a name="feed-customization-considerations"></a>Considérations de personnalisation de flux  
 Tenez compte des considérations suivantes lorsque vous définissez des mappages de flux personnalisés.  
  
-   Le client [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] traite les éléments mappés dans un flux comme s'ils étaient vides lorsqu'ils contiennent seulement un espace blanc. De ce fait, les éléments mappés qui contiennent seulement un espace blanc ne sont pas matérialisés sur le client avec le même espace blanc. Pour conserver cet espace blanc sur le client, vous devez définir la valeur de `KeepInContext` sur `true` dans l'attribut de mappage de flux.  
  
## <a name="versioning-requirements"></a>Conditions requises pour le contrôle de version  
 La personnalisation de flux a les conditions requises pour le contrôle de version de protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] suivantes :  
  
-   La personnalisation de flux requiert que le client et le service de données prennent en charge les versions 2.0 et ultérieures du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .  
  
 Pour plus d’informations, consultez [contrôle de version de Service de données](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fournisseur de réflexion](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
