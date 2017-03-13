---
title: "Walkthrough: Writing Queries in C# (LINQ) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "get-started-article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], walkthroughs"
  - "LINQ [C#], writing queries"
  - "queries [LINQ in C#], writing"
  - "writing LINQ queries"
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# Walkthrough: Writing Queries in C# (LINQ)
Cette procédure pas à pas présente les fonctionnalités du langage C\# utilisées pour écrire des expressions de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Une fois cette procédure pas à pas terminée, vous serez prêt à passer aux exemples et à la documentation du fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] spécifique qui vous intéresse, tel que [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)], [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] to DataSets ou [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)].  
  
## Composants requis  
 Cette procédure pas \- à \- pas requiert des fonctionnalités qui sont présentées dans Visual Studio 2008.  
  
 ![lien vers la vidéo](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [Vidéo : comment écrire des requêtes LINQ en C\# \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=100393).  
  
## Création d'un projet C\#.  
  
#### Pour créer un projet  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Project**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Développez **Installé**, développez **Modèles**, développez **Visual C\#**, puis choisissez **Application console**.  
  
4.  Dans la zone de texte **Nom**, entrez un nom différent ou acceptez le nom par défaut, puis choisissez le bouton **OK** .  
  
     Le nouveau projet s'affiche dans l'**Explorateur de solutions**.  
  
5.  Notez que votre projet a une référence à System.Core.dll et une directive `using` pour l'espace de noms <xref:System.Linq?displayProperty=fullName>.  
  
## Création d'une source de données en mémoire  
 La source de données pour les requêtes est une simple liste d'objets `Student`.  Chaque enregistrement `Student` comporte un prénom, un nom et un tableau d'entiers représentant les notes d'examens en classe.  Copiez ce code dans votre projet.  Notez les caractéristiques suivantes :  
  
-   La classe `Student` se compose de propriétés implémentées automatiquement.  
  
-   Chaque étudiant de la liste est initialisé avec un initialiseur d'objet.  
  
-   La liste elle\-même est initialisée avec un initialiseur de collection.  
  
 La totalité de cette structure de données sera initialisée et instanciée sans appels explicites à un constructeur quelconque ou accès au membre explicite.  Pour plus d'informations sur ces nouvelles fonctionnalités, consultez [Propriétés implémentées automatiquement](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) et [Initialiseurs d'objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### Pour ajouter la source de données  
  
-   Ajoutez la classe `Student` et la liste initialisée d'étudiants à la classe `Program` dans votre projet.  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### Pour ajouter un nouvel étudiant à la liste des étudiants  
  
1.  Ajoutez un nouveau `Student` à la liste `Students` et utilisez le nom et les notes d'examens de votre choix.  Essayez d'entrer toutes les informations relatives au nouvel étudiant pour mieux apprendre la syntaxe de l'initialiseur d'objet.  
  
## Création de la requête  
  
#### Pour créer une requête simple  
  
-   Dans la méthode `Main` de l'application, créez une requête simple qui, lorsqu'elle est exécutée, produit une liste de tous les étudiants dont la note pour le premier test est supérieure à 90.  Notez que, puisque l'objet `Student` entier est sélectionné, le type de la requête est `IEnumerable<Student>`.  Bien que le code puisse également utiliser un type implicite à l'aide du mot clé [var](../../../../csharp/language-reference/keywords/var.md), les types explicites sont utilisés pour illustrer clairement les résultats.  Pour plus d'informations sur `var`, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
     Notez également que la variable de portée de la requête, `student`, sert de référence à chaque `Student` dans la source, en fournissant l'accès au membre pour chaque objet.  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## Exécution de la requête  
  
#### Pour exécuter la requête  
  
1.  Écrivez maintenant la boucle `foreach` qui entraînera l'exécution de la requête.  Notez les points suivants concernant le code :  
  
    -   Chaque élément de la séquence retournée est accessible via la variable d'itération dans la boucle `foreach`.  
  
    -   Le type de cette variable est `Student` et le type de la variable de requête est compatible \(`IEnumerable<Student>`\).  
  
2.  Après avoir ajouté ce code, générez et exécutez l'application en appuyant sur Ctrl \+ F5 pour visualiser les résultats dans la fenêtre de **console**.  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### Pour ajouter une autre condition de filtre  
  
1.  Vous pouvez associer plusieurs conditions booléennes dans la clause `where` pour affiner davantage une requête.  Le code suivant ajoute une condition afin que la requête retourne les étudiants dont la première note est supérieure à 90 et dont la dernière est inférieure à 80.  La clause `where` doit être semblable au code suivant.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Pour plus d'informations, consultez [where, clause](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## Modifier la requête  
  
#### Pour classer les résultats  
  
1.  Il sera plus facile d'analyser les résultats s'ils sont classés.  Vous pouvez classer la séquence retournée selon tous les champs accessibles dans les éléments sources.  Par exemple, la clause `orderby` suivante classe les résultats dans l'ordre alphabétique de A à Z d'après le nom de chaque étudiant.  Ajoutez la clause `orderby` suivante à votre requête, juste après l'instruction `where` et avant l'instruction `select` :  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Modifiez à présent la clause `orderby` pour qu'elle classe les résultats dans l'ordre inverse d'après la note au premier examen, de la plus élevée à la plus faible.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Modifiez la chaîne de format `WriteLine` pour pouvoir consulter les notes :  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Pour plus d'informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### Pour regrouper les résultats  
  
1.  Le regroupement est une fonction puissante des expressions de requête.  Une requête avec une clause group produit une séquence de groupes dont chaque groupe contient lui\-même un `Key` et une séquence composée de tous les membres de ce groupe.  La nouvelle requête suivante regroupe les étudiants en utilisant la première lettre de leur nom comme clé.  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Notez que le type de la requête a maintenant changé.  Il produit désormais une séquence de groupes qui ont un type `char` comme clé et une séquence d'objets `Student`.  Étant donné que le type de la requête a changé, le code suivant modifie également la boucle d'exécution `foreach` :  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Appuyez sur Ctrl \+ F5 pour exécuter l'application et visualiser les résultats dans la fenêtre de **console**.  
  
     Pour plus d'informations, consultez [group, clause](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### Pour rendre les variables implicitement typées  
  
1.  Le codage explicite de `IEnumerables` de `IGroupings` peut rapidement s'avérer laborieux.  Vous pouvez écrire la même requête et la même boucle `foreach` beaucoup plus facilement à l'aide de `var`.  Le mot clé `var` ne modifie pas les types de vos objets ; il indique simplement au compilateur de déduire les types.  Modifiez le type d' `studentQuery` et l'itération `group`variable par `var` et réexécuter la requête.  Notez que dans la boucle `foreach` interne, la variable d'itération est encore typée comme `Student` et que la requête fonctionne exactement comme précédemment.  Modifiez la variable d'itération `s` en `var` et exécutez à nouveau la requête.  Vous pouvez constater que les résultats obtenus sont exactement les mêmes.  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Pour plus d'informations sur [var](../../../../csharp/language-reference/keywords/var.md), consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### Pour classer les groupes selon leur valeur de clé  
  
1.  Lorsque vous exécutez la requête précédente, vous remarquez que les groupes ne sont pas dans l'ordre alphabétique.  Pour modifier cet ordre, vous devez fournir une clause `orderby` après la clause `group`.  Toutefois, pour utiliser une clause `orderby`, vous avez d'abord besoin d'un identificateur servant de référence aux groupes créés par la clause `group`.  Fournissez l'identificateur à l'aide du mot clé `into`, comme suit :  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Lorsque vous exécuterez cette requête, vous verrez que les groupes seront désormais classés dans l'ordre alphabétique.  
  
#### Pour introduire un identificateur à l'aide de let  
  
1.  Vous pouvez utiliser le mot clé `let` pour introduire un identificateur pour tous les résultats d'expression dans l'expression de requête.  Cet identificateur peut être pratique, comme dans l'exemple suivant, ou améliorer les performances en stockant les résultats d'une expression afin d'éviter qu'ils ne soient calculés plusieurs fois.  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Pour plus d'informations, consultez [let, clause](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### Pour utiliser la syntaxe de méthode dans une expression de requête  
  
1.  Comme décrit dans [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), certaines opérations de requête peuvent être exprimées uniquement à l'aide de la syntaxe de méthode.  Le code suivant calcule la note totale de chaque `Student` dans la séquence source, puis appelle la méthode `Average()` sur les résultats de cette requête pour calculer la note moyenne de la classe.  Notez la présence de parenthèses de part et d'autre de l'expression de requête.  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### Pour transformer ou projeter la clause select  
  
1.  Il n'est pas rare qu'une requête produise une séquence dont les éléments diffèrent des éléments des séquences sources.  Supprimez ou commentez votre requête et votre boucle d'exécution précédentes et remplacez\-les par le code suivant.  Notez que la requête retourne une séquence de chaînes \(pas de `Students`\) et que ce fait est répercuté dans la boucle `foreach`.  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Le code utilisé précédemment dans cette procédure pas à pas indique que la note moyenne de la classe est d'environ 334.  Pour produire une séquence de `Students` dont la note totale est supérieure à la moyenne de classe, avec les `Student ID` correspondants, vous pouvez utiliser un type anonyme dans l'instruction `select` :  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## Étapes suivantes  
 Une fois que vous êtes familiarisé avec les aspects de base de l'utilisation de requêtes en C\#, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] qui vous intéresse :  
  
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [Procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)