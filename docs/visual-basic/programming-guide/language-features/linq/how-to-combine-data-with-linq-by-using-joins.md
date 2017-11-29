---
title: "Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 432be646ce4353fd4627a34f363e7562f6181e92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a>Comment : combiner des données avec LINQ à l'aide de jointures (Visual Basic)
Visual Basic fournit le `Join` et `Group Join` pour vous permettre de combiner le contenu de plusieurs collections basées sur des valeurs communes entre les collections de clauses de requête. Ces valeurs sont appelées *clé* valeurs. Les développeurs familiarisés avec les concepts de base de données relationnelle reconnaîtront la `Join` clause INNER JOIN et `Group Join` clause en tant que, en effet, une jointure externe gauche.  
  
 Les exemples de cette rubrique montrent quelques façons de combiner des données à l’aide de la `Join` et `Group Join` clauses de requête.  
  
## <a name="create-a-project-and-add-sample-data"></a>Créez un projet et ajouter des exemples de données  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a>Pour créer un projet qui contient des types et des exemples de données  
  
1.  Pour exécuter les exemples dans cette rubrique, ouvrez Visual Studio et ajoutez un nouveau projet d’Application Console Visual Basic. Double-cliquez sur le fichier Module1.vb créé par Visual Basic.  
  
2.  Les exemples de cette rubrique utilisent le `Person` et `Pet` types et les données de l’exemple de code suivant. Copiez ce code dans la valeur par défaut `Module1` module créé par Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a>Effectuer une jointure interne à l’aide de la Clause de jointure  
 Une jointure interne combine les données des deux collections. Éléments pour lesquels les valeurs de clé spécifiés correspond à sont inclus. Tous les éléments à partir de des collections qui n’ont pas d’élément correspondant dans l’autre collection sont exclus.  
  
 En Visual Basic, LINQ fournit deux options pour effectuer une jointure interne : une jointure implicite et une jointure explicite.  
  
 Une jointure implicite spécifie les collections à joindre dans une `From` clause et identifie les champs clés correspondants dans un `Where` clause. Visual Basic joint implicitement les deux collections basées sur les champs de clé spécifiés.  
  
 Vous pouvez spécifier une jointure explicite en utilisant la `Join` clause lorsque vous souhaitez être spécifique sur les champs clés dans la jointure. Dans ce cas, un `Where` clause peut toujours être utilisée pour filtrer les résultats de requête.  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a>Pour effectuer une jointure interne à l’aide de la clause de jointure  
  
1.  Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples de jointure interne implicite et explicite.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a>Effectuer une jointure externe gauche à l’aide de la Clause de jointure de groupe  
 Une jointure externe gauche comprend tous les éléments de la collection située du côté gauche de la jointure et uniquement les valeurs de la collection située du côté droit de la jointure correspondantes. Tous les éléments de la collection située du côté droit de la jointure qui n’ont pas d’élément correspondant dans la collection de gauche sont exclus du résultat de la requête.  
  
 Le `Group Join` clause effectue, en effet, une jointure externe gauche. La différence entre ce qui est généralement appelé une jointure externe gauche et ce que le `Group Join` clause retourne une valeur qui est la `Group Join` résultats de groupes de clause de la collection située du côté droit de la jointure pour chaque élément dans la collection de gauche. Dans une base de données relationnelle, une jointure externe gauche retourne un résultat non groupé dans laquelle chaque élément dans la requête résultat contient des éléments correspondants des deux collections dans la jointure. Dans ce cas, les éléments de la collection située du côté gauche de la jointure sont répétées pour chaque élément correspondant de la collection de droite. Vous verrez à quoi cela ressemble lorsque vous effectuez la procédure suivante.  
  
 Vous pouvez récupérer les résultats d’une `Group Join` requête sous la forme d’un résultat dégroupé en étendant votre requête afin de retourner un élément pour chaque résultat de requête groupé. Pour ce faire, vous devez vous assurer que vous interrogez le `DefaultIfEmpty` méthode de la collection groupée. Cela garantit que les éléments de la collection située du côté gauche de la jointure sont toujours inclus dans le résultat de la requête même s’ils n’ont aucun résultat correspondant à partir de la collection située à droite. Vous pouvez ajouter du code à votre requête pour fournir une valeur de résultat par défaut lorsqu’il n’existe aucune valeur correspondante dans la collection située à droite de la jointure.  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a>Pour effectuer une jointure externe gauche à l’aide de la clause Group Join  
  
1.  Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples d’une jointure externe gauche groupée et une jointure externe gauche non groupée.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a>Effectuer une jointure à l’aide d’une clé Composite  
 Vous pouvez utiliser la `And` mot clé dans un `Join` ou `Group Join` clause pour identifier les différents champs clés à utiliser lors de la mise en correspondance les valeurs des collections jointes. Le `And` mot clé spécifie que tous les spécifiés les champs clés doivent correspondre pour les éléments à joindre.  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a>Pour effectuer une jointure à l’aide d’une clé composite  
  
1.  Ajoutez le code suivant à la `Module1` module dans votre projet pour voir des exemples d’une jointure qui utilise une clé composite.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a>Exécutez le Code  
  
#### <a name="to-add-code-to-run-the-examples"></a>Pour ajouter du code pour exécuter les exemples  
  
1.  Remplacez le `Sub Main` dans le `Module1` module dans votre projet avec le code suivant pour exécuter les exemples dans cette rubrique.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Appuyez sur F5 pour exécuter les exemples.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Join (clause)](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join (clause)](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [From (clause)](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where (clause)](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)  
 [Transformations de données avec LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
