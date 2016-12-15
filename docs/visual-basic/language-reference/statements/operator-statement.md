---
title: "Operator Statement | Microsoft Docs"
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
  - "vb.operator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic]"
  - "procedures, operator"
  - "Narrowing keyword, conversion operators"
  - "Visual Basic code, operators"
  - "Widening keyword, conversion operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
  - "Operator statement"
  - "CType function, Operator statement"
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare le symbole d'opérateur, les opérandes et le code qui définissent une procédure d'opérateur sur une classe ou une structure.  
  
## Syntaxe  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## Composants  
 `attrlist`  
 Facultatif.  Consultez [Liste d'attributs](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `Public`  
 Obligatoire.  Indique que cette procédure d'opérateur dispose d'un accès [Public](../../../visual-basic/language-reference/modifiers/public.md).  
  
 `Overloads`  
 Facultatif.  Consultez [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).  
  
 `Shared`  
 Obligatoire.  Indique que cette procédure d'opérateur est une procédure [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 `Shadows`  
 Facultatif.  Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `Widening`  
 Obligatoire pour un opérateur de conversion sauf si vous spécifiez `Narrowing`.  Indique que cette procédure d'opérateur définit une conversion [Widening](../../../visual-basic/language-reference/modifiers/widening.md).  Consultez « Conversions étendues et restrictives » sur cette page d'aide.  
  
 `Narrowing`  
 Obligatoire pour un opérateur de conversion sauf si vous spécifiez `Widening`.  Indique que cette procédure d'opérateur définit une conversion [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md).  Consultez « Conversions étendues et restrictives » sur cette page d'aide.  
  
 `operatorsymbol`  
 Obligatoire.  Symbole ou identificateur de l'opérateur défini par cette procédure d'opérateur.  
  
 `operand1`  
 Obligatoire.  Nom et type de l'opérande unique d'un opérateur unaire \(y compris un opérateur de conversion\) ou opérande gauche d'un opérateur binaire.  
  
 `operand2`  
 Obligatoire pour les opérateurs binaires.  Nom et type de l'opérande droit d'un opérateur binaire.  
  
 `operand1` et `operand2` emploient la syntaxe et les paramètres suivants :  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|Élément|Description|  
|-------------|-----------------|  
|`ByVal`|Facultatif, mais le mécanisme de passage doit être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).|  
|`operandname`|Obligatoire.  Nom de la variable représentant cet opérande.  Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`operandtype`|Facultatif sauf si `Option Strict` a la valeur `On`.  Type de données de cet opérande.|  
  
 `type`  
 Facultatif sauf si `Option Strict` a la valeur `On`.  Type de données de la valeur retournée par la procédure d'opérateur.  
  
 `statements`  
 Facultatif.  Bloc d'instructions exécutées par la procédure d'opérateur.  
  
 `returnvalue`  
 Obligatoire.  Valeur retournée par la procédure d'opérateur au code appelant.  
  
 `End` `Operator`  
 Obligatoire.  Met fin à la définition de cette procédure d'opérateur.  
  
## Notes  
 Vous pouvez utiliser `Operator` uniquement dans une classe ou une structure.  Cela signifie que le *contexte de déclaration* pour un opérateur ne peut pas être un fichier source, un espace de noms, un module, une interface, une procédure ou un bloc.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Tous les opérateurs doivent être `Public Shared`.  Vous ne pouvez pas spécifier `ByRef`, `Optional` ou `ParamArray` pour l'un ou l'autre des opérandes.  
  
 Vous ne pouvez pas utiliser le symbole ou l'identificateur d'opérateur pour stocker une valeur de retour.  Vous devez utiliser l'instruction `Return`, et elle doit spécifier une valeur.  Il n'existe pas de limite au nombre d'instructions `Return` pouvant apparaître n'importe où dans la procédure.  
  
 Cette définition d'un opérateur est appelée *surcharge d'opérateur*, que vous utilisiez ou non le mot clé `Overloads`.  Le tableau suivant présente les opérateurs que vous pouvez définir.  
  
|Type|Opérateurs|  
|----------|----------------|  
|Unaire|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binaire|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversion \(unaire\)|`CType`|  
  
 Notez que l'opérateur `=` dans la liste binaire est l'opérateur de comparaison, et non l'opérateur d'assignation.  
  
 Lorsque vous définissez `CType`, vous devez spécifier `Widening` ou `Narrowing`.  
  
## Paires appariées  
 Vous devez définir certains opérateurs comme des paires appariées.  Si vous définissez l'un des opérateurs de cette paire, vous devez également définir l'autre.  Les paires appariées sont les suivantes :  
  
-   `=` et `<>`  
  
-   `>` et `<`  
  
-   `>=` et `<=`  
  
-   `IsTrue` et `IsFalse`  
  
## Restrictions de type de données  
 Chaque opérateur que vous définissez doit impliquer la classe ou la structure sur laquelle vous le définissez.  Cela signifie que la classe ou la structure doit être définie comme le type de données des éléments suivants :  
  
-   l'opérande d'un opérateur unaire ;  
  
-   au moins l'un des opérandes d'un opérateur binaire ;  
  
-   l'opérande ou le type de retour d'un opérateur de conversion.  
  
 Certains opérateurs présentent d'autres restrictions de type de données, à savoir :  
  
-   Si vous définissez les opérateurs `IsTrue` et `IsFalse`, tous deux doivent retourner le type `Boolean`.  
  
-   Si vous définissez les opérateurs `<<` et `>>`, tous deux doivent spécifier le type `Integer` pour `operandtype` de `operand2`.  
  
 Le type de retour ne doit pas correspondre au type de l'un ou l'autre des opérandes.  Par exemple, un opérateur de comparaison tel que `=` ou `<>` peut retourner `Boolean` même si aucun des opérandes n'a la valeur `Boolean`.  
  
## Opérateurs logiques et au niveau du bit  
 Les opérateurs `And`, `Or`, `Not` et `Xor` peuvent exécuter des opérations logiques ou au niveau du bit en Visual Basic.  Toutefois, si vous définissez l'un de ces opérateurs sur une classe ou une structure, vous pouvez définir uniquement son opération au niveau du bit.  
  
 Vous ne pouvez pas définir directement l'opérateur `AndAlso` avec une instruction `Operator`.  Toutefois, vous pouvez utiliser `AndAlso` si vous avez rempli les conditions suivantes :  
  
-   Vous avez défini `And` sur les mêmes types d'opérande que vous souhaitez utiliser pour `AndAlso`.  
  
-   Votre définition de `And` retourne le même type que la classe ou la structure sur laquelle vous l'avez défini.  
  
-   Vous avez défini l'opérateur `IsFalse` sur la classe ou la structure sur laquelle vous avez défini `And`.  
  
 De la même façon, vous pouvez utiliser `OrElse` si vous avez défini `Or` sur les mêmes opérandes, avec le type de retour de la classe ou la structure, et si vous avez défini `IsTrue` sur la classe ou la structure.  
  
## Conversions étendues et restrictives  
 Une *conversion étendue* réussit toujours au moment de l'exécution, alors qu'une *conversion restrictive* peut échouer au moment de l'exécution.  Pour plus d'informations, consultez [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Si vous déclarez une procédure de conversion comme étant `Widening`, votre code de procédure ne doit pas générer d'échecs.  Notamment :  
  
-   Elle doit toujours retourner une valeur valide de type `type`.  
  
-   Elle doit gérer toutes les exceptions possibles et les autres conditions d'erreur.  
  
-   Elle doit gérer les retours en cas d'erreur des procédures qu'elle appelle.  
  
 S'il existe un risque d'échec d'une procédure de conversion, ou si celle\-ci peut générer une exception non gérée, vous devez la déclarer comme étant `Narrowing`.  
  
## Exemple  
 L'exemple de code suivant utilise l'instruction `Operator` pour définir le plan d'une structure qui inclut des procédures d'opérateur pour les opérateurs `And`, `Or`, `IsFalse` et `IsTrue`.  `And` et `Or` acceptent chacun deux opérandes de type `abc` et retournent le type `abc`.  `IsFalse` et `IsTrue` acceptent chacun un opérande unique de type `abc` et retournent `Boolean`.  Ces définitions permettent au code appelant d'utiliser `And`, `AndAlso`, `Or` et `OrElse` avec des opérandes de type `abc`.  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## Voir aussi  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)   
 [How to: Use a Class that Defines Operators](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)