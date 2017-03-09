---
redirect_url: /dotnet/articles/csharp/linq/join-by-using-composite-keys
caps.handback.revision: 8
---
# Comment&#160;: effectuer des op&#233;rations de jointure &#224; l&#39;aide de cl&#233;s composites (Guide de programmation&#160;C#)
Cet exemple indique comment exécuter des opérations de jointure dans lesquelles vous souhaitez utiliser plusieurs clés pour définir une correspondance.  Pour ce faire, vous devez utiliser une clé composite.  Vous créez une clé composite comme un type anonyme ou nommé typé avec les valeurs que vous souhaitez comparer.  Si la variable de requête doit être passée au\-delà des limites de méthode, utilisez un type nommé qui substitue <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> pour la clé.  Les noms des propriétés et l'ordre dans lequel elles se produisent doit être identique dans chaque clé.  
  
## Exemple  
 L'exemple suivant montre comment utiliser une clé composite pour joindre des données de trois tables :  
  
```  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,         d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 L'inférence de type sur les clés composite dépend des noms des propriétés dans les clés et de l'ordre dans lequel elles se produisent.  Si les propriétés dans les séquences sources n'ont pas les mêmes noms, vous devez assigner de nouveaux noms dans les clés.  Par exemple, si la table `Orders` et la table `OrderDetails` utilisent chacune des noms différents pour leurs colonnes, vous pourriez créer des clés composites en assignant des noms identiques dans les types anonymes :  
  
```  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 Des clés composites peuvent également être utilisées dans une clause `group`.  
  
## Compilation du code  
  
-   Pour compiler et exécuter ce code, effectuez la procédure suivante :  
  
-   Ouvrez [Comment : se connecter à la base de données Northwind](../Topic/How%20to:%20Connect%20to%20the%20Northwind%20Database.md) et suivez les instructions pour configurer le projet et créer la connexion de base de données.  Pour plus d'informations, consultez [Comment : installer des exemples de bases de données](../Topic/How%20to:%20Install%20Sample%20Databases.md).  
  
-   Dans samples.cs, créez une nouvelle méthode vide qui accepte un paramètre d'entrée Northwind nommé db \(similaire aux autres méthodes dans ce fichier\).  Collez le code de cet exemple dans le corps de méthode.  
  
-   Modifiez program.cs pour appeler la nouvelle méthode à partir de `Main`.  
  
-   Appuyez sur F5 pour compiler et exécuter la requête.  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [join, clause](../../../csharp/language-reference/keywords/join-clause.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)