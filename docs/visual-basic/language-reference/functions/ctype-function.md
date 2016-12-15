---
title: "Fonction CType (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "résultats de conversion d'expression"
  - "conversions de types de données explicites"
  - "CType (fonction)"
  - "conversions, expression"
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fonction CType (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Retourne le résultat d'une conversion explicite d'une expression en un type de données, objet, structure, classe ou interface spécifié.  
  
## Syntaxe  
  
```  
CType(expression, typename)  
```  
  
## Composants  
 `expression`  
 Toute expression valide.  Si la valeur de `expression` se trouve en dehors de la plage autorisée par `typename`, Visual Basic lève une exception.  
  
 `typename`  
 Toute expression valide au sein d'une clause `As` d'une instruction `Dim`, c'est\-à\-dire le nom de tout type de données, objet, structure, classe ou interface.  
  
## Notes  
  
> [!TIP]
>  Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :  
>   
>  -   Fonctions de conversion de type telles que `CByte`, `CDbl` et `CInt` qui exécutent une conversion vers un type de données spécifique.  Pour plus d'informations, consultez [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).  Ces opérateurs requièrent qu'un type hérite de l'autre type ou l'implémente.  Ils peuvent fournir des performances quelque peu meilleures que `CType` lors de la conversion vers ou depuis le type de données`Object`.  
  
 `CType` est compilé "inline", c'est\-à\-dire que le code de conversion fait partie du code qui évalue l'expression.  Dans certains cas, le code s'exécute plus vite car aucune procédure n'est appelée pour effectuer la conversion.  
  
 Si aucune conversion n'est définie de `expression` à `typename` \(par exemple de `Integer` à `Date`\), Visual Basic affiche un message d'erreur de compilation.  
  
 Si une conversion échoue au moment de l'exécution, l'exception appropriée est levée.  Si une conversion restrictive échoue, le résultat le plus courant est un <xref:System.OverflowException>.  Si la conversion n'est pas définie, une <xref:System.InvalidCastException> est levée.  Par exemple, cela peut arriver si `expression` est de type `Object` et que son type d'exécution n'a aucune conversion en `typename`.  
  
 Si le type de données de `expression` ou `typename` est une classe ou structure que vous avez définie, vous pouvez définir `CType` comme opérateur de conversion sur cette classe ou structure.  Ainsi, `CType` agit comme un *opérateur surchargé*.  En faisant ceci, vous pouvez contrôler le comportement des conversions effectuées vers et à partir de votre classe ou structure, y compris les exceptions pouvant être levées.  
  
## Surcharge  
 L'opérateur `CType` peut également être surchargé sur une classe ou structure définie en dehors de votre code.  Si votre code convertit vers et à partir d'une telle classe ou structure, assurez\-vous d'avoir bien compris le comportement de son opérateur `CType`.  Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## Conversion d'objets dynamiques  
 Les conversions de type des objets dynamiques sont exécutées par les conversions dynamiques définies par l'utilisateur qui utilisent les méthodes <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>.  Si vous utilisez des objets dynamiques, utilisez la méthode <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> pour convertir l'objet dynamique.  
  
## Exemple  
 L'exemple suivant utilise la fonction `CType` pour convertir une expression en type de données `Single` .  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Pour obtenir d'autres exemples, consultez [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## Voir aussi  
 <xref:System.OverflowException>   
 <xref:System.InvalidCastException>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Conversion de type dans le .NET Framework](../Topic/Type%20Conversion%20in%20the%20.NET%20Framework.md)