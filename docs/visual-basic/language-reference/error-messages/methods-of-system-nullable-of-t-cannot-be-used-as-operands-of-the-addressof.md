---
title: "Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator | Microsoft Docs"
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
  - "vbc32126"
  - "bc32126"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32126"
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methods of &#39;System.Nullable(Of T)&#39; cannot be used as operands of the &#39;AddressOf&#39; operator
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction utilise l'opérateur `AddressOf` avec un opérande qui représente une procédure de la structure <xref:System.Nullable%601>.  
  
 **ID d'erreur :** BC32126  
  
### Pour corriger cette erreur  
  
-   Remplacez le nom de la procédure dans la clause `AddressOf` par un opérande qui n'est pas un membre de <xref:System.Nullable%601>.  
  
-   Écrivez une classe qui encapsule la méthode de <xref:System.Nullable%601> que vous souhaitez utiliser.  Dans l'exemple suivant, la classe `NullableWrapper` définit une nouvelle méthode nommée `GetValueOrDefault`.  Étant donné que cette nouvelle méthode n'est pas un membre de <xref:System.Nullable%601>, elle peut s'appliquer à `nullInstance`, une instance d'un type Nullable, pour former un argument pour `AddressOf`.  
  
    ```vb#  
    Module Module1  
  
        Delegate Function Deleg() As Integer  
  
        Sub Main()  
            Dim nullInstance As New Nullable(Of Integer)(1)  
  
            Dim del As Deleg  
  
            ' GetValueOrDefault is a method of the Nullable generic  
            ' type. It cannot be used as an operand of AddressOf.  
            ' del = AddressOf nullInstance.GetValueOrDefault  
  
            ' The following line uses the GetValueOrDefault method  
            ' defined in the NullableWrapper class.  
            del = AddressOf (New NullableWrapper(  
                Of Integer)(nullInstance)).GetValueOrDefault  
  
            Console.WriteLine(del.Invoke())  
        End Sub  
  
        Class NullableWrapper(Of T As Structure)  
            Private m_Value As Nullable(Of T)  
  
            Sub New(ByVal Value As Nullable(Of T))  
                m_Value = Value  
            End Sub  
  
            Public Function GetValueOrDefault() As T  
                Return m_Value.Value  
            End Function  
        End Class  
    End Module  
    ```  
  
## Voir aussi  
 <xref:System.Nullable%601>   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)