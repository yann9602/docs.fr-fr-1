---
title: "Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
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
translationtype: Human Translation
ms.sourcegitcommit: 9460c8b6ca8db927af4064e3567eca34c1bf5c91
ms.openlocfilehash: c7acce9d41af7e72b04b89751a7b186c9581dfea
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-grid-control39s-space-allocation-to-star-columns"></a>Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile

À compter des applications qui ciblent .NET Framework 4.7, WPF remplace l’algorithme que le contrôle <xref:System.Windows.Controls.Grid> utilise pour allouer de l’espace aux colonnes \*. 

## <a name="whats-changed"></a>Nouveautés

Le nouvel algorithme résout plusieurs bogues présents dans l’ancien algorithme :

1. L’allocation totale à des colonnes peut dépasser la largeur de la grille. Cela peut se produire lors de l’allocation d’espace pour une colonne dont la part proportionnelle est inférieure à sa taille minimale. L’algorithme alloue la taille minimale, ce qui réduit l’espace disponible pour les autres colonnes. S’il ne reste aucune colonne \* à allouer, l’allocation totale est trop grande.

1. L’allocation totale peut être inférieure à la largeur de la grille. C’est le double problème pour #1, survenant lors de l’affectation à une colonne dont la part proportionnelle est supérieure à sa taille maximale, sans colonnes \* restantes pour combler.

1. Deux colonnes \* peuvent recevoir des allocations non proportionnelles à leurs poids. Il s’agit d’une version atténuée de #1/2, survenant lors de l’allocation aux colonnes * A, B et C (dans cet ordre), où la part proportionnelle de B ne respecte pas la contrainte min (ou max). Comme ci-dessus, cela modifie l’espace disponible pour la colonne C, qui obtient une allocation proportionnelle inférieure (ou supérieure) à A,

1. Les colonnes avec des poids extrêmement volumineux (> 10 ^ 298) sont traitées comme si elles avaient un poids de 10 ^ 298. Les différences proportionnelles entre elles (et entre les colonnes avec des poids légèrement inférieurs) ne sont pas respectées.

1. Les colonnes avec des poids infinis ne sont pas gérées correctement. [Il est en fait impossible de définir un poids infini, mais il s’agit d’une restriction artificielle. Le code d’allocation essayait de le gérer, sans succès.]

1. Plusieurs problèmes mineurs en évitant le dépassement de capacité positif ou négatif, la perte de précision et autres problèmes liées aux nombres à virgule flottante.

1. Les ajustements d’arrondi de disposition sont incorrects à un niveau de PPP suffisamment élevé.

Le nouvel algorithme produit des résultats qui répondent aux critères suivants :

Un fichier . La largeur réelle affectée à une colonne * n’est jamais inférieure à sa largeur minimale ni supérieure à sa largeur maximale.

B. Chaque colonne qui n’a pas de largeur minimale ou maximale affectée reçoit une largeur proportionnelle à son poids. Pour être exact, si deux colonnes sont déclarées avec les largeurs x et y, respectivement, et qu’aucune colonne ne reçoit sa largeur minimale ou maximale, les largeurs effectives v et w affectées aux colonnes respectent les mêmes proportions : v / w == x / y.

C. La largeur totale allouée aux colonnes \* proportionnelles est égale à l’espace disponible après avoir alloué les colonnes avec contrainte (les colonnes fixes, auto, et \* affectées à leur largeur min ou max). Cela peut être égal à zéro, par exemple si la somme des largeurs minimales dépasse la largeur disponible de la grille.

D. Toutes ces instructions doivent être interprétées en considérant la mise en page « idéale ». Lorsque l’arrondi de disposition est activé, la largeur réelle peut différer de la largeur idéale jusqu’à un pixel.

L’ancien algorithme respectait (A), sans pouvoir en faire autant pour les autres critères dans les cas présentés ci-dessus.

Tout ce que qui a été évoqué sur les colonnes et les largeurs dans cette rubrique s’applique également aux lignes et leurs hauteurs.

## <a name="impact"></a>Impact

Le nouvel algorithme modifie la largeur réelle affectée aux colonnes \* dans plusieurs cas :

- Lorsqu’une ou plusieurs colonnes \* ont également une largeur minimale ou maximale qui remplace l’allocation proportionnelle pour cette colonne. (La largeur minimale peut dériver d’une déclaration <xref:System.Windows.FrameworkElement.MinWidth%2A> explicite, ou d’un minimum implicite obtenu à partir du contenu de la colonne. La largeur maximale ne peut être définie qu’explicitement, par une déclaration <xref:System.Windows.FrameworkElement.MaxWidth%2A>.)

- Lorsqu’une ou plusieurs colonnes \* déclarent un très grand poids \*, supérieur à 10 ^ 298.

- Lorsque les poids \* sont suffisamment différents pour rencontrer une instabilité du calcul en virgule flottante (dépassement de capacité positif ou négatif, perte de précision).

- Lorsque l’arrondi de disposition est activé, et que la résolution d’affichage efficace en PPP est suffisamment élevée.

Dans les deux premiers cas, les largeurs produites par le nouvel algorithme peuvent être considérablement différentes de celles générées par l’ancien algorithme ; dans le dernier cas, la différence sera au plus de un ou deux pixels.

## <a name="mitigation"></a>Atténuation

Par défaut, les applications qui ciblent les versions de .NET Framework ultérieures à .NET Framework 4.7 utiliseront le nouvel algorithme, tandis que les applications qui ciblent .NET Framework 4.6.2 ou versions antérieures utiliseront l’ancien algorithme.

Pour remplacer la valeur par défaut, utilisez les paramètres de configuration suivants :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true" /> 
</runtime>
```

La valeur true sélectionne l’ancien algorithme, et false le nouvel algorithme.

## <a name="see-also"></a>Voir aussi
[Reciblage des modifications dans le .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

