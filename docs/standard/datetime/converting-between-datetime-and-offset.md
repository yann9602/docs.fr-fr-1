---
title: "Conversion entre DateTime et DateTimeOffset | Microsoft Docs"
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
  - "convertir des valeurs DateTime et DateTimeOffset"
  - "convertir des heures"
  - "Date (type de données), convertir"
  - "dates (.NET Framework), convertir"
  - "DateTime (structure), convertir"
  - "DateTimeOffset (structure), convertir"
  - "conversions en heure locale"
  - "fuseaux horaires (.NET Framework), conversions"
  - "temps UTC, convertir"
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Conversion entre DateTime et DateTimeOffset
Même si la structure <xref:System.DateTimeOffset> assure un niveau de prise en charge des fuseaux horaires supérieur à celui de la structure <xref:System.DateTime>, les paramètres <xref:System.DateTime> sont plus fréquemment utilisés dans les appels de méthode.  La capacité à convertir des valeurs <xref:System.DateTimeOffset> en valeurs <xref:System.DateTime> et vice versa revêt de ce fait une importance particulière.  Cette rubrique indique comment effectuer ces conversions de manière à conserver autant d'informations sur les fuseaux horaires que possible.  
  
> [!NOTE]
>  Les types <xref:System.DateTime> et <xref:System.DateTimeOffset> présentent des restrictions lors de la représentation d'heures dans des fuseaux horaires.  Avec sa propriété <xref:System.DateTime.Kind%2A>, <xref:System.DateTime> ne peut refléter que l'heure UTC et le fuseau horaire local du système.  <xref:System.DateTimeOffset> reflète un décalage par rapport à l'heure UTC, mais ne reflète pas le fuseau horaire réel auquel ce décalage appartient.  Pour plus d'informations sur les valeurs d'heure et la prise en charge des fuseaux horaires, consultez [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).  
  
## Conversions de DateTime en DateTimeOffset  
 La structure <xref:System.DateTimeOffset> propose deux méthodes de conversion de <xref:System.DateTime> en <xref:System.DateTimeOffset> qui se prêtent à la plupart des conversions :  
  
-   Le constructeur <xref:System.DateTimeOffset.%23ctor%2A>, qui crée un objet <xref:System.DateTimeOffset> sur la base d'une valeur <xref:System.DateTime>.  
  
-   L'opérateur de conversion implicite, qui vous permet d'assigner une valeur <xref:System.DateTime> à un objet <xref:System.DateTimeOffset>.  
  
 Pour les valeurs <xref:System.DateTime> locales et UTC, la propriété <xref:System.DateTimeOffset.Offset%2A> de la valeur <xref:System.DateTimeOffset> résultante indique le décalage par rapport à l'heure UTC ou au fuseau horaire local.  Par exemple, le code suivant convertit une heure UTC dans sa valeur <xref:System.DateTimeOffset> équivalente.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]  
  
 Dans ce cas, le décalage de la variable `utcTime2` est 00:00.  De même, le code suivant convertit une heure locale en sa valeur <xref:System.DateTimeOffset> équivalente.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]  
  
 Pour les valeurs <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind?displayProperty=fullName>, ces deux méthodes de conversion génèrent toutefois une valeur <xref:System.DateTimeOffset> dont le décalage correspond au fuseau horaire local.  Cela est montré dans l'exemple suivant, exécuté dans le fuseau horaire U.S. Pacific Standard Time.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]  
  
 Si la valeur <xref:System.DateTime> indique la date et l'heure dans autre chose que le fuseau horaire local ou l'heure UTC, vous pouvez la convertir en valeur <xref:System.DateTimeOffset> et conserver ses informations sur les fuseaux horaires en appelant le constructeur <xref:System.DateTimeOffset.%23ctor%2A> surchargé.  L'exemple suivant instancie un objet <xref:System.DateTimeOffset> qui indique l'heure du Centre \(des États\-Unis\).  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]  
  
 Le deuxième paramètre passé à cette surcharge de constructeur, un objet <xref:System.TimeSpan> qui représente le décalage de l'heure par rapport à l'heure UTC, doit être récupéré en appelant la méthode <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=fullName> du fuseau horaire correspondant à l'heure.  Le seul paramètre de la méthode a la valeur <xref:System.DateTime> qui représente la date et l'heure à convertir.  Si le fuseau horaire prend en charge l'heure d'été, ce paramètre permet alors à la méthode de déterminer le décalage correspondant à la date et à l'heure données.  
  
## Conversions de DateTimeOffset en DateTime  
 La propriété <xref:System.DateTimeOffset.DateTime%2A> permet le plus souvent de convertir <xref:System.DateTimeOffset> en <xref:System.DateTime>.  Elle retourne toutefois une valeur <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind>, comme illustré dans l'exemple suivant.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]  
  
 En d'autres termes, toutes les informations sur la relation de la valeur <xref:System.DateTimeOffset> par rapport à l'heure UTC sont perdues lors de la conversion lorsque la propriété <xref:System.DateTimeOffset.DateTime%2A> est utilisée.  Cela influe sur les valeurs <xref:System.DateTimeOffset> qui correspondent à l'heure UTC ou à l'heure locale du système, car la structure <xref:System.DateTimeOffset.DateTime%2A> n'indique que les deux fuseaux horaires de sa propriété <xref:System.DateTime.Kind%2A>.  
  
 Pour conserver autant d'informations sur les fuseaux horaires que possible lorsque vous convertissez une valeur <xref:System.DateTimeOffset> en valeur <xref:System.DateTime>, vous pouvez utiliser les propriétés <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> et <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName>.  
  
### Conversion d'une heure UTC  
 Pour indiquer qu'une valeur <xref:System.DateTimeOffset.DateTime%2A> convertie est l'heure UTC, vous pouvez récupérer la valeur à partir de la propriété <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName>.  Elle diffère de la propriété <xref:System.DateTimeOffset.DateTime%2A> de deux façons :  
  
-   Elle retourne une valeur <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind>.  
  
-   Si la propriété <xref:System.DateTimeOffset.Offset%2A> n'a pas la valeur <xref:System.TimeSpan.Zero?displayProperty=fullName>, elle convertit l'heure en heure UTC.  
  
> [!NOTE]
>  Si votre application exige que les valeurs <xref:System.DateTime> converties identifient de manière univoque un point unique dans le temps, vous devez alors envisager d'utiliser la propriété <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=fullName> pour gérer toutes les conversions de <xref:System.DateTimeOffset> en <xref:System.DateTime>.  
  
 Le code suivant utilise la propriété <xref:System.DateTimeOffset.UtcDateTime%2A> pour convertir une valeur <xref:System.DateTimeOffset> dont le décalage équivaut à <xref:System.TimeSpan.Zero?displayProperty=fullName> en valeur <xref:System.DateTime>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]  
  
 Le code suivant utilise la propriété <xref:System.DateTimeOffset.UtcDateTime%2A> pour effectuer une conversion de fuseau horaire et une conversion de type sur une valeur <xref:System.DateTimeOffset>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]  
  
### Conversion d'une heure locale  
 Pour indiquer qu'une valeur <xref:System.DateTimeOffset> représente l'heure locale, vous pouvez passer la valeur <xref:System.DateTime> retournée par la propriété <xref:System.DateTimeOffset.DateTime%2A?displayProperty=fullName> à la méthode <xref:System.DateTime.SpecifyKind%2A> `static` \(`Shared` dans Visual Basic\).  La méthode retourne la date et l'heure qui lui ont été passées par son premier paramètre, mais elle affecte la valeur spécifiée par son deuxième paramètre à la propriété <xref:System.DateTime.Kind%2A>.  Le code suivant utilise la méthode <xref:System.DateTime.SpecifyKind%2A> lors de la conversion d'une valeur <xref:System.DateTimeOffset> dont le décalage correspond à celui du fuseau horaire local.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]  
  
 Vous pouvez également utiliser la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> pour convertir une valeur <xref:System.DateTimeOffset> en valeur <xref:System.DateTime> locale.  La propriété <xref:System.DateTime.Kind%2A> de la valeur <xref:System.DateTime> retournée à la valeur <xref:System.DateTimeKind>.  Le code suivant utilise la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> lors de la conversion d'une valeur <xref:System.DateTimeOffset> dont le décalage correspond à celui du fuseau horaire local.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]  
  
 Lorsque vous récupérez une valeur <xref:System.DateTime> à l'aide de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName>, l'accesseur `get` de la propriété convertit d'abord la valeur <xref:System.DateTimeOffset> en heure UTC, puis il la convertit en heure locale en appelant la méthode <xref:System.DateTimeOffset.ToLocalTime%2A>.  En d'autres termes, vous pouvez récupérer une valeur à partir de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> pour effectuer simultanément une conversion de fuseau horaire et une conversion de type.  Cela signifie également que les règles d'ajustement du fuseau horaire local sont appliquées lors de la conversion.  Le code suivant illustre l'utilisation de la propriété <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=fullName> pour effectuer une conversion de fuseau horaire et une conversion de type.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]  
  
### Méthode de conversion à usage général  
 L'exemple suivant définit une méthode nommée `ConvertFromDateTimeOffset` qui convertit des valeurs <xref:System.DateTimeOffset> en valeurs <xref:System.DateTime>.  En fonction de son décalage, elle détermine si la valeur <xref:System.DateTimeOffset> est une heure UTC, une heure locale ou toute autre heure et elle définit en conséquence la propriété <xref:System.DateTime.Kind%2A> de la valeur de date et d'heure retournée.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]  
  
 L'exemple suivant appelle la méthode `ConvertFromDateTimeOffset` pour convertir des valeurs <xref:System.DateTimeOffset> qui représentent une heure UTC, une heure locale et une heure dans le fuseau horaire U.S. Central Standard Time.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
 [!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]  
  
 Notez que ce code part de deux hypothèses qui, selon l'application et la source de ses valeurs de date et d'heure, risquent de ne pas toujours être valides :  
  
-   Il part du principe qu'une valeur de date et d'heure dont le décalage a la valeur <xref:System.TimeSpan.Zero?displayProperty=fullName> représente l'heure UTC.  En fait, l'heure UTC n'est pas une heure dans un fuseau horaire donné, mais l'heure par rapport à laquelle les heures des fuseaux horaires dans le monde sont normalisées.  Les fuseaux horaires peuvent également avoir un décalage de <xref:System.TimeSpan.Zero>.  
  
-   Il part du principe qu'une date et une heure dont le décalage équivaut à celui du fuseau horaire local représente le fuseau horaire local.  Comme les valeurs de date et d'heure sont dissociées de leur fuseau horaire d'origine, cela peut ne pas être le cas ; la date et l'heure peuvent provenir d'un autre fuseau horaire ayant le même décalage.  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)