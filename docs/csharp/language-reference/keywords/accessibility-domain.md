---
title: "Domaine d'accessibilité (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
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
ms.openlocfilehash: 90faf22d8a7d515ae8bd062f0b95f4be5e051f79
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="dccd6-102">Domaine d'accessibilité (référence C#)</span><span class="sxs-lookup"><span data-stu-id="dccd6-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="dccd6-103">Le domaine d’accessibilité d’un membre indique dans quelles sections du programme un membre peut être référencé.</span><span class="sxs-lookup"><span data-stu-id="dccd6-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="dccd6-104">Si le membre est imbriqué dans un autre type, son domaine d’accessibilité est déterminé à la fois par le [niveau d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) du membre et par le domaine d’accessibilité du type conteneur immédiat.</span><span class="sxs-lookup"><span data-stu-id="dccd6-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="dccd6-105">Le domaine d’accessibilité d’un type de niveau supérieur est au moins le texte du programme du projet dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="dccd6-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="dccd6-106">Cela signifie que le domaine inclut tous les fichiers sources de ce projet.</span><span class="sxs-lookup"><span data-stu-id="dccd6-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="dccd6-107">Le domaine d’accessibilité d’un type imbriqué est au moins le texte de programme du type dans lequel il est déclaré.</span><span class="sxs-lookup"><span data-stu-id="dccd6-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="dccd6-108">Autrement dit, le domaine est le corps du type, qui inclut tous les types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="dccd6-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="dccd6-109">Le domaine d’accessibilité d’un type imbriqué ne dépasse jamais celui du type conteneur.</span><span class="sxs-lookup"><span data-stu-id="dccd6-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="dccd6-110">Ces concepts sont illustrés dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dccd6-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dccd6-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="dccd6-111">Example</span></span>  
 <span data-ttu-id="dccd6-112">Cet exemple comporte un type de niveau supérieur, `T1`, et deux classes imbriquées, `M1` et `M2`.</span><span class="sxs-lookup"><span data-stu-id="dccd6-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="dccd6-113">Les classes contiennent des champs qui ont des accessibilités déclarées différentes.</span><span class="sxs-lookup"><span data-stu-id="dccd6-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="dccd6-114">Dans la méthode `Main`, un commentaire suit chaque instruction pour indiquer le domaine d’accessibilité de chaque membre.</span><span class="sxs-lookup"><span data-stu-id="dccd6-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="dccd6-115">Notez que les instructions qui tentent de référencer les membres inaccessibles sont commentées.</span><span class="sxs-lookup"><span data-stu-id="dccd6-115">Notice that the statements that try to reference the inaccessible members are commented out.</span></span> <span data-ttu-id="dccd6-116">Si vous voulez examiner les erreurs du compilateur causées par une référence à un membre inaccessible, supprimez les commentaires un à un.</span><span class="sxs-lookup"><span data-stu-id="dccd6-116">If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
 <span data-ttu-id="dccd6-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dccd6-117">[!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dccd6-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="dccd6-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dccd6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dccd6-119">See Also</span></span>  
 <span data-ttu-id="dccd6-120">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dccd6-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dccd6-122">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="dccd6-123">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-123">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="dccd6-124">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-124">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="dccd6-125">[Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-125">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md) </span></span>  
 <span data-ttu-id="dccd6-126">[Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="dccd6-127">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-127">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="dccd6-128">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-128">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="dccd6-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="dccd6-129">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="dccd6-130">internal</span><span class="sxs-lookup"><span data-stu-id="dccd6-130">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

