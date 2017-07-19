---
title: "Comment&#160;: cr&#233;er des fuseaux horaires avec des r&#232;gles d&#39;ajustement | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "règle d'ajustement (.NET Framework)"
  - "fuseaux horaires (.NET Framework), et règles d'ajustement"
  - "fuseaux horaires (.NET Framework), créer"
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er des fuseaux horaires avec des r&#232;gles d&#39;ajustement
Les informations de fuseau horaire précises requises par une application peuvent être absentes d'un système particulier pour plusieurs raisons :  
  
-   Le fuseau horaire n'a jamais été défini dans le Registre du système local.  
  
-   Les données relatives au fuseau horaire ont été modifiées ou supprimées du Registre.  
  
-   Le fuseau horaire ne dispose pas d'informations exactes sur les ajustements des fuseaux horaires pour une période donnée.  
  
 Dans ces cas précis, vous pouvez appeler la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> pour définir le fuseau horaire requis par votre application.  Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d'ajustement.  Si le fuseau horaire prend en charge l'heure d'été, vous pouvez définir des ajustements avec des règles d'ajustement de date fixe ou flottante. \(Pour obtenir les définitions de ces termes, consultez la section « Terminologie de fuseau horaire » dans [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md).\)  
  
> [!IMPORTANT]
>  Les fuseaux horaires personnalisés créés en appelant la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ne sont pas ajoutés au Registre.  Seule la référence d'objet retournée par l'appel de méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> permet d'y accéder.  
  
 Cette rubrique indique comment créer un fuseau horaire avec des règles d'ajustement.  Pour créer un fuseau horaire qui ne prend pas en charge les règles d'ajustement de l'heure d'été, consultez [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md).  
  
### Pour créer un fuseau horaire avec des règles d'ajustement de date flottante  
  
1.  Pour chaque ajustement \(autrement dit, pour chaque passage à\/de l'heure d'hiver sur une période donnée\), procédez comme suit :  
  
    1.  Définissez l'heure de début de la période de transition pour l'ajustement de fuseau horaire.  
  
         Vous devez appeler la méthode <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> et lui passer une valeur <xref:System.DateTime> qui définit l'heure de la transition, deux entiers qui définissent la transition et la semaine durant laquelle la transition se produit et une valeur <xref:System.DayOfWeek> qui définit le jour de la semaine auquel survient la transition.  Cet appel de méthode instancie un objet <xref:System.TimeZoneInfo.TransitionTime>.  
  
    2.  Définissez l'heure de fin de la période de transition pour l'ajustement de fuseau horaire.  La méthode <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=fullName> est de nouveau appelée.  Cet appel de méthode instancie un deuxième objet <xref:System.TimeZoneInfo.TransitionTime>.  
  
    3.  Appelez la méthode <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> et passez\-lui les dates de début et de fin de l'ajustement, un objet <xref:System.TimeSpan> qui définit la durée de la transition et les deux objets <xref:System.TimeZoneInfo.TransitionTime> qui définissent quand a lieu le passage à\/de l'heure d'été.  Cet appel de méthode instancie un objet <xref:System.TimeZoneInfo.AdjustmentRule>.  
  
    4.  Assignez l'objet <xref:System.TimeZoneInfo.AdjustmentRule> à un tableau d'objets <xref:System.TimeZoneInfo.AdjustmentRule>.  
  
2.  Définissez le nom complet du fuseau horaire.  Le nom complet respecte un format relativement standard dans lequel l'offset du fuseau horaire par rapport au temps universel coordonné \(UTC, Coordinated Universal Time\) est mis entre parenthèses et suivi d'une chaîne qui identifie le fuseau horaire, ainsi qu'une ou plusieurs villes ou un ou plusieurs pays ou régions du fuseau horaire.  
  
3.  Définissez le nom de l'heure d'hiver du fuseau horaire.  En général, cette chaîne est également utilisée comme identificateur de fuseau horaire.  
  
4.  Définissez le nom de l'heure d'été du fuseau horaire.  
  
5.  Si vous souhaitez utiliser un identificateur différent du nom standard du fuseau horaire, définissez l'identificateur de fuseau horaire.  
  
6.  Instanciez un objet <xref:System.TimeSpan> qui définit l'offset du fuseau horaire par rapport à l'heure UTC.  Les fuseaux horaires dont les heures sont ultérieures à l'heure UTC présentent un offset positif.  Inversement, les fuseaux horaires dont les heures sont antérieures à l'heure UTC présentent un offset négatif.  
  
7.  Appelez la méthode [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName> pour instancier le nouveau fuseau horaire.  
  
## Exemple  
 L'exemple suivant définit un fuseau horaire du Centre des États\-Unis qui inclut des règles d'ajustement pour diverses périodes à partir de 1918.  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
 [!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]  
  
 Le fuseau horaire créé dans cet exemple comporte plusieurs règles d'ajustement.  Veillez à ce que les dates de début et de fin de toute règle d'ajustement ne chevauchent pas les dates d'une autre règle d'ajustement.  En cas de chevauchement, une exception <xref:System.InvalidTimeZoneException> est levée.  
  
 Pour les règles d'ajustement de date flottante, la valeur 5 est passée au paramètre `week` de la méthode <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> pour indiquer que la transition se produit la dernière semaine d'un mois donné.  
  
 En créant le tableau d'objets <xref:System.TimeZoneInfo.AdjustmentRule> à utiliser dans l'appel de méthode [TimeZoneInfo.CreateCustomTimeZone\(String, TimeSpan, String, String, String, TimeZoneInfo.AdjustmentRule\<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=fullName>, le code pourrait initialiser le tableau à la taille requise par le nombre d'ajustements à créer pour le fuseau horaire.  Au lieu de cela, cet exemple de code appelle la méthode <xref:System.Collections.Generic.List%601.Add%2A> pour ajouter chaque règle d'ajustement à une collection générique <xref:System.Collections.Generic.List%601> d'objets <xref:System.TimeZoneInfo.AdjustmentRule>.  Le code appelle ensuite la méthode <xref:System.Collections.Generic.List%601.CopyTo%2A> pour copier les membres de cette collection vers le tableau.  
  
 L'exemple utilise également la méthode <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> pour définir des ajustements de date fixe.  Cela revient à appeler la méthode <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A>, sauf que seuls l'heure, le mois et le jour des paramètres de transition sont requis.  
  
 L'exemple peut être testé à l'aide du code suivant :  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
 [!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que les espaces de noms suivants soient importés :  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)   
 [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)