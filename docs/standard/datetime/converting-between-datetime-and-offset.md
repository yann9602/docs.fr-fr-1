---
title: Conversion entre DateTime et DateTimeOffset
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
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2055df26618664ee130be417599f4ec46e439444
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="converting-between-datetime-and-datetimeoffset"></a>Conversion entre DateTime et DateTimeOffset

Bien que le <xref:System.DateTimeOffset> structure fournit une plus grande des fuseaux horaires que le <xref:System.DateTime> structure, <xref:System.DateTime> paramètres sont plus fréquemment utilisés dans les appels de méthode. Pour cette raison, la capacité à convertir <xref:System.DateTimeOffset> valeurs <xref:System.DateTime> les valeurs et vice versa, est particulièrement important. Cette rubrique montre comment effectuer ces conversions de manière à conserver les informations de fuseau horaire que possible.

> [!NOTE]
> À la fois le <xref:System.DateTime> et <xref:System.DateTimeOffset> types présentent des restrictions lors de la représentation d’heures dans des fuseaux horaires. Avec son <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTime> est en mesure de refléter le temps universel coordonné (UTC) et fuseau horaire local du système. <xref:System.DateTimeOffset>reflète un temps de décalage à l’heure UTC, mais il ne reflète pas le fuseau horaire réel auquel ce décalage appartient. Pour plus d’informations sur les valeurs d’heure et la prise en charge des fuseaux horaires, consultez [Choosing Between DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).

## <a name="conversions-from-datetime-to-datetimeoffset"></a>Conversions de DateTime en DateTimeOffset

Le <xref:System.DateTimeOffset> structure fournit deux méthodes <xref:System.DateTime> à <xref:System.DateTimeOffset> conversion qui conviennent à la plupart des conversions :

* Le <xref:System.DateTimeOffset.%23ctor%2A> constructeur, ce qui crée un <xref:System.DateTimeOffset> objet basé sur un <xref:System.DateTime> valeur.

* L’opérateur de conversion implicite, qui vous permet d’affecter un <xref:System.DateTime> valeur un <xref:System.DateTimeOffset> objet.

Heure UTC et local <xref:System.DateTime> valeurs, le <xref:System.DateTimeOffset.Offset%2A> propriété des résultats de <xref:System.DateTimeOffset> valeur reflète précisément le décalage de fuseau UTC ou l’heure locale. Par exemple, le code suivant convertit une heure UTC en son équivalent <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

Dans ce cas, le décalage de la variable `utcTime2` est 00:00. De même, le code suivant convertit une heure locale en son équivalent <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

Toutefois, pour <xref:System.DateTime> dont les valeurs <xref:System.DateTime.Kind%2A> propriété est <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, ces deux méthodes de conversion produisent un <xref:System.DateTimeOffset> valeur dont le décalage du fuseau horaire local. Cela est illustré dans l’exemple suivant, qui se déroule dans le fuseau horaire Pacifique (É.-U.).

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

Si le <xref:System.DateTime> valeur reflète la date et l’heure dans un élément autre que le fuseau horaire local ou l’heure UTC, vous pouvez le convertir en un <xref:System.DateTimeOffset> valeur et conserver ses informations de fuseau horaire en appelant surchargées <xref:System.DateTimeOffset.%23ctor%2A> constructeur. Par exemple, l’exemple suivant instancie un <xref:System.DateTimeOffset> objet reflétant centrale.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

Le deuxième paramètre de cette surcharge de constructeur, un <xref:System.TimeSpan> objet qui représente l’offset d’heure à l’heure UTC, doit être récupéré en appelant le <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> méthode du fuseau horaire correspondant de l’heure. Le paramètre de la méthode unique est la <xref:System.DateTime> valeur qui représente la date et l’heure à convertir. Si le fuseau horaire prend en charge l’heure d’été, ce paramètre permet à la méthode de déterminer le décalage approprié pour cette date et cette heure particulières.

## <a name="conversions-from-datetimeoffset-to-datetime"></a>Conversions de DateTimeOffset vers DateTime

Le <xref:System.DateTimeOffset.DateTime%2A> propriété est couramment utilisée pour effectuer <xref:System.DateTimeOffset> à <xref:System.DateTime> conversion. Toutefois, elle retourne un <xref:System.DateTime> dont la valeur <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Unspecified>, comme l’illustre l’exemple suivant.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

Cela signifie que toutes les informations sur le <xref:System.DateTimeOffset> relation de valeur au format UTC est perdue lors de la conversion lorsque la <xref:System.DateTimeOffset.DateTime%2A> propriété est utilisée. Cela affecte <xref:System.DateTimeOffset> les valeurs qui correspondent à l’heure UTC ou à l’heure du système local, car le <xref:System.DateTimeOffset.DateTime%2A> structure reflète uniquement les deux fuseaux horaires dans son <xref:System.DateTime.Kind%2A> propriété.

Pour conserver les informations de fuseau horaire que possible lorsque vous convertissez un <xref:System.DateTimeOffset> à un <xref:System.DateTime> valeur, vous pouvez utiliser la <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> et <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriétés.

### <a name="converting-a-utc-time"></a>Conversion d’une heure UTC

Pour indiquer qu’un texte converti <xref:System.DateTimeOffset.DateTime%2A> valeur est l’heure UTC, vous pouvez récupérer la valeur de la <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriété. Il diffère de la <xref:System.DateTimeOffset.DateTime%2A> propriété de deux manières :

* Elle retourne un <xref:System.DateTime> dont la valeur <xref:System.DateTime.Kind%2A> propriété est <xref:System.DateTimeKind.Utc>.

* Si le <xref:System.DateTimeOffset.Offset%2A> différente de la valeur de la propriété <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, elle convertit l’heure au format UTC.

> [!NOTE]
> Si votre application nécessite que converti <xref:System.DateTime> valeurs identifient sans ambiguïté un point unique dans le temps, vous devez envisager d’utiliser le <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> propriété pour gérer toutes les <xref:System.DateTimeOffset> à <xref:System.DateTime> conversions.

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour convertir un <xref:System.DateTimeOffset> valeur dont l’offset est égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType> à un <xref:System.DateTime> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

Le code suivant utilise la <xref:System.DateTimeOffset.UtcDateTime%2A> propriété pour effectuer une conversion de fuseau horaire et une conversion de type sur un <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a>Conversion d’une heure locale

Pour indiquer qu’un <xref:System.DateTimeOffset> valeur représente l’heure locale, vous pouvez passer le <xref:System.DateTime> valeur retournée par la <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> propriété le `static` (`Shared` en Visual Basic) <xref:System.DateTime.SpecifyKind%2A> (méthode). La méthode retourne la date et l’heure passée comme premier paramètre, mais définit le <xref:System.DateTime.Kind%2A> propriété à la valeur spécifiée par son deuxième paramètre. Le code suivant utilise la <xref:System.DateTime.SpecifyKind%2A> méthode lorsque vous convertissez un <xref:System.DateTimeOffset> valeur dont le décalage correspond à celui du fuseau horaire local.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

Vous pouvez également utiliser le <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour convertir un <xref:System.DateTimeOffset> valeur dans une variable locale <xref:System.DateTime> valeur. Le <xref:System.DateTime.Kind%2A> propriété retourné <xref:System.DateTime> valeur est <xref:System.DateTimeKind.Local>. Le code suivant utilise la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété lorsque vous convertissez un <xref:System.DateTimeOffset> valeur dont le décalage correspond à celui du fuseau horaire local. 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

Lorsque vous récupérez un <xref:System.DateTime> valeur à l’aide de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété, de la propriété `get` accesseur convertit d’abord la <xref:System.DateTimeOffset> valeur au format UTC, puis la convertit en heure locale en appelant le <xref:System.DateTimeOffset.ToLocalTime%2A> (méthode). Cela signifie que vous pouvez récupérer une valeur à partir de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> propriété pour effectuer une conversion de fuseau horaire en même temps que vous effectuez une conversion de type. Cela signifie également que les règles d’ajustement du fuseau horaire local sont appliquées lors de la conversion. Le code suivant illustre l’utilisation de la <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> pour effectuer une conversion de fuseau horaire et un type de propriété.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a>Une méthode de conversion à usage général

L’exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit <xref:System.DateTimeOffset> valeurs <xref:System.DateTime> valeurs. En fonction de son décalage, elle détermine si le <xref:System.DateTimeOffset> valeur est une heure UTC, une heure locale ou un autre moment et définit la date renvoyée et la valeur d’heure <xref:System.DateTime.Kind%2A> propriété en conséquence.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

L’exemple suivant appelle la `ConvertFromDateTimeOffset` méthode pour convertir <xref:System.DateTimeOffset> valeurs qui représentent une heure UTC, une heure locale et une heure aux États-Unis. horaire Centre des États-Unis.

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

Notez que ce code part de deux hypothèses qui, selon l’application et la source de ses valeurs de date et d’heure, peuvent ne pas toujours être valides :

* Il part du principe qu’une date et heure de valeur dont le décalage est <xref:System.TimeSpan.Zero?displayProperty=nameWithType> représente l’heure UTC. En fait, l’heure UTC n’est pas une heure dans un fuseau horaire particulier, mais l’heure par rapport à laquelle les heures des fuseaux horaires du monde sont normalisées. Fuseaux horaires peuvent également avoir un décalage de <xref:System.TimeSpan.Zero>.

* Il suppose qu’une date et une heure dont le décalage est égal à celui du fuseau horaire local représentent le fuseau horaire local. Étant donné que les valeurs de date et d’heure sont dissociées de leur fuseau horaire d’origine, cela peut ne pas être le cas ; la date et l’heure peuvent provenir d’un autre fuseau horaire affichant le même décalage.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
