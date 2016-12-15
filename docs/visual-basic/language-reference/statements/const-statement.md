---
title: "Const Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Const statement [Visual Basic]"
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Const Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare et définit une ou plusieurs constantes.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## Composants  
 `attributelist`  
 Facultatif.  Liste d'attributs s'appliquant à toutes les constantes déclarées dans cette instruction.  [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) est mis entre des signes "inférieur à" et "supérieur à" \("`<`" et "`>`"\).  
  
 `accessmodifier`  
 Facultatif.  Utilisez cet élément pour spécifier le code qui peut accéder à ces constantes.  Peut être [Public](../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend` ou [Private](../../../visual-basic/language-reference/modifiers/private.md).  
  
 `Shadows`  
 Facultatif.  Utilisez cet élément pour redéclarer et masquer un élément de programmation dans une classe de base.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Obligatoire.  Liste des constantes qui sont déclarées dans cette instruction.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Chaque `constant` emploie la syntaxe et les paramètres suivants :  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Élément|Description|  
|-------------|-----------------|  
|`constantname`|Obligatoire.  Nom de la constante.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Requis si `Option Strict` a la valeur `On`.  Type de données de la constante.|  
|`initializer`|Obligatoire.  Expression qui est évaluée au moment de la compilation et assignée à la constante.|  
  
## Notes  
 Si votre application contient une valeur qui ne change jamais, vous pouvez définir une constante nommée et l'utiliser à la place d'une valeur littérale.  Il est plus facile de se rappeler d'un nom que d'une valeur.  Vous pouvez définir la constante une seule fois et l'utiliser dans plusieurs zones de votre code.  Si vous devez redéfinir la valeur dans une version ultérieure, l'instruction `Const` est la seule zone que vous devez modifier.  
  
 Vous pouvez utiliser `Const` seulement au niveau du module ou de la procédure.  Cela signifie que le *contexte de déclaration* pour une variable doit être une classe, une structure, un module, une procédure ou un bloc et ne peut pas être un fichier source, un espace de noms ou une interface.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Les constantes locales \(dans une procédure\) disposent par défaut d'un accès public, et vous ne pouvez pas leur appliquer des modificateurs d'accès.  Les constantes membres de la classe et du module \(en dehors d'une procédure\) disposent par défaut d'un accès privé, et les constantes membres de la structure disposent par défaut d'un accès public.  Vous pouvez régler leurs niveaux d'accès avec les modificateurs d'accès.  
  
## Règles  
  
-   **Contexte de déclaration.** Une constante déclarée au niveau du module, à l'extérieur de toute procédure, est une *constante membre* ; elle est membre de la classe, de la structure ou du module qui la déclare.  
  
     Une constante déclarée au niveau de la procédure est une *constante locale* ; elle est locale à la procédure ou au bloc qui la déclare.  
  
-   **Attributs.** Vous ne pouvez appliquer des attributs qu'aux constantes membres, mais pas aux constantes locales.  Un attribut fournit des informations aux métadonnées de l'assembly, qui ne sont pas explicites pour le stockage temporaire tel que les constantes locales.  
  
-   **Modificateurs.** Par défaut, toutes les constantes sont `Shared`, `Static` et `ReadOnly`.  Vous ne pouvez pas utiliser l'un de ces mots clés lors de la déclaration d'une constante.  
  
     Au niveau de la procédure, vous ne pouvez pas utiliser `Shadows` ou les modificateurs d'accès pour déclarer des constantes locales.  
  
-   **Constantes multiples.** Vous pouvez déclarer plusieurs constantes dans la même instruction de déclaration, en spécifiant la partie `constantname` pour chacune d'elles.  Les constantes, lorsqu'il y en a plusieurs, sont séparées par des virgules.  
  
## Règles relatives aux types de données  
  
-   **Types de données.** L'instruction `Const` peut déclarer le type de données d'une variable.  Vous pouvez spécifier un type de données ou le nom d'une énumération.  
  
-   **Type par défaut.** Si vous ne spécifiez pas `datatype`, la constante prend le type de données de `initializer`.  Si vous spécifiez `datatype` et `initializer`, le type de données de `initializer` doit pouvoir être converti en `datatype`.  Si ni l'élément `datatype` ni l'élément `initializer` n'est présent, le type de données a la valeur `Object` par défaut.  
  
-   **Types divers.** Vous pouvez spécifier différents types de données pour les constantes en utilisant une clause `As` distincte pour chaque variable que vous déclarez.  Toutefois, vous ne pouvez pas déclarer plusieurs constantes comme étant du même type en utilisant une clause `As` commune.  
  
-   **Initialisation.** Vous devez initialiser la valeur de chaque constante dans `constantlist`.  Vous utilisez `initializer` pour fournir une expression à assigner à la constante.  L'expression peut être une combinaison de littéraux, d'autres constantes qui sont déjà définies et des membres de l'énumération qui sont déjà définis.  Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner ces éléments.  
  
     Vous ne pouvez pas utiliser de variables ni de fonctions dans `initializer`.  Toutefois, vous pouvez utiliser des mots clés de conversions, tels que `CByte` et `CShort`.  Vous pouvez également utiliser `AscW` si vous l'appelez avec une constante `String` ou un argument `Char`, car l'évaluation peut se produire au moment de la compilation.  
  
## Comportement  
  
-   **Portée.** Les constantes locales sont uniquement accessibles à partir de leur procédure ou bloc.  Les constantes membres sont accessibles à partir de n'importe quelle zone de leur classe, structure ou module.  
  
-   **Qualification.** Le code à l'extérieur d'une classe, d'une structure ou d'un module doit qualifier le nom d'une constante membre avec le nom de cette classe, de cette structure ou de ce module.  Le code à l'extérieur d'une procédure ou d'un bloc ne peut pas faire référence aux constantes locales de cette procédure ou de ce bloc.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Const` pour déclarer les constantes à utiliser à la place de valeurs littérales.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## Exemple  
 Si vous définissez une constante avec le type de données `Object`, le compilateur Visual Basic lui affecte le type de `initializer` au lieu de `Object`.  Dans l'exemple suivant, la constante `naturalLogBase` a le type d'exécution `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 L'exemple précédent utilise la méthode <xref:System.Type.ToString%2A> sur l'objet <xref:System.Type> retourné par [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), car <xref:System.Type> ne peut pas être converti en `String` à l'aide de `CStr`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Constants and Enumerations](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)