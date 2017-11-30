---
title: Comparaison du GUID et des valeurs uniqueidentifier
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
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bdd8108261e1e1bc18dd636ba654f7fb6bed981
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Comparaison du GUID et des valeurs uniqueidentifier
Le type de données GUID (Identificateur Global Unique) dans SQL Server est représenté par le type de données `uniqueidentifier`, qui stocke une valeur binaire de 16 octets. Un GUID est un nombre binaire et son usage principal est celui d'identificateur qui doit être unique dans un réseau comportant de nombreux ordinateurs implantés dans de nombreux sites. Il est possible de générer des GUID en appelant la fonction Transact-SQL NEWID et il est garanti qu'ils sont uniques dans le monde entier. Pour plus d'informations, voir « Using uniqueidentifier Data » dans la documentation en ligne de SQL Server.  
  
## <a name="working-with-sqlguid-values"></a>Utilisation de valeurs SqlGuid  
 Comme les valeurs GUID sont longues et obscures, elles ont peu de signification pour les utilisateurs. Si des GUID générés de façon aléatoire sont utilisés pour les valeurs clés et si vous insérez un grand nombre de lignes, vous obtenez des E/S aléatoires dans les index, ce qui peut contribuer à altérer les performances. Les GUID sont également relativement volumineux en comparaison d'autres types de données. En règle générale, il est recommandé d'utiliser les GUID uniquement pour des scénarios très restrictifs pour lesquels aucun autre type de données ne convient.  
  
### <a name="comparing-guid-values"></a>Comparaison de valeurs GUID  
 Des opérateurs de comparaison peuvent être utilisés avec des valeurs `uniqueidentifier`. Toutefois, la mise en ordre n’est pas implémentée en comparant les modèles binaires des deux valeurs. Les seules opérations autorisées sur un `uniqueidentifier` valeur sont les comparaisons (=, <>, \<, >, \<=, > =) et la vérification de la valeur NULL (IS NULL et IS NOT NULL). Aucun autre opérateur arithmétique n'est autorisé.  
  
 <xref:System.Guid> et <xref:System.Data.SqlTypes.SqlGuid> possèdent tous deux une méthode `CompareTo` pour comparer différentes valeurs GUID. Toutefois, `System.Guid.CompareTo` et `SqlTypes.SqlGuid.CompareTo` sont implémentés différemment. <xref:System.Data.SqlTypes.SqlGuid> implémente `CompareTo` à l'aide du comportement SQL Server, dans lequel les six derniers octets d'une valeur sont significatifs. <xref:System.Guid> évalue les 16 octets. L'exemple suivant illustre cette différence de comportement. La première section du code affiche les valeurs <xref:System.Guid> non triées et la seconde les valeurs <xref:System.Guid> triées. La troisième section affiche les valeurs <xref:System.Data.SqlTypes.SqlGuid> triées. La sortie s'affiche sous les codes.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Cet exemple génère les résultats suivants :  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
