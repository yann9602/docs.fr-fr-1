---
title: "Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- Grid control retargeting changes
ms.assetid: 707c064d-85e9-4ea1-aefb-e42b60b88679
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 54391538ac0b2daf307cba2f7ceff1984d26b0ce
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a><span data-ttu-id="b59c4-102">Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile</span><span class="sxs-lookup"><span data-stu-id="b59c4-102">Mitigation: Grid Control&#39;s Space Allocation to Star-columns</span></span>

<span data-ttu-id="b59c4-103">À compter des applications qui ciblent le .NET Framework 4.7, WPF remplace l’algorithme que le contrôle <xref:System.Windows.Controls.Grid> utilise pour allouer de l’espace aux colonnes \*.</span><span class="sxs-lookup"><span data-stu-id="b59c4-103">Starting with applications that the .NET Framework 4.7, WPF replaces the algorithm that the <xref:System.Windows.Controls.Grid> control uses to allocate space to \*-columns.</span></span> 

## <a name="whats-changed"></a><span data-ttu-id="b59c4-104">Nouveautés</span><span class="sxs-lookup"><span data-stu-id="b59c4-104">What's changed</span></span>

<span data-ttu-id="b59c4-105">Le nouvel algorithme résout plusieurs bogues présents dans l’ancien algorithme :</span><span class="sxs-lookup"><span data-stu-id="b59c4-105">The new algorithm fixes several bugs present in the old algorithm:</span></span>

1. <span data-ttu-id="b59c4-106">L’allocation totale à des colonnes peut dépasser la largeur de la grille.</span><span class="sxs-lookup"><span data-stu-id="b59c4-106">Total allocation to columns can exceed the Grid's width.</span></span> <span data-ttu-id="b59c4-107">Cela peut se produire lors de l’allocation d’espace pour une colonne dont la part proportionnelle est inférieure à sa taille minimale.</span><span class="sxs-lookup"><span data-stu-id="b59c4-107">This can occur when allocating space to a column whose proportional share is less than its minimum size.</span></span> <span data-ttu-id="b59c4-108">L’algorithme alloue la taille minimale, ce qui réduit l’espace disponible pour les autres colonnes.</span><span class="sxs-lookup"><span data-stu-id="b59c4-108">The algorithm allocates the minimum size, which decreases the space available to other columns.</span></span> <span data-ttu-id="b59c4-109">S’il ne reste aucune colonne \* à allouer, l’allocation totale est trop grande.</span><span class="sxs-lookup"><span data-stu-id="b59c4-109">If there are no \*-columns left to allocate, the total allocation will be too large.</span></span>

1. <span data-ttu-id="b59c4-110">L’allocation totale peut être inférieure à la largeur de la grille.</span><span class="sxs-lookup"><span data-stu-id="b59c4-110">Total allocation can fall short of the Grid's width.</span></span> <span data-ttu-id="b59c4-111">C’est le double problème pour #1, survenant lors de l’affectation à une colonne dont la part proportionnelle est supérieure à sa taille maximale, sans colonnes \* restantes pour combler.</span><span class="sxs-lookup"><span data-stu-id="b59c4-111">This is the dual problem to #1, arising when allocating to a column whose proportional share is greater than its maximum size, with no \*-columns left to take up the slack.</span></span>

1. <span data-ttu-id="b59c4-112">Deux colonnes \* peuvent recevoir des allocations non proportionnelles à leurs poids.</span><span class="sxs-lookup"><span data-stu-id="b59c4-112">Two \*-columns can receive allocations not proportional to their -weights.</span></span> <span data-ttu-id="b59c4-113">Il s’agit d’une version atténuée de #1/2, survenant lors de l’allocation aux colonnes * A, B et C (dans cet ordre), où la part proportionnelle de B ne respecte pas la contrainte min (ou max).</span><span class="sxs-lookup"><span data-stu-id="b59c4-113">This is a milder version of #1/#2, arising when allocating to *-columns A, B, and C (in that order), where B's proportional share violates its min (or max) constraint.</span></span> <span data-ttu-id="b59c4-114">Comme ci-dessus, cela modifie l’espace disponible pour la colonne C, qui obtient une allocation proportionnelle inférieure (ou supérieure) à A,</span><span class="sxs-lookup"><span data-stu-id="b59c4-114">As above, this changes the space available to column C, who gets less (or more) proportional allocation than A did,</span></span>

1. <span data-ttu-id="b59c4-115">Les colonnes avec des poids extrêmement volumineux (> 10 ^ 298) sont traitées comme si elles avaient un poids de 10 ^ 298.</span><span class="sxs-lookup"><span data-stu-id="b59c4-115">Columns with extremely large weights (> 10^298) are all treated as if they had weight 10^298.</span></span> <span data-ttu-id="b59c4-116">Les différences proportionnelles entre elles (et entre les colonnes avec des poids légèrement inférieurs) ne sont pas respectées.</span><span class="sxs-lookup"><span data-stu-id="b59c4-116">Proportional differences between them (and between columns with slightly smaller weights) are not honored.</span></span>

1. <span data-ttu-id="b59c4-117">Les colonnes avec des poids infinis ne sont pas gérées correctement.</span><span class="sxs-lookup"><span data-stu-id="b59c4-117">Columns with infinite weights are not handled correctly.</span></span> <span data-ttu-id="b59c4-118">[Il est en fait impossible de définir un poids infini, mais il s’agit d’une restriction artificielle.</span><span class="sxs-lookup"><span data-stu-id="b59c4-118">[Actually you can't set a weight to Infinity, but this is an artificial restriction.</span></span> <span data-ttu-id="b59c4-119">Le code d’allocation essayait de le gérer, sans succès.]</span><span class="sxs-lookup"><span data-stu-id="b59c4-119">The allocation code was trying to handle it, but doing a bad job.]</span></span>

1. <span data-ttu-id="b59c4-120">Plusieurs problèmes mineurs en évitant le dépassement de capacité positif ou négatif, la perte de précision et autres problèmes liées aux nombres à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="b59c4-120">Several minor problems while avoiding overflow, underflow, loss of precision and similar floating-point issues.</span></span>

1. <span data-ttu-id="b59c4-121">Les ajustements d’arrondi de disposition sont incorrects à un niveau de PPP suffisamment élevé.</span><span class="sxs-lookup"><span data-stu-id="b59c4-121">Adjustments for layout rounding are incorrect at sufficiently high DPI.</span></span>

<span data-ttu-id="b59c4-122">Le nouvel algorithme produit des résultats qui répondent aux critères suivants :</span><span class="sxs-lookup"><span data-stu-id="b59c4-122">The new algorithm produces results that meet the following criteria:</span></span>

<span data-ttu-id="b59c4-123">Un fichier .</span><span class="sxs-lookup"><span data-stu-id="b59c4-123">A.</span></span> <span data-ttu-id="b59c4-124">La largeur réelle affectée à une colonne * n’est jamais inférieure à sa largeur minimale ni supérieure à sa largeur maximale.</span><span class="sxs-lookup"><span data-stu-id="b59c4-124">The actual width assigned to a *-column is never less than its minimum width nor greater than its maximum width.</span></span>

<span data-ttu-id="b59c4-125">B.</span><span class="sxs-lookup"><span data-stu-id="b59c4-125">B.</span></span> <span data-ttu-id="b59c4-126">Chaque colonne qui n’a pas de largeur minimale ou maximale affectée reçoit une largeur proportionnelle à son poids.</span><span class="sxs-lookup"><span data-stu-id="b59c4-126">Each -column that is not assigned its minimum or maximum width is assigned a width proportional to its -weight.</span></span> <span data-ttu-id="b59c4-127">Pour être exact, si deux colonnes sont déclarées avec les largeurs x et y, respectivement, et qu’aucune colonne ne reçoit sa largeur minimale ou maximale, les largeurs effectives v et w affectées aux colonnes respectent les mêmes proportions : v / w == x / y.</span><span class="sxs-lookup"><span data-stu-id="b59c4-127">To be precise, if two columns are declared with width x and y respectively, and if neither column receives its minimum or maximum width, the actual widths v and w assigned to the columns are in the same proportion: v / w == x / y.</span></span>

<span data-ttu-id="b59c4-128">C.</span><span class="sxs-lookup"><span data-stu-id="b59c4-128">C.</span></span> <span data-ttu-id="b59c4-129">La largeur totale allouée aux colonnes \* proportionnelles est égale à l’espace disponible après avoir alloué les colonnes avec contrainte (les colonnes fixes, auto, et \* affectées à leur largeur min ou max).</span><span class="sxs-lookup"><span data-stu-id="b59c4-129">The total width allocated to "proportional" \*-columns is equal to the space available after allocating to the constrained columns (fixed, auto, and \*-columns that are allocated their min or max width).</span></span> <span data-ttu-id="b59c4-130">Cela peut être égal à zéro, par exemple si la somme des largeurs minimales dépasse la largeur disponible de la grille.</span><span class="sxs-lookup"><span data-stu-id="b59c4-130">This might be zero, for instance if the sum of the minimum widths exceeds the Grid's availbable width.</span></span>

<span data-ttu-id="b59c4-131">D.</span><span class="sxs-lookup"><span data-stu-id="b59c4-131">D.</span></span> <span data-ttu-id="b59c4-132">Toutes ces instructions doivent être interprétées en considérant la mise en page « idéale ».</span><span class="sxs-lookup"><span data-stu-id="b59c4-132">All these statements are to be interpreted with respect to the "ideal" layout.</span></span> <span data-ttu-id="b59c4-133">Lorsque l’arrondi de disposition est activé, la largeur réelle peut différer de la largeur idéale jusqu’à un pixel.</span><span class="sxs-lookup"><span data-stu-id="b59c4-133">When layout rounding is in effect, the actual widths can differ from the ideal widths by as much as one pixel.</span></span>

<span data-ttu-id="b59c4-134">L’ancien algorithme respectait (A), sans pouvoir en faire autant pour les autres critères dans les cas présentés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b59c4-134">The old algorithm honored (A) but failed to honor the other criteria in the cases outlined above.</span></span>

<span data-ttu-id="b59c4-135">Tout ce que qui a été évoqué sur les colonnes et les largeurs dans cette rubrique s’applique également aux lignes et leurs hauteurs.</span><span class="sxs-lookup"><span data-stu-id="b59c4-135">Everything said about columns and widths in this topic applies as well to rows and heights.</span></span>

## <a name="impact"></a><span data-ttu-id="b59c4-136">Impact</span><span class="sxs-lookup"><span data-stu-id="b59c4-136">Impact</span></span>

<span data-ttu-id="b59c4-137">Le nouvel algorithme modifie la largeur réelle affectée aux colonnes \* dans plusieurs cas :</span><span class="sxs-lookup"><span data-stu-id="b59c4-137">The new algorithm changes the actual width assigned to \*-columns in a number of cases:</span></span>

- <span data-ttu-id="b59c4-138">Lorsqu’une ou plusieurs colonnes \* ont également une largeur minimale ou maximale qui remplace l’allocation proportionnelle pour cette colonne.</span><span class="sxs-lookup"><span data-stu-id="b59c4-138">When one or more \*-columns also have a minimum or maximum width that overrides the proportional allocation for that column.</span></span> <span data-ttu-id="b59c4-139">(La largeur minimale peut dériver d’une déclaration <xref:System.Windows.FrameworkElement.MinWidth%2A> explicite, ou d’un minimum implicite obtenu à partir du contenu de la colonne.</span><span class="sxs-lookup"><span data-stu-id="b59c4-139">(The minimum width can derive from an explicit <xref:System.Windows.FrameworkElement.MinWidth%2A> declaration, or from an implicit minimum obtained from the column's content.</span></span> <span data-ttu-id="b59c4-140">La largeur maximale ne peut être définie qu’explicitement, à partir d’une déclaration <xref:System.Windows.FrameworkElement.MaxWidth%2A>.)</span><span class="sxs-lookup"><span data-stu-id="b59c4-140">The maximum width can only be defined explicitly, from a <xref:System.Windows.FrameworkElement.MaxWidth%2A> declaration.)</span></span>

- <span data-ttu-id="b59c4-141">Lorsqu’une ou plusieurs colonnes \* déclarent un très grand poids \*, supérieur à 10 ^ 298.</span><span class="sxs-lookup"><span data-stu-id="b59c4-141">When one or more \*-columns declare an extremely large \*-weight, greater than 10^298.</span></span>

- <span data-ttu-id="b59c4-142">Lorsque les poids \* sont suffisamment différents pour rencontrer une instabilité du calcul en virgule flottante (dépassement de capacité positif ou négatif, perte de précision).</span><span class="sxs-lookup"><span data-stu-id="b59c4-142">When the \*-weights are sufficiently different to encounter floating-point instability (overflow, underflow, loss of precision).</span></span>

- <span data-ttu-id="b59c4-143">Lorsque l’arrondi de disposition est activé, et que la résolution d’affichage efficace en PPP est suffisamment élevée.</span><span class="sxs-lookup"><span data-stu-id="b59c4-143">When layout rounding is enabled, and the effective display DPI is sufficiently high.</span></span>

<span data-ttu-id="b59c4-144">Dans les deux premiers cas, les largeurs produites par le nouvel algorithme peuvent être considérablement différentes de celles générées par l’ancien algorithme ; dans le dernier cas, la différence sera au plus de un ou deux pixels.</span><span class="sxs-lookup"><span data-stu-id="b59c4-144">In the first two cases, the widths produced by the new algorithm can be significantly different from those produced by the old algorithm; in the last case, the difference will be at most one or two pixels.</span></span>

## <a name="mitigation"></a><span data-ttu-id="b59c4-145">Atténuation</span><span class="sxs-lookup"><span data-stu-id="b59c4-145">Mitigation</span></span>

<span data-ttu-id="b59c4-146">Par défaut, les applications qui ciblent les versions de .NET Framework ultérieures à .NET Framework 4.7 utiliseront le nouvel algorithme, tandis que les applications qui ciblent .NET Framework 4.6.2 ou versions antérieures utiliseront l’ancien algorithme.</span><span class="sxs-lookup"><span data-stu-id="b59c4-146">By default, apps that target versions of the .NET Framework starting with the .NET Framework 4.7 will use the new algorithm, while apps that target the .NET Framework 4.6.2 or earlier versions will use the old algorithm.</span></span>

<span data-ttu-id="b59c4-147">Pour remplacer la valeur par défaut, utilisez les paramètres de configuration suivants :</span><span class="sxs-lookup"><span data-stu-id="b59c4-147">To override the default, use the following configuration setting:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

<span data-ttu-id="b59c4-148">La valeur true sélectionne l’ancien algorithme, et false le nouvel algorithme.</span><span class="sxs-lookup"><span data-stu-id="b59c4-148">The value 'true' selects the old algorithm, and 'false' selects the new algorithm.</span></span>

## <a name="see-also"></a><span data-ttu-id="b59c4-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b59c4-149">See also</span></span>
[<span data-ttu-id="b59c4-150">Reciblage des modifications dans le .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b59c4-150">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

