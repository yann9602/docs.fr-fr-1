---
title: "Guide pratique pour substituer la méthode ToString (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 60cec855286a3bb572a0bacd08c0f7920a1fc912
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="692c1-102">Guide pratique pour substituer la méthode ToString (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="692c1-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="692c1-103">En C#, chaque classe ou struct hérite implicitement de la classe <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="692c1-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="692c1-104">Ainsi, chaque objet en C# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet.</span><span class="sxs-lookup"><span data-stu-id="692c1-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="692c1-105">Par exemple, toutes les variables de type `int` ont une méthode `ToString`, ce qui leur permet de retourner leur contenu sous forme de chaîne :</span><span class="sxs-lookup"><span data-stu-id="692c1-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 <span data-ttu-id="692c1-106">[!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="692c1-106">[!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]</span></span>  
  
 <span data-ttu-id="692c1-107">Quand vous créez une classe ou un struct personnalisé, vous devez substituer la méthode <xref:System.Object.ToString%2A> pour fournir des informations sur votre type au code client.</span><span class="sxs-lookup"><span data-stu-id="692c1-107">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="692c1-108">Pour plus d’informations sur l’utilisation de chaînes de format et d’autres types de mise en forme personnalisée avec la méthode `ToString`, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="692c1-108">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="692c1-109">Quand vous choisissez les informations à fournir par l’intermédiaire de cette méthode, déterminez si votre classe ou struct sera utilisé par du code non fiable.</span><span class="sxs-lookup"><span data-stu-id="692c1-109">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="692c1-110">Veillez à ne pas fournir d’informations susceptibles d’être exploitées par du code malveillant.</span><span class="sxs-lookup"><span data-stu-id="692c1-110">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="692c1-111">Pour substituer la méthode ToString dans votre classe ou struct</span><span class="sxs-lookup"><span data-stu-id="692c1-111">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="692c1-112">Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :</span><span class="sxs-lookup"><span data-stu-id="692c1-112">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="692c1-113">Implémentez la méthode pour qu’elle retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="692c1-113">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="692c1-114">L’exemple suivant retourne le nom de la classe en plus des données propres à une instance particulière de la classe.</span><span class="sxs-lookup"><span data-stu-id="692c1-114">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     <span data-ttu-id="692c1-115">[!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="692c1-115">[!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]</span></span>  
  
     <span data-ttu-id="692c1-116">Vous pouvez tester la méthode `ToString` comme illustré dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="692c1-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     <span data-ttu-id="692c1-117">[!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="692c1-117">[!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692c1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="692c1-118">See Also</span></span>  
 <span data-ttu-id="692c1-119"><xref:System.IFormattable></span><span class="sxs-lookup"><span data-stu-id="692c1-119"><xref:System.IFormattable></span></span>   
 <span data-ttu-id="692c1-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="692c1-121">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-121">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="692c1-122">[Chaînes](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-122">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="692c1-123">[string](../../../csharp/language-reference/keywords/string.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-123">[string](../../../csharp/language-reference/keywords/string.md) </span></span>  
 <span data-ttu-id="692c1-124">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-124">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 <span data-ttu-id="692c1-125">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-125">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 <span data-ttu-id="692c1-126">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span><span class="sxs-lookup"><span data-stu-id="692c1-126">[virtual](../../../csharp/language-reference/keywords/virtual.md) </span></span>  
 [<span data-ttu-id="692c1-127">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="692c1-127">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

