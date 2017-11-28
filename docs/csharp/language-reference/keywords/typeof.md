---
title: "typeof (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a><span data-ttu-id="38cb3-102">typeof (référence C#)</span><span class="sxs-lookup"><span data-stu-id="38cb3-102">typeof (C# Reference)</span></span>
<span data-ttu-id="38cb3-103">Permet d’obtenir l’objet `System.Type` pour un type.</span><span class="sxs-lookup"><span data-stu-id="38cb3-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="38cb3-104">Une expression `typeof` prend la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="38cb3-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="38cb3-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="38cb3-105">Remarks</span></span>  
 <span data-ttu-id="38cb3-106">Pour obtenir le type au moment de l’exécution d’une expression, vous pouvez utiliser la méthode <xref:System.Object.GetType%2A> du .NET Framework, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="38cb3-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="38cb3-107">L’opérateur `typeof` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="38cb3-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="38cb3-108">L’opérateur `typeof` peut également être utilisé sur les types génériques ouverts.</span><span class="sxs-lookup"><span data-stu-id="38cb3-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="38cb3-109">Les types avec plusieurs paramètres de type doivent avoir le nombre approprié de virgules dans la spécification.</span><span class="sxs-lookup"><span data-stu-id="38cb3-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="38cb3-110">L’exemple suivant montre comment déterminer si le type de retour d’une méthode est un <xref:System.Collections.Generic.IEnumerable%601> générique.</span><span class="sxs-lookup"><span data-stu-id="38cb3-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="38cb3-111">Supposons que la méthode est une instance d’un type MethodInfo :</span><span class="sxs-lookup"><span data-stu-id="38cb3-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="38cb3-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="38cb3-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="38cb3-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="38cb3-113">Example</span></span>  
 <span data-ttu-id="38cb3-114">Cet exemple utilise la méthode <xref:System.Object.GetType%2A> pour déterminer le type utilisé pour contenir le résultat d’un calcul numérique.</span><span class="sxs-lookup"><span data-stu-id="38cb3-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="38cb3-115">Cela dépend des besoins de stockage du nombre résultant.</span><span class="sxs-lookup"><span data-stu-id="38cb3-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="38cb3-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="38cb3-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38cb3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38cb3-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="38cb3-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="38cb3-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="38cb3-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="38cb3-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="38cb3-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="38cb3-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="38cb3-121">is</span><span class="sxs-lookup"><span data-stu-id="38cb3-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="38cb3-122">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="38cb3-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
