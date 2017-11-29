---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a><span data-ttu-id="35bd5-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35bd5-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="35bd5-103">Indique qu’un opérateur de conversion (`CType`) convertit une classe ou structure en un type qui peut contenir toutes les valeurs possibles de la classe ou la structure d’origine.</span><span class="sxs-lookup"><span data-stu-id="35bd5-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="35bd5-104">Conversion avec le mot clé étendue</span><span class="sxs-lookup"><span data-stu-id="35bd5-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="35bd5-105">La procédure de conversion doit spécifier `Public Shared` à `Widening`.</span><span class="sxs-lookup"><span data-stu-id="35bd5-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="35bd5-106">Les conversions étendues réussissent toujours en cours d’exécution et sans jamais aucune perte de données.</span><span class="sxs-lookup"><span data-stu-id="35bd5-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="35bd5-107">Exemples `Single` à `Double`, `Char` à `String`et un type dérivé vers son type de base.</span><span class="sxs-lookup"><span data-stu-id="35bd5-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="35bd5-108">Cette dernière conversion est étendue parce que le type dérivé contient tous les membres du type de base et est donc une instance du type de base.</span><span class="sxs-lookup"><span data-stu-id="35bd5-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="35bd5-109">Le code utilisateur ne doit pas utiliser `CType` pour les conversions étendues, même si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="35bd5-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="35bd5-110">Le `Widening` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="35bd5-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="35bd5-111">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="35bd5-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="35bd5-112">Par exemple des définitions d’étendues et restrictives des opérateurs de conversion, consultez [Comment : définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="35bd5-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35bd5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35bd5-113">See Also</span></span>  
 [<span data-ttu-id="35bd5-114">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="35bd5-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="35bd5-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="35bd5-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="35bd5-116">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="35bd5-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="35bd5-117">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="35bd5-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="35bd5-118">CType (fonction)</span><span class="sxs-lookup"><span data-stu-id="35bd5-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="35bd5-119">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="35bd5-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="35bd5-120">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="35bd5-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
