---
title: "Accéder à des attributs à l’aide de la réflexion (Visual Basic) | Documents Microsoft"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
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
ms.openlocfilehash: ac1e017ae13fc1291fd41e5747171160a9d70238
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="a8d1f-102">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8d1f-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="a8d1f-103">Le fait que vous pouvez définir des attributs personnalisés et les placer dans votre code source serait peu d’intérêt la possibilité de récupérer ces informations et en agissant sur elle.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="a8d1f-104">En utilisant la réflexion, vous pouvez récupérer les informations qui a été définies avec des attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="a8d1f-105">La méthode clé est `GetCustomAttributes`, qui retourne un tableau d’objets qui sont les équivalents de l’exécution des attributs du code source.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="a8d1f-106">Cette méthode a plusieurs versions surchargées.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-106">This method has several overloaded versions.</span></span> <span data-ttu-id="a8d1f-107">Pour plus d’informations, consultez <xref:System.Attribute>.</xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="a8d1f-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="a8d1f-108">Une spécification d’attribut tels que :</span><span class="sxs-lookup"><span data-stu-id="a8d1f-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="a8d1f-109">est semblable à ceci :</span><span class="sxs-lookup"><span data-stu-id="a8d1f-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="a8d1f-110">Toutefois, le code n’est pas exécuté jusqu'à ce que `SampleClass` est interrogée sur les attributs.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="a8d1f-111">Appel de `GetCustomAttributes` sur `SampleClass` entraîne une `Author` objet et l’initialisation comme illustré ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="a8d1f-112">Si la classe a d’autres attributs, les autres objets d’attribut sont construits de la même façon.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="a8d1f-113">`GetCustomAttributes`Renvoie la `Author` objet et autres objets d’attribut dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="a8d1f-114">Vous pouvez ensuite itérer sur ce tableau, déterminer les attributs ont été appliqués en fonction du type de chaque élément du tableau et extraire des informations à partir des objets des attributs.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d1f-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="a8d1f-115">Example</span></span>  
 <span data-ttu-id="a8d1f-116">Voici un exemple complet.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-116">Here is a complete example.</span></span> <span data-ttu-id="a8d1f-117">Un attribut personnalisé est défini, appliqué à plusieurs entités et récupéré par réflexion.</span><span class="sxs-lookup"><span data-stu-id="a8d1f-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8d1f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d1f-118">See Also</span></span>  
 <span data-ttu-id="a8d1f-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="a8d1f-119"><xref:System.Reflection></span></span>   
 <span data-ttu-id="a8d1f-120"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="a8d1f-120"><xref:System.Attribute></span></span>   
<span data-ttu-id="a8d1f-121"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a8d1f-121"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="a8d1f-122"> [Récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span><span class="sxs-lookup"><span data-stu-id="a8d1f-122"> [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span></span>  
<span data-ttu-id="a8d1f-123"> [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="a8d1f-123"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="a8d1f-124"> [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="a8d1f-124"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="a8d1f-125"> [Création d’attributs personnalisés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a8d1f-125"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span></span>
