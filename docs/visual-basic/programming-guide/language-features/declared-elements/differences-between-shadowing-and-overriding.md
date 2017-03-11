---
title: "Differences Between Shadowing and Overriding (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "shadowing, vs. overriding"
  - "overriding, vs. shadowing"
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Differences Between Shadowing and Overriding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous définissez une classe qui hérite d'une classe de base, vous souhaitez parfois redéfinir un ou plusieurs des éléments de classe de base dans la classe dérivée.  L'occultation et la substitution sont disponibles à cette fin.  
  
## Comparaison  
 Les mécanismes d'occultation et de substitution sont tous deux utilisés lorsqu'une classe dérivée hérite d'une classe de base et redéfinissent un élément déclaré par un autre.  Il existe toutefois des différences notables entre l'occultation et la substitution.  
  
 Le tableau suivant compare l'occultation à la substitution.  
  
||||  
|-|-|-|  
|Point de comparaison|Occultation|Substitution|  
|Objectif|Protège contre une modification de classe de base suivante qui introduit un membre déjà défini dans votre classe dérivée|Atteint le polymorphisme en définissant une implémentation différente d'une procédure ou d'une propriété avec la même séquence d'appel <sup>1</sup>|  
|Élément redéfini|Tout type d'élément déclaré|Seulement une procédure \(`Function`, `Sub` ou `Operator`\) ou une propriété|  
|Élément redéfinissant|Tout type d'élément déclaré|Seulement une procédure ou une propriété avec une séquence d'appel identique<sup>1</sup>|  
|Niveau d'accès de l'élément redéfinissant|N'importe quel niveau d'accès|Impossible de modifier le niveau d'accès de l'élément substitué|  
|Lisibilité et accessibilité en écriture de l'élément redéfinissant|Toute combinaison|Ne peut pas modifier la lisibilité et la facilité d'écriture de la propriété substituée|  
|Contrôle sur la redéfinition|L'élément de classe de base ne peut pas appliquer ou interdire l'occultation|L'élément de classe de base peut spécifier `MustOverride`, `NotOverridable` ou `Overridable`|  
|Utilisation de mot clé|`Shadows` recommandé dans la classe dérivée ; `Shadows` supposé lorsque ni `Shadows` ni `Overrides` ne sont spécifiés<sup>2</sup>|`Overridable` ou `MustOverride` requis dans la classe de base ; `Overrides` requis dans la classe dérivée|  
|Héritage d'élément redéfinissant par des classes dérivant de votre classe dérivée|Élément occultant hérité par des classes plus dérivées ; élément occulté toujours masqué<sup>3</sup>|Élément substituant hérité par des classes plus dérivées ; élément substitué toujours substitué|  
  
 <sup>1</sup> La *séquence d'appel* se compose du type d'élément \(`Function`, `Sub`, `Operator` ou `Property`\), du nom, de la liste d'arguments et du type de retour.  Vous ne pouvez pas substituer une procédure par une propriété, ou vice versa.  Vous ne pouvez pas substituer un genre de procédure \(`Function`, `Sub` ou `Operator`\) par un autre genre.  
  
 <sup>2</sup> Si vous ne spécifiez pas `Shadows` ou `Overrides`, le compilateur signale un message d'avertissement pour vous aider à vérifier le genre de redéfinition que vous souhaitez utiliser.  Si vous ignorez l'avertissement, le mécanisme d'occultation est utilisé.  
  
 <sup>3</sup> Si l'élément occultant est inaccessible dans une classe plus dérivée, l'occultation n'est pas héritée.  Par exemple, si vous déclarez l'élément occultant comme `Private`, une classe dérivant de votre classe dérivée hérite de l'élément d'origine et non de l'élément occultant.  
  
## Indications  
 Vous utilisez normalement la substitution dans les cas suivants :  
  
-   Vous définissez des classes dérivées polymorphes.  
  
-   Vous souhaitez la sécurité du compilateur qui applique le type d'élément et la séquence d'appel identiques.  
  
 Vous utilisez normalement l'occultation dans les cas suivants :  
  
-   Vous savez que votre classe de base peut être modifiée et peut définir un élément à l'aide du même nom que le vôtre.  
  
-   Vous souhaitez pouvoir modifier le type d'élément ou la séquence d'appel.  
  
## Voir aussi  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)