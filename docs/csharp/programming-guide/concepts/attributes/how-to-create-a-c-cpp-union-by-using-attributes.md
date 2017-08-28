---
title: "Guide pratique pour créer une union C-C++ à l’aide d’attributs (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4532829080d994cf4cec92d64a12e3bf1890dc6a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Guide pratique pour créer une union C-C++ à l’aide d’attributs (C#)
Vous pouvez personnaliser la disposition des structs en mémoire à l’aide d’attributs. Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide des attributs `StructLayout(LayoutKind.Explicit)` et `FieldOffset`.  
  
## <a name="example"></a>Exemple  
 Dans ce segment de code, tous les champs de `TestUnion` débutent au même emplacement en mémoire.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a>Exemple  
 Voici un autre exemple où les champs débutent à différents emplacements définis explicitement.  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 Les deux champs entiers, `i1` et `i2`, partagent leurs emplacements de mémoire avec `lg`. Ce type de contrôle sur la disposition des structs est utile quand vous utilisez des appels de code non managé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)   
 [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Attributs (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

