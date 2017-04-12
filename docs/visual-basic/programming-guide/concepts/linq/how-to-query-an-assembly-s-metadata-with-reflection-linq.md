---
title: "Comment : interroger les métadonnées d’un Assembly avec réflexion (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c1bc26d7b23135dd45ad58ea0bd2510b7157448
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Comment : interroger les métadonnées d’un Assembly avec réflexion (LINQ) (Visual Basic)
L’exemple suivant montre comment LINQ peut être utilisé avec la réflexion pour récupérer des métadonnées spécifiques concernant des méthodes qui correspondent à un critère de recherche spécifié. Dans ce cas, la requête identifie les noms de toutes les méthodes dans l’assembly qui retournent des types énumérables tels que les tableaux.  
  
## <a name="example"></a>Exemple  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 L’exemple utilise le <xref:System.Reflection.Assembly.GetTypes%2A>méthode pour retourner un tableau de types dans l’assembly spécifié.</xref:System.Reflection.Assembly.GetTypes%2A> Le [une Clause Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtre est appliqué afin que seuls les types publics sont retournés. Pour chaque type public, une sous-requête est générée à l’aide de le <xref:System.Reflection.MethodInfo>tableau qui est retourné à partir de la <xref:System.Type.GetMethods%2A>appeler.</xref:System.Type.GetMethods%2A> </xref:System.Reflection.MethodInfo> Ces résultats sont filtrés pour retourner uniquement les méthodes dont le type de retour est un tableau ou un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Enfin, ces résultats sont regroupés en utilisant le nom de type en tant que clé.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
