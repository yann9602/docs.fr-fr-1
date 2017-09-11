---
title: "readonly (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
dev_langs:
- CSharp
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
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
ms.openlocfilehash: 2660aa56721815cbbeb668328863956473cce8f1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="readonly-c-reference"></a><span data-ttu-id="499af-102">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="499af-102">readonly (C# Reference)</span></span>
<span data-ttu-id="499af-103">Le mot clé `readonly` est un modificateur que vous pouvez utiliser sur des champs.</span><span class="sxs-lookup"><span data-stu-id="499af-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="499af-104">Lorsqu’une déclaration de champ inclut un modificateur `readonly`, les assignations aux champs introduites par la déclaration peuvent se produire uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe.</span><span class="sxs-lookup"><span data-stu-id="499af-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="499af-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="499af-105">Example</span></span>  
 <span data-ttu-id="499af-106">Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear`, même si une valeur lui est affectée dans le constructeur de classe :</span><span class="sxs-lookup"><span data-stu-id="499af-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 <span data-ttu-id="499af-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="499af-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span></span>  
  
 <span data-ttu-id="499af-108">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="499af-108">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="499af-109">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="499af-109">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="499af-110">Pour un champ d’instance, dans les constructeurs d’instance de la classe qui contient la déclaration de champ, ou pour un champ statique, dans le constructeur statique de la classe qui contient la déclaration de champ.</span><span class="sxs-lookup"><span data-stu-id="499af-110">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="499af-111">Ce sont également les seuls contextes dans lesquels il est valide de passer un champ `readonly` comme paramètre [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="499af-111">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="499af-112">Le mot clé `readonly` est différent du mot clé [const](../../../csharp/language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="499af-112">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="499af-113">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="499af-113">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="499af-114">Un champ `readonly` peut être initialisé dans la déclaration ou dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="499af-114">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="499af-115">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="499af-115">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="499af-116">De même, alors qu’un champ `const` est une constante au moment de la compilation, le champ `readonly` peut être utilisé pour des constantes au moment de l’exécution, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="499af-116">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="499af-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="499af-117">Example</span></span>  
 <span data-ttu-id="499af-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="499af-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span></span>  
  
 <span data-ttu-id="499af-119">Dans l’exemple précédent, si vous utilisez une instruction telle que :</span><span class="sxs-lookup"><span data-stu-id="499af-119">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="499af-120">vous obtenez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="499af-120">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="499af-121">qui est la même erreur que vous obtenez lorsque vous tentez d’assigner une valeur à une constante.</span><span class="sxs-lookup"><span data-stu-id="499af-121">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="499af-122">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="499af-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="499af-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="499af-123">See Also</span></span>  
 <span data-ttu-id="499af-124">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="499af-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="499af-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="499af-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="499af-126">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="499af-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="499af-127">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="499af-127">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="499af-128">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="499af-128">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 [<span data-ttu-id="499af-129">Champs</span><span class="sxs-lookup"><span data-stu-id="499af-129">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

