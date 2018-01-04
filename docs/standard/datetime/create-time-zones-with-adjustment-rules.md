---
title: "Comment : créer des fuseaux horaires avec des règles d’ajustement"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eddc1d400f5f63cb2790fc4c660b70ebfdd0efc1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Comment : créer des fuseaux horaires avec des règles d’ajustement

Les informations de fuseau horaire précises requises par une application ne peuvent pas être présentes sur un système particulier pour plusieurs raisons :

* Le fuseau horaire n’a jamais été défini dans le Registre du système local.

* Données sur le fuseau horaire a été modifiées ou supprimées à partir du Registre.

* Le fuseau horaire ne dispose pas des informations précises sur l’ajustement de fuseau horaire pour une période donnée.

Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application. Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement. Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements avec deux règles d’ajustement fixe ou flottant. (Pour les définitions de ces termes, consultez la section « Terminologie de fuseau horaire » dans [vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Fuseaux horaires personnalisés créés en appelant le <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode ne sont pas ajoutés au Registre. Au lieu de cela, ils sont accessibles uniquement par le biais de la référence d’objet retournée par la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appel de méthode.

Cette rubrique montre comment créer un fuseau horaire avec des règles d’ajustement. Pour créer un fuseau horaire qui ne prend pas en charge les règles d’ajustement de l’heure d’été, consultez [Comment : créer des fuseaux horaires sans règles ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Pour créer un fuseau horaire avec flottante des règles d’ajustement

1. Pour chaque ajustement (c'est-à-dire, pour chaque transition d’et heure standard pour revenir sur un intervalle de temps particulier), procédez comme suit :

    1. Définir la durée de transition de départ pour l’ajustement de fuseau horaire.

       Vous devez appeler la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> méthode et lui passer une <xref:System.DateTime> valeur qui définit la durée de la transition, une valeur entière qui définit le mois de la transition, une valeur entière qui définit la semaine où la transition se produit, et un <xref:System.DayOfWeek> valeur qui définit le jour de la semaine où la transition se produit. Cet appel de méthode instancie un <xref:System.TimeZoneInfo.TransitionTime> objet.

    2. Définir la durée de transition de fin de l’ajustement de fuseau horaire. Cela nécessite un autre appel à la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> (méthode). Cet appel de méthode instancie une seconde <xref:System.TimeZoneInfo.TransitionTime> objet.

    3. Appelez le <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> (méthode) et lui passer la date de début effective et de fin de l’ajustement, un <xref:System.TimeSpan> objet qui définit la durée de la transition et les deux <xref:System.TimeZoneInfo.TransitionTime> objets qui définissent quand les transitions vers et à partir de l’heure d’été temps se produisent. Cet appel de méthode instancie un <xref:System.TimeZoneInfo.AdjustmentRule> objet.

    4. Affecter le <xref:System.TimeZoneInfo.AdjustmentRule> objet vers un tableau de <xref:System.TimeZoneInfo.AdjustmentRule> objets.

2. Définir le nom d’affichage du fuseau horaire. Le nom complet respecte un format relativement standard dans lequel l’offset du fuseau horaire par rapport au temps universel coordonné (UTC) est placée entre parenthèses et est suivie par une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes dans le fuseau horaire, ou l’un ou plusieurs du parmi gra ou des régions dans le fuseau horaire.

3. Définir le nom de l’heure d’hiver du fuseau horaire. En règle générale, cette chaîne est également utilisée comme identificateur de fuseau horaire.

4. Définir le nom de l’heure d’été du fuseau horaire.

5. Si vous souhaitez utiliser un autre identificateur que le nom de standard du fuseau horaire, définissez l’identificateur de fuseau horaire.

6. Instancier une <xref:System.TimeSpan> objet qui définit le décalage du fuseau horaire à l’heure UTC. Fuseaux horaires avec les heures sont ultérieures à l’heure UTC présentent un offset positif. Fuseaux horaires avec les heures sont antérieures à l’heure UTC présentent un offset négatif.

7. Appelez le <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.

## <a name="example"></a>Exemple

L’exemple suivant définit un fuseau horaire Standard Central pour les États-Unis qui inclut des règles d’ajustement pour une variété d’intervalles de temps à partir de 1918 du présent.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Le fuseau horaire créé dans cet exemple comporte plusieurs règles d’ajustement. Veillez à vous assurer que les dates de fin de toute règle d’ajustement de début et de fin ne se chevauchent pas avec les dates d’une autre règle d’ajustement. S’il existe un chevauchement, un <xref:System.InvalidTimeZoneException> est levée.

Pour les règles d’ajustement de date flottante, la valeur 5 est passée à la `week` paramètre de la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> méthode pour indiquer que la transition se produit la dernière semaine d’un mois donné.

Dans la création d’un tableau de <xref:System.TimeZoneInfo.AdjustmentRule> objets à utiliser dans le <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> appel de méthode, le code peut initialiser le tableau à la taille requise par le nombre d’ajustements à créer pour le fuseau horaire. Au lieu de cela, cet exemple de code appelle la <xref:System.Collections.Generic.List%601.Add%2A> méthode pour ajouter chaque règle d’ajustement générique <xref:System.Collections.Generic.List%601> collection de <xref:System.TimeZoneInfo.AdjustmentRule> objets. Le code appelle ensuite la <xref:System.Collections.Generic.List%601.CopyTo%2A> méthode pour copier les membres de cette collection dans le tableau.

L’exemple utilise également la <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> méthode pour définir des ajustements de date fixe. Cela ressemble à appeler le <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> (méthode), à ceci près qu’il requiert uniquement l’heure, le mois et le jour des paramètres de transition.

L’exemple peut être testé à l’aide de code semblable au suivant :

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

* Une référence à System.Core.dll à ajouter au projet.

* Que les espaces de noms suivants soient importés :

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md)
[Comment : créer des fuseaux horaires sans règles d’ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
