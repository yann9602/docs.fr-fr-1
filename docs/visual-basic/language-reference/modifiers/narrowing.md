---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="32e9b-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32e9b-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="32e9b-103">Indique qu’un opérateur de conversion (`CType`) convertit une classe ou structure en un type qui peut ne pas pouvoir contenir certaines des valeurs possibles de la classe ou la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="32e9b-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="32e9b-104">Conversion avec le mot clé restrictive</span><span class="sxs-lookup"><span data-stu-id="32e9b-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="32e9b-105">La procédure de conversion doit spécifier `Public Shared` à `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="32e9b-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="32e9b-106">Les conversions restrictives ne pas toujours réussisse au moment de l’exécution et peut échouer ou entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="32e9b-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="32e9b-107">Exemples `Long` à `Integer`, `String` à `Date`et un type de base en un type dérivé.</span><span class="sxs-lookup"><span data-stu-id="32e9b-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="32e9b-108">Cette dernière conversion est restrictive parce que le type de base ne peut pas contenir tous les membres du type dérivé et n’est donc pas une instance du type dérivé.</span><span class="sxs-lookup"><span data-stu-id="32e9b-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="32e9b-109">Si `Option Strict` est `On`, le code utilisateur doit utiliser `CType` pour toutes les conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="32e9b-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="32e9b-110">Le `Narrowing` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="32e9b-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="32e9b-111">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="32e9b-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="32e9b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32e9b-112">See Also</span></span>  
 [<span data-ttu-id="32e9b-113">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="32e9b-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="32e9b-114">Widening</span><span class="sxs-lookup"><span data-stu-id="32e9b-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="32e9b-115">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="32e9b-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="32e9b-116">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="32e9b-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="32e9b-117">CType (fonction)</span><span class="sxs-lookup"><span data-stu-id="32e9b-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="32e9b-118">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="32e9b-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
