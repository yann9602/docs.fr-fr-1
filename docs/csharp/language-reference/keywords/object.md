---
title: "object (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
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
ms.openlocfilehash: 744debc51f68cc52f03bce09c9f276a66ae085e1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="object-c-reference"></a><span data-ttu-id="d71c4-102">object (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="d71c4-102">object (C# Reference)</span></span>
<span data-ttu-id="d71c4-103">Le type `object` est un alias du type <xref:System.Object> du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d71c4-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="d71c4-104">Dans le système de type unifié de C#, tous les types (les types référence et valeur, prédéfinis ou définis par l’utilisateur) héritent directement ou indirectement du type <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d71c4-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="d71c4-105">Vous pouvez assigner des valeurs de tout type aux variables de type `object`.</span><span class="sxs-lookup"><span data-stu-id="d71c4-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="d71c4-106">Quand une variable d’un type valeur est convertie en type objet, elle est dite *boxed*.</span><span class="sxs-lookup"><span data-stu-id="d71c4-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="d71c4-107">Quand une variable de type objet est convertie en type valeur, elle est dite *unboxed*.</span><span class="sxs-lookup"><span data-stu-id="d71c4-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="d71c4-108">Pour plus d’informations, consultez [Boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="d71c4-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71c4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="d71c4-109">Example</span></span>  
 <span data-ttu-id="d71c4-110">L’exemple suivant montre comment les variables de type `object` acceptent des valeurs de tout type de données et comment les variables de type `object` utilisent des méthodes d’<xref:System.Object> du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d71c4-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 <span data-ttu-id="d71c4-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d71c4-111">[!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d71c4-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d71c4-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d71c4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d71c4-113">See Also</span></span>  
 <span data-ttu-id="d71c4-114">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d71c4-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d71c4-115">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d71c4-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d71c4-116">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d71c4-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="d71c4-117">[Types référence](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="d71c4-117">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 [<span data-ttu-id="d71c4-118">Types valeur</span><span class="sxs-lookup"><span data-stu-id="d71c4-118">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)

