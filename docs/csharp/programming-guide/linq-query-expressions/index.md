---
redirect_url: /dotnet/articles/csharp/linq/index
caps.handback.revision: 21
---
# Expressions de requ&#234;te LINQ (Guide de programmation&#160;C#)
[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext-md.md)] est le nom d'un ensemble de technologies basé sur l'intégration de fonctions de requête directement dans le langage C\# \(également dans Visual Basic et potentiellement dans tout autre langage .NET\).  Avec [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], une requête est désormais une construction de langage de premier ordre, comme les classes, les méthodes, les événements, etc.  
  
 Pour un développeur qui écrit des requêtes, la partie « intégrée par langage » la plus visible de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] est l'expression de requête.  Les expressions de requête sont écrites dans une *syntaxe de requête* déclarative, introduite dans C\# 3.0.  En utilisant la syntaxe de requête, vous pouvez même effectuer des opérations de filtrage, de classement et de regroupement complexes sur les sources de données avec une quantité minimale de code.  Vous utilisez les mêmes modèles de base d'expression de requête pour interroger et transformer des données dans les bases de données SQL, les groupes de données du [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)], les documents XML et les flux de données, ainsi que les collections .NET.  
  
 L'exemple suivant présente l'ensemble de l'opération de requête.  L'opération complète inclut la création d'une source de données, la définition de l'expression de requête et l'exécution de la requête dans une instruction `foreach`.  
  
 [!code-cs[csProgGuideLINQ#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
 Pour plus d'informations sur l'essentiel de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] en C\#, consultez [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
## Vue d'ensemble des expressions de requête  
  
-   Les expressions de requête peuvent être utilisées pour interroger et transformer des données à partir de n'importe quelle source de données [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].  Par exemple, une requête unique peut récupérer des données d'une base de données SQL et générer un flux de données XML en sortie.  
  
-   Les expressions de requête sont faciles à maîtriser car elles utilisent de nombreuses constructions de langage C\# familières.  Pour plus d'informations, consultez [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
-   Les variables d'une expression de requête sont toutes fortement typées, bien que dans de nombreux cas vous ne devez pas fournir le type explicitement parce que le compilateur peut le déduire.  Pour plus d'informations, consultez [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
-   Une requête est exécutée une fois que vous avez itéré la variable de requête dans une instruction `foreach`.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   À la compilation, les expressions de requête sont converties en appels de méthode d'opérateur de requête standard d'après les règles présentées dans la spécification C\#.  Toute requête qui peut être exprimée en utilisant la syntaxe de requête peut également être exprimée en utilisant la syntaxe de méthode.  Toutefois, dans la plupart des cas, la syntaxe de requête est plus lisible et concise.  Pour plus d'informations, consultez [Spécification du langage C\#](../../../csharp/language-reference/language-specification.md) et [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
-   En règle générale, quand vous écrivez des requêtes [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], nous vous recommandons d'utiliser la syntaxe de requête chaque fois que cela est possible et la syntaxe de méthode lorsque cela est nécessaire.  Il y a aucune différence en termes de sémantique ou de performance entre les deux différentes formes.  Les expressions de requête sont souvent plus lisibles que les expressions équivalentes écrites dans la syntaxe de méthode.  
  
-   Quelques\-unes des opérations de requête, telles que <xref:System.Linq.Enumerable.Count%2A> ou <xref:System.Linq.Enumerable.Max%2A>, n'ont aucune clause d'expression de requête équivalente et doivent par conséquent être exprimées comme un appel de méthode.  La syntaxe de méthode peut être associée de plusieurs façons avec la syntaxe de requête.  Pour plus d'informations, consultez [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
-   Les expressions de requête peuvent être compilées en arborescences d'expression ou en délégués, selon le type auquel la requête s'applique.  Les requêtes <xref:System.Collections.Generic.IEnumerable%601> sont compilées en délégués.  Les requêtes <xref:System.Linq.IQueryable> et <xref:System.Linq.IQueryable%601> sont compilées en arborescences d'expression.  Pour plus d'informations, consultez [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Le tableau suivant répertorie les rubriques qui fournissent des informations supplémentaires à propos des requêtes et des exemples de code pour les tâches courantes.  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Concepts de base des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/query-expression-basics.md)|Introduit des concepts de requête fondamentaux et fournit des exemples de syntaxe de requête de C\#.|  
|[Comment : écrire des requêtes LINQ en C\#](../../../csharp/programming-guide/linq-query-expressions/how-to-write-linq-queries.md)|Fournit des exemples de plusieurs types de base d'expressions de requête.|  
|[Comment : gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)|Comment et quand déplacer le code potentiel levant des exceptions à l'extérieur d'une expression de requête.|  
|[How to: Populate Object Collections from Multiple Sources \(LINQ\)](../Topic/How%20to:%20Populate%20Object%20Collections%20from%20Multiple%20Sources%20\(LINQ\).md)|Comment utiliser l'instruction `select` pour fusionner des données de sources différentes dans un nouveau type.|  
|[Comment : regrouper les résultats d'une requête](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)|Montre différentes manières d'utiliser la clause `group`.|  
|[Comment : créer un groupe imbriqué](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)|Montre comment créer des groupes imbriqués.|  
|[Comment : effectuer une sous\-requête sur une opération de regroupement](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)|Montre comment utiliser une sous\-expression dans une requête comme une source de données pour une nouvelle requête.|  
|[Comment : regrouper des résultats par clés contiguës](../../../csharp/programming-guide/linq-query-expressions/how-to-group-results-by-contiguous-keys.md)|Explique comment implémenter un opérateur de requête standard thread\-safe capable de réaliser des opérations de regroupement sur des sources de données en continu.|  
|[Comment : spécifier dynamiquement des filtres de prédicat au moment de l'exécution](../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)|Montre comment fournir un nombre arbitraire de valeurs à utiliser dans les comparaisons d'égalité dans une clause `where`.|  
|[Comment : stocker les résultats d’une requête dans la mémoire](../../../csharp/programming-guide/linq-query-expressions/how-to-store-the-results-of-a-query-in-memory.md)|Montre comment matérialiser et stocker les résultats d'une requête sans nécessairement utiliser une boucle `foreach`.|  
|[Comment : retourner une requête à partir d'une méthode](../../../csharp/programming-guide/linq-query-expressions/how-to-return-a-query-from-a-method.md)|Montre comment retourner des variables de requête à partir de méthodes et comment les passer aux méthodes comme paramètres d'entrée.|  
|[Comment : effectuer des opérations de jointure personnalisées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)|Montre comment effectuer des opérations de jointure à partir de n'importe quel type de fonction de prédicat.|  
|[Comment : effectuer des opérations de jointure à l'aide de clés composites](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)|Montre comment joindre deux sources basées sur plusieurs clés correspondantes.|  
|[Comment : classer les résultats d'une clause Join](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)|Montre comment classer une séquence générée par une opération de jointure.|  
|[Comment : effectuer des jointures internes](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)|Montre comment effectuer une jointure interne dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].|  
|[Comment : effectuer des jointures groupées](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)|Montre comment générer une jointure groupée dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].|  
|[Procédures : effectuer des jointures externes gauches](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)|Montre comment générer une jointure externe gauche dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].|  
|[Comment : gérer des valeurs Null dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-null-values-in-query-expressions.md)|Montre comment gérer des valeurs Null dans les requêtes [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)].|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Basic LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)   
 [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Fonctionnement des requêtes Linq to Objects Queries \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=112389)   
 [Lecture et écriture de requêtes \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=112391)   
 [Qu'est\-ce qu'une collection ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=112394)   
 [Liens tous azimuts : liste de fournisseurs LINQ \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=112411)