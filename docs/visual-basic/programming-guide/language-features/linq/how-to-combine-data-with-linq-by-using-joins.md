---
title: "How to: Combine Data with LINQ by Using Joins (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], joins"
  - "joins [LINQ in Visual Basic]"
  - "Join clause [LINQ in Visual Basic]"
  - "Group Join clause [Visual Basic]"
  - "joining [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Combine Data with LINQ by Using Joins (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Visual Basic fournit les clauses de requête `Join` et `Group Join` pour vous permettre de combiner le contenu de plusieurs collections en fonction de leurs valeurs communes.  Ces valeurs sont appelées valeurs de *clés*.  Les développeurs familiarisés avec les concepts de base de données relationnelle reconnaîtront la clause `Join` comme une JOINTURE INTERNE et la clause `Group Join` comme, indéniablement, une JOINTURE EXTERNE GAUCHE.  
  
 Les exemples de cette rubrique illustrent quelques façons de combiner des données à l'aide des clauses de requête `Join` et `Group Join`.  
  
## Création d'un projet et ajout d'exemples de données  
  
#### Pour créer un projet qui contient des exemples de données et des types  
  
1.  Pour exécuter les exemples de cette rubrique, ouvrez Visual Studio et ajoutez un nouveau projet d'application console Visual Basic.  Double\-cliquez sur le fichier Module1.vb créé par Visual Basic.  
  
2.  Les exemples de cette rubrique utilisent les types `Person` et `Pet` et les données de l'exemple de code suivant.  Copiez ce code dans le module `Module1` par défaut créé par Visual Basic.  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## Réalisation d'une jointure interne en utilisant la clause Join  
 Une JOINTURE INTERNE combine les données de deux collections.  Les éléments pour lesquels les correspondances de valeurs de clés spécifiées sont incluses.  Tous les éléments de l'une ou l'autre des collections qui n'ont pas d'élément correspondant dans l'autre collection sont exclus.  
  
 Dans Visual Basic, LINQ fournit deux options pour effectuer une JOINTURE INTERNE : une jointure implicite et une jointure explicite.  
  
 Une jointure implicite spécifie les collections à joindre dans une clause `From` et identifie les champs clés correspondants dans une clause `Where`.  Visual Basic joint implicitement les deux collections en fonction des champs clés spécifiés.  
  
 Vous pouvez spécifier une jointure explicite en utilisant la clause `Join` lorsque vous souhaitez utiliser des champs clés spécifiques dans la jointure.  Dans ce cas, une clause `Where` peut encore être utilisée pour filtrer les résultats de la requête.  
  
#### Pour effectuer une jointure interne en utilisant la clause Join  
  
1.  Ajoutez le code suivant au module `Module1` dans votre projet pour voir des exemples de jointure interne implicite et explicite.  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## Réalisation d'une jointure externe gauche à l'aide de la clause Group Join  
 Une JOINTURE EXTERNE GAUCHE inclut tous les éléments de la collection située à gauche de la jointure et uniquement les valeurs correspondantes de la collection située à droite de la jointure.  Tous les éléments de la collection située du côté droit de la jointure qui ne possèdent pas d'élément correspondant dans la collection de gauche sont exclus du résultat de la requête.  
  
 La clause `Group Join` effectue, en effet, une JOINTURE EXTERNE GAUCHE.  La différence entre ce qui est habituellement appelé JOINTURE EXTERNE GAUCHE et ce que retourne la clause `Group Join` est que la clause `Group Join` regroupe des résultats de la collection située du côté droit de la jointure pour chaque élément de la collection de gauche.  Dans une base de données relationnelle, une JOINTURE EXTERNE GAUCHE retourne un résultat dégroupé dans lequel chaque élément du résultat de la requête contient des éléments correspondants des deux collections de la jointure.  Dans ce cas, les éléments de la collection située du côté gauche de la jointure sont répétés pour chaque élément correspondant de la collection située du côté droit.  Vous verrez mieux de quoi il s'agit en complétant la procédure suivante.  
  
 Vous pouvez récupérer les résultats d'une requête `Group Join` sous la forme d'un résultat dégroupé en étendant votre requête afin de retourner un élément pour chaque résultat de requête groupé.  Pour ce faire, vous devez vous assurer que vous interrogez la méthode `DefaultIfEmpty` de la collection groupée.  Cela permet de garantir que les éléments de la collection située du côté gauche de la jointure sont toujours inclus dans le résultat de la requête même s'ils n'ont pas de résultats correspondants dans la collection située du côté droit.  Vous pouvez ajouter du code à votre requête pour fournir une valeur de résultat par défaut lorsqu'il n'existe aucune valeur correspondante dans la collection située du côté droit de la jointure.  
  
#### Pour effectuer une jointure externe gauche en utilisant la clause Group Join  
  
1.  Ajoutez le code suivant au module `Module1` dans votre projet pour consulter des exemples de jointure externe gauche groupée et de jointure externe gauche dégroupée.  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## Réalisation d'une jointure à l'aide d'une clé composite  
 Vous pouvez utiliser le mot clé `And` dans une clause `Join` ou `Group Join` pour identifier les différents champs clés à utiliser lors de l'établissement de correspondances entre les valeurs des collections qui sont jointes.  Le mot clé `And` spécifie que tous les champs clés spécifiés doivent correspondre pour les éléments à joindre.  
  
#### Pour effectuer une jointure en utilisant une clé composite  
  
1.  Ajoutez le code suivant au module `Module1` de votre projet pour consulter des exemples d'une jointure qui utilise une clé composite.  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## Exécution du code  
  
#### Pour ajouter du code pour exécuter les exemples  
  
1.  Remplacez le `Sub Main` dans le module `Module1` de votre projet par le code suivant pour exécuter les exemples de cette rubrique.  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  Appuyez sur F5 pour exécuter les exemples.  
  
## Voir aussi  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Transformations de données avec LINQ \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)