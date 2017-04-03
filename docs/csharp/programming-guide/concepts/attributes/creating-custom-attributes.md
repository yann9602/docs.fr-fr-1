---
title: "Création d’attributs personnalisés (C#) | Microsoft Docs"
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
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b71bf8fe1f4d448bf373fcab4bccd89bca4672b8
ms.lasthandoff: 03/13/2017

---
# <a name="creating-custom-attributes-c"></a>Création d’attributs personnalisés (C#)
Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs. Cette classe dérive directement ou indirectement d’<xref:System.Attribute>, ce qui permet d’identifier rapidement et facilement des définitions d’attributs dans des métadonnées. Supposons que vous souhaitiez baliser des types avec le nom du programmeur qui les a écrits. Vous pouvez définir une classe d’attributs `Author` personnalisés :  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Le nom de la classe est le nom de l’attribut, `Author`. Étant dérivée de `System.Attribute`, il s’agit donc d’une classe d’attributs personnalisés. Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé. Dans cet exemple, `name` est un paramètre positionnel. Les propriétés ou champs de type public accessibles en lecture/écriture sont des paramètres nommés. Dans le cas présent, `version` est le seul paramètre nommé. Notez l’utilisation de l’attribut `AttributeUsage` pour rendre l’attribut `Author` valide uniquement sur les déclarations de classe et de `struct`.  
  
 Vous pouvez utiliser ce nouvel attribut de la manière suivante :  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` a un paramètre nommé, `AllowMultiple`, qui permet de déclarer un attribut personnalisé comme étant à usage unique ou multiple. Dans l’exemple de code suivant, un attribut à usage multiple est créé.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  Si votre classe d’attributs contient une propriété, celle-ci doit être en lecture/écriture.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection>   
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Écriture des attributs personnalisés](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc)   
 [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Attributs (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)   
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
