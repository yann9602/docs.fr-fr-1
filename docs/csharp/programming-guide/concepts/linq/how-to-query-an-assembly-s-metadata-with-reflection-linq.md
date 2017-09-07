---
title: "Guide pratique pour interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)"
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
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 181d72db228bbc43c00ce3d3266fde8e1d3324e9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Guide pratique pour interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)
L’exemple suivant montre comment utiliser LINQ avec la réflexion pour récupérer des métadonnées spécifiques concernant des méthodes qui correspondent à un critère de recherche spécifié. Ici, la requête va rechercher les noms de toutes les méthodes dans l’assembly qui retournent des types énumérables tels que des tableaux.  
  
## <a name="example"></a>Exemple  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
        {  
            Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
            var pubTypesQuery = from type in assembly.GetTypes()  
                        where type.IsPublic  
                            from method in type.GetMethods()  
                            where method.ReturnType.IsArray == true   
                                || ( method.ReturnType.GetInterface(  
                                    typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                                && method.ReturnType.FullName != "System.String" )  
                            group method.ToString() by type.ToString();  
  
            foreach (var groupOfMethods in pubTypesQuery)  
            {  
                Console.WriteLine("Type: {0}", groupOfMethods.Key);  
                foreach (var method in groupOfMethods)  
                {  
                    Console.WriteLine("  {0}", method);  
                }  
            }  
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 L’exemple utilise la méthode <xref:System.Reflection.Assembly.GetTypes%2A> pour retourner un tableau de types de l’assembly spécifié. Le filtre [where](../../../../csharp/language-reference/keywords/where-clause.md) est appliqué pour que seuls des types publics soient retournés. Pour chaque type public, une sous-requête est générée en utilisant le tableau <xref:System.Reflection.MethodInfo> qui est retourné à partir de l’appel <xref:System.Type.GetMethods%2A>. Ces résultats sont filtrés pour retourner uniquement les méthodes dont le type de retour est un tableau ou un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>. Pour finir, ces résultats sont regroupés en utilisant le nom de type comme clé.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créez un projet qui cible le .NET Framework version 3.5 ou version ultérieure, avec une référence à System.Core.dll et des directives `using` pour les espaces de noms System.Linq et System.IO.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)

