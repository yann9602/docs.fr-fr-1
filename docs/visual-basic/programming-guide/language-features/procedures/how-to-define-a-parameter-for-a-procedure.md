---
title: "How to: Define a Parameter for a Procedure (Visual Basic) | Microsoft Docs"
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
  - "procedure parameters, defining data types for"
  - "procedures, parameters"
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "procedure parameters, defining"
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Define a Parameter for a Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Un *paramètre* permet au code appelant de passer une valeur à la procédure lorsqu'il l'appelle.  Vous devez déclarer chaque paramètre d'une procédure de la même façon qu'une variable, en spécifiant son nom et le type de données.  Vous pouvez également spécifier le mécanisme de passage et indiquer si le paramètre est facultatif ou non.  
  
 Pour plus d'informations, consultez [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md).  
  
### Pour définir un paramètre de procédure  
  
1.  Dans la déclaration de procédure, ajoutez le nom de paramètre à la liste de paramètres de la procédure, en le séparant des autres paramètres par des virgules.  
  
2.  Décidez du type de données du paramètre.  
  
3.  Faites suivre le nom du paramètre d'une clause `As` qui spécifie le type de données.  
  
4.  Décidez du mécanisme de passage que vous souhaitez utiliser pour le paramètre.  Normalement vous passez un paramètre par valeur, sauf si vous souhaitez que la procédure soit capable de modifier sa valeur dans le code appelant.  
  
5.  Faites précéder le nom de paramètre de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour spécifier le mécanisme de passage.  Pour plus d'informations, consultez [Differences Between Passing an Argument By Value and By Reference](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Si le paramètre est facultatif, faites précéder le mécanisme de passage de [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) et faites suivre le type de données de paramètre d'un signe égal \(`=`\) et d'une valeur par défaut.  
  
     L'exemple suivant définit le plan d'une procédure `Sub` avec trois paramètres.  Les deux premiers sont requis et le troisième est facultatif.  Les déclarations de paramètre sont séparées dans la liste de paramètres par des virgules.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     Les premiers paramètres acceptent un objet  `customer`  et `updateCustomer` peut directement mettre à jour la variable passée à `c` parce que l'argument est passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  La procédure ne peut pas modifier les valeurs des deux derniers arguments parce qu'ils sont passés [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Si le code appelant ne fournit pas de valeur pour le paramètre  `level` , [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] le définit à la valeur 0 par défaut.  
  
     Si le commutateur de vérification de type \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) a la valeur `Off`, la clause `As` est facultative lorsque vous définissez un paramètre.  Toutefois, si un paramètre utilise une clause `As`, ils doivent tous l'utiliser.  Si le commutateur de vérification de type est `On`, la clause `As` est requise pour chaque définition de paramètre.  
  
     Le processus qui consiste à spécifier des types de données pour tous les éléments de programmation est appelé *typage fort*.  Lorsque vous définissez `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] met en vigueur le typage fort.  Cela est recommandé fortement, pour les raisons suivantes :  
  
    -   Cela permet la prise en charge de IntelliSens pour vos variables et vos paramètres.  Cela vous permet de voir leurs propriétés et leurs autres membres à mesure que vous tapez le code.  
  
    -   Il permet au compilateur d'effectuer la vérification des types.  Il permet d'intercepter les instructions susceptibles de provoquer, au moment de l'exécution, des erreurs telles qu'un dépassement de capacité.  Il intercepte également les appels aux méthodes dans des objets qui ne les prennent pas en charge.  
  
    -   Il permet ainsi à votre code de s'exécuter plus rapidement.  Une raison pour ceci est que si vous ne spécifiez pas de type de données pour un élément de programmation, le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] lui assigne le type `Object`.  Votre code compilé peut avoir à passer de la conversion d'`Object` à celle d'autres types de données ce qui réduit la performance.  
  
## Voir aussi  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function, procédures](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [How to: Pass Arguments to a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passing Arguments by Value and by Reference](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Recursive Procedures](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programmation orientée objet dans Visual Basic](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)