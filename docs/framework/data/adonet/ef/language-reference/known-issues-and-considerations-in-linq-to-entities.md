---
title: "Probl&#232;mes connus dans LINQ to Entities et &#233;l&#233;ments &#224; prendre en consid&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Probl&#232;mes connus dans LINQ to Entities et &#233;l&#233;ments &#224; prendre en consid&#233;ration
Cette section fournit des informations sur les problèmes connus au niveau des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
-   [Requêtes LINQ qui ne peuvent pas être mises en cache](#LINQQueriesThatAreNotCached)  
  
-   [Perte des informations de tri](#OrderingInfoLost)  
  
-   [Entiers non signés non pris en charge](#UnsignedIntsUnsupported)  
  
-   [Erreurs de conversion de type](#TypeConversionErrors)  
  
-   [Référencement de variables non scalaires non pris en charge](#RefNonScalarClosures)  
  
-   [Les requêtes imbriquées peuvent échouer avec SQL Server 2000](#NestedQueriesSQL2000)  
  
-   [Projection dans un type anonyme](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## Requêtes LINQ qui ne peuvent pas être mises en cache  
 Depuis le .NET Framework 4.5, les requêtes LINQ to Entities sont automatiquement mises en cache.  Cependant, les requêtes LINQ to Entities qui appliquent l'opérateur `Enumerable.Contains` aux collections en mémoire ne sont pas automatiquement mises en cache.  Le paramétrage des collections en mémoire dans les requêtes LINQ compilées n'est pas autorisé.  
  
<a name="OrderingInfoLost"></a>   
## Perte des informations de tri  
 La projection de colonnes dans un type anonyme entraînera la perte des informations de tri dans certains requêtes exécutées sur une base de données [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] définie à un niveau de compatibilité de « 80 ».  Cela se produit lorsqu'un nom de colonne figurant dans la liste Order by correspond à un nom de colonne dans le sélecteur, comme l'illustre l'exemple suivant :  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## Entiers non signés non pris en charge  
 La définition d'un type d'entier non signé dans une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] n'est pas pris en charge, car [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ne prend pas en charge les entiers non signés. Si vous spécifiez un entier non signé, une exception d'<xref:System.ArgumentException> est levée pendant la traduction des expressions de la requête, comme l'illustre l'exemple suivant.  Dans cet exemple, la requête vise à extraire une commande dont le numéro est 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## Erreurs de conversion de type  
 En Visual Basic, lorsqu'une propriété est mappée à une colonne de type bit SQL Server avec une valeur de 1 à l'aide de la fonction `CByte`, une exception <xref:System.Data.SqlClient.SqlException> est levée avec un message « Erreur de dépassement arithmétique ».  L'exemple suivant interroge la colonne `Product.MakeFlag` dans l'exemple de base de données AdventureWorks et une exception est levée lorsque les résultats de la requête sont itérés.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## Référencement de variables non scalaires non pris en charge  
 Le référencement d'une variable non scalaire, telle qu'une entité, dans une requête n'est pas pris en charge.  Lorsqu'une telle requête s'exécute, une exception <xref:System.NotSupportedException> est levée avec un message indiquant « Impossible de créer une valeur constante de type «`EntityType`.  Seuls les types primitifs \(« Int32, String et Guid »\) sont pris en charge dans ce contexte. »  
  
> [!NOTE]
>  Le référencement d'une collection de variables scalaires est pris en charge.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## Les requêtes imbriquées peuvent échouer avec SQL Server 2000  
 Avec SQL Server 2000, les requêtes LINQ to Entities peuvent échouer si elles produisent des requêtes Transact\-SQL imbriquées qui ont trois niveaux ou plus de profondeur.  
  
<a name="ProjectToAnonymousType"></a>   
## Projection dans un type anonyme  
 Si vous définissez le chemin d'accès de votre requête initiale pour inclure des objets connexes à l'aide de la méthode <xref:System.Data.Objects.ObjectQuery%601.Include%2A> sur <xref:System.Data.Objects.ObjectQuery%601> et si vous utilisez LINQ pour projeter les objets retournés dans un type anonyme, les objets spécifiés dans la méthode d'inclusion ne sont pas inclus dans les résultats de la requête.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Pour obtenir des objets connexes, ne projetez pas les types retournés dans un type anonyme.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## Voir aussi  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)