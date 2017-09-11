---
title: AttributeUsage (C#)
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
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
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
ms.openlocfilehash: c008c1a696e93bc3b756a926a046aa5a6942bc10
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="attributeusage-c"></a><span data-ttu-id="2e9d8-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="2e9d8-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="2e9d8-103">Détermine de quelle manière une classe d’attributs personnalisés peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="2e9d8-104">`AttributeUsage` est un attribut qui peut être appliqué à des définitions d’attributs personnalisés pour contrôler le mode d’application du nouvel attribut.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="2e9d8-105">Voici le code quand les paramètres par défaut sont appliqués de manière explicite :</span><span class="sxs-lookup"><span data-stu-id="2e9d8-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="2e9d8-106">Dans cet exemple, la classe `NewAttribute` peut être appliquée à toutes les entités de code acceptant un attribut, mais uniquement une fois par entité.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="2e9d8-107">Elle est héritée par les classes dérivées quand elle est appliquée à une classe de base.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="2e9d8-108">Les arguments `AllowMultiple` et `Inherited` étant facultatifs, ce code produit le même résultat :</span><span class="sxs-lookup"><span data-stu-id="2e9d8-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="2e9d8-109">Le premier argument `AttributeUsage` doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="2e9d8-110">Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e9d8-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="2e9d8-111">Si l’argument `AllowMultiple` est défini sur `true`, l’attribut qui en résulte peut être appliqué plusieurs fois à une même entité, comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e9d8-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="2e9d8-112">Dans ce cas, `MultiUseAttr` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="2e9d8-113">Les deux formats indiqués pour appliquer plusieurs attributs sont valides.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="2e9d8-114">Si `Inherited` est défini sur `false`, l’attribut n’est pas hérité par les classes qui sont dérivées d’une classe avec attributs.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="2e9d8-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2e9d8-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="2e9d8-116">Dans ce cas, `Attr1` n’est pas appliqué à `DClass` par héritage.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9d8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="2e9d8-117">Remarks</span></span>  
 <span data-ttu-id="2e9d8-118">L’attribut `AttributeUsage` est un attribut à usage unique : il ne peut pas être appliqué plusieurs fois à la même classe.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="2e9d8-119">`AttributeUsage` est un alias pour <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="2e9d8-120">Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="2e9d8-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9d8-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="2e9d8-121">Example</span></span>  
 <span data-ttu-id="2e9d8-122">L’exemple suivant illustre l’effet des arguments `Inherited` et `AllowMultiple` sur l’attribut `AttributeUsage`, et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="2e9d8-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="2e9d8-123">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="2e9d8-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e9d8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e9d8-124">See Also</span></span>  
 <span data-ttu-id="2e9d8-125"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="2e9d8-125"><xref:System.Attribute></span></span>   
 <span data-ttu-id="2e9d8-126"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="2e9d8-126"><xref:System.Reflection></span></span>   
 <span data-ttu-id="2e9d8-127">[Guide de programmation C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2e9d8-127">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2e9d8-128">[Attributs](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="2e9d8-128">[Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
 <span data-ttu-id="2e9d8-129">[Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="2e9d8-129">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 <span data-ttu-id="2e9d8-130">[Attributs](../../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="2e9d8-130">[Attributes](../../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 <span data-ttu-id="2e9d8-131">[Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="2e9d8-131">[Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
 [<span data-ttu-id="2e9d8-132">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="2e9d8-132">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

