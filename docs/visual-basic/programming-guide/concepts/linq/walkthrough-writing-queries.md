---
title: "Proc&#233;dure pas &#224; pas&#160;: &#233;criture de requ&#234;tes dans Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "requêtes [LINQ en Visual Basic], écrire"
  - "LINQ [Visual Basic], procédures pas à pas"
  - "LINQ [Visual Basic], écrire des requêtes"
  - "écrire des requêtes LINQ (Visual Basic)"
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
caps.handback.revision: 68
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dure pas &#224; pas&#160;: &#233;criture de requ&#234;tes dans Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment vous pouvez utiliser les fonctionnalités du langage Visual Basic pour écrire des expressions de requête [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].  La procédure pas à pas indique comment créer des requêtes dans une liste d'objets Student, comment exécuter les requêtes et comment les modifier.  Les requêtes incorporent plusieurs fonctionnalités qui étaient nouvelles dans Visual Basic 2008, y compris les initialiseurs d'objets, l'inférence de type locale et les types anonymes.  
  
 Une fois cette procédure pas à pas terminée, vous serez prêt à passer aux exemples et à la documentation du fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] spécifique qui vous intéresse.  Les fournisseurs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] incluent [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/linq-query-expressions/includes/linq_dataset_md.md)] et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## Créer un projet  
  
#### Pour créer un projet d'application console  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la liste **Modèles installés**, cliquez sur **Visual Basic.**  
  
4.  Dans la liste des types de projets, cliquez sur **Application console**.  Dans la zone **Nom**, tapez un nom pour le projet, puis cliquez sur **OK**.  
  
     Un projet est créé.  Par défaut, il contient une référence à System.Core.dll.  En outre, la liste **Espaces de noms importés** dans [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic) comprend l'espace de noms <xref:System.Linq?displayProperty=fullName>.  
  
5.  Dans [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic), assurez\-vous que **L'option déduisent** a la valeur **Dans**.  
  
## Ajouter une source de données en mémoire  
 La source de données pour les requêtes de cette procédure pas à pas est une liste d'objets `Student`.  Chaque objet `Student` contient un prénom, un nom, une année de classe et un classement dans le corps Student.  
  
#### Pour ajouter la source de données  
  
-   Définissez une classe `Student` et créez une liste d'instances de la classe.  
  
    > [!IMPORTANT]
    >  Le code requis pour définir la classe `Student` et créer la liste utilisée dans les exemples de la procédure pas à pas est fourni dans [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  Vous pouvez le copier et le coller dans votre projet.  Le nouveau code remplace le code qui est apparu lorsque vous avez créé le projet.  
  
#### Pour ajouter un nouvel étudiant à la liste des étudiants  
  
-   Suivez le modèle dans la méthode `getStudents` pour ajouter une autre instance de la classe `Student` à la liste.  L'ajout de l'étudiant vous permet de découvrir les initialiseurs d'objets.  Pour plus d'informations, consultez [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## Créer une requête  
 Lors de son exécution, la requête ajoutée dans cette section génère la liste des étudiants qui sont les dix premiers dans le classement.  Étant donné que la requête sélectionne à chaque fois l'objet `Student` complet, le type du résultat de la requête est `IEnumerable(Of Student)`.  Toutefois, le type de la requête n'est généralement pas spécifié dans les définitions de requête.  À la place, le compilateur utilise l'inférence de type local pour déterminer le type.  Pour plus d'informations, consultez [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  La variable de portée de la requête, `currentStudent`, sert de référence à chaque instance `Student` dans la source, `students`, en fournissant l'accès aux propriétés de chaque objet dans `students`.  
  
#### Pour créer une requête simple  
  
1.  Recherchez l'endroit dans la méthode `Main` du projet marqué comme suit :  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Copiez le code suivant et collez\-le.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Placez le pointeur de la souris sur `studentQuery` dans votre code pour vérifier que le type assigné par le compilateur est `IEnumerable(Of Student)`.  
  
## Exécuter la requête  
 La variable `studentQuery` contient la définition de la requête mais ne contient pas les résultats de l'exécution de la requête.  Une boucle `For Each` est un mécanisme classique pour exécuter une requête.  Chaque élément de la séquence retournée est accessible via la variable d'itération de boucle.  Pour plus d'informations sur l'exécution de la requête, consultez [Écriture de votre première requête LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### Pour exécuter la requête  
  
1.  Ajoutez la boucle `For Each` suivante sous la requête dans votre projet.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Placez le pointeur de la souris sur la variable de contrôle de boucle `studentRecord` pour consulter son type de données.  Le type de `studentRecord`, `Student`, est déduit car `studentQuery` retourne une collection d'instances `Student`.  
  
3.  Générez et exécutez l'application en appuyant sur CTRL\+F5.  Notez les résultats dans la fenêtre de console.  
  
## Modifier la requête  
 Il est plus facile d'analyser des résultats de requête s'ils sont dans un ordre spécifié.  Vous pouvez trier la séquence retournée à partir de n'importe quel champ disponible.  
  
#### Pour classer les résultats  
  
1.  Ajoutez la clause `Order By` suivante entre l'instruction `Where` et l'instruction `Select` de la requête.  La clause `Order By` classera les résultats en ordre alphabétique de A à Z, d'après le nom de chaque étudiant.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Pour classer par nom puis par prénom, ajoutez les deux champs à la requête :  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Vous pouvez également spécifier `Descending` pour classer de Z à A.  
  
3.  Générez et exécutez l'application en appuyant sur CTRL\+F5.  Notez les résultats dans la fenêtre de console.  
  
#### Pour introduire un identificateur local  
  
1.  Ajoutez le code de cette section pour introduire un identificateur local dans l'expression de requête.  L'identificateur local contiendra un résultat intermédiaire.  Dans l'exemple suivant, `name` est un identificateur qui contient une concaténation du nom et du prénom de l'étudiant.  Un identificateur local peut être utilisé pour des raisons pratiques ou peut améliorer les performances en stockant les résultats d'une expression qui, sinon, serait calculée plusieurs fois.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Générez et exécutez l'application en appuyant sur CTRL\+F5.  Notez les résultats dans la fenêtre de console.  
  
#### Pour projeter un champ dans la clause Select  
  
1.  Ajoutez la requête et la boucle `For Each` de cette section pour créer une requête qui génère une séquence dont les éléments diffèrent des éléments dans la source.  Dans l'exemple suivant, la source est une collection d'objets `Student`, mais un seul membre de chaque objet est retourné : le prénom des étudiants dont le nom est Garcia.  Étant donné que `currentStudent.First` est une chaîne, le type de données de la séquence retournée par `studentQuery3` est `IEnumerable(Of String)`, une séquence de chaînes.  Comme dans les exemples précédents, l'assignation d'un type de données à `studentQuery3` est effectuée par le compilateur à l'aide de l'inférence de type local.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Placez le pointeur de la souris sur `studentQuery3` dans votre code pour vérifier que le type assigné est `IEnumerable(Of String)`.  
  
3.  Générez et exécutez l'application en appuyant sur CTRL\+F5.  Notez les résultats dans la fenêtre de console.  
  
#### Pour créer un type anonyme dans la clause Select  
  
1.  Ajoutez le code de cette section pour voir comment les types anonymes sont utilisés dans les requêtes.  Utilisez\-les dans les requêtes lorsque vous souhaitez retourner plusieurs champs de la source de données plutôt que des enregistrements complets \(enregistrements `currentStudent` dans les exemples précédents\) ou des champs uniques \(`First` dans la section précédente\).  Au lieu de définir un nouveau type nommé qui contient les champs que vous souhaitez inclure dans le résultat, vous spécifiez les champs dans la clause d' `Select` et le compilateur crée un type anonyme dont ces champs comme ses propriétés. Pour plus d'informations, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     L'exemple suivant crée une requête qui retourne le nom et le classement dans l'ordre des dix étudiants les mieux classés.  Dans cet exemple, le type de `studentQuery4` doit être déduit car la clause `Select` retourne une instance d'un type anonyme, et un type anonyme n'a pas de nom utilisable.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Générez et exécutez l'application en appuyant sur CTRL\+F5.  Notez les résultats dans la fenêtre de console.  
  
## Exemples supplémentaires  
 Maintenant que vous avez assimilé les éléments fondamentaux, voici une liste d'exemples supplémentaires pour illustrer la souplesse et la puissance des requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Chaque exemple est précédé d'une brève description de leur fonction.  Placez le pointeur de la souris sur la variable de résultat de requête pour chaque requête pour consulter le type déduit. Utilisez une boucle d' `For Each` pour produire les résultats.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## Informations supplémentaires  
 Une fois que vous vous êtes familiarisé avec les concepts de base relatifs à l'utilisation des requêtes, vous pouvez consulter la documentation et les exemples pour le type spécifique de fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] qui vous intéresse :  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)