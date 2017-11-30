---
title: "Opérateurs conditionnels Null (C# et Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="49766-102">Opérateurs conditionnels Null (C# et Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49766-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="49766-103">Ces opérateurs sont utilisés pour rechercher les valeurs Null avant d'effectuer une opération d'accès au membre (`?.`) ou d'indexation (`?[`).</span><span class="sxs-lookup"><span data-stu-id="49766-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="49766-104">Ils permettent d'écrire moins de code pour gérer les vérifications Null, notamment pour l'exploration des structures de données.</span><span class="sxs-lookup"><span data-stu-id="49766-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="49766-105">Le dernier exemple montre que les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="49766-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="49766-106">Si une opération dans une chaîne d'opérations d'accès au membre et d'indexation conditionnelles retourne une valeur Null, l'exécution du reste de la chaîne s'arrête.</span><span class="sxs-lookup"><span data-stu-id="49766-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="49766-107">Les autres opérations ayant une priorité moins élevée dans l'expression continuent.</span><span class="sxs-lookup"><span data-stu-id="49766-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="49766-108">Dans l’exemple ci-dessous, `E` s’exécute à la seconde ligne, et les opérations `??` et `==` sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="49766-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="49766-109">Dans la première ligne, `??` court-circuite et `E` ne s’exécute pas quand la partie gauche à une valeur non null.</span><span class="sxs-lookup"><span data-stu-id="49766-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="49766-110">L'accès au membre conditionnel Null s'utilise également pour appeler des délégués de façon thread-safe, avec beaucoup moins de code.</span><span class="sxs-lookup"><span data-stu-id="49766-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="49766-111">Avec l'ancienne méthode, vous deviez utiliser un code similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="49766-111">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="49766-112">La nouvelle méthode est beaucoup plus simple :</span><span class="sxs-lookup"><span data-stu-id="49766-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="49766-113">La nouvelle méthode est thread-safe, car le compilateur génère du code qui évalue `PropertyChanged` une seule fois, en conservant le résultat dans une variable temporaire.</span><span class="sxs-lookup"><span data-stu-id="49766-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="49766-114">Vous devez explicitement appeler la méthode `Invoke`, car il n'existe pas de syntaxe d'appel de délégué conditionnel Null `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="49766-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="49766-115">Il y avait trop de situations d'analyse ambiguës pour pouvoir utiliser une telle syntaxe.</span><span class="sxs-lookup"><span data-stu-id="49766-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="49766-116">Spécifications du langage</span><span class="sxs-lookup"><span data-stu-id="49766-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="49766-117">Pour plus d’informations, consultez [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="49766-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49766-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49766-118">See Also</span></span>  
 [<span data-ttu-id="49766-119">?? (opérateur de fusion null)</span><span class="sxs-lookup"><span data-stu-id="49766-119">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="49766-120">Référence C#</span><span class="sxs-lookup"><span data-stu-id="49766-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="49766-121">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="49766-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="49766-122">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49766-122">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="49766-123">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49766-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
