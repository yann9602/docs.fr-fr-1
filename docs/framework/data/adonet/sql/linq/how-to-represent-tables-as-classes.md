---
title: "Comment : représenter des tables en tant que classes"
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
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 30bdb3334b574053595565e94993563959f49694
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-tables-as-classes"></a>Comment : représenter des tables en tant que classes
Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribut pour désigner une classe comme classe d’entité associée à une table de base de données.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Pour mapper une classe à une table de base de données  
  
-   Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la déclaration de classe.  
  
## <a name="example"></a>Exemple  
 Le code suivant établit la classe `Customer` comme une classe d'entité associée à la table de base de données `Customers`.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Il n'est pas nécessaire de spécifier la propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> si le nom peut être déduit. Si vous ne spécifiez pas de nom, on considère qu'il s'agit du même nom que pour la propriété ou le champ.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
