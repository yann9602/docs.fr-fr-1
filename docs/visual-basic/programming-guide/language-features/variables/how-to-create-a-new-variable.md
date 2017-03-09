---
title: "How to: Create a New Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Dim statement"
  - "variables [Visual Basic], creating"
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# How to: Create a New Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Créez une variable à l'aide d'un [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### Pour créer une variable  
  
1.  Déclarez la variable dans une instruction `Dim`.  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  Insérez les spécifications pour les caractéristiques de la variable, telles que [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).  Pour plus d'informations, consultez [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Vous n'avez pas besoin du mot clé `Dim` si vous utilisez d'autres mots clés dans la déclaration.  
  
3.  Faites suivre les spécifications du nom de la variable qui doit se conformer aux règles et aux conventions [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Pour plus d'informations, consultez [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Faites suivre le nom de la clause [As](../../../../visual-basic/language-reference/statements/as-clause.md) pour spécifier le type de données de la variable.  
  
    ```  
    Public Static newCustomer As Customer   
    ```  
  
     Si vous ne spécifiez pas le type de données, la valeur par défaut est `Object`.  
  
5.  Faites suivre la clause `As` d'un signe égal \(`=`\) et faites suivre le signe égal de la valeur initiale de la variable.  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] assigne la valeur spécifiée à la variable à chaque exécution de l'instruction `Dim`.  Si vous ne spécifiez pas de valeur initiale, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] assigne la valeur initiale par défaut pour le type de données de la variable lorsqu'elle entre pour la première fois dans le code contenant l'instruction `Dim`.  
  
     Si la variable est un type référence, vous pouvez créer une instance de sa classe en insérant le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) dans la clause `As`.  Si vous n'utilisez pas `New`, la valeur initiale de la variable est [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## Voir aussi  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)