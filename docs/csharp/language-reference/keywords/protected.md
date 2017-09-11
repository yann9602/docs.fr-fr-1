---
title: "protected (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
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
ms.openlocfilehash: c3d24389f66edec313d4f5238b0aee02518e33b7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="protected-c-reference"></a><span data-ttu-id="dd28e-102">protected (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dd28e-102">protected (C# Reference)</span></span>
<span data-ttu-id="dd28e-103">Le mot clé `protected` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="dd28e-103">The `protected` keyword is a member access modifier.</span></span> <span data-ttu-id="dd28e-104">Un membre protégé est accessible dans sa classe et par les instances de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="dd28e-104">A protected member is accessible within its class and by derived class instances.</span></span> <span data-ttu-id="dd28e-105">Pour obtenir une comparaison de `protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dd28e-105">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd28e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd28e-106">Example</span></span>  
 <span data-ttu-id="dd28e-107">Un membre protégé d’une classe de base est accessible dans une classe dérivée uniquement si l’accès s’effectue par le biais du type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="dd28e-107">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="dd28e-108">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="dd28e-108">For example, consider the following code segment:</span></span>  
  
 <span data-ttu-id="dd28e-109">[!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd28e-109">[!code-cs[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]</span></span>  
  
 <span data-ttu-id="dd28e-110">L’instruction `a.x = 10` génère une erreur, car elle est appelée dans la méthode statique Main, et pas dans une instance de la classe B.</span><span class="sxs-lookup"><span data-stu-id="dd28e-110">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="dd28e-111">Les membres de struct ne peuvent pas être protégés, car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="dd28e-111">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd28e-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd28e-112">Example</span></span>  
 <span data-ttu-id="dd28e-113">Dans cet exemple, la classe `DerivedPoint` est dérivée de `Point`.</span><span class="sxs-lookup"><span data-stu-id="dd28e-113">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="dd28e-114">Vous pouvez donc accéder aux membres protégés de la classe de base directement à partir de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="dd28e-114">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 <span data-ttu-id="dd28e-115">[!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd28e-115">[!code-cs[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]</span></span>  
  
 <span data-ttu-id="dd28e-116">Si vous changez les niveaux d’accès de `x` et `y` à [private](../../../csharp/language-reference/keywords/private.md), le compilateur affiche les messages d’erreur suivants :</span><span class="sxs-lookup"><span data-stu-id="dd28e-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="dd28e-117">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dd28e-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd28e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd28e-118">See Also</span></span>  
 <span data-ttu-id="dd28e-119">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dd28e-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dd28e-121">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-121">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="dd28e-122">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-122">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="dd28e-123">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-123">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="dd28e-124">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-124">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="dd28e-125">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-125">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="dd28e-126">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="dd28e-126">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="dd28e-127">internal</span><span class="sxs-lookup"><span data-stu-id="dd28e-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

