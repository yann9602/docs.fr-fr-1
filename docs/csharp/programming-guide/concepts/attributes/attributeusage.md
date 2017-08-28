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
# <a name="attributeusage-c"></a>AttributeUsage (C#)
Détermine de quelle manière une classe d’attributs personnalisés peut être utilisée. `AttributeUsage` est un attribut qui peut être appliqué à des définitions d’attributs personnalisés pour contrôler le mode d’application du nouvel attribut. Voici le code quand les paramètres par défaut sont appliqués de manière explicite :  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 Dans cet exemple, la classe `NewAttribute` peut être appliquée à toutes les entités de code acceptant un attribut, mais uniquement une fois par entité. Elle est héritée par les classes dérivées quand elle est appliquée à une classe de base.  
  
 Les arguments `AllowMultiple` et `Inherited` étant facultatifs, ce code produit le même résultat :  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 Le premier argument `AttributeUsage` doit correspondre à un ou plusieurs éléments de l’énumération <xref:System.AttributeTargets>. Plusieurs types de cibles peuvent être liés avec l’opérateur OR, comme suit :  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 Si l’argument `AllowMultiple` est défini sur `true`, l’attribut qui en résulte peut être appliqué plusieurs fois à une même entité, comme suit :  
  
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
  
 Dans ce cas, `MultiUseAttr` peut être appliqué à plusieurs reprises, car `AllowMultiple` est défini sur `true`. Les deux formats indiqués pour appliquer plusieurs attributs sont valides.  
  
 Si `Inherited` est défini sur `false`, l’attribut n’est pas hérité par les classes qui sont dérivées d’une classe avec attributs. Exemple :  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 Dans ce cas, `Attr1` n’est pas appliqué à `DClass` par héritage.  
  
## <a name="remarks"></a>Remarques  
 L’attribut `AttributeUsage` est un attribut à usage unique : il ne peut pas être appliqué plusieurs fois à la même classe. `AttributeUsage` est un alias pour <xref:System.AttributeUsageAttribute>.  
  
 Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’effet des arguments `Inherited` et `AllowMultiple` sur l’attribut `AttributeUsage`, et la manière dont les attributs personnalisés appliqués à une classe peuvent être énumérés.  
  
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
 <xref:System.Attribute>   
 <xref:System.Reflection>   
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)   
 [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Attributs](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

