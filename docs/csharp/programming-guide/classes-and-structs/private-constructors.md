---
title: "Constructeurs privés (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
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
ms.openlocfilehash: 1ccd3db5f95e3a237bb37d9e09c34f415fcfd752
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="b4d1a-102">Constructeurs privés (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b4d1a-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="b4d1a-103">Un constructeur privé est un constructeur d’instance spécial.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="b4d1a-104">Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="b4d1a-105">Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="b4d1a-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="b4d1a-106">For example:</span></span>  
  
 <span data-ttu-id="b4d1a-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b4d1a-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="b4d1a-108">La déclaration du constructeur vide empêche la génération automatique d’un constructeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-108">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="b4d1a-109">Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-109">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="b4d1a-110">En règle générale, le modificateur [private](../../../csharp/language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-110">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="b4d1a-111">Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-111">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="b4d1a-112">Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-112">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="b4d1a-113">Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="b4d1a-113">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4d1a-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4d1a-114">Example</span></span>  
 <span data-ttu-id="b4d1a-115">L’exemple suivant montre une classe qui utilise un constructeur privé.</span><span class="sxs-lookup"><span data-stu-id="b4d1a-115">The following is an example of a class using a private constructor.</span></span>  
  
 <span data-ttu-id="b4d1a-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b4d1a-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="b4d1a-117">Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :</span><span class="sxs-lookup"><span data-stu-id="b4d1a-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 <span data-ttu-id="b4d1a-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b4d1a-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b4d1a-119">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b4d1a-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4d1a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4d1a-120">See Also</span></span>  
 <span data-ttu-id="b4d1a-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b4d1a-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b4d1a-122">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="b4d1a-122">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="b4d1a-123">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="b4d1a-123">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="b4d1a-124">[Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="b4d1a-124">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 <span data-ttu-id="b4d1a-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="b4d1a-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="b4d1a-126">public</span><span class="sxs-lookup"><span data-stu-id="b4d1a-126">public</span></span>](../../../csharp/language-reference/keywords/public.md)

