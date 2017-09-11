---
title: "unsafe (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
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
ms.openlocfilehash: ceba9e518caf6618cf2f457b930ce08f18273d8c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-reference"></a><span data-ttu-id="290a2-102">unsafe (référence C#)</span><span class="sxs-lookup"><span data-stu-id="290a2-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="290a2-103">Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs.</span><span class="sxs-lookup"><span data-stu-id="290a2-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="290a2-104">Pour plus d’informations, consultez l’article [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="290a2-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="290a2-105">Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre.</span><span class="sxs-lookup"><span data-stu-id="290a2-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="290a2-106">Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="290a2-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="290a2-107">Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :</span><span class="sxs-lookup"><span data-stu-id="290a2-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="290a2-108">La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :</span><span class="sxs-lookup"><span data-stu-id="290a2-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="290a2-109">Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="290a2-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="290a2-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="290a2-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="290a2-111">Pour compiler du code unsafe, vous devez spécifier l’option de compilateur [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="290a2-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="290a2-112">Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="290a2-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="290a2-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="290a2-113">Example</span></span>  
 <span data-ttu-id="290a2-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="290a2-114">[!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="290a2-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="290a2-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="290a2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="290a2-116">See Also</span></span>  
 <span data-ttu-id="290a2-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="290a2-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="290a2-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="290a2-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="290a2-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="290a2-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="290a2-120">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="290a2-120">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 <span data-ttu-id="290a2-121">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="290a2-121">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 [<span data-ttu-id="290a2-122">Mémoires tampons de taille fixe</span><span class="sxs-lookup"><span data-stu-id="290a2-122">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

