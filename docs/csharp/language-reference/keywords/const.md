---
title: "const (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
dev_langs:
- CSharp
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: 28
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
ms.openlocfilehash: b8f6d567deed513ff5693fe39bd21c8607677402
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="const-c-reference"></a><span data-ttu-id="a1508-102">const (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a1508-102">const (C# Reference)</span></span>
<span data-ttu-id="a1508-103">Vous utilisez le mot clé `const` pour déclarer un champ constant ou un élément local constant.</span><span class="sxs-lookup"><span data-stu-id="a1508-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="a1508-104">Les champs et les éléments locaux constants ne sont pas des variables et ne peuvent pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="a1508-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="a1508-105">Les constantes peuvent être des chiffres, des valeurs booléennes, des chaînes ou une référence null.</span><span class="sxs-lookup"><span data-stu-id="a1508-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="a1508-106">Ne créez pas une constante pour représenter des informations qui doivent être modifiées.</span><span class="sxs-lookup"><span data-stu-id="a1508-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="a1508-107">Par exemple, n'utilisez pas un champ constant pour stocker le prix d'un service, le numéro de version du produit ou le nom de la marque d'une société.</span><span class="sxs-lookup"><span data-stu-id="a1508-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="a1508-108">Ces valeurs peuvent changer dans le temps, et dans la mesure où les compilateurs propagent les constantes, le code compilé avec vos bibliothèques devra être recompilé pour refléter ces modifications.</span><span class="sxs-lookup"><span data-stu-id="a1508-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="a1508-109">Consultez également le mot clé [readonly](../../../csharp/language-reference/keywords/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a1508-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="a1508-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a1508-110">For example:</span></span>  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1508-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1508-111">Remarks</span></span>  
 <span data-ttu-id="a1508-112">Le type d'une déclaration constante indique le type des membres introduit par la déclaration.</span><span class="sxs-lookup"><span data-stu-id="a1508-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="a1508-113">L'initialiseur d'un élément local constant ou d'un champ constant doit être une expression constante qui peut être implicitement convertie en type cible.</span><span class="sxs-lookup"><span data-stu-id="a1508-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>  
  
 <span data-ttu-id="a1508-114">Une expression constante est une expression qui peut être complètement évaluée au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a1508-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="a1508-115">C'est pourquoi, les seules valeurs possibles pour les constantes des types référence sont `string` et une référence null.</span><span class="sxs-lookup"><span data-stu-id="a1508-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>  
  
 <span data-ttu-id="a1508-116">La déclaration constante peut déclarer plusieurs constantes, notamment :</span><span class="sxs-lookup"><span data-stu-id="a1508-116">The constant declaration can declare multiple constants, such as:</span></span>  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 <span data-ttu-id="a1508-117">Le modificateur `static` n'est pas autorisé dans une déclaration constante.</span><span class="sxs-lookup"><span data-stu-id="a1508-117">The `static` modifier is not allowed in a constant declaration.</span></span>  
  
 <span data-ttu-id="a1508-118">Une constante peut être utilisée dans une expression constante, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a1508-118">A constant can participate in a constant expression, as follows:</span></span>  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  <span data-ttu-id="a1508-119">Le mot clé [readonly](../../../csharp/language-reference/keywords/readonly.md) est différent du mot clé `const`.</span><span class="sxs-lookup"><span data-stu-id="a1508-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="a1508-120">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="a1508-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="a1508-121">Un champ `readonly` peut être initialisé dans la déclaration ou dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="a1508-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="a1508-122">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="a1508-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="a1508-123">De même, bien qu'un champ `const` soit une constante au moment de la compilation, le champ `readonly` peut être utilisé pour des constantes au moment de l'exécution, comme ci-après : `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="a1508-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1508-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1508-124">Example</span></span>  
 <span data-ttu-id="a1508-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1508-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1508-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1508-126">Example</span></span>  
 <span data-ttu-id="a1508-127">Cet exemple montre comment utiliser des constantes en tant que variables locales.</span><span class="sxs-lookup"><span data-stu-id="a1508-127">This example demonstrates how to use constants as local variables.</span></span>  
  
 <span data-ttu-id="a1508-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1508-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1508-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a1508-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1508-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1508-130">See Also</span></span>  
 <span data-ttu-id="a1508-131">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1508-131">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a1508-132">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1508-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a1508-133">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1508-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="a1508-134">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="a1508-134">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="a1508-135">readonly</span><span class="sxs-lookup"><span data-stu-id="a1508-135">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)

