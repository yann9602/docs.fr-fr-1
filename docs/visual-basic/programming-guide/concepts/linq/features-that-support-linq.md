---
title: "Fonctionnalités de Visual Basic qui prennent en charge LINQ | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 3bca15a07a88195589b9c9de5f9842eea42912f1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-features-that-support-linq"></a>Fonctionnalités Visual Basic prenant en charge LINQ
Le nom [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] fait référence à la technologie dans Visual Basic prend en charge la syntaxe de requête et les autres constructions de langage directement dans le langage. Avec [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], vous n’avez pas à apprendre un nouveau langage de requête sur une source de données externe. Vous pouvez interroger les données dans les bases de données relationnelles, de magasins XML ou d’objets à l’aide de Visual Basic. Cette intégration de fonctions de requête dans le langage permet la vérification de la compilation pour les erreurs de syntaxe et de la sécurité de type. Cette intégration garantit également que vous connaissez déjà la plupart de ce que vous devez savoir pour écrire des requêtes riches et variées dans Visual Basic.  
  
 Les sections suivantes décrivent les constructions de langage qui prennent en charge LINQ de manière suffisamment détaillée pour vous permettent de lire les documentations d’introduction, les exemples de code et exemples d’applications. Vous pouvez également cliquer sur les liens pour trouver des explications plus détaillées de manière les fonctionnalités de langage ensemble pour activer des requêtes LINQ. Un bon point de départ est [procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Expressions de requête  
 Dans Visual Basic, les expressions de requête peuvent être exprimées dans une syntaxe déclarative semblable à celle de SQL ou XQuery. Au moment de la compilation, la syntaxe de requête est convertie en appels de méthode à l’implémentation d’un fournisseur LINQ des méthodes d’extension de requête standard (opérateur). Contrôle des applications qui sont des opérateurs de requête standard dans la portée en spécifiant l’espace de noms approprié avec une `Imports` instruction. Syntaxe d’une expression de requête Visual Basic ressemble à ceci :  
  
 [!code-vb[VbLINQVbFeatures n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Pour plus d’informations, consultez [Introduction à LINQ dans Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Variables implicitement typées  
 Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez activer au compilateur de déduire et d’assigner le type. Cela est appelé *l’inférence de type local*.  
  
 Les variables dont les types sont déduits sont fortement typées, comme les variables dont vous spécifiez explicitement le type. Inférence de type local fonctionne uniquement lorsque vous définissez une variable locale à l’intérieur d’un corps de méthode. Pour plus d’informations, consultez [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 L’exemple suivant illustre l’inférence de type local. Pour utiliser cet exemple, vous devez définir `Option Infer` à `On`.  
  
 [!code-vb[VbLINQVbFeatures n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Inférence de type local rend également possible de créer des types anonymes, qui sont décrites plus loin dans cette section et sont nécessaires pour les requêtes LINQ.  
  
 Dans l’exemple LINQ suivant, l’inférence de type se produit si `Option Infer` est `On` ou `Off`. Une erreur de compilation se produit si `Option Infer` est `Off` et `Option Strict` est `On`.  
  
 [!code-vb[VbLINQVbFeatures n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Initialiseurs d'objets  
 Initialiseurs d’objets sont utilisés dans les expressions de requête lorsque vous devez créer un type anonyme pour contenir les résultats d’une requête. Elles peuvent également servir à initialiser des objets de types nommés en dehors de requêtes. En utilisant un initialiseur d’objet, vous pouvez initialiser un objet dans une seule ligne sans appeler explicitement un constructeur. En supposant que vous ayez une classe nommée `Customer` qui a public `Name` et `Phone` propriétés, ainsi que d’autres propriétés, un initialiseur d’objet peut être utilisé de cette manière :  
  
 [!code-vb[VbLINQVbFeatures n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Pour plus d’informations, consultez [initialiseurs d’objets : Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Types anonymes  
 Les types anonymes fournissent un moyen pratique pour regrouper temporairement un ensemble de propriétés dans un élément que vous souhaitez inclure dans un résultat de requête. Cela vous permet de choisir n’importe quelle combinaison des champs disponibles dans la requête, dans n’importe quel ordre, sans définir un type de données nommé pour l’élément.  
  
 Un *type anonyme* est généré dynamiquement par le compilateur. Le nom du type est assigné par le compilateur, et il peut varier avec chaque nouvelle compilation. Par conséquent, le nom ne peut pas être utilisé directement. Les types anonymes sont initialisés de la manière suivante :  
  
 [!code-vb[VbLINQVbFeatures n °&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Pour plus d’informations, consultez [les Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>méthodes d’extension.  
 Méthodes d’extension permettent d’ajouter des méthodes à un type de données ou d’une interface en dehors de la définition. Cette fonctionnalité vous permet, en effet, ajoutez de nouvelles méthodes à un type existant sans modifier réellement. Les opérateurs de requête standard sont eux-mêmes un ensemble de méthodes d’extension qui fournissent des [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fonctionnalité de requête pour n’importe quel type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Autres extensions <xref:System.Collections.Generic.IEnumerable%601>incluent <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>et <xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601>  
  
 La méthode d’extension suivante ajoute une méthode d’impression à la <xref:System.String>classe.</xref:System.String>  
  
 [!code-vb[VbLINQVbFeatures n °&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 La méthode est appelée comme une méthode d’instance ordinaire de <xref:System.String>:</xref:System.String>  
  
 [!code-vb[VbLINQVbFeatures&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Pour plus d’informations, consultez [les méthodes d’Extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressions lambda  
 Une expression lambda est une fonction sans nom qui calcule et retourne une valeur unique. Contrairement aux fonctions nommées, une expression lambda peut être définie et exécutée en même temps. L’exemple suivant affiche 4.  
  
 [!code-vb[VbLINQVbFeatures n °&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Vous pouvez affecter la définition d’expression lambda à un nom de variable, puis utiliser le nom d’appeler la fonction. L’exemple suivant affiche également 4.  
  
 [!code-vb[VbLINQVbFeatures&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], expressions lambda offrent de nombreux opérateurs de requête standard. Le compilateur crée des expressions lambda pour capturer les calculs qui sont définis dans les méthodes de requête fondamentales, telles que `Where`, `Select`, `Order By`, `Take While`et d’autres.  
  
 Par exemple, le code suivant définit une requête qui retourne tous les étudiants seniors dans une liste d’étudiants.  
  
 [!code-vb[VbLINQVbFeatures&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 La définition de requête est compilée en code qui ressemble à l’exemple suivant, qui utilise deux expressions lambda pour spécifier les arguments de `Where` et `Select`.  
  
 [!code-vb[VbLINQVbFeatures&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Deux versions peuvent être exécutées en utilisant un `For Each` boucle :  
  
 [!code-vb[VbLINQVbFeatures&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Pour plus d’informations, consultez [Expressions Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Instruction Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
