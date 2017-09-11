---
title: "Création d’attributs personnalisés (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
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
ms.openlocfilehash: fbfc3f84f6287d233d475f01869dab63b937a521
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="f6e80-102">Création d’attributs personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6e80-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="f6e80-103">Vous pouvez créer vos propres attributs personnalisés en définissant une classe d’attributs, une classe qui dérive directement ou indirectement de <xref:System.Attribute>, qui permet d’identifier les définitions d’attributs dans les métadonnées rapide et facile.</xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="f6e80-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="f6e80-104">Supposons que vous souhaitez les types de balise avec le nom du programmeur qui a écrit le type.</span><span class="sxs-lookup"><span data-stu-id="f6e80-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="f6e80-105">Vous pouvez définir une personnalisée `Author` classe d’attributs :</span><span class="sxs-lookup"><span data-stu-id="f6e80-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f6e80-106">Le nom de classe est le nom d’attribut, `Author`.</span><span class="sxs-lookup"><span data-stu-id="f6e80-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="f6e80-107">Elle est dérivée de `System.Attribute`, il est donc une classe d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="f6e80-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="f6e80-108">Les paramètres du constructeur sont les paramètres positionnels de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f6e80-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="f6e80-109">Dans cet exemple, `name` est un paramètre positionnel.</span><span class="sxs-lookup"><span data-stu-id="f6e80-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="f6e80-110">Les champs en lecture-écriture publics ou les propriétés sont des paramètres nommées.</span><span class="sxs-lookup"><span data-stu-id="f6e80-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="f6e80-111">Dans ce cas, `version` est le seul paramètre nommé.</span><span class="sxs-lookup"><span data-stu-id="f6e80-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="f6e80-112">Notez l’utilisation de la `AttributeUsage` attribut pour rendre le `Author` attribut valide uniquement sur la classe et `Structure` déclarations.</span><span class="sxs-lookup"><span data-stu-id="f6e80-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="f6e80-113">Vous pouvez utiliser ce nouvel attribut comme suit :</span><span class="sxs-lookup"><span data-stu-id="f6e80-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="f6e80-114">`AttributeUsage`a un paramètre nommé, `AllowMultiple`, avec lequel vous pouvez apporter un attribut personnalisé à usage unique ou multiple.</span><span class="sxs-lookup"><span data-stu-id="f6e80-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="f6e80-115">Dans l’exemple de code suivant, un attribut à usages multiples est créé.</span><span class="sxs-lookup"><span data-stu-id="f6e80-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="f6e80-116">Dans l’exemple de code suivant, plusieurs attributs du même type sont appliqués à une classe.</span><span class="sxs-lookup"><span data-stu-id="f6e80-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="f6e80-117">Si votre classe d’attributs contient une propriété, cette propriété doit être en lecture-écriture.</span><span class="sxs-lookup"><span data-stu-id="f6e80-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e80-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6e80-118">See Also</span></span>  
 <span data-ttu-id="f6e80-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="f6e80-119"><xref:System.Reflection></span></span>   
<span data-ttu-id="f6e80-120"> [Guide de programmation Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f6e80-120"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="f6e80-121"> [Écriture des attributs personnalisés](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span><span class="sxs-lookup"><span data-stu-id="f6e80-121"> [Writing Custom Attributes](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span></span>  
<span data-ttu-id="f6e80-122"> [Réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="f6e80-122"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="f6e80-123"> [Attributs (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="f6e80-123"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="f6e80-124"> [Accéder à des attributs à l’aide de la réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span><span class="sxs-lookup"><span data-stu-id="f6e80-124"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span></span>  
<span data-ttu-id="f6e80-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span><span class="sxs-lookup"><span data-stu-id="f6e80-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span></span>
