---
title: "L’expression est le type de &#39; &lt;typename&gt;&#39; qui est un type restreint et ne peut pas être utilisé pour accéder aux membres hérités de &#39; objet &#39; ou &#39; ValueType &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords: BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30742bd46ccd1a3e5a688ebd2621e2c8a3d50e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a><span data-ttu-id="a06a3-102">L’expression est le type de &#39; &lt;typename&gt;&#39; qui est un type restreint et ne peut pas être utilisé pour accéder aux membres hérités de &#39; objet &#39; ou &#39; ValueType &#39;</span><span class="sxs-lookup"><span data-stu-id="a06a3-102">Expression has the type &#39;&lt;typename&gt;&#39; which is a restricted type and cannot be used to access members inherited from &#39;Object&#39; or &#39;ValueType&#39;</span></span>
<span data-ttu-id="a06a3-103">Une expression est évaluée à un type qui ne peut pas être convertie (boxed) par le common language runtime (CLR) mais accède à un membre qui nécessite une conversion boxing.</span><span class="sxs-lookup"><span data-stu-id="a06a3-103">An expression evaluates to a type that cannot be boxed by the common language runtime (CLR) but accesses a member that requires boxing.</span></span>  
  
 <span data-ttu-id="a06a3-104">Le*boxing* est le traitement nécessaire à la conversion d’un type en `Object` ou, à l’occasion, en <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="a06a3-104">*Boxing* refers to the processing necessary to convert a type to `Object` or, on occasion, to <xref:System.ValueType>.</span></span> <span data-ttu-id="a06a3-105">Le common language runtime ne peut pas convertir certains types de structure, par exemple <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, et <xref:System.TypedReference>.</span><span class="sxs-lookup"><span data-stu-id="a06a3-105">The common language runtime cannot box certain structure types, for example <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, and <xref:System.TypedReference>.</span></span>  
  
 <span data-ttu-id="a06a3-106">Cette expression tente d’utiliser le type restreint pour appeler une méthode héritée <xref:System.Object> ou <xref:System.ValueType>, tel que <xref:System.Object.GetHashCode%2A> ou <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="a06a3-106">This expression attempts to use the restricted type to call a method inherited from <xref:System.Object> or <xref:System.ValueType>, such as <xref:System.Object.GetHashCode%2A> or <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="a06a3-107">Pour accéder à cette méthode, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] a tenté une conversion boxing implicite qui provoque cette erreur.</span><span class="sxs-lookup"><span data-stu-id="a06a3-107">To access this method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] has attempted an implicit boxing conversion that causes this error.</span></span>  
  
 <span data-ttu-id="a06a3-108">**ID d’erreur :** BC31393</span><span class="sxs-lookup"><span data-stu-id="a06a3-108">**Error ID:** BC31393</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a06a3-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a06a3-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="a06a3-110">Recherchez l’expression évaluée comme étant le type cité.</span><span class="sxs-lookup"><span data-stu-id="a06a3-110">Locate the expression that evaluates to the cited type.</span></span>  
  
2.  <span data-ttu-id="a06a3-111">Recherchez la partie de votre instruction qui essaie d’appeler la méthode héritée <xref:System.Object> ou <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="a06a3-111">Locate the part of your statement that attempts to call the method inherited from <xref:System.Object> or <xref:System.ValueType>.</span></span>  
  
3.  <span data-ttu-id="a06a3-112">Réécrivez l’instruction pour éviter l’appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="a06a3-112">Rewrite the statement to avoid the method call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06a3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a06a3-113">See Also</span></span>  
 [<span data-ttu-id="a06a3-114">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="a06a3-114">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
