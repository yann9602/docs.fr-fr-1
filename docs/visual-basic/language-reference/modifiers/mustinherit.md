---
title: "MustInherit (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MustInherit"
  - "vb.MustInherit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], abstract"
  - "MustInherit classes, MustInherit keyword"
  - "abstract classes, MustInherit class"
  - "MustInherit keyword"
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# MustInherit (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'une classe peut être utilisée uniquement comme classe de base et que vous ne pouvez pas créer un objet directement à partir de cette classe.  
  
## Notes  
 Le but d'une *classe de base* \(également connue sous le nom *classe abstraite*\) est de définir une fonctionnalité commune à toutes les classes qui en sont dérivées.  Cela évite aux classes dérivées de devoir redéfinir les éléments communs.  Cette fonctionnalité commune n'est parfois pas suffisamment complète pour faire un objet utilisable, et chaque classe dérivée définit la fonctionnalité manquante.  Dans ce cas, vous souhaitez que le code utilisateur crée uniquement des objets à partir des classes dérivées.  Utilisez `MustInherit` sur la classe de base pour appliquer ceci.  
  
 Une autre utilisation d'une classe `MustInherit` consiste à restreindre une variable à un jeu de classes connexes.  Vous pouvez définir une classe de base et en dériver toutes ces classes connexes.  La classe de base n'a pas besoin de fournir une fonctionnalité commune à toutes les classes dérivées, mais peut servir de filtre pour assigner des valeurs aux variables.  Si votre code utilisateur déclare une variable comme classe de base, Visual Basic vous permet d'assigner uniquement objet de l'une des classes dérivées à cette variable.  
  
 Le .NET Framework définit plusieurs classes `MustInherit`, parmi elles <xref:System.Array>, <xref:System.Enum> et <xref:System.ValueType>.  <xref:System.ValueType> est un exemple d'une classe de base qui restreint une variable.  Tous les types valeur dérivent de <xref:System.ValueType>.  Si vous déclarez une variable comme <xref:System.ValueType>, vous ne pouvez assigner que des types valeur à cette variable.  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `MustInherit` uniquement dans une instruction `Class`.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `MustInherit` avec `NotInheritable` dans la même déclaration.  
  
## Exemple  
 L'exemple suivant illustre à la fois l'héritage et la substitution forcés.  La classe de base `shape` définit une variable `acrossLine`.  Les classes `circle` et `square` dérivent de `shape`.  Elles héritent de la définition de `acrossLine`, mais elles doivent définir la fonction `area`parce que ce calcul est différent pour chaque type de forme.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Vous pouvez déclarer `shape1` et `shape2` comme type `shape`.  Toutefois, vous ne pouvez pas créer un objet de `shape` parce que la fonctionnalité de la fonction `area` est manquante et il est marqué comme `MustInherit`.  
  
 Puisqu'elles sont déclarées comme `shape`, les variables `shape1` et `shape2` sont restreintes aux objets des classes dérivées `circle` et `square`.  Visual Basic ne vous permet pas d'assigner un autre objet à ces variables, ce qui vous procure un niveau de sécurité de type élevé.  
  
## Utilisation  
 Le modificateur `MustInherit` peut être utilisé dans le contexte suivant :  
  
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## Voir aussi  
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)