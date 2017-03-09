---
title: "Inherits Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Inherits"
  - "Inherits"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Inherits statement"
  - "Inherits statement, syntax"
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Inherits Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La classe ou l'interface en cours hérite des attributs, variables, propriétés, procédures et événements d'une autre classe ou d'un autre ensemble d'interfaces.  
  
## Syntaxe  
  
```  
Inherits basetypenames  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`basetypenames`|Obligatoire.  Nom de la classe dont cette classe dérive.<br /><br /> ou<br /><br /> Noms des interfaces d'où dérive cette interface.  Utilisez des virgules pour séparer plusieurs noms.|  
  
## Notes  
 Si elle est utilisée, l'instruction `Inherits` doit être la première ligne non vide et sans commentaire dans une définition de classe ou d'interface.  Elle doit suivre immédiatement l'instruction `Class` ou `Interface`.  
  
 Vous pouvez utiliser `Inherits` uniquement dans une classe ou une interface.  Cela signifie que le contexte de déclaration pour un héritage ne peut pas être un fichier source, un espace de noms, une structure, un module, une procédure ou un bloc.  
  
## Règles  
  
-   **Héritage de la classe.** Si une classe utilise l'instruction `Inherits`, vous ne pouvez spécifier qu'une seule classe de base.  
  
     Une classe ne peut pas hériter d'une classe imbriquée dans celle\-ci.  
  
-   **Héritage de l'interface.** Si une interface utilise l'instruction `Inherits`, vous pouvez spécifier une ou plusieurs interfaces de base.  Vous pouvez hériter de deux interfaces même si chacune définit un membre avec le même nom.  Dans ce cas, le code d'implémentation doit utiliser la qualification de nom pour spécifier le membre qu'il implémente.  
  
     Une interface ne peut pas hériter d'une autre interface dont le niveau d'accès est plus restrictif.  Par exemple, une interface `Public` ne peut pas hériter d'une interface `Friend`.  
  
     Une interface ne peut pas hériter d'une interface qui y est imbriquée.  
  
 Un exemple d'héritage de classe dans le .NET Framework est la classe <xref:System.ArgumentException> qui hérite de la classe <xref:System.SystemException>.  Elle fournit à <xref:System.ArgumentException> toutes les propriétés et procédures prédéfinies requises par les exceptions système, telles que la propriété <xref:System.Exception.Message%2A> et la méthode <xref:System.Exception.ToString%2A>.  
  
 Un exemple d'héritage d'interface dans le .NET Framework est l'interface <xref:System.Collections.ICollection> qui hérite de l'interface <xref:System.Collections.IEnumerable>.  <xref:System.Collections.ICollection> hérite de la définition de l'énumérateur permettant de parcourir une collection.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Inherits` pour montrer comment une classe nommée `thisClass` peut hériter de tous les membres d'une classe de base nommée `anotherClass`.  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/inherits-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant présente l'héritage de plusieurs interfaces.  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/inherits-statement_2.vb)]  
  
 L'interface nommée `thisInterface` contient maintenant toutes les définitions des interfaces <xref:System.IComparable>, <xref:System.IDisposable> et <xref:System.IFormattable>. Les membres hérités fournissent respectivement la comparaison spécifique au type de deux objets, en libérant des ressources allouées et en exprimant la valeur d'un objet en tant que `String`.  Une classe qui implémente `thisInterface` doit implémenter chaque membre de chaque interface de base.  
  
## Voir aussi  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)