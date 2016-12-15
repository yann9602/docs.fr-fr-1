---
title: "Of Clause (Visual Basic) | Microsoft Docs"
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
  - "Of"
  - "vb.Of"
  - "vb.of"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Of keyword"
  - "arguments [Visual Basic], data types"
  - "constraints, Visual Basic generic types"
  - "generic parameters"
  - "generics [Visual Basic], constraints"
  - "parameters, type"
  - "types [Visual Basic], generic"
  - "parameters, generic"
  - "type parameters"
  - "data type arguments"
ms.assetid: 0db8f65c-65af-4089-ab7f-6fcfecb60444
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Of Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Introduit une clause `Of` qui identifie un *paramètre de type* sur une classe, une structure, une interface, un délégué ou une procédure *générique*.  Pour plus d'informations sur les types génériques, consultez [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).  
  
## Utilisation du mot clé Of  
 L'exemple de code suivant utilise le mot clé `Of` pour définir le cadre d'une classe qui prend deux paramètres de type.  Il *contraint* le paramètre `keyType` par l'interface <xref:System.IComparable>, ce qui signifie que le code utilisateur doit fournir un argument de type qui implémente <xref:System.IComparable>.  Cela est nécessaire afin que la procédure `add` puisse appeler la méthode <xref:System.IComparable.CompareTo%2A?displayProperty=fullName>.  Pour plus d'informations sur les contraintes, consultez [Type List](../../../visual-basic/language-reference/statements/type-list.md).  
  
```  
Public Class Dictionary(Of entryType, keyType As IComparable)  
    Public Sub add(ByVal e As entryType, ByVal k As keyType)  
        Dim dk As keyType  
        If k.CompareTo(dk) = 0 Then  
        End If  
    End Sub  
    Public Function find(ByVal k As keyType) As entryType  
    End Function  
End Class  
```  
  
 Si vous terminez la définition de la classe précédente, vous pouvez construire diverses classes `dictionary` à partir de celle\-ci.  Les types que vous fournissez à `entryType` et `keyType` déterminent le type d'entrée que la classe contient et le type de clé qu'elle associe à chaque entrée.  À cause de la contrainte, vous devez fournir à `keyType` un type qui implémente <xref:System.IComparable>.  
  
 L'exemple de code suivant crée un objet qui contient des entrées `String` et associe une clé `Integer` à chacune de ces entrées.  `Integer` implémente <xref:System.IComparable> et par conséquent satisfait la contrainte sur `keyType`.  
  
```  
Dim d As New dictionary(Of String, Integer)  
```  
  
 Le mot clé `Of` peut être utilisé dans les contextes suivants :  
  
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Structure, instruction](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 <xref:System.IComparable>   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)