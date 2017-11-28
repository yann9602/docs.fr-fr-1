---
title: "Comment : écrire un constructeur de copie (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="2a399-102">Comment : écrire un constructeur de copie (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2a399-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="2a399-103">C# ne fournit pas de constructeur de copie pour les objets, mais vous pouvez en écrire un vous-même.</span><span class="sxs-lookup"><span data-stu-id="2a399-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a399-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2a399-104">Example</span></span>  
 <span data-ttu-id="2a399-105">Dans l’exemple suivant, la `Person`[classe](../../../csharp/language-reference/keywords/class.md) définit un constructeur de copie qui prend comme argument une instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="2a399-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="2a399-106">Les valeurs des propriétés de l’argument sont assignées aux propriétés de la nouvelle instance de `Person`.</span><span class="sxs-lookup"><span data-stu-id="2a399-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="2a399-107">Le code contient un autre constructeur de copie qui envoie les propriétés `Name` et `Age` de l’instance que vous voulez copier au constructeur d’instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="2a399-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2a399-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a399-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="2a399-109">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2a399-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a399-110">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="2a399-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="2a399-111">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="2a399-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="2a399-112">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="2a399-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
