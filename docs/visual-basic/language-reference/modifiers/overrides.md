---
title: "Overrides (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Overrides"
  - "vb.Overrides"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "properties [Visual Basic], redefining"
  - "procedures, overriding"
  - "procedures, redefining"
  - "overriding"
  - "Overrides keyword"
  - "overriding, Overrides keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Overrides (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'une propriété ou procédure substitue une propriété ou procédure ayant un nom identique et ayant été héritée d'une classe de base.  
  
## Notes  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Overrides` uniquement dans une instruction de déclaration de propriété ou de procédure.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Overrides` avec `Shadows` ou `Shared` dans la même déclaration.  Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.  
  
-   **Correspondance entre signatures.** La signature de cette déclaration doit correspondre exactement à la *signature* de la propriété ou de la procédure à laquelle elle se substitue.  Cela signifie que les listes de paramètres doivent avoir le même nombre de paramètres, dans le même ordre, avec les mêmes types de données.  
  
     Outre la signature, la déclaration de substitution doit également correspondre exactement à ce qui suit :  
  
    -   Niveau d'accès  
  
    -   Type de retour, le cas échéant  
  
-   **Signatures génériques.** Pour une procédure générique, la signature inclut le nombre de paramètres de type.  Par conséquent, la déclaration de substitution doit correspondre à la version de la classe de base également selon ce critère.  
  
-   **Correspondance supplémentaire.** Cette déclaration doit non seulement correspondre à la signature de la version de la classe de base, mais aussi lui correspondre selon les critères suivants :  
  
    -   Modificateur de niveau d'accès \(tel que [Public](../../../visual-basic/language-reference/modifiers/public.md)\)  
  
    -   Mécanisme de passage de chaque paramètre \([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../visual-basic/language-reference/modifiers/byref.md)\)  
  
    -   Listes de contraintes pour chaque paramètre de type d'une procédure générique  
  
-   **Occultation et substitution.** L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.  Pour plus d'informations, consultez [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C\#.  
  
 Le modificateur `Overrides` peut être utilisé dans les contextes suivants :  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)