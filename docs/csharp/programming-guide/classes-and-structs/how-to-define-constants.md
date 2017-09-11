---
title: "Guide pratique pour définir des constantes en C#"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: 7
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
ms.openlocfilehash: 6c5a6f63675893eb0700afab462bf237f5639d74
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="41edf-102">Guide pratique pour définir des constantes en C#</span><span class="sxs-lookup"><span data-stu-id="41edf-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="41edf-103">Les constantes sont des champs dont les valeurs sont définies au moment de la compilation et ne sont pas modifiables.</span><span class="sxs-lookup"><span data-stu-id="41edf-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="41edf-104">Utilisez des constantes pour fournir des noms explicites au lieu de littéraux numériques (« nombres magiques ») pour les valeurs spéciales.</span><span class="sxs-lookup"><span data-stu-id="41edf-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41edf-105">En C#, la directive de préprocesseur [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ne peut pas être utilisée pour définir des constantes de la manière généralement utilisée en C et C++.</span><span class="sxs-lookup"><span data-stu-id="41edf-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="41edf-106">Pour définir des valeurs constantes de types intégraux (`int`, `byte`, etc.), utilisez un type énuméré.</span><span class="sxs-lookup"><span data-stu-id="41edf-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="41edf-107">Pour plus d’informations, consultez [enum](../../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="41edf-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="41edf-108">Pour définir des constantes non intégrales, une approche consiste à les regrouper dans une classe statique unique nommée `Constants`.</span><span class="sxs-lookup"><span data-stu-id="41edf-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="41edf-109">Cette opération exige que toutes les références aux constantes soient précédées par le nom de classe, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="41edf-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41edf-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="41edf-110">Example</span></span>  
 <span data-ttu-id="41edf-111">[!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="41edf-111">[!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]</span></span>  
  
 <span data-ttu-id="41edf-112">L’utilisation du qualificateur de nom de classe permet de garantir que les personnes qui utilisent la constante, dont vous-même, comprennent qu’il s’agit d’une valeur constante et qu’elle ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="41edf-112">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41edf-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41edf-113">See Also</span></span>  
 [<span data-ttu-id="41edf-114">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="41edf-114">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)

