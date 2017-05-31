---
title: "Procédure pas à pas : écriture de requêtes en C# (LINQ) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 5692bd4b2fae4c5e17d48c12e98eb2e18523ba61
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="walkthrough-writing-queries-in-c-linq"></a>Procédure pas à pas : écriture de requêtes en C# (LINQ)
Cette procédure pas à pas présente les fonctionnalités du langage C# utilisées pour écrire des expressions de requête LINQ.  
  
## <a name="create-a-c-project"></a>Créer un projet C#  
  
> [!NOTE]
>  Les instructions suivantes s’appliquent à Visual Studio. Si vous utilisez un environnement de développement différent, créez un projet console avec une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=fullName>.  
  
#### <a name="to-create-a-project-in-visual-studio"></a>Pour créer un projet dans Visual Studio  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Développez **Installé**, **Modèles**, **Visual C#**, puis choisissez **Application console**.  
  
4.  Dans la zone de texte **Nom**, entrez un nom différent ou acceptez le nom par défaut, puis choisissez le bouton **OK**.  
  
     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.  
  
5.  Notez que votre projet a une référence à System.Core.dll et une directive `using` pour l’espace de noms <xref:System.Linq?displayProperty=fullName>.  
  
## <a name="create-an-in-memory-data-source"></a>Créer une source de données en mémoire  
 La source de données pour les requêtes est une simple liste d’objets `Student`. Chaque enregistrement `Student` comporte un prénom, un nom et un tableau d’entiers représentant les notes d’examens en classe. Copiez ce code dans votre projet. Notez les caractéristiques suivantes :  
  
-   La classe `Student` se compose de propriétés implémentées automatiquement.  
  
-   Chaque étudiant de la liste est initialisé avec un initialiseur d’objet.  
  
-   La liste elle-même est initialisée avec un initialiseur de collection.  
  
 La totalité de cette structure de données est initialisée et instanciée sans appels explicites à un constructeur quelconque ni accès au membre explicite. Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [Propriétés implémentées automatiquement](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) et [Initialiseurs d’objets et de collection](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### <a name="to-add-the-data-source"></a>Pour ajouter la source de données  
  
-   Ajoutez la classe `Student` et la liste initialisée d’étudiants à la classe `Program` dans votre projet.  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Pour ajouter un nouvel étudiant à la liste des étudiants  
  
1.  Ajoutez un nouvel élément `Student` à la liste `Students` et utilisez le nom et les notes d’examens de votre choix. Essayez d’entrer toutes les informations relatives au nouvel étudiant pour mieux apprendre la syntaxe de l’initialiseur d’objet.  
  
## <a name="create-the-query"></a>Créer la requête  
  
#### <a name="to-create-a-simple-query"></a>Pour créer une requête simple  
  
-   Dans la méthode `Main` de l’application, créez une requête simple qui, quand elle est exécutée, produit une liste de tous les étudiants dont la note pour le premier test est supérieure à 90. Notez que, puisque l’objet `Student` entier est sélectionné, le type de la requête est `IEnumerable<Student>`. Bien que le code puisse également utiliser un type implicite à l’aide du mot clé [var](../../../../csharp/language-reference/keywords/var.md), les types explicites sont utilisés pour illustrer clairement les résultats. (Pour plus d’informations sur `var`, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)  
  
     Notez également que la variable de portée de la requête, `student`, sert de référence à chaque `Student` dans la source, en fournissant l’accès au membre pour chaque objet.  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a>Exécuter la requête  
  
#### <a name="to-execute-the-query"></a>Pour exécuter la requête  
  
1.  Écrivez maintenant la boucle `foreach` qui entraînera l’exécution de la requête. Notez les points suivants concernant le code :  
  
    -   Chaque élément de la séquence retournée est accessible via la variable d’itération dans la boucle `foreach`.  
  
    -   Le type de cette variable est `Student` et le type de la variable de requête est compatible, `IEnumerable<Student>`.  
  
2.  Après avoir ajouté ce code, générez et exécutez l’application pour visualiser les résultats dans la fenêtre de **console**.  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a>Pour ajouter une autre condition de filtre  
  
1.  Vous pouvez associer plusieurs conditions booléennes dans la clause `where` pour affiner davantage une requête. Le code suivant ajoute une condition afin que la requête retourne les étudiants dont la première note est supérieure à 90 et dont la dernière est inférieure à 80. La clause `where` doit être semblable au code suivant.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Pour plus d’informations, consultez [where, clause](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## <a name="modify-the-query"></a>Modifier la requête  
  
#### <a name="to-order-the-results"></a>Pour classer les résultats  
  
1.  Il est plus facile d’analyser les résultats s’ils sont classés. Vous pouvez classer la séquence retournée selon tous les champs accessibles dans les éléments sources. Par exemple, la clause `orderby` suivante classe les résultats dans l’ordre alphabétique de A à Z d’après le nom de chaque étudiant. Ajoutez la clause `orderby` suivante à votre requête, juste après l’instruction `where` et avant l’instruction `select` :  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Modifiez à présent la clause `orderby` pour qu’elle classe les résultats dans l’ordre inverse d’après la note au premier examen, de la plus élevée à la plus faible.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Modifiez la chaîne de format `WriteLine` pour pouvoir consulter les notes :  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### <a name="to-group-the-results"></a>Pour regrouper les résultats  
  
1.  Le regroupement est une fonction puissante des expressions de requête. Une requête avec une clause group produit une séquence de groupes dont chaque groupe contient lui-même un élément `Key` et une séquence composée de tous les membres de ce groupe. La nouvelle requête suivante regroupe les étudiants en utilisant la première lettre de leur nom comme clé.  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Notez que le type de la requête a maintenant changé. Elle produit désormais une séquence de groupes qui ont un type `char` comme clé et une séquence d’objets `Student`. Étant donné que le type de la requête a changé, le code suivant modifie également la boucle d’exécution `foreach` :  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Exécutez l’application et affichez les résultats dans la fenêtre de **console**.  
  
     Pour plus d’informations, consultez [group, clause](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### <a name="to-make-the-variables-implicitly-typed"></a>Pour rendre les variables implicitement typées  
  
1.  Le codage explicite de `IEnumerables` de `IGroupings` peut rapidement s’avérer laborieux. Vous pouvez écrire la même requête et la même boucle `foreach` beaucoup plus facilement à l’aide de `var`. Le mot clé `var` ne modifie pas les types de vos objets ; il indique simplement au compilateur de déduire les types. Remplacez le type de `studentQuery` et la variable d’itération `group` par `var` et réexécutez la requête. Notez que, dans la boucle `foreach` interne, la variable d’itération est encore typée comme `Student` et que la requête fonctionne exactement comme précédemment. Remplacez la variable d’itération `s` par `var` et exécutez à nouveau la requête. Vous pouvez constater que les résultats obtenus sont exactement les mêmes.  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Pour plus d’informations sur [var](../../../../csharp/language-reference/keywords/var.md), consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### <a name="to-order-the-groups-by-their-key-value"></a>Pour classer les groupes selon leur valeur de clé  
  
1.  Quand vous exécutez la requête précédente, vous remarquez que les groupes ne sont pas dans l’ordre alphabétique. Pour modifier cet ordre, vous devez fournir une clause `orderby` après la clause `group`. Toutefois, pour utiliser une clause `orderby`, vous avez d’abord besoin d’un identificateur servant de référence aux groupes créés par la clause `group`. Fournissez l’identificateur à l’aide du mot clé `into`, comme suit :  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Quand vous exécutez cette requête, vous voyez que les groupes sont désormais classés par ordre alphabétique.  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a>Pour introduire un identificateur à l’aide de let  
  
1.  Vous pouvez utiliser le mot clé `let` pour introduire un identificateur pour tous les résultats d’expression dans l’expression de requête. Cet identificateur peut être pratique, comme dans l’exemple suivant, ou améliorer les performances en stockant les résultats d’une expression afin d’éviter qu’ils ne soient calculés plusieurs fois.  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Pour plus d’informations, consultez [let, clause](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a>Pour utiliser la syntaxe de méthode dans une expression de requête  
  
1.  Comme décrit dans [Syntaxe de requête et syntaxe de méthode dans LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), certaines opérations de requête peuvent être exprimées uniquement à l’aide de la syntaxe de méthode. Le code suivant calcule la note totale de chaque `Student` dans la séquence source, puis appelle la méthode `Average()` sur les résultats de cette requête pour calculer la note moyenne de la classe. Notez la présence de parenthèses de part et d’autre de l’expression de requête.  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a>Pour transformer ou projeter la clause select  
  
1.  Il n’est pas rare qu’une requête produise une séquence dont les éléments diffèrent des éléments des séquences sources. Supprimez ou commentez votre requête et votre boucle d’exécution précédentes, et remplacez-les par le code suivant. Notez que la requête retourne une séquence de chaînes (pas `Students`) et que ce fait est répercuté dans la boucle `foreach`.  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Le code utilisé précédemment dans cette procédure pas à pas indique que la note moyenne de la classe est d’environ 334. Pour produire une séquence de `Students` dont la note totale est supérieure à la moyenne de classe, avec les `Student ID` correspondants, vous pouvez utiliser un type anonyme dans l’instruction `select` :  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a>Étapes suivantes  
 Une fois que vous êtes familiarisé avec les aspects de base de l’utilisation de requêtes en C#, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de fournisseur LINQ qui vous intéresse :  
  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language-Integrated Query) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressions de requête LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
