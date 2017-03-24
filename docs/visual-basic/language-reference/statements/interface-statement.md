---
title: "Interface Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Interface"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interface statement [Visual Basic]"
  - "interfaces, interface definition"
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Interface Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare le nom d'une interface et introduit les définitions des membres contenus dans l'interface.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attributelist`|Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Facultatif.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Facultatif.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Obligatoire.  Nom de cette interface.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Facultatif.  Indique qu'il s'agit d'une interface générique.|  
|`typelist`|Obligatoire si vous utilisez le mot clé [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Liste de paramètres de type pour cette interface.  Éventuellement, chaque paramètre de type peut être déclaré variant à l'aide des modificateurs génériques `In` et `Out`.  Consultez [Liste de types](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Facultatif.  Indique que cette interface hérite des attributs et des membres d'une autre ou d'autres interfaces.  Consultez [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Requis si vous utilisez l'instruction `Inherits`.  Noms des interfaces d'où dérive cette interface.|  
|`modifiers`|Facultatif.  Modificateurs appropriés pour le membre d'interface défini.|  
|`Property`|Facultatif.  Définit une propriété qui est membre de l'interface.|  
|`Function`|Facultatif.  Définit une procédure `Function` qui est membre de l'interface.|  
|`Sub`|Facultatif.  Définit une procédure `Sub` qui est membre de l'interface.|  
|`Event`|Facultatif.  Définit un événement qui est membre de l'interface.|  
|`Interface`|Facultatif.  Définit une interface qui est imbriquée dans cette interface.  La définition de l'interface imbriquée doit se terminer par une instruction `End Interface`.|  
|`Class`|Facultatif.  Définit une classe qui est membre de l'interface.  La définition de la classe membre doit se terminer par une instruction `End Class`.|  
|`Structure`|Facultatif.  Définit une structure qui est membre de l'interface.  La définition de la structure membre doit se terminer par une instruction `End Structure`.|  
|`membername`|Obligatoire pour chaque propriété, procédure, événement, interface, classe ou structure défini comme membre de l'interface.  Nom du membre.|  
|`End Interface`|Met fin à la définition `Interface`.|  
  
## Notes  
 Une *interface* définit un ensemble de membres, par exemple des propriétés et des procédures que les classes et les structures peuvent implémenter.  L'interface définit uniquement les signatures des membres, mais pas leurs mécanismes internes.  
  
 Une classe ou une structure implémente l'interface en fournissant un code pour chaque membre défini par l'interface.  Enfin, lorsque l'application crée une instance à partir de cette classe ou structure, un objet existe et s'exécute en mémoire.  Pour plus d'informations, consultez [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) et [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Vous pouvez utiliser `Interface` uniquement au niveau de l'espace de noms ou du module.  Cela signifie que le *contexte de déclaration* pour une interface doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ou un bloc.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Les interfaces disposent par défaut d'un accès [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Règles  
  
-   **Imbrication des interfaces.** Vous pouvez définir une interface dans une autre.  L'interface externe est appelée *interface conteneur*, et l'interface interne est appelée *interface imbriquée*.  
  
-   **Déclaration de membre.** Lorsque vous déclarez une propriété ou une procédure comme membre d'une interface, vous définissez uniquement la *signature* de cette propriété ou procédure.  Cela inclut le type d'élément \(propriété ou procédure\), ses paramètres et types de paramètre et son type de retour.  De ce fait, la définition du membre utilise une seule ligne de code, et les instructions de fin telles que `End Function` ou `End Property` ne sont pas valides dans une interface.  
  
     En revanche, lorsque vous définissez une énumération ou une structure, ou encore une classe ou une interface imbriquée, il est nécessaire d'inclure leurs données membres.  
  
-   **Modificateurs de membre.** Vous ne pouvez pas utiliser des modificateurs d'accès lors de la définition de membres de module, et vous ne pouvez pas spécifier [Shared](../../../visual-basic/language-reference/modifiers/shared.md) ou un modificateur de procédure sauf [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).  Vous pouvez déclarer tout membre avec [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md), et vous pouvez utiliser [Default](../../../visual-basic/language-reference/modifiers/default.md), ainsi que [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ou [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md), lors de la définition d'une propriété.  
  
-   **Héritage.** Si l'interface utilise [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md), vous pouvez spécifier une ou plusieurs interfaces de base.  Vous pouvez hériter de deux interfaces même si chacune définit un membre avec le même nom.  Dans ce cas, le code d'implémentation doit utiliser la qualification de nom pour spécifier le membre qu'il implémente.  
  
     Une interface ne peut pas hériter d'une autre interface dont le niveau d'accès est plus restrictif.  Par exemple, une interface `Public` ne peut pas hériter d'une interface `Friend`.  
  
     Une interface ne peut pas hériter d'une interface qui y est imbriquée.  
  
-   **Implémentation.** Lorsqu'une classe utilise l'instruction [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) pour implémenter cette interface, elle doit implémenter chaque membre défini dans l'interface.  En outre, chaque signature dans le code d'implémentation doit correspondre exactement à la signature associée définie dans cette interface.  Toutefois, le nom du membre dans le code d'implémentation ne doit pas correspondre au nom du membre défini dans l'interface.  
  
     Lorsqu'une classe implémente une procédure, elle ne peut pas désigner la procédure comme `Shared`.  
  
-   **Default, propriété.** Une interface peut spécifier au plus une propriété comme sa *propriété par défaut*, qui peut être référencée sans utiliser le nom de la propriété.  Vous spécifiez cette propriété en la déclarant avec le modificateur [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
     Cela signifie qu'une interface peut définir une propriété par défaut uniquement si elle n'en hérite d'aucune.  
  
## Comportement  
  
-   **Niveau d'accès.** Tous les membres d'interface possèdent implicitement un accès [Public](../../../visual-basic/language-reference/modifiers/public.md).  Vous ne pouvez pas utiliser un modificateur d'accès lors de la définition d'un membre.  Toutefois, une classe qui implémente l'interface peut déclarer un niveau d'accès pour chaque membre implémenté.  
  
     Si vous assignez une instance de classe à une variable, le niveau d'accès de ses membres varie selon que le type de données de la variable est l'interface sous\-jacente ou la classe d'implémentation.  L'exemple suivant illustre ce comportement.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Si vous accédez aux membres d'une classe par l'intermédiaire de `varAsInterface`, ils disposent tous d'un accès public.  Toutefois, si vous accédez aux membres par l'intermédiaire de `varAsClass`, la procédure `Sub` `doSomething` dispose d'un accès privé.  
  
-   **Portée.** Une interface est présente dans la portée dans l'ensemble de son espace de noms, sa classe, sa structure ou son module.  
  
     La portée de chaque membre d'interface est l'interface entière.  
  
-   **Durée de vie.** Une interface proprement dite n'a pas de durée de vie, ni ses membres.  Lorsqu'une classe implémente une interface et qu'un objet est créé en tant qu'instance de cette classe, l'objet a une durée de vie dans l'application dans laquelle il s'exécute.  Pour plus d'informations, consultez « Durée de vie » dans [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Interface` pour définir une interface nommée `thisInterface`, qui doit être implémentée avec une instruction `Property` et une instruction `Function`.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Notez que les instructions `Property` et `Function` n'introduisent pas de blocs se terminant par `End Property` et `End Function` dans l'interface.  L'interface définit uniquement les signatures de ses membres.  Les blocs `Property` et `Function` complets apparaissent dans une classe qui implémente `thisInterface`.  
  
## Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Variance dans les interfaces génériques](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)