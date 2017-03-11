---
title: "Visual Basic Features That Support LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic, LINQ features"
  - "LINQ [Visual Basic], features supporting LINQ"
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Visual Basic Features That Support LINQ
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Le nom [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] fait référence à la technologie dans Visual Basic qui prend en charge la syntaxe de requête et d'autres constructions de langage directement dans le langage.  Avec [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], vous n'avez pas à apprendre un nouveau langage pour exécuter une requête sur une source de données externe.  Vous pouvez exécuter une requête sur les données de bases de données relationnelles, de magasins XML ou d'objets à l'aide de Visual Basic.  Cette intégration de fonctions de requête dans le langage active le contrôle de compilation pour les erreurs de syntaxe et la cohérence des types.  Grâce à cette intégration, vous avez pratiquement toutes les connaissances nécessaires pour écrire des requêtes puissantes et variées dans Visual Basic.  
  
 Les sections suivantes décrivent les constructions de langage qui prennent en charge LINQ de manière suffisamment détaillée pour vous permettre de lire les documentations d'introduction, les exemples de code et les applications d'exemple.  Vous pouvez également cliquer sur les liens pour consulter des explications plus détaillées sur la manière dont les fonctionnalités de langage se combinent pour activer LINQ \(Language\-Integrated Query\).  Il est conseillé de commencer par [Procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## Expressions de requête  
 Les expressions de requête dans Visual Basic peuvent être exprimées dans une syntaxe déclarative semblable à celle de SQL ou de XQuery.  Lors de la compilation, la syntaxe de requête est convertie en appels de méthode à l'implémentation d'un fournisseur LINQ des méthodes d'extension d'opérateur de requête standard.  Les applications déterminent les opérateurs de requête standard qui sont dans la portée en spécifiant l'espace de noms approprié avec une instruction `Imports`.  La syntaxe pour une expression de requête Visual Basic se présente sous la forme suivante :  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_1.vb)]  
  
 Pour plus d'informations, consultez [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## Variables implicitement typées  
 Au lieu de spécifier un type explicitement lorsque vous déclarez et initialisez une variable, vous pouvez maintenant permettre au compilateur de déduire et d'assigner le type.  Cette opération est dénommée *inférence de type locale*.  
  
 Les variables dont les types sont déduits sont fortement typées, comme les variables dont vous spécifiez le type de manière explicite.  L'inférence de type locale fonctionne uniquement lorsque vous définissez une variable locale à l'intérieur d'un corps de méthode.  Pour plus d'informations, consultez [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 L'exemple suivant illustre l'inférence de type locale.  Pour utiliser cet exemple, vous devez affecter à `Option Infer` la valeur `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_2.vb)]  
  
 L'inférence de type locale permet également de créer des types anonymes, qui sont décrits plus loin dans cette section et sont nécessaires aux requêtes LINQ.  
  
 Dans l'exemple LINQ suivant, l'inférence de type se produit si `Option Infer` a la valeur `On` ou `Off`.  Une erreur de compilation se produit si `Option Infer` a la valeur `Off` et `Option Strict` a la valeur `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_3.vb)]  
  
## Initialiseurs d'objets  
 Les initialiseurs d'objets sont utilisés dans les expressions de requête lorsque vous devez créer un type anonyme pour contenir les résultats d'une requête.  Ils peuvent également être utilisés pour initialiser des objets de types nommés en dehors de requêtes.  À l'aide d'un initialiseur d'objet, vous pouvez initialiser un objet sur une ligne sans appeler explicitement un constructeur.  Supposons que vous ayez une classe nommée `Customer` possédant des propriétés `Name` et `Phone` publiques, ainsi que d'autres propriétés, un initialiseur d'objet peut être utilisé de la manière suivante :  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_4.vb)]  
  
 Pour plus d'informations, consultez [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## Types anonymes  
 Les types anonymes offrent un moyen commode pour regrouper temporairement un ensemble de propriétés en un élément que vous souhaitez inclure dans un résultat de requête.  Ceci vous permet de choisir toute combinaison de champs disponibles dans la requête, dans l'ordre voulu, sans définir un type de données nommé pour l'élément.  
  
 Un *type anonyme* est généré dynamiquement par le compilateur.  Le nom du type est assigné par le compilateur et il peut varier avec chaque nouvelle compilation.  Le nom ne peut donc pas être utilisé directement.  Les types anonymes sont initialisés de la manière suivante :  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_5.vb)]  
  
 Pour plus d'informations, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## Méthodes d'extension  
 Les méthodes d'extension vous permettent d'ajouter des méthodes à un type de données ou à une interface à partir de l'extérieur de la définition.  Cette fonctionnalité vous permet en fait d'ajouter de nouvelles méthodes à un type existant sans le modifier réellement.  Les opérateurs de requête standard sont eux\-mêmes un ensemble de méthodes d'extension qui fournissent les fonctionnalités de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] pour tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>. Les autres extensions à <xref:System.Collections.Generic.IEnumerable%601> comprennent <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A> et <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 La méthode d'extension suivante ajoute une méthode d'impression à la classe <xref:System.String>.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_6.vb)]  
  
 Cette méthode est appelée comme une méthode d'instance ordinaire de <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_7.vb)]  
  
 Pour plus d'informations, consultez [méthodes d'extension.](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## Expressions lambda  
 Une expression lambda est une fonction sans nom qui calcule et retourne une valeur unique.  Contrairement aux fonctions nommées, une expression lambda peut être définie et exécutée simultanément.  L'exemple suivant affiche 4.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_8.vb)]  
  
 Vous pouvez assigner la définition d'expression lambda à un nom de variable, puis utiliser ce nom pour appeler la fonction.  L'exemple suivant affiche également 4.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_9.vb)]  
  
 Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], les expressions lambda sont à la base d'un grand nombre d'opérateurs de requête standard.  Le compilateur crée des expressions lambda pour capturer les calculs qui sont définis dans des méthodes de requête fondamentales, telles que `Where`, `Select`, `Order By`, `Take While`, etc.  
  
 Par exemple, le code suivant définit une requête qui retourne tous les étudiants de second cycle dans une liste d'étudiants.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_10.vb)]  
  
 La définition de la requête est compilée dans un code semblable à l'exemple suivant, qui utilise deux expressions lambda pour spécifier les arguments pour `Where` et `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_11.vb)]  
  
 Les deux versions peuvent être exécutées à l'aide d'une boucle `For Each` :  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/features-that-support-linq_12.vb)]  
  
 Pour plus d'informations, consultez [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ et chaînes](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [C\# Features That Support LINQ](../../../../csharp/programming-guide/concepts/linq/features-that-support-linq.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)