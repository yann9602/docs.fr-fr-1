---
title: "Conversion des Types de données (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 53d8ad292891a567e13ec8a5396bcc114b379351
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-visual-basic"></a>Conversion des Types de données (Visual Basic)
Méthodes de conversion modifient le type d’objets d’entrée.  
  
 Les opérations de conversion dans les requêtes LINQ sont utiles dans une variété d’applications. Voici quelques exemples :  
  
-   Le <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>méthode peut être utilisée pour masquer l’implémentation personnalisée d’un type d’opérateur de requête standard.</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>  
  
-   Le <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>méthode peut être utilisée pour activer des collections non paramétrées pour l’interrogation LINQ.</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>  
  
-   Le <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>, et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>méthodes peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu'à ce que la requête est énumérée.</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de type de données.  
  
 Les méthodes de conversion de cette table dont le nom commence par « As » modifient le type statique de la collection source, mais ne l’énumèrent pas. Les méthodes qui commencent par « To » énumèrent la collection source et placer les éléments dans la collection correspondante type.  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|Retourne l’entrée typée en tant que <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>|Non applicable.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|Convertit un (générique) <xref:System.Collections.IEnumerable> <xref:System.Linq.IQueryable>.</xref:System.Linq.IQueryable> (générique)</xref:System.Collections.IEnumerable>|Non applicable.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|Convertit les éléments d’une collection en un type spécifié.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|Filtre les valeurs, en fonction de leur capacité à être casté en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|Convertit une collection vers un tableau. Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|Met des éléments dans un <xref:System.Collections.Generic.Dictionary%602>basé sur une fonction de sélection de clé.</xref:System.Collections.Generic.Dictionary%602> Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|Convertit une collection en un <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601> Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|Met des éléments dans un <xref:System.Linq.Lookup%602>(un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélection de clé.</xref:System.Linq.Lookup%602> Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe de requête Expression  
 Le code suivant exemple utilise le `From As` clause pour convertir un type en un sous-type avant d’accéder à un membre qui est uniquement disponible sur le sous-type.  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [La Clause FROM](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Comment : interroger un ArrayList avec LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
