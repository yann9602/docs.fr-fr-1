---
title: "Comment : appeler des fonctions de chaînes canoniques"
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
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2c33bd80635d2bcfb98421c37860596b1367c86b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-canonical-functions"></a>Comment : appeler des fonctions de chaînes canoniques
La classe <xref:System.Data.Objects.EntityFunctions> contient des méthodes qui exposent les fonctions canoniques à utiliser dans les requêtes LINQ to Entities. Pour plus d’informations sur les fonctions canoniques, consultez [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  Les méthodes <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> et <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> dans la classe <xref:System.Data.Objects.EntityFunctions> n'ont pas d'équivalents de fonction canonique.  
  
 Les fonctions canoniques qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions canoniques d'agrégation) peuvent être appelées directement. Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities. Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction. Pour plus d'informations, consultez le second exemple ci-dessous.  
  
 Vous pouvez appeler certaines fonctions canoniques en utilisant des méthodes CLR (Common Language Runtime) dans les requêtes LINQ to Entities. Pour obtenir la liste des méthodes CLR qui mappent aux fonctions canoniques, consultez [méthode CLR pour le mappage de fonction canonique](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> pour retourner tous les produits pour lesquels la différence entre `SellEndDate` et `SellStartDate` est inférieure à 365 jours :  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). L'exemple appelle directement la méthode <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> d'agrégation pour retourner l'écart type des sous-totaux `SalesOrderHeader`. Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Appel de fonctions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
