---
title: "Comment : écrire un constructeur de copie (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: 20
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
ms.openlocfilehash: 712d9d5e792d025dd7c91d4c1809eeba96759757
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="9ab16-102">Comment : écrire un constructeur de copie (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9ab16-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="9ab16-103">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="9ab16-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab16-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ab16-104">Example</span></span>  
 <span data-ttu-id="9ab16-105">Dans l’exemple suivant, la `Person`[classe](../../../csharp/language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="9ab16-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="9ab16-106">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="9ab16-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="9ab16-107">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="9ab16-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 <span data-ttu-id="9ab16-108">[!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9ab16-108">[!code-cs[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab16-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ab16-109">See Also</span></span>  
 <span data-ttu-id="9ab16-110"><xref:System.ICloneable></span><span class="sxs-lookup"><span data-stu-id="9ab16-110"><xref:System.ICloneable></span></span>   
 <span data-ttu-id="9ab16-111">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ab16-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9ab16-112">[Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="9ab16-112">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="9ab16-113">[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="9ab16-113">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 [<span data-ttu-id="9ab16-114">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="9ab16-114">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

