---
title: "Création d’attributs personnalisés (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
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
ms.openlocfilehash: 1aa97a591fdbdfab931a8b5e4f70ec3c00762332
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-visual-basic"></a>Création d’attributs personnalisés (Visual Basic)
Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs, une classe qui dérive directement ou indirectement de <xref:System.Attribute>, qui permet d’identifier les définitions d’attributs dans les métadonnées rapide et facile.</xref:System.Attribute> Supposons que vous souhaitez les types de balise avec le nom du programmeur qui a écrit le type. Vous pouvez définir une personnalisée `Author` classe d’attributs :  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 Le nom de classe est le nom d’attribut, `Author`. Elle est dérivée de `System.Attribute`, il est donc une classe d’attributs personnalisés. Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé. Dans cet exemple, `name` est un paramètre positionnel. Les champs en lecture-écriture publics ou les propriétés sont des paramètres nommées. Dans ce cas, `version` est le seul paramètre nommé. Notez l’utilisation de la `AttributeUsage` attribut pour rendre le `Author` attribut valide uniquement sur la classe et `Structure` déclarations.  
  
 Vous pouvez utiliser ce nouvel attribut comme suit :  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 `AttributeUsage`a un paramètre nommé, `AllowMultiple`, avec lequel vous pouvez apporter un attribut personnalisé à usage unique ou multiple. Dans l’exemple de code suivant, un attribut à usages multiples est créé.  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  Si votre classe d’attributs contient une propriété, cette propriété doit être en lecture-écriture.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection></xref:System.Reflection>   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Écriture des attributs personnalisés](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
