---
title: "Comment : créer une Union C-C++ à l’aide d’attributs (Visual Basic) | Documents Microsoft"
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
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ff1686328630b233b25839c79d0009d48aab5ab
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Comment : créer une Union C/C++ à l’aide d’attributs (Visual Basic)
À l’aide d’attributs, vous pouvez personnaliser la disposition des structures en mémoire. Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide de la `StructLayout(LayoutKind.Explicit)` et `FieldOffset` les attributs.  
  
## <a name="example"></a>Exemple  
 Dans ce segment de code, tous les champs de `TestUnion` démarrer au même emplacement en mémoire.  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## <a name="example"></a>Exemple  
 Voici un autre exemple où champs commencent à différentes définie explicitement les emplacements.  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 Les champs de deux entiers, `i1` et `i2`, partagent les mêmes emplacements de mémoire et `lg`. Ce type de contrôle sur la disposition d’une structure est utile lorsque vous utilisez l’appel de plate-forme.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)   
 [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
