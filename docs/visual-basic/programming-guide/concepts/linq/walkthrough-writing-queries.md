---
title: "Écriture de requêtes dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e870d5d0640c68fa57b07986f2bf8268fd5246c9
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Procédure pas à pas : écriture de requêtes dans Visual Basic
Cette procédure pas à pas montre comment vous pouvez utiliser les fonctionnalités du langage Visual Basic pour écrire [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions de requête. La procédure pas à pas montre comment créer des requêtes sur une liste d’objets Student, comment exécuter des requêtes et comment les modifier. Les requêtes incorporent plusieurs fonctionnalités, y compris les initialiseurs d’objets, l’inférence de type local et les types anonymes.  
  
 À l’issue de cette procédure pas à pas, vous serez prêt à passer aux exemples et documentation spécifique [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fournisseur qui vous intéresse. [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]fournisseurs incluent [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## <a name="create-a-project"></a>Créer un projet  
  
#### <a name="to-create-a-console-application-project"></a>Pour créer un projet d’application console  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le **modèles installés** , cliquez sur **Visual Basic**.  
  
4.  Dans la liste des types de projets, cliquez sur **Application Console**. Dans le **nom** zone, tapez un nom pour le projet, puis cliquez sur **OK**.  
  
     Un projet est créé. Par défaut, il contient une référence à System.Core.dll. En outre, les **espaces de noms importés** liste sur le [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) inclut la <xref:System.Linq?displayProperty=fullName>espace de noms.</xref:System.Linq?displayProperty=fullName>  
  
5.  Sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), assurez-vous que **Option infer** a **sur**.  
  
## <a name="add-an-in-memory-data-source"></a>Ajouter une Source de données en mémoire  
 La source de données pour les requêtes de cette procédure pas à pas est une liste de `Student` objets. Chaque `Student` objet contient un prénom, un nom, une année de classe et un classement dans le corps student.  
  
#### <a name="to-add-the-data-source"></a>Pour ajouter la source de données  
  
-   Définir un `Student` de classe et créer une liste d’instances de la classe.  
  
    > [!IMPORTANT]
    >  Le code nécessaire pour définir le `Student` de classe et créer la liste utilisée dans la procédure pas à pas exemples sont fournis de [Comment : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Vous pouvez copier et coller dans votre projet. Le nouveau code remplace le code qui s’affichent lorsque vous avez créé le projet.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Pour ajouter un nouvel étudiant à la liste des étudiants  
  
-   Suivre le modèle dans le `getStudents` pour ajouter une autre instance de la `Student` classe à la liste. Ajout de l’étudiant, vous présentera les initialiseurs d’objets. Pour plus d’informations, consultez [initialiseurs d’objets : Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Créer une requête  
 Lorsqu’elle est exécutée, la requête ajoutée dans cette section génère une liste des étudiants dont le rang academic les place dans les dix. Étant donné que la requête sélectionne l’ensemble `Student` objet chaque fois que le type du résultat de requête est `IEnumerable(Of Student)`. Toutefois, le type de la requête en général n'est pas spécifié dans les définitions de requête. Au lieu de cela, le compilateur utilise l’inférence de type local pour déterminer le type. Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Variable de portée de la requête, `currentStudent`, sert de référence à chaque `Student` instance dans la source de `students`, en fournissant un accès aux propriétés de chaque objet dans `students`.  
  
#### <a name="to-create-a-simple-query"></a>Pour créer une requête simple  
  
1.  Recherchez l’endroit dans le `Main` méthode du projet qui est marqué comme suit :  
  
     [!code-vb[VbLINQWalkthrough n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Copiez le code suivant et collez-le dans.  
  
     [!code-vb[VbLINQWalkthrough n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Placez le pointeur de la souris sur `studentQuery` dans votre code pour vérifier que le type attribué par le compilateur est `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Exécutez la requête  
 La variable `studentQuery` contient la définition de la requête, pas les résultats de la requête en cours d’exécution. Un mécanisme classique pour exécuter une requête est un `For Each` boucle. Chaque élément de la séquence retournée est accessible via la variable d’itération de boucle. Pour plus d’informations sur l’exécution des requêtes, consultez [écrire votre première requête LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Pour exécuter la requête  
  
1.  Ajoutez le code suivant `For Each` boucle sous la requête dans votre projet.  
  
     [!code-vb[VbLINQWalkthrough n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  Placez le pointeur de la souris sur la variable de contrôle de boucle `studentRecord` pour consulter son type de données. Le type de `studentRecord` doit donc pour être `Student`, car `studentQuery` retourne une collection de `Student` instances.  
  
3.  Générez et exécutez l’application en appuyant sur CTRL + F5. Notez que les résultats dans la fenêtre de console.  
  
## <a name="modify-the-query"></a>Modifier la requête  
 Il est plus facile à analyser les résultats de la requête s’ils sont dans un ordre spécifié. Vous pouvez trier la séquence retournée selon n’importe quel champ disponible.  
  
#### <a name="to-order-the-results"></a>Pour trier les résultats  
  
1.  Ajoutez le code suivant `Order By` clause entre la `Where` instruction et la `Select` instruction de la requête. Le `Order By` clause sera classer les résultats par ordre alphabétique de A à Z, après le nom de chaque étudiant.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Pour trier par nom puis par prénom, ajoutez les deux champs à la requête :  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Vous pouvez également spécifier `Descending` pour classer de Z à A.  
  
3.  Générez et exécutez l’application en appuyant sur CTRL + F5. Notez que les résultats dans la fenêtre de console.  
  
#### <a name="to-introduce-a-local-identifier"></a>Pour introduire un identificateur local  
  
1.  Ajoutez le code de cette section pour introduire un identificateur local dans l’expression de requête. L’identificateur local contiendra un résultat intermédiaire. Dans l’exemple suivant, `name` est un identificateur qui contient une concaténation de l’étudiant et du nom de famille. Un identificateur local peut être utilisé pour des raisons pratiques, ou elle peut améliorer les performances en stockant les résultats d’une expression qui serait sinon calculée plusieurs fois.  
  
     [!code-vb[VbLINQWalkthrough n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Générez et exécutez l’application en appuyant sur CTRL + F5. Notez que les résultats dans la fenêtre de console.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Pour projeter un champ dans la clause Select  
  
1.  Ajoutez la requête et `For Each` boucle à partir de cette section pour créer une requête qui génère une séquence dont les éléments diffèrent des éléments dans la source. Dans l’exemple suivant, la source est une collection de `Student` les objets, mais qu’un seul membre de chaque objet est retourné : le prénom des étudiants dont le nom est Garcia. Étant donné que `currentStudent.First` est une chaîne, le type de données de la séquence retournée par `studentQuery3` est `IEnumerable(Of String)`, une séquence de chaînes. Comme dans les exemples précédents, l’attribution d’une donnée de type pour `studentQuery3` est effectuée par le compilateur à déterminer à l’aide de l’inférence de type local.  
  
     [!code-vb[VbLINQWalkthrough n °&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Placez le pointeur de la souris sur `studentQuery3` dans votre code pour vérifier que le type assigné est `IEnumerable(Of String)`.  
  
3.  Générez et exécutez l’application en appuyant sur CTRL + F5. Notez que les résultats dans la fenêtre de console.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Pour créer un type anonyme dans la clause Select  
  
1.  Ajoutez le code à partir de cette section pour voir comment les types anonymes sont utilisés dans les requêtes. Utilisez-les dans les requêtes lorsque vous souhaitez retourner plusieurs champs de la source de données plutôt que des enregistrements complets (`currentStudent` enregistrements dans les exemples précédents) ou des champs uniques (`First` dans la section précédente). Au lieu de définir un nouveau type nommé qui contient les champs que vous souhaitez inclure dans le résultat, vous spécifiez les champs dans le `Select` clause et le compilateur crée un type anonyme dont ces champs ses propriétés. Pour plus d’informations, consultez [les Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     L’exemple suivant crée une requête qui retourne le nom et le rang garantiront academic dont le rang est comprise entre 1 et 10, dans l’ordre de classement. Dans cet exemple, le type de `studentQuery4` doit être déduit, car les `Select` clause retourne une instance d’un type anonyme, et un type anonyme n’a pas de nom utilisable.  
  
     [!code-vb[VbLINQWalkthrough n °&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Générez et exécutez l’application en appuyant sur CTRL + F5. Notez que les résultats dans la fenêtre de console.  
  
## <a name="additional-examples"></a>Exemples supplémentaires  
 Maintenant que vous comprenez les notions de base, ce qui suit est une liste d’exemples supplémentaires pour illustrer la souplesse et la puissance de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] des requêtes. Chaque exemple est précédé d’une brève description de ce qu’il fait. Placez le pointeur de la souris sur la variable de résultat de chaque requête pour consulter le type déduit. Utilisez un `For Each` boucle pour produire les résultats.  
  
 [!code-vb[VbLINQWalkthrough&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Informations supplémentaires  
 Une fois que vous êtes familiarisé avec les concepts de base de l’utilisation des requêtes, vous êtes prêt à lire la documentation et les exemples pour le type spécifique de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fournisseur qui vous intéressez :  
  
 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
## <a name="see-also"></a>Voir aussi  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Initialiseurs d’objets : Les Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)
