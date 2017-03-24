---
title: "Class Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Class"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class modules"
  - "Class statement"
  - "classes [Visual Basic], fields"
  - "fields, of classes"
  - "class types, class statements"
  - "classes [Visual Basic], creating"
  - "classes [Visual Basic], data members"
  - "data members, of classes"
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# Class Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare le nom d'une classe et introduit la définition des variables, des propriétés, des événements et des procédures que la classe contient.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attributelist`|Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Facultatif.  Consultez [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Facultatif.  Consultez [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Facultatif.  Indique une définition partielle de la classe.  Consultez [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Obligatoire.  Nom de cette classe.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Facultatif.  Spécifie qu'il s'agit d'une classe générique.|  
|`typelist`|Requis si vous utilisez le mot clé [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Liste de paramètres de type pour cette classe.  Consultez [Liste de types](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Facultatif.  Indique que cette classe hérite des membres d'une autre classe.  Consultez [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Requis si vous utilisez l'instruction `Inherits`.  Nom de la classe dont cette classe dérive.|  
|`Implements`|Facultatif.  Indique que cette classe implémente les membres d'une ou plusieurs interfaces.  Consultez [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez l'instruction `Implements`.  Noms des interfaces que cette classe implémente.|  
|`statements`|Facultatif.  Instructions qui définissent les membres de cette classe.|  
|`End Class`|Obligatoire.  Met fin à la définition `Class`.|  
  
## Notes  
 Une instruction `Class` définit un nouveau type de données.  Une *classe* est un bloc de construction fondamental d'une programmation orientée objet \(OOP\).  Pour plus d'informations, consultez [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Vous pouvez utiliser `Class` uniquement au niveau de l'espace de noms ou du module.  Cela signifie que le *contexte de déclaration* pour une classe doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ni un bloc.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Chaque instance d'une classe a une durée de vie indépendante de toutes les autres instances.  Cette durée de vie commence lorsqu'elle est créée par une clause [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) ou par une fonction telle que <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>.  Elle prend fin lorsque la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou les instances d'autres classes ont été affectées à toutes les variables pointant sur l'instance.  
  
 Les classes prennent par défaut l'accès [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Règles  
  
-   **Imbrication.** Vous pouvez définir une classe dans une autre.  La classe externe est appelée *classe conteneur* et la classe interne *classe imbriquée*.  
  
-   **Héritage.** Si la classe utilise l'[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md), vous ne pouvez spécifier qu'une seule classe de base ou interface.  Une classe ne peut pas hériter de plusieurs éléments.  
  
     Une classe ne peut pas hériter d'une autre classe avec un niveau d'accès plus restrictif.  Par exemple, une classe `Public` ne peut pas hériter d'une classe `Friend`.  
  
     Une classe ne peut pas hériter d'une classe imbriquée dans celle\-ci.  
  
-   **Implémentation.** Si la classe utilise l'[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`.  La nouvelle implémentation d'un membre de classe de base est une exception.  Pour plus d'informations, consultez « Nouvelle implémentation » dans [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Default, propriété.** Une classe peut spécifier qu'une propriété comme étant sa *propriété par défaut*.  Pour plus d'informations, consultez [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportement  
  
-   **Niveau d'accès.** Dans une classe, vous pouvez déclarer chaque membre avec son propre niveau d'accès.  Les membres de la classe prennent par défaut l'accès [Public](../../../visual-basic/language-reference/modifiers/public.md), à l'exception des variables et des constantes qui prennent par défaut l'accès [Private](../../../visual-basic/language-reference/modifiers/private.md).  Lorsqu'une classe a un accès plus limité que l'un de ses membres, le niveau d'accès de la classe a la priorité.  
  
-   **Portée.** Une classe est dans la portée dans tout son espace de noms, sa classe, sa structure ou son module conteneur.  
  
     La portée de chaque membre de classe est la classe entière.  
  
     **Durée de vie.** Visual Basic ne prend pas en charge des classes statiques.  L'équivalent fonctionnel d'une classe statique est fourni par un module.  Pour plus d'informations, consultez [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Les durées de vie des membres de classe dépendent de la manière et de l'emplacement où elles sont déclarées.  Pour plus d'informations, consultez [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Qualification.** Le code à l'extérieur d'une classe doit qualifier le nom d'un membre portant le même nom que cette classe.  
  
     Si le code à l'intérieur d'une classe imbriquée établit une référence non qualifiée à un élément de programmation, Visual Basic recherche d'abord l'élément dans sa classe imbriquée, puis dans sa classe conteneur, etc. jusqu'à l'élément conteneur le plus éloigné.  
  
## Classes et Modules  
 Ces éléments présentent beaucoup de similitudes, mais ils comportent également beaucoup de différences.  
  
-   **Terminologie.** Les versions précédentes de Visual Basic reconnaissent deux types de modules : *modules de classe* \(fichiers .cls\) et *modules standard* \(fichiers .bas\).  La version actuelle appelle respectivement ces *classes* et ces *modules*.  
  
-   **Membres partagés.** Vous pouvez contrôler si un membre d'une classe est un membre partagé ou un membre d'instance.  
  
-   **Orientation objet.** Les classes sont orientées objet, ce qui n'est pas le cas des modules.  Vous pouvez créer une ou plusieurs instances d'une classe.  Pour plus d'informations, consultez [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Exemple  
 L'exemple suivant utilise une instruction `Class` pour définir une classe et plusieurs membres.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## Voir aussi  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)