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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 195dc0c64cb01e38ede0b7c34c30ca7912aea685
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="fcd99-102">Comment : créer une Union C/C++ à l’aide d’attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcd99-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="fcd99-103">À l’aide d’attributs, vous pouvez personnaliser la disposition des structures en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcd99-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="fcd99-104">Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide de la `StructLayout(LayoutKind.Explicit)` et `FieldOffset` les attributs.</span><span class="sxs-lookup"><span data-stu-id="fcd99-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcd99-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="fcd99-105">Example</span></span>  
 <span data-ttu-id="fcd99-106">Dans ce segment de code, tous les champs de `TestUnion` démarrer au même emplacement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fcd99-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="fcd99-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="fcd99-107">Example</span></span>  
 <span data-ttu-id="fcd99-108">Voici un autre exemple où champs commencent à différentes définie explicitement les emplacements.</span><span class="sxs-lookup"><span data-stu-id="fcd99-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="fcd99-109">Les champs de deux entiers, `i1` et `i2`, partagent les mêmes emplacements de mémoire et `lg`.</span><span class="sxs-lookup"><span data-stu-id="fcd99-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="fcd99-110">Ce type de contrôle sur la disposition d’une structure est utile lorsque vous utilisez l’appel de plate-forme.</span><span class="sxs-lookup"><span data-stu-id="fcd99-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd99-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcd99-111">See Also</span></span>  
 <span data-ttu-id="fcd99-112"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="fcd99-112"><xref:System.Reflection></span></span>   
 <span data-ttu-id="fcd99-113"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="fcd99-113"><xref:System.Attribute></span></span>   
<span data-ttu-id="fcd99-114"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fcd99-114"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="fcd99-115"> [Attributs](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="fcd99-115"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="fcd99-116"> [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="fcd99-116"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="fcd99-117"> [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="fcd99-117"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="fcd99-118"> [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="fcd99-118"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="fcd99-119"> [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="fcd99-119"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
