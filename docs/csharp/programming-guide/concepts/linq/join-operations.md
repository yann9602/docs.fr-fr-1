---
title: "Opérations de jointure (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 158d035985dae0d1c1daf0f276a9df7b913f2263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="join-operations-c"></a>Opérations de jointure (C#)
Une *jointure* de deux sources de données est l’association des objets d’une source de données aux objets qui partagent un attribut commun dans une autre source de données.  
  
 La jointure est une opération importante dans les requêtes qui ciblent les sources de données dont les relations ne peuvent pas être suivies directement. En programmation orientée objet, cela peut correspondre à une corrélation entre objets qui n'est pas modélisée, par exemple la direction vers l'arrière dans une relation à sens unique. Voici un exemple de relation à sens unique : une classe Customer a une propriété de type City, alors que la classe City n'a aucune propriété correspondant à une collection d'objets Customer. Si vous avez une liste d'objets City et si vous souhaitez rechercher tous les clients de chaque ville, vous pouvez recourir à une opération de jointure.  
  
 Les méthodes de jointure fournies dans le framework LINQ sont <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>. Ces méthodes effectuent des équijointures, qui sont des jointures associant deux sources de données en fonction de l’égalité de leurs clés. (À titre de comparaison, Transact-SQL prend en charge d'autres opérateurs de jointure que « égal », par exemple, l'opérateur « inférieur à »). Dans le contexte des bases de données relationnelles, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne, qui est un type de jointure dans lequel seuls sont retournés les objets qui ont une correspondance dans l’autre jeu de données. La méthode <xref:System.Linq.Enumerable.GroupJoin%2A> n’a aucun équivalent direct dans le contexte des bases de données relationnelles, mais elle implémente un sur-ensemble de jointures internes et de jointures externes gauches. Une jointure externe gauche est une jointure qui retourne chaque élément de la source de données (gauche), même si elle n’a pas d’éléments corrélés dans l’autre source de données.  
  
 L'illustration suivante présente une vue conceptuelle de deux ensembles, ainsi que leurs éléments inclus dans une jointure interne ou une jointure externe gauche.  
  
 ![Deux cercles se chevauchant montrant l’interne/externe.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|Joint deux séquences selon les fonctions de sélection de clé et extrait des paires de valeurs.|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|Joint deux séquences selon les fonctions de sélection de clé et regroupe les résultats correspondants pour chaque élément.|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>  
 [Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Formuler des jointures et des requêtes entre les produits](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)  
 [join, clause](../../../../csharp/language-reference/keywords/join-clause.md)  
 [Comment : effectuer des opérations de jointure à l’aide de clés composites](../../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)  
 [Guide pratique pour joindre du contenu issu de fichiers non similaires (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)  
 [Comment : classer les résultats d’une clause Join](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [Comment : effectuer des opérations de jointure personnalisées](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)  
 [Comment : effectuer des jointures groupées](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)  
 [Comment : effectuer des jointures internes](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)  
 [Comment : effectuer des jointures externes gauches](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)  
 [Guide pratique pour remplir des collections d’objets issues de plusieurs sources (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
