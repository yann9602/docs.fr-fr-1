---
title: "Accès à des attributs à l’aide de la réflexion (C#)"
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
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
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
ms.openlocfilehash: 36724c7b6a2a786aff837db5bcf2ad2ccfa39205
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="cb669-102">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="cb669-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="cb669-103">La définition d’attributs personnalisés et leur ajout à votre code source présentent peu d’intérêt si vous ne pouvez pas ensuite récupérer et manipuler ces informations.</span><span class="sxs-lookup"><span data-stu-id="cb669-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="cb669-104">La réflexion vous permet de récupérer les informations qui ont été définies à l’aide d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="cb669-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="cb669-105">La méthode clé est `GetCustomAttributes`. Elle retourne un tableau d’objets qui sont les équivalents des attributs du code source au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="cb669-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="cb669-106">Cette méthode a plusieurs versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="cb669-106">This method has several overloaded versions.</span></span> <span data-ttu-id="cb669-107">Pour plus d'informations, consultez <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="cb669-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="cb669-108">Par exemple, cette spécification d’attribut :</span><span class="sxs-lookup"><span data-stu-id="cb669-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="cb669-109">est semblable à celle-ci d’un point de vue conceptuel :</span><span class="sxs-lookup"><span data-stu-id="cb669-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="cb669-110">Toutefois, le code n’est pas exécuté tant qu’une requête n’est pas effectuée sur `SampleClass` pour obtenir les attributs.</span><span class="sxs-lookup"><span data-stu-id="cb669-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="cb669-111">L’appel de `GetCustomAttributes` sur `SampleClass` entraîne la construction et l’initialisation d’un objet `Author` comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="cb669-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="cb669-112">Si la classe a d’autres attributs, les autres objets attribut sont construits de la même façon.</span><span class="sxs-lookup"><span data-stu-id="cb669-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="cb669-113">`GetCustomAttributes` retourne ensuite l’objet `Author` et les autres objets attribut dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="cb669-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="cb669-114">Vous pouvez ensuite itérer sur ce tableau, déterminer quels attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations des objets attribut.</span><span class="sxs-lookup"><span data-stu-id="cb669-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb669-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb669-115">Example</span></span>  
 <span data-ttu-id="cb669-116">Voici un exemple complet.</span><span class="sxs-lookup"><span data-stu-id="cb669-116">Here is a complete example.</span></span> <span data-ttu-id="cb669-117">Un attribut personnalisé est défini, appliqué à plusieurs entités, puis récupéré par réflexion.</span><span class="sxs-lookup"><span data-stu-id="cb669-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb669-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb669-118">See Also</span></span>  
 <span data-ttu-id="cb669-119"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="cb669-119"><xref:System.Reflection></span></span>   
 <span data-ttu-id="cb669-120"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="cb669-120"><xref:System.Attribute></span></span>   
 <span data-ttu-id="cb669-121">[Guide de programmation C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cb669-121">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cb669-122">[Récupération des informations stockées dans les attributs](../../../../standard/attributes/retrieving-information-stored-in-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="cb669-122">[Retrieving Information Stored in Attributes](../../../../standard/attributes/retrieving-information-stored-in-attributes.md) </span></span>  
 <span data-ttu-id="cb669-123">[Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="cb669-123">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 <span data-ttu-id="cb669-124">[Attributs (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="cb669-124">[Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 [<span data-ttu-id="cb669-125">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="cb669-125">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)

