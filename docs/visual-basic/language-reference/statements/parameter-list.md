---
title: "Parameter List (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "parameters, Visual Basic"
  - "parameters, lists"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "arguments [Visual Basic], Visual Basic"
  - "procedures, parameter lists"
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Parameter List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie les paramètres qu'une procédure attend lorsqu'elle est appelée.  Les paramètres, lorsqu'il y en a plusieurs, sont séparés par des virgules.  La syntaxe pour un paramètre est la suivante.  
  
## Syntaxe  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## Composants  
 `attributelist`  
 Facultatif.  Liste des attributs qui s'appliquent à ce paramètre.  Vous devez placer le [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) entre des signes "inférieur à" et "supérieur à" \("`<`" et "`>`"\).  
  
 `Optional`  
 Facultatif.  Spécifie que ce paramètre n'est pas requis lorsque la procédure est appelée.  
  
 `ByVal`  
 Facultatif.  Spécifie que la procédure ne peut pas remplacer ou réassigner l'élément de variable sous\-jacent de l'argument correspondant dans le code appelant.  
  
 `ByRef`  
 Facultatif.  Spécifie que la procédure peut modifier l'élément de variable sous\-jacent dans le code appelant comme le ferait le code appelant lui\-même.  
  
 `ParamArray`  
 Facultatif.  Spécifie que le dernier paramètre dans la liste de paramètres est un tableau facultatif d'éléments du type de données spécifié.  Cela permet au code appelant de passer un nombre arbitraire d'arguments à la procédure.  
  
 `parametername`  
 Obligatoire.  Nom de la variable locale représentant le paramètre.  
  
 `parametertype`  
 Requis si `Option Strict` a la valeur `On`.  Type de données de la variable locale représentant le paramètre.  
  
 `defaultvalue`  
 Requis pour les paramètres `Optional`.  Toute constante ou expression constante qui prend la valeur du type de données du paramètre.  Si le type est `Object` ou bien une classe, une interface, un tableau ou une structure, la valeur par défaut ne peut être que `Nothing`.  
  
## Notes  
 Les paramètres sont placés entre parenthèses et sont séparés par des virgules.  Un paramètre peut être déclaré avec n'importe quel type de données.  Si vous ne spécifiez pas `parametertype`, la valeur prise par défaut est `Object`.  
  
 Lorsque le code appelant appelle la procédure, il passe un *argument* à chaque paramètre requis.  Pour plus d'informations, consultez [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).  
  
 L'argument que le code appelant passe à chaque paramètre est un pointeur vers un élément sous\-jacent dans le code appelant.  Si cet élément est *non variable* \(une constante, un littéral, une énumération ou une expression\), aucun code ne pourra le modifier.  S'il s'agit d'un élément *variable* \(une variable, un champ, une propriété, un élément de tableau ou un élément de structure déclaré\), le code appelant peut le modifier.  Pour plus d'informations, consultez [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).  
  
 Si un élément variable est passé `ByRef`, la procédure peut également le modifier.  Pour plus d'informations, consultez [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## Règles  
  
-   **Parenthèses.** Si vous spécifiez une liste de paramètres, vous devez la placer entre parenthèses.  S'il n'y a aucun paramètre, vous pouvez tout de même utiliser des parenthèses entourant une liste vide.  Cela permet d'améliorer la lisibilité de votre code en clarifiant que l'élément est une procédure.  
  
-   **Paramètres facultatifs.** Si vous utilisez le modificateur `Optional` sur un paramètre, tous les paramètres suivants dans la liste doivent également être facultatifs et être déclarés à l'aide du modificateur `Optional` .  
  
     Chaque déclaration de paramètre facultative doit fournir la clause `defaultvalue`.  
  
     Pour plus d'informations, consultez [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).  
  
-   **Tableaux de paramètres.** Vous devez spécifier `ByVal` pour un paramètre `ParamArray`.  
  
     Vous ne pouvez pas utiliser à la fois `Optional` et `ParamArray` dans la même liste de paramètres.  
  
     Pour plus d'informations, consultez [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
-   **Mécanisme de passage.** Le mécanisme par défaut pour chaque argument est `ByVal`, ce qui signifie que la procédure ne peut pas modifier l'élément de variable sous\-jacent.  Toutefois, si l'élément est un type référence, la procédure peut modifier le contenu ou les membres de l'objet sous\-jacent, bien qu'il ne puisse pas remplacer ou réassigner l'objet lui\-même.  
  
-   **Noms de paramètres.** Si le type de données du paramètre est un tableau, insérez des parenthèses immédiatement après `parametername`.  Pour plus d'informations sur les noms de paramètres, consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Exemple  
 L'exemple suivant indique une procédure `Function` qui définit deux paramètres.  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)