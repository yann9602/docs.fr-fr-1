---
title: "Module Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Module"
  - "vb.Module"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "modules, classes"
  - "modules"
  - "Module statement"
  - "modules, declaring"
  - "standard modules"
  - "classes [Visual Basic], vs. modules"
  - "declarations, modules"
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Module Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare le nom d'un module et introduit la définition des variables, propriétés, événements et procédures contenus dans le module.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## Composants  
 `attributelist`  
 Facultatif.  Consultez [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Facultatif.  Il peut s'agir de l'une des valeurs suivantes :  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Obligatoire.  Nom de ce module.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Facultatif.  Instructions qui définissent les variables, propriétés, événements, procédures et types imbriqués de ce module.  
  
 `End Module`  
 Met fin à la définition `Module`.  
  
## Notes  
 Une instruction `Module` définit un type référence disponible dans l'ensemble de son espace de noms.  Un *module* \(parfois appelé *module standard*\)est semblable à une classe, à quelques distinctions importantes près.  Chaque module contient exactement une instance et ne doit pas être créé ou assigné à une variable.  Les modules ne prennent pas en charge l'héritage ou n'implémentent pas d'interfaces.  Notez qu'un module n'est pas un *type* dans le sens où une classe ou une structure l'est ; vous ne pouvez pas déclarer un élément de programmation comme ayant le type de données d'un module.  
  
 Vous pouvez utiliser `Module` seulement au niveau de l'espace de noms.  Cela signifie que le *contexte de déclaration* pour un module doit être un fichier source ou un espace de noms, et ne peut pas être une classe, une structure, un module, une interface, une procédure ou un bloc.  Vous ne pouvez pas imbriquer un module dans un autre module, ou dans un type.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Un module a la même durée de vie que votre programme.  Ses membres étant tous `Shared`, ils ont également une durée de vie équivalente à celle du programme.  
  
 Les modules disposent par défaut d'un accès [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Tous les membres d'un module sont implicitement `Shared`.  
  
## Classes et Modules  
 Ces éléments présentent beaucoup de similitudes, mais ils comportent également beaucoup de différences.  
  
-   **Terminologie.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : *modules de classe* \(fichiers .cls\) et *modules standard* \(fichiers .bas\).  La version actuelle appelle respectivement ces *classes* et ces *modules*.  
  
-   **Membres partagés.** Vous pouvez contrôler si un membre d'une classe est un membre partagé ou un membre d'instance.  
  
-   **Orientation objet.** Les classes sont orientées objet, ce qui n'est pas le cas des modules.  Par conséquent, seules les classes peuvent être instanciées comme des objets.  Pour plus d'informations, consultez [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Règles  
  
-   **Modificateurs.** Tous les membres de module sont implicitement [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  Vous ne pouvez pas utiliser le mot clé `Shared` lors de la déclaration d'un membre, et vous ne pouvez pas modifier l'état partagé d'un membre.  
  
-   **Héritage.** Un module ne peut pas hériter d'un type autre que <xref:System.Object>, d'où héritent tous les modules.  En particulier, un module ne peut pas hériter d'un autre.  
  
     Vous ne pouvez pas utiliser l'[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) dans une définition de module, même pour spécifier <xref:System.Object>.  
  
-   **Default, propriété.** Vous ne pouvez pas définir de propriétés par défaut dans un module.  Pour plus d'informations, consultez [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportement  
  
-   **Niveau d'accès.** Dans un module, vous pouvez déclarer chaque membre avec son propre niveau d'accès.  Les membres de module disposent par défaut d'un accès [Public](../../../visual-basic/language-reference/modifiers/public.md), sauf les variables et les constantes qui possèdent par défaut un accès [Private](../../../visual-basic/language-reference/modifiers/private.md).  Lorsqu'un module dispose d'un accès plus restreint que l'un de ses membres, le niveau d'accès du module spécifié est prioritaire.  
  
-   **Portée.** Un module est présent dans la portée pour son espace de noms.  
  
     La portée de chaque membre de module est le module entier.  Notez que tous les membres subissent une *promotion de type* qui entraîne la promotion de leur portée dans l'espace de noms qui contient le module.  Pour plus d'informations, consultez [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Qualification.** Un projet peut contenir plusieurs modules, et vous pouvez déclarer des membres avec le même nom dans au moins deux modules.  Toutefois, vous devez qualifier toute référence à ce membre avec le nom de module approprié si la référence est externe à ce module.  Pour plus d'informations, consultez [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## Exemple  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/module-statement_1.vb)]  
  
## Voir aussi  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)