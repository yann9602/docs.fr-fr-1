---
title: "Fonctionnalités Visual Basic prenant en charge LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42465dbb168b7961792aec6b3c2bb7ae8f0a3355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-features-that-support-linq"></a>Fonctionnalités Visual Basic prenant en charge LINQ
Le nom [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] fait référence à la technologie en Visual Basic prend en charge la syntaxe de requête et les autres constructions de langage directement dans le langage. Avec [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous n’avez pas à apprendre un nouveau langage de requête sur une source de données externe. Vous pouvez interroger les données dans les bases de données relationnelles, de magasins XML ou d’objets à l’aide de Visual Basic. Cette intégration de fonctions de requête dans la langue permet la vérification de la compilation pour les erreurs de syntaxe et de la sécurité de type. Cette intégration garantit également que vous connaissez déjà la majeure partie de ce que vous devez savoir pour écrire des requêtes riches et variées dans Visual Basic.  
  
 Les sections suivantes décrivent les constructions de langage qui prend en charge de LINQ dans assez de détails pour vous permettre de lire les documentations d’introduction, les exemples de code et les exemples d’applications. Vous pouvez également cliquer sur les liens pour consulter des explications plus détaillées de la façon dont les fonctionnalités de langage collaborer pour activer language integrated query. Un bon point de départ est [procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).  
  
## <a name="query-expressions"></a>Expressions de requête  
 En Visual Basic, les expressions de requête peuvent être exprimées dans une syntaxe déclarative similaire à celle de SQL ou XQuery. Au moment de la compilation, syntaxe de requête est convertie en appels de méthode à l’implémentation d’un fournisseur LINQ des méthodes d’extension de requête standard opérateur. Contrôle des applications qui sont des opérateurs de requête standard dans la portée en spécifiant l’espace de noms approprié avec une `Imports` instruction. Syntaxe pour une expression de requête Visual Basic ressemble à ceci :  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 Pour plus d’informations, consultez [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## <a name="implicitly-typed-variables"></a>Variables implicitement typées  
 Au lieu de spécifier explicitement un type lorsque vous déclarez et initialisez une variable, vous pouvez activer au compilateur de déduire et d’assigner le type. Cela est appelé *l’inférence de type local*.  
  
 Les variables dont les types sont déduits sont fortement typées, comme les variables dont vous spécifiez explicitement le type. Inférence de type local fonctionne uniquement lorsque vous définissez une variable locale à l’intérieur d’un corps de méthode. Pour plus d’informations, consultez [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 L’exemple suivant illustre l’inférence de type local. Pour utiliser cet exemple, vous devez définir `Option Infer` à `On`.  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 Inférence de type local rend également possible de créer des types anonymes, qui sont décrites plus loin dans cette section et sont nécessaires pour les requêtes LINQ.  
  
 Dans l’exemple LINQ suivant, l’inférence de type se produit si `Option Infer` est `On` ou `Off`. Une erreur de compilation se produit si `Option Infer` est `Off` et `Option Strict` est `On`.  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>Initialiseurs d'objets  
 Initialiseurs d’objets sont utilisés dans les expressions de requête lorsque vous avez besoin de créer un type anonyme pour contenir les résultats d’une requête. Ils peuvent également servir à initialiser des objets de types nommés en dehors de requêtes. En utilisant un initialiseur d’objet, vous pouvez initialiser un objet dans une seule ligne sans appeler explicitement un constructeur. En supposant que vous ayez une classe nommée `Customer` qui a public `Name` et `Phone` propriétés, ainsi que d’autres propriétés, un initialiseur d’objet peut être utilisé de cette manière :  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 Pour plus d’informations, consultez [initialiseurs d’objets : Types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="anonymous-types"></a>Types anonymes  
 Les types anonymes fournissent un moyen pratique pour regrouper temporairement un ensemble de propriétés dans un élément que vous souhaitez inclure dans un résultat de requête. Cela vous permet de choisir n’importe quelle combinaison des champs disponibles dans la requête, dans n’importe quel ordre, sans définir un type de données nommé pour l’élément.  
  
 Un *type anonyme* est construit dynamiquement par le compilateur. Le nom du type est attribué par le compilateur, et il peut changer à chaque nouvelle compilation. Par conséquent, le nom ne peut pas être utilisé directement. Les types anonymes sont initialisés de la manière suivante :  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 Pour plus d’informations, consultez [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="extension-methods"></a>méthodes d’extension.  
 Méthodes d’extension permettent d’ajouter des méthodes à un type de données ou d’une interface à partir d’à l’extérieur de la définition. Cette fonctionnalité vous permet, en effet, ajouter de nouvelles méthodes à un type existant sans modifier réellement. Les opérateurs de requête standard sont eux-mêmes un ensemble de méthodes d’extension qui fournissent des [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fonctionnalité de requête pour n’importe quel type qui implémente <xref:System.Collections.Generic.IEnumerable%601>. Autres extensions <xref:System.Collections.Generic.IEnumerable%601> incluent <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, et <xref:System.Linq.Enumerable.Intersect%2A>.  
  
 La méthode d’extension suivante ajoute une méthode d’impression à la <xref:System.String> classe.  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 La méthode est appelée comme une méthode d’instance ordinaire de <xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 Pour plus d’informations, consultez la page [Méthodes d’extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Expressions lambda  
 Une expression lambda est une fonction sans nom qui calcule et retourne une valeur unique. Contrairement aux fonctions nommées, une expression lambda peut être définie et exécutée en même temps. L’exemple suivant affiche 4.  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 Vous pouvez affecter la définition d’expression lambda à un nom de variable, puis utiliser le nom d’appeler la fonction. L’exemple suivant affiche également 4.  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 Dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], expressions lambda sous-tendent à la plupart des opérateurs de requête standard. Le compilateur crée des expressions lambda pour capturer les calculs qui sont définis dans les méthodes de requête fondamentaux tels que `Where`, `Select`, `Order By`, `Take While`et d’autres.  
  
 Par exemple, le code suivant définit une requête qui retourne tous les étudiants supérieurs à partir d’une liste d’étudiants.  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 La définition de requête est compilée en code similaire à l’exemple suivant, qui utilise deux expressions lambda pour spécifier les arguments pour `Where` et `Select`.  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 Deux versions peuvent être exécutées à l’aide un `For Each` boucle :  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 Pour plus d’informations, consultez [Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Bien démarrer avec LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
