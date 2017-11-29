---
title: "&#39; &lt;expression&gt;&#39; ne peut pas être utilisé comme contrainte de type"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords: BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 054c05747491afb02601df00225a703560cbe91c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="57d05-102">&#39; &lt;expression&gt;&#39; ne peut pas être utilisé comme contrainte de type</span><span class="sxs-lookup"><span data-stu-id="57d05-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="57d05-103">Une liste de contraintes contient une expression qui ne représente pas une contrainte valide sur un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="57d05-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="57d05-104">Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="57d05-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="57d05-105">Vous pouvez spécifier les exigences suivantes dans toute combinaison :</span><span class="sxs-lookup"><span data-stu-id="57d05-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="57d05-106">L’argument de type doit implémenter une ou plusieurs interfaces</span><span class="sxs-lookup"><span data-stu-id="57d05-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="57d05-107">L’argument de type doit hériter d’une classe au plus</span><span class="sxs-lookup"><span data-stu-id="57d05-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="57d05-108">L’argument de type doit exposer un constructeur sans paramètre accessible par le code de création (ajoutez la contrainte `New` )</span><span class="sxs-lookup"><span data-stu-id="57d05-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="57d05-109">Si vous n’incluez pas de classe ni d’interface spécifique dans la liste de contraintes, vous pouvez imposer une condition plus générale en spécifiant l’une des obligations suivantes :</span><span class="sxs-lookup"><span data-stu-id="57d05-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="57d05-110">L’argument de type doit être un type valeur (ajoutez la contrainte `Structure` )</span><span class="sxs-lookup"><span data-stu-id="57d05-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="57d05-111">L’argument de type doit être un type référence (ajoutez la contrainte `Class` )</span><span class="sxs-lookup"><span data-stu-id="57d05-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="57d05-112">Vous ne pouvez pas spécifier à la fois `Structure` et `Class` pour le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="57d05-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="57d05-113">**ID d’erreur :** BC32061</span><span class="sxs-lookup"><span data-stu-id="57d05-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57d05-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="57d05-114">To correct this error</span></span>  
  
-   <span data-ttu-id="57d05-115">Vérifiez que l’expression et ses éléments sont correctement orthographiés.</span><span class="sxs-lookup"><span data-stu-id="57d05-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="57d05-116">Si l’expression ne répond pas à la précédente liste d’exigences, supprimez-la de la liste des contraintes.</span><span class="sxs-lookup"><span data-stu-id="57d05-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="57d05-117">Si l’expression fait référence à une interface ou une classe, vérifiez que le compilateur a accès à cette interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="57d05-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="57d05-118">Vous devrez peut-être qualifier son nom et ajouter une référence à votre projet.</span><span class="sxs-lookup"><span data-stu-id="57d05-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="57d05-119">Pour plus d’informations, consultez « Références aux projets » dans [références aux éléments de déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="57d05-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d05-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57d05-120">See Also</span></span>  
 [<span data-ttu-id="57d05-121">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57d05-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="57d05-122">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="57d05-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="57d05-123">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="57d05-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="57d05-124">NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="57d05-124">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
