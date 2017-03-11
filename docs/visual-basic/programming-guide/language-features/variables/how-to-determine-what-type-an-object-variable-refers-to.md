---
title: "How to: Determine What Type an Object Variable Refers To (Visual Basic) | Microsoft Docs"
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
  - "TypeOf operator [Visual Basic], determining object variable type"
  - "variables [Visual Basic], object"
  - "object variables, determining type"
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Determine What Type an Object Variable Refers To (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une variable objet contient un pointeur vers des données stockées ailleurs.  Le type de ces données peut changer durant l'exécution.  À tout moment, vous pouvez utiliser la méthode <xref:System.Type.GetTypeCode%2A> pour déterminer le type d'exécution actuel ou le [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si le type d'exécution en cours est compatible avec un type spécifié.  
  
### Pour déterminer le type exact auquel une variable objet fait actuellement référence  
  
1.  Sur la variable objet, appelez la méthode <xref:System.Object.GetType%2A> pour récupérer un objet <xref:System.Type?displayProperty=fullName>.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Sur la classe <xref:System.Type?displayProperty=fullName>, appelez la méthode partagée <xref:System.Type.GetTypeCode%2A> pour récupérer la valeur d'énumération <xref:System.TypeCode> pour le type de l'objet.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Vous pouvez tester la valeur d'énumération <xref:System.TypeCode> contre tout membre d'énumération digne d'intérêt, tel que `Double`.  
  
### Pour déterminer si le type d'une variable objet est compatible avec un type spécifié  
  
-   Utilisez l'opérateur `TypeOf` avec l'[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) pour tester l'objet avec une expression `TypeOf`...`Is`.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     L'expression `TypeOf`...`Is` retourne `True` si le type de l'objet à l'exécution est compatible avec le type spécifié.  
  
     Le critère de compatibilité varie selon que le type spécifié est une classe, une structure ou une interface.  En général, les types sont compatibles si l'objet est du même type, hérite du type spécifié ou l'implémente.  Pour plus d'informations, consultez [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## Compilation du code  
 Notez que le type spécifié ne peut pas être une variable ni une expression.  Il doit s'agir du nom d'un type défini, tel qu'une classe, une structure ou une interface.  Cela inclut des types intrinsèques, tels que `Integer` et `String`.  
  
## Voir aussi  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.GetTypeCode%2A>   
 <xref:System.TypeCode>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)