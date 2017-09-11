---
title: "Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
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
ms.openlocfilehash: 808a74f75e4dcbcec47735d98063138e2c7456e5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="ca45c-102">Comment : utiliser des pointeurs pour copier un tableau d'octets (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ca45c-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>
<span data-ttu-id="ca45c-103">L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.</span><span class="sxs-lookup"><span data-stu-id="ca45c-103">The following example uses pointers to copy bytes from one array to another.</span></span>  
  
 <span data-ttu-id="ca45c-104">Cet exemple utilise le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`.</span><span class="sxs-lookup"><span data-stu-id="ca45c-104">This example uses the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="ca45c-105">L’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination.</span><span class="sxs-lookup"><span data-stu-id="ca45c-105">The [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="ca45c-106">Elle *épingle* l’emplacement des tableaux source et de destination en mémoire pour qu’ils ne soient pas déplacés par l’opération de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ca45c-106">This *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="ca45c-107">Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué.</span><span class="sxs-lookup"><span data-stu-id="ca45c-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="ca45c-108">Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur **/unsafe**.</span><span class="sxs-lookup"><span data-stu-id="ca45c-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the **/unsafe** compiler option.</span></span> <span data-ttu-id="ca45c-109">Pour définir l’option dans Visual Studio, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="ca45c-109">To set the option in Visual Studio, right-click the project name, and then click **Properties**.</span></span> <span data-ttu-id="ca45c-110">Sous l’onglet **Générer**, sélectionnez **Autoriser le code unsafe**.</span><span class="sxs-lookup"><span data-stu-id="ca45c-110">On the **Build** tab, select **Allow unsafe code**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca45c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca45c-111">Example</span></span>  
 <span data-ttu-id="ca45c-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca45c-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]</span></span>  
  
 <span data-ttu-id="ca45c-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca45c-113">[!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca45c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca45c-114">See Also</span></span>  
 <span data-ttu-id="ca45c-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca45c-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ca45c-116">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca45c-116">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="ca45c-117">[-unsafe (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="ca45c-117">[/unsafe (C# Compiler Options)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) </span></span>  
 [<span data-ttu-id="ca45c-118">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="ca45c-118">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

