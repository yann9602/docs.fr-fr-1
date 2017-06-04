---
title: "Proc&#233;dure&#160;: appeler des fonctions canoniques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: appeler des fonctions canoniques
La classe <xref:System.Data.Objects.EntityFunctions> contient des méthodes qui exposent les fonctions canoniques à utiliser dans les requêtes LINQ to Entities.  Pour plus d'informations sur les fonctions canoniques, consultez [Fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  Les méthodes <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> et <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> dans la classe <xref:System.Data.Objects.EntityFunctions> n'ont pas d'équivalents de fonction canonique.  
  
 Les fonctions canoniques qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique \(également appelées fonctions canoniques d'agrégation\) peuvent être appelées directement.  Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities.  Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction.  Pour plus d'informations, consultez le second exemple ci\-dessous.  
  
 Vous pouvez appeler certaines fonctions canoniques en utilisant des méthodes CLR \(Common Language Runtime\) dans les requêtes LINQ to Entities.  Pour obtenir la liste des méthodes CLR qui sont mappées aux fonctions canoniques, consultez [Mappage de méthodes CLR à des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## Exemple  
 L'exemple ci\-dessous utilise le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> pour retourner tous les produits pour lesquels la différence entre `SellEndDate` et `SellStartDate` est inférieure à 365 jours :  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## Exemple  
 L'exemple ci\-dessous utilise le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832).  L'exemple appelle directement la méthode <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> d'agrégation pour retourner l'écart type des sous\-totaux `SalesOrderHeader`.  Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## Voir aussi  
 [Appel de fonctions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)   
 [Requêtes dans LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)