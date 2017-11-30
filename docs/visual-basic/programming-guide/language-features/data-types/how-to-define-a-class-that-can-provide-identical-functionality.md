---
title: "Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7cc2563f193fba9f9e30fcdfd5ea2766be16ba63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Comment : définir une classe qui fournisse des fonctionnalités identiques pour différents types de données (Visual Basic)
Vous pouvez définir une classe à partir de laquelle vous créez des objets qui fournissent les mêmes fonctions pour des types de données différents. Pour cela, vous spécifiez un ou plusieurs *paramètres de type* dans la définition. La classe peut ensuite servir de modèle pour les objets qui utilisent différents types de données. Une classe définie de cette façon est appelée *classe générique*.  
  
 L’avantage de définir une classe générique est que vous la définissez une seule fois. Votre code peut ensuite l’utiliser pour créer divers objets qui utilisent différents types de données. Cette approche offre de meilleures performances que la définition d’une classe avec le type `Object` .  
  
 En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Pour définir une classe avec un paramètre de type  
  
1.  Définissez la classe comme vous le faites habituellement.  
  
2.  Ajoutez `(Of` *typeparameter*`)` juste après le nom de classe pour spécifier un paramètre de type.  
  
3.  Si vous utilisez plusieurs paramètres de type, spécifiez-les dans une liste séparée par des virgules et mise entre parenthèses. Ne répétez pas le mot clé `Of` .  
  
4.  Si votre code effectue des opérations sur un paramètre de type autre qu’une simple assignation, faites suivre ce paramètre de type d’une clause `As` pour ajouter une ou plusieurs *contraintes*. Une contrainte garantit que le type fourni pour ce paramètre de type remplit une exigence similaire aux exigences suivantes :  
  
    -   Prend en charge une opération, par exemple `>`, que votre code exécute.  
  
    -   Prend en charge un membre, tel qu’une méthode, auquel votre code accède.  
  
    -   Expose un constructeur sans paramètre.  
  
     Si vous ne spécifiez pas de contraintes, votre code peut utiliser uniquement les opérations et membres qui sont pris en charge par [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md). Pour plus d'informations, consultez [Type List](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Identifiez chaque membre de classe qui doit être déclaré avec un type fourni et déclarez-le dans `As` `typeparameter`. Cela s’applique au stockage interne, aux paramètres de procédure et aux valeurs renvoyées.  
  
6.  Vérifiez que votre code utilise uniquement des opérations et des méthodes qui sont prises en charge par tous les types de données qu’il peut fournir à `itemType`.  
  
     L’exemple suivant définit une classe qui gère une liste très simple. Cette liste est contenue dans le tableau interne `items`. Le code utilisé peut déclarer le type de données des éléments de la liste. Un constructeur paramétrable permet au code utilisé de définir la limite supérieure de `items`, et le constructeur par défaut définit cette limite à 9 (sur un total de 10 éléments).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Vous pouvez déclarer une classe à partir de `simpleList` pour contenir une liste de valeurs `Integer` , une deuxième classe pour contenir une liste de valeurs `String` et une troisième classe pour contenir des valeurs `Date` . À l’exception du type de données des membres de la liste, les objets créés à partir de toutes ces classes ont un comportement identique.  
  
     L’argument de type que le code utilisé fournit à `itemType` peut être un type intrinsèque tel que `Boolean` ou `Double`, une structure, une énumération ou un type de classe, y compris l’un des types de classe définis par votre application.  
  
     Vous pouvez tester la classe `simpleList` à l’aide du code suivant.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Types génériques en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3)  
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Liste de types](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Guide pratique : utiliser une classe générique](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
