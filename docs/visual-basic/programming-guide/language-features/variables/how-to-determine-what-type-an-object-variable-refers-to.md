---
title: "Comment : déterminer le type désigné par une variable objet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5dd6785ecd48be3f0455de63b9e3f13a485ddbb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>Comment : déterminer le type désigné par une variable objet (Visual Basic)
Une variable objet contient un pointeur vers les données qui sont stockés ailleurs. Le type de données peut changer pendant l’exécution. À tout moment, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode pour déterminer le type d’exécution en cours, ou le [typeof, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si l’actuel type au moment de l’exécution est compatible avec un type spécifié.  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>Pour déterminer que le type exact auquel une variable objet actuellement fait référence à  
  
1.  Sur la variable objet, appelez le <xref:System.Object.GetType%2A> méthode pour récupérer un <xref:System.Type?displayProperty=nameWithType> objet.  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  Sur le <xref:System.Type?displayProperty=nameWithType> de classe, appelez la méthode partagée <xref:System.Type.GetTypeCode%2A> pour récupérer le <xref:System.TypeCode> valeur d’énumération pour le type d’objet.  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     Vous pouvez tester le <xref:System.TypeCode> contre tout membre d’énumération est dignes d’intérêt, comme valeur d’énumération `Double`.  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>Pour déterminer si un objet de type de variable est compatible avec un type spécifié  
  
-   Utilisez le `TypeOf` opérateur en combinaison avec la [est un opérateur](../../../../visual-basic/language-reference/operators/is-operator.md) pour tester l’objet avec un `TypeOf`... `Is` expression.  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     Le `TypeOf`... `Is` retourne `True` si l’objet du runtime type est compatible avec le type spécifié.  
  
     Le critère de compatibilité varie selon que le type spécifié est une classe, structure ou interface. En règle générale, les types sont compatibles si l’objet est du même type que, hérite ou implémente le type spécifié. Pour plus d’informations, consultez [typeof, opérateur](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Notez que le type spécifié ne peut pas être une variable ou une expression. Il doit être le nom d’un type défini, par exemple une classe, structure ou interface. Cela inclut des types intrinsèques, tels que `Integer` et `String`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Valeurs des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)
