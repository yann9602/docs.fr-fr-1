---
title: "Proc&#233;dures de propri&#233;t&#233; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instruction Set, procédures de propriété"
  - "code Visual Basic, procédures"
  - "valeurs de retour, procédures de propriété"
  - "syntaxe, procédures de propriété"
  - "procédures, propriété"
  - "code Visual Basic, propriétés"
  - "procédures, appel"
  - "propriétés [Visual Basic], personnalisées"
  - "procédures de propriété"
  - "instruction Get, procédures de propriété"
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Proc&#233;dures de propri&#233;t&#233; (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une procédure de propriété est une série d'instructions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qui manipulent une propriété personnalisée d'un module, d'une classe ou d'une structure.  Les procédures de propriété sont également appelées *accesseurs de propriété*.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prend en charge les procédures de propriété suivantes :  
  
-   Une procédure `Get` retourne la valeur d'une propriété.  Elle est appelée lorsque vous accédez à la propriété dans une expression.  
  
-   Une procédure `Set` affecte une valeur à une propriété, y compris une référence d'objet.  Elle est appelée lorsque vous assignez une valeur à la propriété.  
  
 Les procédures de propriété sont généralement définies par paires, à l'aide des instructions `Get` et `Set`, mais vous pouvez définir chaque procédure à part selon que la propriété est en lecture seule \([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)\) ou en écriture seule \([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)\).  
  
 Vous pouvez omettre la procédure `Get` et `Set` lors de l'utilisation d'une propriété implémentée automatiquement.  Pour plus d'informations, consultez [Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).  
  
 Vous pouvez définir des propriétés dans les classes, les structures et les modules.  Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler de n'importe où dans votre application qui peut accéder au conteneur de la propriété.  
  
 Pour une comparaison des propriétés et des variables, consultez [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## Syntaxe de déclaration  
 Une propriété est définie comme un bloc de code délimité par les instructions [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) et `End Property`.  À l'intérieur de ce bloc, chaque procédure de propriété s'affiche sous forme de bloc interne encadré par une instruction de déclaration \(`Get` ou `Set`\) et l'instruction de fin `End` correspondante.  
  
 La syntaxe de déclaration d'une propriété et de ses procédures est la suivante :  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 Les `Modifiers` peuvent spécifier un niveau d'accès et des informations concernant la surcharge, la substitution, le partage et l'occultation, ainsi que spécifier si la propriété est en lecture seule ou en écriture seule.  `AccessLevel` dans la procédure d' `Get` ou d' `Set` peut être n'importe quel niveau qui est plus restrictif que le niveau d'accès spécifié pour la propriété elle\-même.  Pour plus d'informations, consultez [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).  
  
### Type de données  
 Le type de données et le niveau d'accès principal d'une propriété sont définis dans l'instruction `Property`, et non dans les procédures de propriété.  Une propriété peut avoir uniquement un type de données.  Par exemple, vous ne pouvez pas définir une propriété pour stocker une valeur `Decimal` et récupérer une valeur `Double`.  
  
### Niveau d'accès  
 Toutefois, vous pouvez définir un niveau d'accès principal pour une propriété et restreindre encore plus le niveau d'accès dans l'une de ses procédures de propriété.  Par exemple, vous pouvez définir une propriété `Public` puis définir une procédure `Private Set` La procédure `Get` reste `Public`.  Vous pouvez modifier le niveau d'accès dans une seule des procédures d'une propriété et vous pouvez uniquement le rendre plus restrictif que le niveau d'accès principal.  Pour plus d'informations, consultez [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md).  
  
## Déclaration de paramètre  
 Vous déclarez chaque paramètre de la même façon que pour [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md), à la différence que le mécanisme de passage doit être `ByVal`.  
  
 La syntaxe de chaque paramètre dans la liste des paramètres est la suivante :  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.  La syntaxe de spécification d'une valeur par défaut est la suivante :  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## Valeur de la propriété  
 Dans une procédure `Get`, la valeur de retour est fournie à l'expression appelante en tant que valeur de la propriété.  
  
 Dans une procédure `Set`, la nouvelle valeur de propriété est transférée au paramètre de l'instruction `Set`.  Si vous déclarez explicitement un argument, vous devez le faire en utilisant le même type de données que la propriété.  Si vous ne déclarez pas d'argument, le compilateur utilise l'argument implicite `Value` pour représenter la nouvelle valeur à assigner à la propriété.  
  
## Syntaxe d'appel  
 Vous appelez une procédure de propriété implicitement en faisant la référence à la propriété.  Utilisez le nom de la propriété de la même façon que le nom d'une variable, sauf que vous devez fournir des valeurs pour tous les arguments non facultatifs et placer la liste des arguments entre parenthèses.  Si aucun argument n'est spécifié, vous pouvez ne pas mettre les parenthèses.  
  
 La syntaxe d'un appel implicite à une procédure `Set` est la suivante :  
  
 `propertyname[(argumentlist)] = expression`  
  
 La syntaxe d'un appel implicite à une procédure `Get` est la suivante :  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### Illustration de déclaration et d'appel  
 La propriété suivante stocke un nom complet comme deux noms constitutifs, le prénom et le nom.  Lorsque le code appelant lit  `fullName`, la procédure `Get` combine les deux noms constitutifs et retourne le nom complet.  Lorsque le code appelant assigne un nouveau nom complet, la procédure `Set` tente de le décomposer en deux noms constitutifs.  S'il ne trouve pas d'espace, il le stocke en tant que prénom.  
  
 [!code-vb[VbVbcnProcedures#8](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 L'exemple suivant montre des appels typiques aux procédures Property de `fullName`.  
  
 [!code-vb[VbVbcnProcedures#9](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)