---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Spécifie qu’une classe peut être utilisée uniquement comme classe de base et que vous ne pouvez pas créer un objet directement à partir de celui-ci.  
  
## <a name="remarks"></a>Remarques  
 L’objectif d’un *classe de base* (également appelé un *classe abstraite*) consiste à définir des fonctionnalités communes à toutes les classes dérivées. Cela permet d’économiser les classes dérivées de devoir redéfinir les éléments communs. Dans certains cas, cette fonctionnalité commune n’est pas suffisamment complète afin de rendre un objet utilisable, et chaque classe dérivée définit la fonctionnalité manquante. Dans ce cas, vous souhaitez le code de consommation pour créer des objets qu’à partir de classes dérivées. Vous utilisez `MustInherit` sur la classe de base pour appliquer ceci.  
  
 Une autre utilisation d’un `MustInherit` classe consiste à restreindre une variable à un ensemble de classes connexes. Vous pouvez définir une classe de base et dérivent toutes ces classes connexes. La classe de base ne devez pas fournir toutes les fonctionnalités communes à toutes les classes dérivées, mais il peut servir d’un filtre pour assigner des valeurs aux variables. Si votre code de consommation déclare une variable comme classe de base, Visual Basic permet de vous permettent d’attribuer uniquement à un objet à partir d’une des classes dérivées à cette variable.  
  
 Le .NET Framework définit plusieurs `MustInherit` classes <xref:System.Array>, <xref:System.Enum>, et <xref:System.ValueType>. <xref:System.ValueType>est un exemple de classe de base qui restreint une variable. Tous les types valeur dérivent <xref:System.ValueType>. Si vous déclarez une variable en tant que <xref:System.ValueType>, vous pouvez affecter uniquement des types valeur à cette variable.  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `MustInherit` uniquement dans un `Class` instruction.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `MustInherit` avec `NotInheritable` dans la même déclaration.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’héritage et la substitution forcés. La classe de base `shape` définit une variable `acrossLine`. Les classes `circle` et `square` dérivent `shape`. Ils héritent de la définition de `acrossLine`, mais elles doivent définir la fonction `area` parce que ce calcul est différent pour chaque type de forme.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Vous pouvez déclarer `shape1` et `shape2` de type `shape`. Toutefois, vous ne peut pas créer un objet à partir de `shape` , car il ne dispose pas de la fonctionnalité de la fonction `area` et est marqué comme `MustInherit`.  
  
 Puisqu’elles sont déclarées en tant que `shape`, les variables `shape1` et `shape2` sont restreintes aux objets des classes dérivées `circle` et `square`. Visual Basic ne permet pas assigner de tout autre objet à ces variables, qui vous offre un niveau élevé de sécurité de type.  
  
## <a name="usage"></a>Utilisation  
 Le `MustInherit` modificateur peut être utilisé dans ce contexte :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)  
 [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
