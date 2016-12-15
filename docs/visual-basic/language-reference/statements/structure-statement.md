---
title: "Structure Statement | Microsoft Docs"
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
  - "vb.Structure"
  - "Structure"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "user-defined types, Structure statement"
  - "compound data types"
  - "Structure keyword"
  - "Structure statement"
  - "UDT (user-defined types)"
  - "types [Visual Basic], user-defined"
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare le nom d'une structure et introduit la définition des variables, propriétés, événements et procédures contenus dans la structure.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`attributelist`|Optionnel.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Optionnel.  Il peut s'agir de l'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Optionnel.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Optionnel.  Indique une définition partielle de la structure.  Consultez [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Requis.  Nom de cette structure.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Optionnel.  Indique qu'il s'agit d'une structure générique.|  
|`typelist`|Requis si vous utilisez le mot clé [Of](../../../visual-basic/language-reference/statements/of-clause.md).  Liste de paramètres de type pour cette structure.  Consultez [Liste de types](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Optionnel.  Indique que cette structure implémente les membres d'une ou plusieurs interfaces.  Consultez [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Requis si vous utilisez l'instruction `Implements`.  Noms des interfaces que cette structure implémente.|  
|`datamemberdeclarations`|Requis.  Zéro ou plus instructions `Const`, `Dim`, `Enum` ou `Event` qui déclarent des *données membres* de la structure.|  
|`methodmemberdeclarations`|Optionnel.  Zéro ou plusieurs déclarations des procédures `Function`, `Operator`, `Property` ou `Sub` utilisées comme *membres de méthode* de la structure.|  
|`End Structure`|Requis.  Met fin à la définition `Structure`.|  
  
## Notes  
 L'instruction `Structure` définit un type valeur composite que vous pouvez personnaliser.  Une *structure* est une généralisation du type défini par l'utilisateur \(UDT, User\-Defined Type\) des précédentes versions de Visual Basic.  Pour plus d'informations, consultez [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Les structures prennent en charge un grand nombre de mêmes fonctionnalités comme classes.  Par exemple, les structures peuvent avoir des propriétés et des procédures, implémenter des interfaces et posséder des constructeurs paramétrables.  Toutefois, des différences importantes existent entre les structures et les classes dans des domaines tels que l'héritage, les déclarations et l'utilisation.  De même, les classes sont des types référence et les structures des types valeur.  Pour plus d'informations, consultez [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Vous pouvez utiliser `Structure` uniquement au niveau de l'espace de noms ou du module.  Cela signifie que le *contexte de déclaration* pour une structure doit être un fichier source, un espace de noms, une classe, une structure, un module ou une interface, et ne peut pas être une procédure ou un bloc.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Les structures disposent par défaut d'un accès [Friend](../../../visual-basic/language-reference/modifiers/friend.md).  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Règles  
  
-   **Imbrication.** Vous pouvez définir une structure dans une autre.  La structure externe est appelée *structure conteneur*, et la structure interne est appelée *structure imbriquée*.  Toutefois, vous ne pouvez pas accéder aux membres d'une structure imbriquée par l'intermédiaire de la structure conteneur.  Vous devez plutôt déclarer une variable du type de données de la structure imbriquée.  
  
-   **Déclaration de membre.** Vous devez déclarer chaque membre d'une structure.  Un membre d'une structure ne peut pas être [Protected](../../../visual-basic/language-reference/modifiers/protected.md) ou `Protected Friend`, car rien ne peut être hérité d'une structure  Toutefois, la structure proprement dite peut être `Protected` ou `Protected Friend`.  
  
     Vous pouvez déclarer ou non des variables non partagées ou des événements non partagés et non personnalisés dans une structure.  Vous ne pouvez pas posséder uniquement des constantes, propriétés et procédures, même si certaines sont non partagées.  
  
-   **Initialisation.** Vous ne pouvez pas initialiser la valeur d'une donnée membre non partagée d'une structure comme élément de sa déclaration.  Vous devez soit initialiser une donnée membre au moyen d'un constructeur paramétrable sur la structure, soit assigner une valeur au membre après avoir créé une instance de la structure.  
  
-   **Héritage.** Une structure ne peut pas hériter d'un type autre que <xref:System.ValueType>, d'où héritent toutes les structures.  En particulier, une structure ne peut pas hériter d'une autre.  
  
     Vous ne pouvez pas utiliser l'[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) dans une définition de structure, même pour spécifier <xref:System.ValueType>.  
  
-   **Implémentation.** Si la structure utilise l'[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md), vous devez implémenter chaque membre défini par chaque interface que vous spécifiez dans `interfacenames`.  
  
-   **Default, propriété.** Une structure peut spécifier au plus une propriété comme sa *propriété par défaut*, à l'aide du modificateur [Default](../../../visual-basic/language-reference/modifiers/default.md).  Pour plus d'informations, consultez [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## Comportement  
  
-   **Niveau d'accès.** Dans une structure, vous pouvez déclarer chaque membre avec son propre niveau d'accès.  Tous les membres de structure disposent par défaut d'un accès [Public](../../../visual-basic/language-reference/modifiers/public.md).  Notez que si la structure proprement dite a un niveau d'accès plus restreint, cela restreint automatiquement l'accès à ses membres, même si vous modifiez leurs niveaux d'accès à l'aide des modificateurs d'accès.  
  
-   **Portée.** Une structure est présente dans la portée dans l'ensemble de son espace de noms, sa classe, sa structure ou son module conteneur.  
  
     La portée d'un membre de structure est la structure entière.  
  
-   **Durée de vie.** Une structure elle\-même n'a pas de durée de vie.  En revanche, chaque instance de cette structure a une durée de vie indépendante de toutes les autres instances.  
  
     La durée de vie d'une instance commence à sa création par une clause [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) Elle se termine lorsque la durée de vie de la variable qui la contient prend fin.  
  
     Vous ne pouvez pas étendre la durée de vie d'une instance de structure.  Une approximation des fonctionnalités de structure statiques est fournie par un module.  Pour plus d'informations, consultez [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Les membres de structure ont des durées de vie qui varient selon leur méthode et leur lieu de déclaration.  Pour plus d'informations, consultez « Durée de vie » dans [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Qualification.** Le code à l'extérieur d'une structure doit qualifier le nom d'un membre avec le nom de cette structure.  
  
     Si le code à l'intérieur d'une structure imbriquée crée une référence non qualifiée à un élément de programmation, Visual Basic recherche d'abord l'élément dans la structure imbriquée, puis dans sa structure conteneur, et ainsi de suite jusqu'à l'élément conteneur le plus externe.  Pour plus d'informations, consultez [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Consommation de mémoire.** Comme dans le cas de tous les types de données composites, vous ne pouvez pas calculer en toute sécurité la consommation totale de la mémoire d'une structure en additionnant les allocations de stockage nominal de ses membres.  De plus, il est risqué de supposer que l'ordre de stockage dans la mémoire est identique à l'ordre de déclaration.  Si vous devez contrôler la disposition de stockage d'une structure, vous pouvez appliquer l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> à l'instruction `Structure`.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Structure` pour définir un ensemble de données apparentées pour un employé.  Il montre l'utilisation des membres `Public`, `Friend` et `Private` pour refléter la sensibilité des éléments de données.  Il montre également les membres d'une procédure, d'une propriété et d'un événement.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## Voir aussi  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)