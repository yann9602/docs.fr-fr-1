---
title: "Comment : tester l'égalité des références (Identité) (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2dbbd7c0e5ebb507ca3dda0f248d9f1c8f9595fe
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="769d3-102">Comment : tester l'égalité des références (Identité) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="769d3-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="769d3-103">Il n’est pas utile d’implémenter une logique personnalisée pour prendre en charge les comparaisons d’égalité de références dans vos types.</span><span class="sxs-lookup"><span data-stu-id="769d3-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="769d3-104">Cette fonctionnalité est fournie pour tous les types par la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> statique.</span><span class="sxs-lookup"><span data-stu-id="769d3-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="769d3-105">L’exemple suivant montre comment déterminer si deux variables affichent une *égalité de références*, à savoir qu’elles font référence à un même objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="769d3-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="769d3-106">L’exemple montre aussi pourquoi <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> retourne toujours `false` pour les types valeur et pourquoi vous ne devez pas utiliser <xref:System.Object.ReferenceEquals%2A> pour déterminer l’égalité de chaînes.</span><span class="sxs-lookup"><span data-stu-id="769d3-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="769d3-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="769d3-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 <span data-ttu-id="769d3-108">L’implémentation de `Equals` dans la classe de base universelle <xref:System.Object?displayProperty=nameWithType> assure aussi une vérification de l’égalité de références, mais il est préférable de ne pas l’utiliser, car si une classe se substitue à la méthode, vous risquez d’obtenir des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="769d3-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="769d3-109">Il en va de même pour les opérateurs `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="769d3-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="769d3-110">Quand ils s’appliquent à des types référence, le comportement par défaut de == et `!=` consiste à effectuer une vérification de l’égalité de références.</span><span class="sxs-lookup"><span data-stu-id="769d3-110">When they are operating on reference types, the default behavior of == and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="769d3-111">Cependant, les classes dérivées peuvent surcharger l’opérateur pour effectuer une vérification d’égalité de valeurs.</span><span class="sxs-lookup"><span data-stu-id="769d3-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="769d3-112">Pour réduire le risque d’erreurs, il est recommandé d’utiliser systématiquement <xref:System.Object.ReferenceEquals%2A> quand il s’agit de déterminer si deux objets présentent une égalité de références.</span><span class="sxs-lookup"><span data-stu-id="769d3-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="769d3-113">Les chaînes constantes au sein d’un même assembly sont toujours intégrées par le runtime.</span><span class="sxs-lookup"><span data-stu-id="769d3-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="769d3-114">Autrement dit, une seule instance de chaque chaîne littérale unique est conservée.</span><span class="sxs-lookup"><span data-stu-id="769d3-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="769d3-115">En revanche, le runtime ne garantit pas que les chaînes créées au moment de l’exécution sont intégrées, ni que deux chaînes constantes égales d’assemblys différents sont intégrées.</span><span class="sxs-lookup"><span data-stu-id="769d3-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769d3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="769d3-116">See Also</span></span>  
 [<span data-ttu-id="769d3-117">Comparaisons d’égalité</span><span class="sxs-lookup"><span data-stu-id="769d3-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
