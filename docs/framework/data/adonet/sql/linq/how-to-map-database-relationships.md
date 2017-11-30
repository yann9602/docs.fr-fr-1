---
title: "Comment : mapper des relations de base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: aa771fbde889febb269f49603f7d2a2ac5c67784
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-map-database-relationships"></a>Comment : mapper des relations de base de données
Vous pouvez encoder comme références de propriété dans votre classe d'entité toutes les relations de données qui seront toujours fixes. Dans l'exemple de base de données Northwind, par exemple, comme les clients passent généralement des commandes, il existe toujours une relation dans le modèle entre les clients et leurs commandes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]définit un <xref:System.Data.Linq.Mapping.AssociationAttribute> attribut pour représenter ces relations. Cet attribut est utilisé avec les types <xref:System.Data.Linq.EntitySet%601> et <xref:System.Data.Linq.EntityRef%601> pour représenter ce qui serait une relation de clé étrangère dans une base de données. Pour plus d’informations, consultez la section AssociationAttribute de [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Les valeurs des propriétés AssociationAttribute et ColumnAttribute Storage respectent la casse. Assurez-vous, par exemple que les valeurs utilisées dans l'attribut de la propriété AssociationAttribute.Storage correspondent à la casse des noms de propriétés correspondants utilisés ailleurs dans le code. Cela s'applique à tous les langages de programmation .NET, y compris à ceux qui ne respectent généralement pas la casse, notamment [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Pour plus d'informations sur la propriété Storage, consultez <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
 La plupart des relations sont de type un-à-plusieurs, comme dans l'exemple présenté ultérieurement dans cette rubrique. Vous pouvez également représenter les relations de type un-à-un et plusieurs à plusieurs comme suit :  
  
-   Relation un-à-un : représentez ce type de relation en incluant <xref:System.Data.Linq.EntitySet%601> des deux côtés.  
  
     Par exemple, considérez un `Customer` - `SecurityCode` relation afin que le code de sécurité du client est introuvable dans le `Customer` de table et sont accessibles uniquement par les personnes autorisées.  
  
-   Plusieurs-à-plusieurs : dans des relations plusieurs-à-plusieurs, la clé primaire de la table de liens (également appelée la *jonction* table) est souvent formée par une combinaison des clés étrangères des deux autres tables.  
  
     Par exemple, considérez un `Employee` - `Project` relation plusieurs-à-plusieurs formée à l’aide de table de liens `EmployeeProject`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige qu'une telle relation soit modélisée à l'aide de trois classes : `Employee`, `Project` et `EmployeeProject`. Dans ce cas, la modification de la relation entre `Employee` et `Project` peut sembler nécessiter une mise à jour de la clé primaire `EmployeeProject`. Toutefois, la modélisation recommandée dans ce cas consiste à supprimer le `EmployeeProject` existant et à créer un autre `EmployeeProject`.  
  
    > [!NOTE]
    >  Les relations dans les bases de données relationnelles sont généralement modélisées comme des valeurs de clé étrangère qui font référence aux clés primaires d'autres tables. Pour naviguer entre elles, vous associez explicitement les deux tables à l’aide de relationnelle *jointure* opération.  
    >   
    >  Objets de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sur l’autre revanche, reportez-vous à l’autre à l’aide de références de propriété ou des collections de références que vous accédez à l’aide de *point* notation.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple un-à-plusieurs suivant, la classe `Customer` a une propriété qui déclare la relation entre les clients et leurs commandes.  La propriété `Orders` est de type <xref:System.Data.Linq.EntitySet%601>. Ce type signifie que cette relation est de type un-à-plusieurs (un client et plusieurs commandes). La propriété <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> est utilisée pour décrire comment cette association est accomplie, à savoir, en spécifiant le nom de la propriété dans la classe connexe à comparer avec celle-ci. Dans cet exemple, le `CustomerID` propriété est comparée, comme une base de données *jointure* compare la valeur de cette colonne.  
  
> [!NOTE]
>  Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour créer une association entre des classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez également inverser la situation. Au lieu d'utiliser la classe `Customer` pour décrire l'association entre les clients et les commandes, vous pouvez utiliser la classe `Order`. La classe `Order` utilise le type <xref:System.Data.Linq.EntityRef%601> pour décrire la relation au client, comme dans l'exemple de code suivant.  
  
> [!NOTE]
>  Le <xref:System.Data.Linq.EntityRef%601> classe prend en charge *chargement différé*. Pour plus d’informations, *consultez* [différée / chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
