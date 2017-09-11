---
title: "typeof (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
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
ms.openlocfilehash: fdb335e44a5a3634520d3a86495a4508597b4f70
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="typeof-c-reference"></a><span data-ttu-id="419f8-102">typeof (référence C#)</span><span class="sxs-lookup"><span data-stu-id="419f8-102">typeof (C# Reference)</span></span>
<span data-ttu-id="419f8-103">Permet d’obtenir l’objet `System.Type` pour un type.</span><span class="sxs-lookup"><span data-stu-id="419f8-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="419f8-104">Une expression `typeof` prend la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="419f8-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="419f8-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="419f8-105">Remarks</span></span>  
 <span data-ttu-id="419f8-106">Pour obtenir le type au moment de l’exécution d’une expression, vous pouvez utiliser la méthode <xref:System.Object.GetType%2A> du .NET Framework, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="419f8-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="419f8-107">L’opérateur `typeof` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="419f8-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="419f8-108">L’opérateur `typeof` peut également être utilisé sur les types génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="419f8-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="419f8-109">Les types avec plusieurs paramètres de type doivent avoir le nombre approprié de virgules dans la spécification.</span><span class="sxs-lookup"><span data-stu-id="419f8-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="419f8-110">L’exemple suivant montre comment déterminer si le type de retour d’une méthode est un <xref:System.Collections.Generic.IEnumerable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="419f8-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="419f8-111">Supposons que la méthode est une instance d’un type MethodInfo :</span><span class="sxs-lookup"><span data-stu-id="419f8-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="419f8-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="419f8-112">Example</span></span>  
 <span data-ttu-id="419f8-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="419f8-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="419f8-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="419f8-114">Example</span></span>  
 <span data-ttu-id="419f8-115">Cet exemple utilise la méthode <xref:System.Object.GetType%2A> pour déterminer le type utilisé pour contenir le résultat d’un calcul numérique.</span><span class="sxs-lookup"><span data-stu-id="419f8-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="419f8-116">Cela dépend des besoins de stockage du nombre résultant.</span><span class="sxs-lookup"><span data-stu-id="419f8-116">This depends on the storage requirements of the resulting number.</span></span>  
  
 <span data-ttu-id="419f8-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="419f8-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="419f8-118">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="419f8-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="419f8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="419f8-119">See Also</span></span>  
 <span data-ttu-id="419f8-120"><xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="419f8-120"><xref:System.Type?displayProperty=fullName></span></span>   
 <span data-ttu-id="419f8-121">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="419f8-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="419f8-122">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="419f8-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="419f8-123">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="419f8-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="419f8-124">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="419f8-124">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 [<span data-ttu-id="419f8-125">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="419f8-125">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

