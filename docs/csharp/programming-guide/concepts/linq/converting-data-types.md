---
title: "Conversion des types de données (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 454fb0ce937d7d20dfce26d92dbf49de24f062f0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="converting-data-types-c"></a>Conversion des types de données (C#)
Les méthodes de conversion changent le type d’objets en entrée.  
  
 Les opérations de conversion dans les requêtes LINQ sont utiles dans diverses applications. En voici quelques exemples :  
  
-   La méthode <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName> peut être utilisée pour masquer l’implémentation personnalisée d’un type d’un opérateur de requête standard.  
  
-   La méthode <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName> peut être utilisée pour activer des collections non paramétrables pour l’interrogation LINQ.  
  
-   Les méthodes <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> et <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> peuvent être utilisées pour forcer l’exécution immédiate de la requête au lieu de la différer jusqu’à ce que la requête soit énumérée.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant répertorie les méthodes d’opérateur de requête standard qui effectuent des conversions de types de données.  
  
 Les méthodes de conversion de ce tableau dont les noms commencent par "As" modifient le type statique de la collection source mais ne l’énumèrent pas. Les méthodes dont les noms commencent par "To" énumèrent la collection source et placent les éléments dans le type de collection correspondant.  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Retourne l’entrée typée comme <xref:System.Collections.Generic.IEnumerable%601>.|Non applicable.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|Convertit un <xref:System.Collections.IEnumerable> (générique) en <xref:System.Linq.IQueryable> (générique).|Non applicable.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|Effectue un cast des éléments d’une collection en un type spécifié.|Utilisez une variable de portée explicitement typée. Exemple :<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|Filtre les valeurs en fonction de leur capacité à faire l’objet d’un cast en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|Convertit une collection en un tableau. Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|Place des éléments dans un <xref:System.Collections.Generic.Dictionary%602> basé sur une fonction de sélecteur de clés. Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|Convertit une collection en <xref:System.Collections.Generic.List%601>. Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|Place des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés. Cette méthode force l’exécution de la requête.|Non applicable.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe d’expression de requête  
 L’exemple de code suivant utilise une variable de portée explicitement typée pour effectuer un cast d’un type en un sous-type avant d’accéder à un membre qui est disponible uniquement sur le sous-type.  
  
```csharp  
class Plant  
{  
    public string Name { get; set; }  
}  
  
class CarnivorousPlant : Plant  
{  
    public string TrapType { get; set; }  
}  
  
static void Cast()  
{  
    Plant[] plants = new Plant[] {  
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },  
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },  
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },  
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }  
    };  
  
    var query = from CarnivorousPlant cPlant in plants  
                where cPlant.TrapType == "Snap Trap"  
                select cPlant;  
  
    foreach (Plant plant in query)  
        Console.WriteLine(plant.Name);  
  
    /* This code produces the following output:  
  
        Venus Fly Trap  
        Waterwheel Plant  
    */  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>   
 [Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [from, clause](../../../../csharp/language-reference/keywords/from-clause.md)   
 [Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Guide pratique pour interroger un ArrayList avec LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)

