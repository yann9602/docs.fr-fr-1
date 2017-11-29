---
title: "Comment : rechercher des chaînes à l'aide d'expressions régulières (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="f94df-102">Comment : rechercher des chaînes à l'aide d'expressions régulières (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f94df-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="f94df-103">La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> permet d’effectuer des recherches de chaînes.</span><span class="sxs-lookup"><span data-stu-id="f94df-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="f94df-104">La complexité de ces recherches peut aller de la plus simple à celle qui exploite au mieux les expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="f94df-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="f94df-105">Voici deux exemples de recherche de chaînes à l’aide de la classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="f94df-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="f94df-106">Pour plus d’informations, consultez [Expressions régulières .NET Framework](https://msdn.microsoft.com/library/hs600312).</span><span class="sxs-lookup"><span data-stu-id="f94df-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f94df-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f94df-107">Example</span></span>  
 <span data-ttu-id="f94df-108">Le code suivant est une application console qui effectue une recherche simple non sensible à la casse dans les chaînes d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f94df-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="f94df-109">La méthode statique <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> effectue la recherche en fonction de la chaîne à rechercher et du modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="f94df-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="f94df-110">Dans ce cas, un troisième argument est utilisé pour indiquer que la casse doit être ignorée.</span><span class="sxs-lookup"><span data-stu-id="f94df-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="f94df-111">Pour plus d'informations, consultez <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f94df-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f94df-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f94df-112">Example</span></span>  
 <span data-ttu-id="f94df-113">Le code suivant est une application console qui utilise des expressions régulières pour valider le format de chaque chaîne d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="f94df-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="f94df-114">La validation exige que chaque chaîne prenne la forme d’un numéro de téléphone constitué de trois groupes de chiffres séparés par des tirets, les deux premiers groupes contenant trois chiffres et le troisième contenant quatre chiffres.</span><span class="sxs-lookup"><span data-stu-id="f94df-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="f94df-115">Cette validation s’appuie sur l’expression régulière `^\\d{3}-\\d{3}-\\d{4}$`.</span><span class="sxs-lookup"><span data-stu-id="f94df-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="f94df-116">Pour plus d’informations, consultez [Langage des expressions régulières - Aide-mémoire](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span><span class="sxs-lookup"><span data-stu-id="f94df-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f94df-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f94df-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="f94df-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f94df-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f94df-119">Chaînes</span><span class="sxs-lookup"><span data-stu-id="f94df-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="f94df-120">.NET Framework (expressions régulières)</span><span class="sxs-lookup"><span data-stu-id="f94df-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="f94df-121">Langage des expressions régulières - Aide-mémoire</span><span class="sxs-lookup"><span data-stu-id="f94df-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
