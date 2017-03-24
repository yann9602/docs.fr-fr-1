---
title: "Shadows (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Shadows"
  - "shadows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "shadowing"
  - "duplicate names"
  - "scope, shadowing"
  - "Shadows keyword"
  - "names, shadowing"
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Shadows (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'un élément de programmation déclaré redéclare et masque un élément de programmation de même nom ou définit un ensemble d'éléments surchargés, dans une classe de base.  
  
## Notes  
 Le principal objectif de l'occultation \(qui est également appelée *masquage par nom*\) est de conserver la définition de vos membres de classe.  La classe de base peut subir un changement qui crée un élément du même nom que celui que vous avez déjà défini.  Dans ce cas, le modificateur `Shadows` oblige les références de votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.  
  
 L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais les deux approches sont significativement différentes.  Pour plus d'informations, consultez [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Shadows` seulement au niveau de la classe.  Cela signifie que le contexte de déclaration pour un élément `Shadows` doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.  
  
     Vous ne pouvez déclarer qu'un élément d'occultation dans une seule instruction de déclaration.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shadows` avec `Overloads`, `Overrides` ou `Static` dans la même déclaration.  
  
-   **Types d'éléments.** Vous pouvez occulter tout type d'élément déclaré par un autre type.  Si vous masquez une propriété ou une procédure avec une autre propriété ou procédure, les paramètres et le type retourné n'ont pas besoin de correspondre à ceux de la propriété ou de la procédure de la classe de base.  
  
-   **Accès.** L'élément occulté dans la classe de base n'est normalement pas disponible dans la classe dérivée qui l'occulte.  Cependant, les considérations suivantes s'appliquent :  
  
    -   Si l'élément d'occultation n'est pas disponible à partir du code qui s'y réfère, la référence correspond à l'élément occulté.  Par exemple, si un élément `Private` occulte un élément de classe de base, le code qui n'est pas autorisé à accéder à l'élément `Private` accède à la place à l'élément de classe de base.  
  
    -   Si vous occultez un élément, vous pouvez toujours accéder à l'élément occulté par l'intermédiaire d'un objet déclaré avec le type de classe de base.  Vous pouvez également y accéder par l'intermédiaire de `MyBase`.  
  
 Le modificateur `Shadows` peut être utilisé dans les contextes suivants :  
  
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instruction](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instruction](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instruction](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)