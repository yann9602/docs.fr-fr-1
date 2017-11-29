---
title: Formuler des projections
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
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8afd48c6ce7c6313e82a7b74c2271f52833d1f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-projections"></a>Formuler des projections
Les exemples suivants expliquent comment l'instruction `select` dans C# et l'instruction `Select` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] peuvent être associées à d'autres fonctionnalités pour former des projections de requête.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) pour retourner une séquence de noms de contact pour `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) et *types anonymes* pour retourner une séquence de noms de contact et numéros de téléphone pour `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) et *types anonymes* pour retourner une séquence de noms et numéros de téléphone pour les employés. Le `FirstName` et `LastName` les champs sont combinés en un seul champ (`Name`) et le `HomePhone` champ a été renommé en `Phone` dans la séquence résultante.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) et *types anonymes* pour retourner une séquence de tous les `ProductID`s et une valeur calculée nommée `HalfPrice`. Cette valeur correspond à `UnitPrice` divisé par 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) et un *instruction conditionnelle* pour retourner une séquence de nom de produit et la disponibilité des produits.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select` clause (`select` clause en c#) et un *type connu* (Name) pour retourner une séquence de noms d’employés.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `Select` et `Where` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` et `where` en c#) pour retourner un *séquence filtrée* de noms de contact pour les clients de Londres.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise un `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) et *types anonymes* pour renvoyer un *en forme de sous-ensemble* des données sur les clients.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des requêtes imbriquées pour retourner les résultats suivants :  
  
-   Séquence de toutes les commandes et des `OrderID` correspondants.  
  
-   Sous-séquence des éléments dans la commande pour laquelle il existe une remise.  
  
-   Montant enregistré si le coût d'expédition n'est pas inclus.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
