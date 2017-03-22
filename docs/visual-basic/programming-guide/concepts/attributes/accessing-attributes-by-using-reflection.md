---
title: "Accéder à des attributs à l’aide de la réflexion (Visual Basic) | Documents Microsoft"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
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
ms.openlocfilehash: 4763eccc5d1a6bdf3e89c1c4d825d5ff5c6caa3e
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a>Accéder à des attributs à l’aide de la réflexion (Visual Basic)
Le fait que vous pouvez définir des attributs personnalisés et les placer dans votre code source serait peu d’intérêt la possibilité de récupérer ces informations et en agissant sur elle. En utilisant la réflexion, vous pouvez récupérer les informations qui a été définies avec des attributs personnalisés. La méthode clé est `GetCustomAttributes`, qui retourne un tableau d’objets qui sont les équivalents de l’exécution des attributs du code source. Cette méthode a plusieurs versions surchargées. Pour plus d’informations, consultez <xref:System.Attribute>.</xref:System.Attribute>  
  
 Une spécification d’attribut tels que :  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 est semblable à ceci :  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 Toutefois, le code n’est pas exécuté jusqu'à ce que `SampleClass` est interrogée sur les attributs. Appel de `GetCustomAttributes` sur `SampleClass` entraîne une `Author` objet et l’initialisation comme illustré ci-dessus. Si la classe a d’autres attributs, les autres objets d’attribut sont construits de la même façon. `GetCustomAttributes`Renvoie la `Author` objet et autres objets d’attribut dans un tableau. Vous pouvez ensuite itérer sur ce tableau, déterminer les attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations à partir des objets des attributs.  
  
## <a name="example"></a>Exemple  
 Voici un exemple complet. Un attribut personnalisé est défini, appliqué à plusieurs entités et récupéré par réflexion.  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)   
 [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
