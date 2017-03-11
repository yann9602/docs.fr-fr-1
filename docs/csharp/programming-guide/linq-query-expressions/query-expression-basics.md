---
redirect_url: /dotnet/articles/csharp/linq/query-expression-basics
caps.handback.revision: 32
---
# Concepts de base des expressions de requ&#234;te (Guide de programmation&#160;C#)
## Qu'est\-ce qu'une requête et quel est son rôle ?  
 Une *requête* est un jeu d'instructions qui décrit quelles données doivent être récupérées à partir d'une source  \(ou de sources\) de données fournie, et quelle forme et organisation les données retournées doivent avoir.  Une requête est distincte des résultats qu'elle génère.  
  
 De manière générale, les données sources sont organisées logiquement comme une séquence d'éléments du même type.  Une table de base de données SQL contient une séquence de lignes.  De même, un [!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] <xref:System.Data.DataTable> contient une séquence d'objets <xref:System.Data.DataRow>.  Un fichier XML contient une « séquence » d'éléments XML \(bien que ceux\-ci soient organisés hiérarchiquement dans une arborescence\).  Une collection en mémoire contient une séquence d'objets.  
  
 Du point de vue d'une application, le type et la structure spécifiques des données sources d'origine ne sont pas importants.  L'application consulte toujours les données sources comme une collection <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.  Dans [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)], les données sources sont rendues visibles comme un `IEnumerable`\<<xref:System.Xml.Linq.XElement>\>.  Dans [!INCLUDE[linq_dataset](../../../csharp/programming-guide/linq-query-expressions/includes/linq-dataset-md.md)], c'est un `IEnumerable`\<<xref:System.Data.DataRow>\>.  Dans [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)], c'est un `IEnumerable` ou un `IQueryable` de tout objet personnalisé que vous avez défini pour représenter les données dans la table SQL.  
  
 Compte tenu de cette séquence source, une requête peut effectuer l'une des trois actions suivantes :  
  
-   Récupérer un sous\-ensemble des éléments pour générer une nouvelle séquence sans modifier les éléments individuels.  La requête peut alors trier ou grouper la séquence retournée de plusieurs façons, comme indiqué dans l'exemple suivant \(supposons que `scores` est un `int[]`\) :  
  
     [!code-cs[csrefQueryExpBasics#45](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_1.cs)]  
  
-   Récupérer une séquence d'éléments comme dans l'exemple précédent, mais les transformer en un nouveau type d'objet.  Par exemple, une requête peut récupérer uniquement les noms de certains enregistrements de client dans une source de données.  Ou elle peut récupérer l'enregistrement complet, puis l'utiliser pour construire un autre type d'objet en mémoire, voire des données XML, avant de générer la séquence de résultat final.  L'exemple suivant affiche une transformation d'un `int` en `string`.  Notez le nouveau type de `highScoresQuery`.  
  
     [!code-cs[csrefQueryExpBasics#46](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_2.cs)]  
  
-   Récupérer une valeur singleton sur les données source, telle que :  
  
    -   Nombre d'éléments qui correspondent à une certaine condition.  
  
    -   Élément qui a la valeur plus grande ou la plus petite.  
  
    -   Premier élément qui correspond à une condition, ou somme de valeurs particulières dans un jeu d'éléments spécifié.  Par exemple, la requête suivante retourne le nombre de scores supérieur à 80 à partir du tableau d'entiers `scores` :  
  
     [!code-cs[csrefQueryExpBasics#47](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_3.cs)]  
  
     Dans l'exemple précédent, notez l'utilisation de parenthèses autour de l'expression de requête avant l'appel à la méthode `Count`.  Vous pouvez également exprimer ceci en utilisant une nouvelle variable pour stocker le résultat concret.  Cette technique est plus explicite, car elle conserve la variable qui stocke la requête à un emplacement distinct de la requête qui stocke un résultat.  
  
     [!code-cs[csrefQueryExpBasics#48](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_4.cs)]  
  
 Dans l'exemple précédent, la requête est exécutée dans l'appel à `Count`, car `Count` doit itérer au sein des résultats afin de déterminer le nombre d'éléments retourné par `highScoresQuery`  
  
## Qu'est\-ce qu'une expression de requête ?  
 Une *expression de requête* est une requête exprimée dans la syntaxe de la requête.  Une expression de requête est une construction de langage de premier ordre.  Elle est similaire à toute autre expression et peut être utilisée dans tous les contextes dans lesquels une expression C\# est valide.  Une expression de requête se compose d'un jeu de clauses écrit dans une syntaxe déclarative semblable à du SQL ou du XQuery.  Chaque clause contient à son tour une ou plusieurs expressions C\#, et ces expressions peuvent elles\-mêmes être une expression de requête ou contenir une expression de requête.  
  
 Une expression de requête doit commencer par une clause [from](../../../csharp/language-reference/keywords/from-clause.md) et doit se terminer par une clause [select](../../../csharp/language-reference/keywords/select-clause.md) ou [group](../../../csharp/language-reference/keywords/group-clause.md).  Entre la première clause `from` et la dernière clause `select` ou `group`, elle peut contenir une ou plusieurs clauses facultatives : [where](../../../csharp/language-reference/keywords/where-clause.md), [orderby](../../../csharp/language-reference/keywords/orderby-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md), [let](../../../csharp/language-reference/keywords/let-clause.md) et même d'autres clauses [from](../../../csharp/language-reference/keywords/from-clause.md) supplémentaires.  Vous pouvez également utiliser le mot clé [into](../../../csharp/language-reference/keywords/into.md) pour que le résultat d'une clause `join` ou `group` puisse servir de source pour des clauses de requête supplémentaires dans la même expression de requête.  
  
### Variable de requête  
 Dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], une variable de requête correspond à n'importe quelle variable qui stocke *une requête* au lieu *des résultats* d'une requête. Plus spécifiquement, une variable de requête est toujours un type énumérable qui produit une séquence d'éléments lorsqu'elle est itérée dans une instruction `foreach` ou un appel direct à sa méthode `IEnumerator.MoveNext`.  
  
 L'exemple de code suivant montre une expression de requête simple avec une source de données, une clause de filtrage, une clause de classement et aucune transformation des éléments source.  La clause `select` termine la requête.  
  
 [!code-cs[csrefQueryExpBasics#49](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_5.cs)]  
  
 Dans l'exemple précédent, `scoreQuery` est une *variable de requête* qui est parfois désignée simplement par le nom de  *requête*.  La variable de requête ne stocke aucune données de résultat réelle, générée dans la boucle `foreach`.  Et lorsque l'instruction `foreach` s'exécute, les résultats de la requête ne sont pas retournés via la variable de requête `scoreQuery`.  En revanche, ils sont retournés via la variable d'itération `testScore`.  La variable `scoreQuery` peut être itérée dans une deuxième boucle `foreach`.  Elle générera les mêmes résultats tant que ni elle ni la source de données ne sont modifiés.  
  
 Une variable de requête peut stocker une requête exprimée dans la syntaxe de requête ou dans la syntaxe de méthode, ou dans une combinaison des deux.  Dans les exemples suivants, `queryMajorCities` et `queryMajorCities2` sont des variables de requête :  
  
 [!code-cs[csrefQueryExpBasics#50](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_6.cs)]  
  
 En revanche, les deux exemples suivants affichent des variables qui ne sont pas des variables de requête, même si chacune d'entre elles est initialisée avec une requête.  Il ne s'agit pas de variables de requête, car elles stockent des résultats :  
  
 [!code-cs[csrefQueryExpBasics#51](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_7.cs)]  
  
> [!NOTE]
>  Dans la documentation de [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], les variables qui stockent une requête contiennent le mot « query » dans leur nom.  Les variables qui stockent un résultat réel ne contiennent pas le mot « query » dans leur nom.  
  
 Pour plus d'informations sur les différents modes d'expression de requêtes, consultez [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
#### Types explicites et implicites de variables de requête  
 Cette documentation fournit généralement le type explicite de la variable de requête pour afficher la relation de type entre la variable de requête et la [clause select](../../../csharp/language-reference/keywords/select-clause.md).  Toutefois, vous pouvez également utiliser le mot clé [var](../../../csharp/language-reference/keywords/var.md) pour indiquer au compilateur de déduire le type d'une variable de requête \(ou toute autre variable locale\) au moment de la compilation.  Par exemple, l'exemple de requête expliqué précédemment dans cette rubrique peut également être exprimé à l'aides de types implicites :  
  
 [!code-cs[csrefQueryExpBasics#52](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_8.cs)]  
  
 Pour plus d'informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
### Démarrage d'une expression de requête  
 Une expression de requête doit commencer par une clause `from`.  Elle spécifie une source de données avec une variable de portée.  La variable de portée représente chaque élément consécutif dans la séquence source comme la séquence source parcourue.  La variable de portée est fortement typée selon le type d'éléments dans la source de données.  Dans l'exemple suivant, comme `countries` est un tableau d'objets `Country`, la variable de portée est également saisie comme `Country`.  Étant donné que la variable de portée est fortement typée, vous pouvez utiliser l'opérateur point pour accéder à tous les membres disponibles du type.  
  
 [!code-cs[csrefQueryExpBasics#53](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_9.cs)]  
  
 La variable de portée est dans la portée tant que la requête n'est pas quittée avec un point\-virgule ou une clause *continuation*.  
  
 Une expression de requête peut contenir plusieurs clauses `from`.  Utilisez des clauses `from` supplémentaires lorsque chaque élément de la séquence source est lui\-même une collection ou contient une collection.  Par exemple, supposons que vous avez une collection d'objets `Country` et que chacun d'entre eux contient une collection d'objets `City` nommés `Cities`.  Pour interroger les objets `City` dans chaque `Country`, utilisez deux clauses `from` comme indiqué ici :  
  
 [!code-cs[csrefQueryExpBasics#54](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_10.cs)]  
  
 Pour plus d'informations, consultez [from, clause](../../../csharp/language-reference/keywords/from-clause.md).  
  
### Fin d'une expression de requête  
 Une expression de requête doit se terminer par une clause `select` ou une clause `group`.  
  
#### Clause group  
 Utilisez la clause `group` pour générer une séquence de groupes organisée par une clé que vous spécifiez.  La clé peut correspondre à tout type de données.  Par exemple, la requête suivante crée une séquence de groupes qui contient un ou plusieurs objets `Country` dont la clé est une valeur `char`.  
  
 [!code-cs[csrefQueryExpBasics#55](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_11.cs)]  
  
 Pour plus d'informations sur le regroupement, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
#### Clause select  
 Utilisez la clause `select` pour générer tous les autres types de séquences.  Une clause `select` simple génère simplement une séquence du même type d'objets que les objets contenus dans la source de données.  Dans cet exemple, la source de données contient des objets `Country`.  La clause `orderby` trie simplement les éléments dans un nouvel ordre et la clause `select` génère une séquence des objets `Country` réorganisés.  
  
 [!code-cs[csrefQueryExpBasics#56](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_12.cs)]  
  
 La clause `select` peut être utilisée pour transformer des données source en séquences de nouveaux types.  Cette transformation est également nommée une *projection*.  Dans l'exemple suivant, la clause `select` *projette* une séquence de types anonymes qui contient uniquement un sous\-ensemble des champs dans l'élément d'origine.  Notez que les nouveaux objets sont initialisés à l'aide d'un initialiseur d'objet.  
  
 [!code-cs[csrefQueryExpBasics#57](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_13.cs)]  
  
 Pour plus d'informations sur toutes les façons de pouvoir utiliser une clause `select` pour transformer des données sources, consultez [select, clause](../../../csharp/language-reference/keywords/select-clause.md).  
  
#### Continuations avec « into »  
 Vous pouvez utiliser le mot clé `into` dans une clause `select` ou `group` pour créer un identificateur temporaire qui stocke une requête.  Procédez ainsi lorsque vous devez effectuer des opérations de requête supplémentaires sur une requête après une opération de regroupement ou de sélection.  Dans l'exemple suivant, les `countries` sont regroupés en fonction du remplissage, par plages de 10 millions.  Une fois ces groupes créés, des clauses supplémentaires éliminent des groupes par filtrage, puis trient les groupes par ordre croissant.  Pour effectuer ces opérations supplémentaires, la continuation représentée par `countryGroup` est requise.  
  
 [!code-cs[csrefQueryExpBasics#58](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_14.cs)]  
  
 Pour plus d'informations, consultez [into](../../../csharp/language-reference/keywords/into.md).  
  
### Filtrage, classement et jonction  
 Entre la clause `from` initiale, et la clause `select` ou `group` finale, toutes les autres clauses \(`where`, `join`, `orderby`, `from`, `let`\) sont facultatives.  Chacune des clauses facultatives peut être utilisée zéro fois ou plusieurs fois dans un corps de requête.  
  
#### Clause Where  
 Utilisez la clause `where` pour éliminer par filtrage des éléments des données source selon une ou plusieurs expressions de prédicat.  La clause `where` de l'exemple suivant a deux prédicats.  
  
 [!code-cs[csrefQueryExpBasics#59](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_15.cs)]  
  
 Pour plus d'informations, consultez [where, clause](../../../csharp/language-reference/keywords/where-clause.md).  
  
#### Clause OrderBy  
 Utilisez la clause `orderby` pour trier les résultats par ordre croissant ou décroissant.  Vous pouvez également spécifier des ordres de tri secondaires.  L'exemple suivant effectue un tri principal sur les objets `country` en utilisant la propriété `Area`.  Il effectue ensuite un tri secondaire en utilisant la propriété `Population`.  
  
 [!code-cs[csrefQueryExpBasics#60](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_16.cs)]  
  
 Le mot clé `ascending` est facultatif ; il s'agit de l'ordre de tri par défaut si aucun ordre n'est spécifié.  Pour plus d'informations, consultez [orderby, clause](../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### Clause Join  
 Utilisez la clause `join` pour associer et\/ou combiner des éléments d'une source de données avec des éléments d'une autre source de données en fonction d'une comparaison d'égalité entre des clés spécifiées dans chaque élément.  Dans [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)], les opérations de jointure sont effectuées sur les séquences des objets dont les éléments sont des types différents.  Après avoir joint deux séquences, vous devez utiliser une instruction `select` ou `group` pour spécifier quel élément stocker dans la séquence de sortie.  Vous pouvez également utiliser un type anonyme pour combiner des propriétés de chaque jeu d'éléments associés dans un nouveau type pour la séquence de sortie.  L'exemple suivant associe des objets `prod` dont la propriété `Category` correspond à l'une des catégories dans le tableau de chaînes `categories`.  Les produits dont `Category` ne correspond pas à une chaîne quelconque dans `categories` sont éliminés par filtrage.  L'instruction `select` projette un nouveau type dont les propriétés sont extraites de `cat` et de `prod`.  
  
 [!code-cs[csrefQueryExpBasics#61](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_17.cs)]  
  
 Vous pouvez également effectuer une jointure groupée en stockant les résultats de l'opération `join` dans une variable temporaire en utilisant le mot clé [into](../../../csharp/language-reference/keywords/into.md).  Pour plus d'informations, consultez [join, clause](../../../csharp/language-reference/keywords/join-clause.md).  
  
#### Clause Let  
 Utilisez la clause `let` pour stocker le résultat d'une expression telle qu'un appel de méthode dans une nouvelle variable de portée.  Dans l'exemple suivant, la variable de portée `firstName` stocke le premier élément du tableau de chaînes retourné par `Split`.  
  
 [!code-cs[csrefQueryExpBasics#62](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_18.cs)]  
  
 Pour plus d'informations, consultez [let, clause](../../../csharp/language-reference/keywords/let-clause.md).  
  
### Sous\-requêtes dans une expression de requête  
 Une clause de requête peut elle\-même contenir une expression de requête, qui est parfois connue sous le nom de *sous\-requête*.  Chaque sous\-requête démarre avec sa propre clause `from` qui ne pointe pas nécessairement vers la même source de données dans la première clause `from`.  Par exemple, la requête suivante montre une expression de requête utilisée dans l'instruction select pour récupérer les résultats d'une opération de regroupement.  
  
 [!code-cs[csrefQueryExpBasics#63](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/query-expression-basics_19.cs)]  
  
 Pour plus d'informations, consultez [Comment : effectuer une sous\-requête sur une opération de regroupement](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)