---
title: AttributeUsage (Visual Basic) | Documents Microsoft
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
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf56f40033f9d1547d63fccd25e3c0561bb62cb1
ms.lasthandoff: 03/13/2017

---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Détermine comment une classe d’attributs personnalisés peut être utilisée. `AttributeUsage`est un attribut qui peut être appliqué à des définitions d’attribut personnalisé pour contrôler comment le nouvel attribut peut être appliqué. Les paramètres par défaut ressembler à ceci lorsque appliqués de manière explicite :  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Dans cet exemple, la `NewAttribute` classe peut être appliqué à toute entité de l’attribut code, mais peut être appliqué qu’une seule fois à chaque entité. Elle est héritée par les classes dérivées lorsqu’il est appliqué à une classe de base.  
  
 Le `AllowMultiple` et `Inherited` les arguments sont facultatifs, donc ce code a le même effet :  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 La première `AttributeUsage` l’argument doit être un ou plusieurs éléments de la <xref:System.AttributeTargets>énumération.</xref:System.AttributeTargets> Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Si le `AllowMultiple` argument est défini sur `true`, puis l’attribut qui en résulte peut être appliqué plusieurs fois à une seule entité, comme suit :  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 Dans ce cas `MultiUseAttr` peut être appliqué à plusieurs reprises car `AllowMultiple` est défini sur `true`. Les deux formats indiqués pour appliquer plusieurs attributs sont valides.  
  
 Si `Inherited` est défini sur `false`, puis l’attribut n’est pas hérité par les classes dérivées d’une classe qui est attribuée. Exemple :  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 Dans ce cas `Attr1` n’est pas appliquée à `DClass` via l’héritage.  
  
## <a name="remarks"></a>Remarques  
 Le `AttributeUsage` attribut est un attribut à usage unique ne peut pas être appliqué plusieurs fois à la même classe. `AttributeUsage`est un alias pour <xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute>  
  
 Pour plus d’informations, consultez [l’accès à des attributs en utilisant la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’effet de la `Inherited` et `AllowMultiple` arguments de le `AttributeUsage` attribut et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a>Résultat de l'exemple  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Attribute></xref:System.Attribute>   
 <xref:System.Reflection></xref:System.Reflection>   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)   
 [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
