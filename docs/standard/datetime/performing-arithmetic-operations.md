---
title: "Ex&#233;cution d&#39;op&#233;rations arithm&#233;tiques avec des dates et heures | Microsoft Docs"
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
  - "opérations arithmétiques (.NET Framework), dates et heures"
  - "dates (.NET Framework), opérations arithmétiques"
  - "dates (.NET Framework), comparer"
  - "DateTime (structure), opérations arithmétiques"
  - "DateTimeOffset (structure), opérations arithmétiques"
  - "fuseaux horaires (.NET Framework), opérations arithmétiques"
  - "heures (.NET Framework), opérations arithmétiques"
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Ex&#233;cution d&#39;op&#233;rations arithm&#233;tiques avec des dates et heures
Même si les structures <xref:System.DateTime> et <xref:System.DateTimeOffset> fournissent des membres qui exécutent des opérations arithmétiques sur leurs valeurs, les résultats des opérations arithmétiques sont très différents.  Cette rubrique examine ces différences, les met en rapport avec les degrés de prise en charge des fuseaux horaires dans les données de date et d'heure et explique comment exécuter des opérations prenant pleinement en charge les fuseaux horaires à l'aide de données de date et d'heure.  
  
## Comparaisons et opérations arithmétiques avec des valeurs DateTime  
 À partir de .NET Framework version 2.0, les valeurs <xref:System.DateTime> possèdent un degré limité de prise en charge des fuseaux horaires.  La propriété <xref:System.DateTime.Kind%2A?displayProperty=fullName> permet d'assigner une valeur <xref:System.DateTimeKind> à la date et à l'heure pour indiquer si elle représente l'heure locale, le temps universel coordonné \(UTC, Coordinated Universal Time\) ou l'heure dans un fuseau horaire non spécifié.  Ces informations limitées sur les fuseaux horaires sont toutefois ignorées lors de la comparaison ou de l'exécution d'opérations arithmétiques avec des dates et des heures sur les valeurs <xref:System.DateTime>.  Ceci est illustré dans l'exemple suivant qui compare l'heure locale actuelle à l'heure UTC actuelle.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]  
  
 La méthode <xref:System.DateTime.CompareTo%28System.DateTime%29> signale que l'heure locale est antérieure \(ou inférieure à\) l'heure UTC, et l'opération de soustraction indique que la différence entre l'heure UTC et l'heure locale pour un système dans le fuseau U.S. Pacific Standard est sept heures.  Mais comme ces deux valeurs donnent des représentations différentes d'un même point dans le temps, il apparaît clairement dans ce cas que cet intervalle de temps est totalement attribuable au décalage du fuseau horaire local par rapport à l'heure UTC.  
  
 De manière générale, la propriété <xref:System.DateTime.Kind%2A?displayProperty=fullName> n'influe pas sur les résultats retournés par des méthodes de comparaison et d'arithmétique <xref:System.DateTime> \(comme la comparaison de deux points identiques dans le temps l'indique\), mais elle peut influer sur l'interprétation de ces résultats.  Par exemple :  
  
-   Le résultat de toute opération arithmétique exécutée sur deux valeurs de date et d'heure dont les propriétés <xref:System.DateTime.Kind%2A?displayProperty=fullName> sont égales à <xref:System.DateTimeKind> indique l'intervalle de temps effectif entre ces deux valeurs.  De même, la comparaison de deux valeurs de date et d'heure de ce type indique précisément la relation entre les heures.  
  
-   Le résultat de toute opération arithmétique ou opération de comparaison exécutée sur deux valeurs de date et d'heure dont les propriétés <xref:System.DateTime.Kind%2A?displayProperty=fullName> sont égales à <xref:System.DateTimeKind> ou sur deux valeurs de date et d'heure dont les propriétés <xref:System.DateTime.Kind%2A?displayProperty=fullName> ont des valeurs différentes indique la différence en temps horloge entre ces deux valeurs.  
  
-   Les opérations arithmétiques ou les opérations de comparaison sur des valeurs de date et d'heure locales ne se soucient pas de savoir si une valeur particulière est ambiguë ou non valide et ne tiennent pas non plus compte de l'incidence de règles d'ajustement qui résultent du passage du fuseau horaire local à l'heure d'été ou à l'heure d'hiver.  
  
-   Toute opération qui compare ou calcule la différence entre l'heure UTC et une heure locale inclut un intervalle de temps égal au décalage du fuseau horaire local par rapport à l'heure UTC dans le résultat.  
  
-   Toute opération qui compare ou calcule la différence entre une heure non spécifiée et l'heure UTC ou l'heure locale indique le temps horloge simple.  Les décalages entre les fuseaux horaires ne sont pas pris en compte et le résultat ne tient pas compte de l'application de règles d'ajustement des fuseaux horaires.  
  
-   Toute opération qui compare ou calcule la différence entre deux heures non spécifiées peut inclure un intervalle inconnu qui indique la différence horaire dans deux fuseaux horaires différents.  
  
 Nombreux sont les scénarios dans lesquels les décalages entre les fuseaux horaires n'influent pas sur les calculs des dates et des heures \(pour plus d'informations sur certains d'entre eux, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)\) ou dans lesquels le contexte des données de date et d'heure définit la signification des opérations de comparaison ou des opérations arithmétiques.  
  
## Comparaisons et opérations arithmétiques avec des valeurs DateTimeOffset  
 Une valeur <xref:System.DateTimeOffset> inclut non seulement une date et une heure, mais également un décalage qui définit clairement cette date et cette heure par rapport à l'heure UTC.  Il est ainsi possible de définir une égalité d'une manière quelque peu différente de celle des valeurs <xref:System.DateTime>.  Les valeurs <xref:System.DateTime> sont égales lorsqu'elles possèdent la même valeur de date et d'heure, alors que les valeurs <xref:System.DateTimeOffset> sont égales lorsqu'elles font toutes les deux référence au même point dans le temps.  Une valeur <xref:System.DateTimeOffset> est de ce fait plus précise et nécessite moins d'interprétation lorsqu'elle est utilisée dans des comparaisons et dans la plupart des opérations arithmétiques qui déterminent l'intervalle entre deux dates et heures.  Cette différence de comportement est illustrée dans l'exemple suivant, qui est l'équivalent <xref:System.DateTimeOffset> de l'exemple précédent dans lequel les valeurs <xref:System.DateTime> de l'heure locale et de l'heure UTC étaient comparées.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]  
  
 Dans cet exemple, la méthode <xref:System.DateTimeOffset.CompareTo%2A> indique que l'heure locale actuelle et l'heure UTC actuelle sont égales et la soustraction des valeurs <xref:System.DateTimeOffset> indique que la différence entre les deux heures est <xref:System.TimeSpan.Zero?displayProperty=fullName>.  
  
 L'utilisation de valeurs <xref:System.DateTimeOffset> dans des opérations arithmétiques de date et d'heure présente une sérieuse limitation : même si les valeurs <xref:System.DateTimeOffset> prennent en charge certains fuseaux horaires, elles ne prennent pas en charge tous les fuseaux horaires.  Même si le décalage de la valeur <xref:System.DateTimeOffset> indique le décalage d'un fuseau horaire par rapport à l'heure UTC lorsqu'une première valeur est assignée à une variable <xref:System.DateTimeOffset>, il se dissocie par la suite du fuseau horaire.  Comme il n'est plus directement associé à une heure identifiable, les règles d'ajustement d'un fuseau horaire ne sont pas prises en compte lors de l'addition et de la soustraction d'intervalles de dates et d'heures.  
  
 Pour illustrer cela, la transition vers l'heure d'été à la zone d'heure du Centre des États\-Unis se produit à 2h00 du matin le le 9 mars 2008.  Cela signifie que l'ajout de deux et un intervalle d'une demi\-heure à une heure à partir du Centre de 1h30 du matin le le 9 mars 2008, doit produire une date et heure est de 5h00 du matin le le 9 mars 2008.  Cependant, comme le montre l'exemple suivant, le résultat de l'addition est 04H00 du matin, le 9 Mars 2008.  Notez que le résultat de cette opération représente l'heure exacte, bien que cela ne soit pas l'heure dans le fuseau horaire qui nous intéresse \(autrement dit, il n'a pas le décalage horaire attendu\).  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]  
  
## Opérations arithmétiques avec des heures et des fuseaux horaires  
 La classe <xref:System.TimeZoneInfo> inclut plusieurs méthodes de conversion qui appliquent automatiquement des ajustements lorsqu'elles convertissent des heures d'un fuseau horaire à un autre.  parmi lesquels :  
  
-   Les méthodes <xref:System.TimeZoneInfo.ConvertTime%2A> et <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, qui convertissent des heures d'un fuseau horaire à un autre.  
  
-   Les méthodes <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> et <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, qui convertissent l'heure d'un fuseau horaire particulier en heure UTC ou qui convertissent l'heure UTC dans l'heure d'un fuseau horaire particulier.  
  
 Pour plus d'informations, consultez [Conversion d'heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
 La classe <xref:System.TimeZoneInfo> ne fournit pas de méthodes qui appliquent automatiquement des règles d'ajustement lorsque vous exécutez des opérations arithmétiques de date et d'heure.  Vous pouvez toutefois procéder en convertissant l'heure d'un fuseau horaire en heure UTC, en exécutant l'opération arithmétique, puis en reconvertissant l'heure UTC dans l'heure du fuseau horaire.  Pour plus d'informations, consultez [Comment : utiliser des fuseaux horaires en arithmétique de date et heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).  
  
 Par exemple, le code suivant est semblable au code précédent qui a ajouté deux heures trente à 02H00 du matin, le 9 Mars 2008.  Cependant, dans la mesure où il convertit l'heure du Centre des États\-Unis en heure UTC avant d'effectuer le calcul, puis convertit le résultat UTC en heure du Centre, l'heure résultante reflète le passage à l'heure d'été du fuseau horaire du Centre des États\-Unis.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Comment : utiliser des fuseaux horaires en arithmétique de date et heure](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)