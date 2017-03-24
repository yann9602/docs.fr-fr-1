---
title: Covariance et Contravariance (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b785e298c5ba38a8e3d8cc549b2dcf2df1ef6bd8
ms.lasthandoff: 03/13/2017

---
# <a name="covariance-and-contravariance-visual-basic"></a>Covariance et Contravariance (Visual Basic)
En Visual Basic, la covariance et contravariance activer la conversion de référence implicite pour les types tableau, types délégués et les arguments de type générique. La covariance conserve la compatibilité d’affectation et la contravariance l’inverse.  
  
 Le code suivant illustre la différence entre la compatibilité d’affectation, la covariance et la contravariance.  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 La covariance des tableaux permet la conversion implicite d’un tableau d’un type plus dérivé dans un tableau d’un type moins dérivé. Mais cette opération n’est pas de type sécurisé, comme illustré dans l’exemple de code suivant.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Covariance et contravariance prise en charge pour les groupes de méthode permet de faire correspondre les signatures de méthode aux types délégués. Cela permet d’attribuer aux délégués pas uniquement les méthodes qui ont la correspondance des signatures, mais également des méthodes qui retournent les que plus dérivées des types (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Pour plus d’informations, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [à l’aide de la Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 L’exemple de code suivant montre la covariance et contravariance prend en charge pour les groupes de méthode.  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 Dans .NET Framework 4 ou version ultérieure de Visual Basic prennent en charge la covariance et contravariance dans les délégués et interfaces génériques et permettent la conversion implicite de paramètres de type générique. Pour plus d’informations, consultez [Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) et [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 L’exemple de code suivant illustre la conversion de référence implicite pour les interfaces génériques.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Une interface générique ou un délégué est appelé *variante* si ses paramètres génériques sont déclarés covariants ou contravariant. Visual Basic vous permet de créer vos propres interfaces et délégués variants. Pour plus d’informations, consultez [création d’Interfaces génériques variantes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) et [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Décrit la covariance et la contravariance dans les interfaces génériques et fournit la liste des interfaces génériques de type variant dans le .NET Framework.|  
|[Création d’Interfaces génériques de type Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Montre comment créer des interfaces variantes personnalisées.|  
|[Utilisation de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Indique comment la prise en charge de la covariance et contravariance dans les <xref:System.Collections.Generic.IEnumerable%601>et <xref:System.IComparable%601>interfaces peuvent vous aider à réutiliser le code.</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601>|  
|[Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Décrit la covariance et contravariance dans les délégués génériques et non génériques et fournit une liste de délégués génériques variants dans le .NET Framework.|  
|[Utilisation de la Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Montre comment utiliser la prise en charge de la covariance et contravariance dans les délégués non génériques pour faire correspondre les signatures de méthode aux types délégués.|  
|[Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Indique comment la prise en charge de la covariance et contravariance dans les `Func` et `Action` délégués peuvent vous aider à réutiliser le code.|
