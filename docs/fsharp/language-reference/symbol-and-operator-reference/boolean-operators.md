---
title: "Opérateurs booléens (F#)"
description: "Obtenir des informations sur les opérateurs booléens sont disponibles dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="2446c-104">Opérateurs booléens</span><span class="sxs-lookup"><span data-stu-id="2446c-104">Boolean Operators</span></span>

<span data-ttu-id="2446c-105">Cette rubrique décrit la prise en charge des opérateurs booléens dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="2446c-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="2446c-106">Résumé des opérateurs booléens</span><span class="sxs-lookup"><span data-stu-id="2446c-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="2446c-107">Le tableau suivant récapitule les opérateurs booléens sont disponibles dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="2446c-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="2446c-108">Le seul type pris en charge par ces opérateurs est le `bool` type.</span><span class="sxs-lookup"><span data-stu-id="2446c-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="2446c-109">Opérateur</span><span class="sxs-lookup"><span data-stu-id="2446c-109">Operator</span></span>|<span data-ttu-id="2446c-110">Description</span><span class="sxs-lookup"><span data-stu-id="2446c-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="2446c-111">Négation booléenne</span><span class="sxs-lookup"><span data-stu-id="2446c-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="2446c-112">Booléen OR</span><span class="sxs-lookup"><span data-stu-id="2446c-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="2446c-113">Booléen AND</span><span class="sxs-lookup"><span data-stu-id="2446c-113">Boolean AND</span></span>|

<span data-ttu-id="2446c-114">Les opérateurs booléens AND et OR effectuent *l’évaluation de court-circuit*, autrement dit, elles évaluent l’expression à droite de l’opérateur uniquement lorsqu’il est nécessaire de déterminer le résultat global de l’expression.</span><span class="sxs-lookup"><span data-stu-id="2446c-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="2446c-115">La deuxième expression de la `&&` opérateur est évalué uniquement si la première expression a la valeur `true`; la deuxième expression de la `||` opérateur est évalué uniquement si la première expression a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="2446c-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2446c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2446c-116">See Also</span></span>
[<span data-ttu-id="2446c-117">Opérateurs au niveau du bit</span><span class="sxs-lookup"><span data-stu-id="2446c-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="2446c-118">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="2446c-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="2446c-119">Informations de référence des symboles et opérateurs</span><span class="sxs-lookup"><span data-stu-id="2446c-119">Symbol and Operator Reference</span></span>](index.md)
