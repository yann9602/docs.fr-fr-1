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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c91f2686a03d2590e1aaf166d27c49744bb13c9b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="6ad71-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ad71-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="6ad71-103">Détermine comment une classe d’attributs personnalisés peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="6ad71-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="6ad71-104">`AttributeUsage`est un attribut qui peut être appliqué à des définitions d’attribut personnalisé pour contrôler comment le nouvel attribut peut être appliqué.</span><span class="sxs-lookup"><span data-stu-id="6ad71-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="6ad71-105">Les paramètres par défaut ressembler à ceci lorsque appliqués de manière explicite :</span><span class="sxs-lookup"><span data-stu-id="6ad71-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="6ad71-106">Dans cet exemple, la `NewAttribute` classe peut être appliqué à toute entité de l’attribut code, mais peut être appliqué qu’une seule fois à chaque entité.</span><span class="sxs-lookup"><span data-stu-id="6ad71-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="6ad71-107">Elle est héritée par les classes dérivées lorsqu’il est appliqué à une classe de base.</span><span class="sxs-lookup"><span data-stu-id="6ad71-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="6ad71-108">Le `AllowMultiple` et `Inherited` les arguments sont facultatifs, donc ce code a le même effet :</span><span class="sxs-lookup"><span data-stu-id="6ad71-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="6ad71-109">La première `AttributeUsage` l’argument doit être un ou plusieurs éléments de la <xref:System.AttributeTargets>énumération.</xref:System.AttributeTargets></span><span class="sxs-lookup"><span data-stu-id="6ad71-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="6ad71-110">Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :</span><span class="sxs-lookup"><span data-stu-id="6ad71-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="6ad71-111">Si le `AllowMultiple` argument est défini sur `true`, puis l’attribut qui en résulte peut être appliqué plusieurs fois à une seule entité, comme suit :</span><span class="sxs-lookup"><span data-stu-id="6ad71-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="6ad71-112">Dans ce cas `MultiUseAttr` peut être appliqué à plusieurs reprises car `AllowMultiple` est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="6ad71-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="6ad71-113">Les deux formats indiqués pour appliquer plusieurs attributs sont valides.</span><span class="sxs-lookup"><span data-stu-id="6ad71-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="6ad71-114">Si `Inherited` est défini sur `false`, puis l’attribut n’est pas hérité par les classes dérivées d’une classe qui est attribuée.</span><span class="sxs-lookup"><span data-stu-id="6ad71-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="6ad71-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6ad71-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="6ad71-116">Dans ce cas `Attr1` n’est pas appliquée à `DClass` via l’héritage.</span><span class="sxs-lookup"><span data-stu-id="6ad71-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ad71-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="6ad71-117">Remarks</span></span>  
 <span data-ttu-id="6ad71-118">Le `AttributeUsage` attribut est un attribut à usage unique ne peut pas être appliqué plusieurs fois à la même classe.</span><span class="sxs-lookup"><span data-stu-id="6ad71-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="6ad71-119">`AttributeUsage`est un alias pour <xref:System.AttributeUsageAttribute>.</xref:System.AttributeUsageAttribute></span><span class="sxs-lookup"><span data-stu-id="6ad71-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="6ad71-120">Pour plus d’informations, consultez [l’accès à des attributs en utilisant la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="6ad71-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ad71-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-121">Example</span></span>  
 <span data-ttu-id="6ad71-122">L’exemple suivant illustre l’effet de la `Inherited` et `AllowMultiple` arguments de le `AttributeUsage` attribut et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="6ad71-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="6ad71-123">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6ad71-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ad71-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ad71-124">See Also</span></span>  
 <span data-ttu-id="6ad71-125"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="6ad71-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="6ad71-126"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="6ad71-126"><xref:System.Reflection></span></span>   
<span data-ttu-id="6ad71-127"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ad71-127"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="6ad71-128"> [Attributs](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="6ad71-128"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="6ad71-129"> [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="6ad71-129"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="6ad71-130"> [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="6ad71-130"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="6ad71-131"> [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="6ad71-131"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="6ad71-132"> [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="6ad71-132"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
