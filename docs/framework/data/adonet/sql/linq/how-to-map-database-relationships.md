---
title: "Proc&#233;dure&#160;: mapper des relations de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: mapper des relations de base de donn&#233;es
Vous pouvez encoder comme références de propriété dans votre classe d'entité toutes les relations de données qui seront toujours fixes.  Dans l'exemple de base de données Northwind, par exemple, comme les clients passent généralement des commandes, il existe toujours une relation dans le modèle entre les clients et leurs commandes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit un attribut <xref:System.Data.Linq.Mapping.AssociationAttribute> pour faciliter la représentation de telles relations.  Cet attribut est utilisé avec les types <xref:System.Data.Linq.EntitySet%601> et <xref:System.Data.Linq.EntityRef%601> pour représenter ce qui serait une relation de clé étrangère dans une base de données. Pour plus d'informations, consultez la section AssociationAttribute de la rubrique [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
> [!NOTE]
>  Les valeurs des propriétés AssociationAttribute et ColumnAttribute Storage respectent la casse.  Assurez\-vous, par exemple que les valeurs utilisées dans l'attribut de la propriété AssociationAttribute.Storage correspondent à la casse des noms de propriétés correspondants utilisés ailleurs dans le code.  Cela s'applique à tous les langages de programmation .NET, y compris à ceux qui ne respectent généralement pas la casse, notamment [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)].  Pour plus d'informations sur la propriété Storage, consultez <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=fullName>.  
  
 La plupart des relations sont de type un\-à\-plusieurs, comme dans l'exemple présenté ultérieurement dans cette rubrique.  Vous pouvez également représenter les relations de type un\-à\-un et plusieurs à plusieurs comme suit :  
  
-   Relation un\-à\-un : représentez ce type de relation en incluant <xref:System.Data.Linq.EntitySet%601> des deux côtés.  
  
     Par exemple, considérons une relation `Customer`\-`SecurityCode` créée afin que le code de sécurité du client ne soit pas trouvé dans la table `Customer` et que seules les personnes autorisées puissent y accéder.  
  
-   Relations plusieurs à plusieurs : dans ce type de relations, la clé primaire de la table de liens \(également nommée table de *jointure*\) est souvent formée par une combinaison des clés étrangères des deux autres tables.  
  
     Par exemple, considérons une relation `Employee`\-`Project` de type plusieurs à plusieurs formée à l'aide de la table de liens `EmployeeProject`.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exige qu'une telle relation soit modélisée à l'aide de trois classes : `Employee`, `Project` et `EmployeeProject`.  Dans ce cas, la modification de la relation entre `Employee` et `Project` peut sembler nécessiter une mise à jour de la clé primaire `EmployeeProject`.  Toutefois, la modélisation recommandée dans ce cas consiste à supprimer le `EmployeeProject` existant et à créer un autre `EmployeeProject`.  
  
    > [!NOTE]
    >  Les relations dans les bases de données relationnelles sont généralement modélisées comme des valeurs de clé étrangère qui font référence aux clés primaires d'autres tables.  Pour naviguer entre elles, vous associez explicitement les deux tables en utilisant une opération de *jointure* relationnelle.  
    >   
    >  En revanche, les objets de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] font référence les uns aux autres en utilisant les références de propriété ou de collection dans lesquelles vous naviguez à l'aide de la notation à *points*.  
  
## Exemple  
 Dans l'exemple un\-à\-plusieurs suivant, la classe `Customer` a une propriété qui déclare la relation entre les clients et leurs commandes.  La propriété `Orders` est de type <xref:System.Data.Linq.EntitySet%601>.  Ce type signifie que cette relation est de type un\-à\-plusieurs \(un client et plusieurs commandes\).  La propriété <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> est utilisée pour décrire comment cette association est accomplie, à savoir, en spécifiant le nom de la propriété dans la classe connexe à comparer avec celle\-ci.  Dans cet exemple, la propriété `CustomerID` est comparée, comme une *jointure* de base de données serait comparée à cette valeur de colonne.  
  
> [!NOTE]
>  Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour créer une association entre des classes.  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## Exemple  
 Vous pouvez également inverser la situation.  Au lieu d'utiliser la classe `Customer` pour décrire l'association entre les clients et les commandes, vous pouvez utiliser la classe `Order`.  La classe `Order` utilise le type <xref:System.Data.Linq.EntityRef%601> pour décrire la relation au client, comme dans l'exemple de code suivant.  
  
> [!NOTE]
>  La classe <xref:System.Data.Linq.EntityRef%601> prend en charge le *chargement différé*.  Pour plus d'informations, *consultez*[Comparaison entre le chargement différé et le chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## Voir aussi  
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)   
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)