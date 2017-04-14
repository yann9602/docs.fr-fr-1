---
title: "Conversion d&#39;heures entre fuseaux horaires | Microsoft Docs"
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
  - "convertir des heures"
  - "conversions en heure locale"
  - "fuseaux horaires (.NET Framework), conversions"
  - "heures (.NET Framework), convertir"
  - "temps UTC, convertir"
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Conversion d&#39;heures entre fuseaux horaires
Il est de plus en plus important que les applications utilisant des dates et des heures puissent gérer les différences entre fuseaux horaires.  Il ne faut plus s'attendre à ce que les heures soient toutes exprimées en heure locale \(heure disponible dans la structure <xref:System.DateTime> \).  Par exemple, une page Web qui affiche l'heure actuelle de l'est des États\-Unis manquera de crédibilité auprès d'un client d'Asie orientale.  Cette rubrique explique comment convertir des heures d'un fuseau horaire à un autre, ainsi que des valeurs <xref:System.DateTimeOffset> qui ne prennent pas complètement en charge les fuseaux horaires.  
  
## Conversion en temps universel coordonné  
 Le temps universel coordonné \(UTC, Coordinated Universal Time\) est une norme de temps atomique extrêmement précise.  Les fuseaux horaires du monde sont exprimés sous la forme d'offsets positifs ou négatifs par rapport à l'heure UTC.  L'heure UTC indique en quelque sorte une heure provenant d'un fuseau horaire neutre ou d'une zone sans fuseau horaire.  Il est recommandé d'utiliser l'heure UTC lorsque la portabilité de la date et de l'heure sur différents ordinateurs est importante. \(Pour obtenir des informations et d'autres meilleures pratiques sur l'utilisation des dates et des heures, consultez [Meilleures pratiques pour le codage à l'aide de DateTime dans le .NET Framework](http://go.microsoft.com/fwlink/?LinkId=92342)\) \(en anglais\). La conversion de fuseaux horaires individuels en heure UTC permet de comparer facilement les heures.  
  
> [!NOTE]
>  Vous pouvez également sérialiser une structure <xref:System.DateTimeOffset> pour représenter clairement un point dans le temps.  Comme les objets <xref:System.DateTimeOffset> stockent une valeur de date et d'heure avec son offset par rapport à l'heure UTC, ils représentent toujours un point particulier dans le temps par rapport à l'heure UTC.  
  
 Pour effectuer une conversion en heure UTC, le plus simple est d'appeler la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> `static` \(`Shared` dans Visual Basic\).  La conversion exacte effectuée par la méthode dépend de la valeur de la propriété `dateTime` du paramètre <xref:System.DateTime.Kind%2A>, comme indiqué dans le tableau ci\-dessous.  
  
|Propriété DateTime.Kind|Conversion|  
|-----------------------------|----------------|  
|<xref:System.DateTimeKind?displayProperty=fullName>|Convertit l'heure locale en heure UTC.|  
|<xref:System.DateTimeKind?displayProperty=fullName>|Suppose que le paramètre `dateTime` est exprimé en heure locale et convertit l'heure locale en heure UTC.|  
|<xref:System.DateTimeKind?displayProperty=fullName>|Retourne le paramètre `dateTime` sans le modifier.|  
  
 Le code suivant convertit l'heure locale actuelle en heure UTC et affiche le résultat sur la console.  
  
 [!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
 [!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]  
  
> [!NOTE]
>  La méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> ne produit pas forcément des résultats identiques à ceux des méthodes <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=fullName> et <xref:System.DateTime.ToUniversalTime%2A?displayProperty=fullName>.  Si le fuseau horaire local du système hôte comprend plusieurs règles d'ajustement, <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=fullName> applique la règle appropriée à une date et une heure particulières.  Les deux autres méthodes appliquent toujours la règle d'ajustement la plus récente.  
  
 Si la valeur de date et d'heure ne représente ni l'heure locale, ni l'heure UTC, la méthode <xref:System.DateTime.ToUniversalTime%2A> retournera vraisemblablement un résultat erroné.  Toutefois, vous pouvez utiliser la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> pour convertir la date et l'heure d'un fuseau horaire spécifié. Pour plus d'informations sur la récupération d'un objet <xref:System.TimeZoneInfo> qui représente le fuseau horaire de destination, consultez [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md). Le code suivant utilise la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=fullName> pour convertir l'heure de la côte est des États\-Unis en heure UTC.  
  
 [!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
 [!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]  
  
 Notez que cette méthode lève une exception <xref:System.ArgumentException> si la propriété <xref:System.DateTime.Kind%2A> de l'objet <xref:System.DateTime> et le fuseau horaire ne correspondent pas.  Une incompatibilité se produit si la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind?displayProperty=fullName> mais l'objet <xref:System.TimeZoneInfo> ne représente pas le fuseau horaire local ou si la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind?displayProperty=fullName> mais l'objet <xref:System.TimeZoneInfo> n'a pas la valeur <xref:System.DateTimeKind?displayProperty=fullName>.  
  
 Toutes ces méthodes prennent des valeurs <xref:System.DateTime> comme paramètres et retournent une valeur <xref:System.DateTime>.  Pour les valeurs <xref:System.DateTimeOffset>, la structure <xref:System.DateTimeOffset> a une méthode d'instance <xref:System.DateTimeOffset.ToUniversalTime%2A> qui convertit la date et l'heure de l'instance actuelle en heure UTC.  L'exemple suivant appelle la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A> pour convertir une heure locale et d'autres heures en temps universel coordonné.  
  
 [!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
 [!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]  
  
## Conversion de l'heure UTC en un fuseau horaire désigné  
 Pour convertir l'heure UTC en heure locale, consultez la section « Conversion de l'heure UTC en heure locale » ci\-dessous.  Pour convertir l'heure UTC en une heure dans n'importe quel fuseau horaire que vous désignez, appelez la méthode <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>.  Cette méthode accepte deux paramètres :  
  
-   Heure UTC à convertir.  Il doit s'agir d'une valeur <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind?displayProperty=fullName> ou <xref:System.DateTimeKind?displayProperty=fullName>.  
  
-   Fuseau horaire vers lequel convertir l'heure UTC.  
  
 Le code suivant convertit l'heure UTC en heure du Centre \(des États\-Unis\).  
  
 [!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
 [!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]  
  
## Conversion de l'heure UTC en heure locale  
 Pour convertir l'heure UTC en heure locale, appelez la méthode <xref:System.DateTime.ToLocalTime%2A> de l'objet <xref:System.DateTime> dont vous souhaitez convertir l'heure.  Le comportement exact de la méthode dépend de la valeur de la propriété <xref:System.DateTime.Kind%2A> de l'objet, comme indiqué dans le tableau suivant.  
  
|Propriété `DateTime.Kind`|Conversion|  
|-------------------------------|----------------|  
|`DateTimeKind.Local`|Retourne la valeur <xref:System.DateTime> sans la modifier.|  
|`DateTimeKind.Unspecified`|Suppose que la valeur <xref:System.DateTime> est exprimée en heure UTC et convertit l'heure UTC en heure locale.|  
|`DateTimeKind.Utc`|Convertit la valeur <xref:System.DateTime> en heure locale.|  
  
 **Remarque** La méthode <xref:System.TimeZone.ToLocalTime%2A?displayProperty=fullName> se comporte comme la méthode `DateTime.ToLocalTime`.  Elle accepte un paramètre qui est la valeur de date et d'heure à convertir.  
  
 Vous pouvez également convertir l'heure d'un fuseau horaire désigné en heure locale en faisant appel à la méthode `static` \(`Shared` dans Visual Basic\) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=fullName>.  Cette technique est expliquée dans la section suivante.  
  
## Conversion entre deux fuseaux horaires  
 Vous pouvez effectuer une conversion entre deux fuseaux horaires en utilisant l'une des deux méthodes `static` suivantes \(`Shared` dans Visual Basic\) de la classe <xref:System.TimeZoneInfo>:  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A>  
  
     Les paramètres de cette méthode sont la valeur de date et d'heure à convertir, un objet `TimeZoneInfo` qui représente le fuseau horaire de la valeur de date et d'heure et un objet `TimeZoneInfo` qui représente le fuseau horaire vers lequel convertir la valeur de date et d'heure.  
  
-   <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>  
  
     Les paramètres de cette méthode sont la valeur de date et d'heure à convertir, l'identificateur du fuseau horaire de la valeur de date et d'heure et l'identificateur du fuseau horaire vers lequel convertir la valeur de date et d'heure.  
  
 Quelle que soit la méthode utilisée, la propriété <xref:System.DateTime.Kind%2A> de la valeur de date et d'heure à convertir ainsi que l'objet <xref:System.TimeZoneInfo> et l'identificateur de fuseau horaire qui représente son fuseau horaire doivent correspondre.  Sinon, une exception <xref:System.ArgumentException> est levée.  Par exemple, si la propriété `Kind` de la valeur de date et d'heure est `DateTimeKind.Local`, une exception est levée si l'objet `TimeZoneInfo` passé comme paramètre à la méthode n'est pas égal à `TimeZoneInfo.Local`.  Une exception est également levée si l'identificateur passé comme paramètre à la méthode n'est pas égal à `TimeZoneInfo.Local.Id`.  
  
 L'exemple suivant utilise la méthode <xref:System.TimeZoneInfo.ConvertTime%2A> pour convertir l'heure d'Hawaii en heure locale.  
  
 [!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
 [!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]  
  
## Conversion de valeurs DateTimeOffset  
 Les valeurs de date et d'heure représentées par les objets <xref:System.DateTimeOffset> ne prennent pas complètement en charge les fuseaux horaires, car l'objet est dissocié de son fuseau horaire lors de son instanciation.  Toutefois, dans de nombreux cas, les application ont simplement besoin de convertir une date et une heure en fonction de deux offsets différents par rapport à l'heure UTC plutôt que de l'heure de fuseaux horaires particuliers.  Pour exécuter cette conversion, vous pouvez appeler la méthode <xref:System.DateTimeOffset.ToOffset%2A> de l'instance actuelle.  L'unique paramètre de la méthode est l'offset de la nouvelle valeur de date et d'heure que la méthode doit retourner.  
  
 Par exemple, si la date et l'heure d'une demande de page Web émanant d'un utilisateur est connue et sérialisée en tant que chaîne au format MM\/jj\/aaaa hh:mm:ss zzzz, la méthode `ReturnTimeOnServer` suivante convertit cette valeur de date et d'heure en date et heure sur le serveur Web.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)]  
  
 Si la chaîne « 01\/09\/2007 17:32:07 \-17:00 » est passée à la méthode, qui représente les date et heure dans un fuseau horaire avec cinq heures de moins que l'heure UTC, elle retourne 01\/09\/2007 03:32:07 \-07:00 pour un serveur situé dans le fuseau U.S. Pacific Standard Time  
  
 La classe <xref:System.TimeZoneInfo> inclut également une surcharge de la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> qui exécute des conversions de fuseau horaire avec les valeurs <xref:System.DateTimeOffset>.  Les paramètres de la méthode sont une valeur <xref:System.DateTimeOffset> et une référence au fuseau horaire vers lequel convertir l'heure.  L'appel de méthode retourne une valeur <xref:System.DateTimeOffset>.  La méthode `ReturnTimeOnServer` de l'exemple précédent pourrait être réécrite comme suit pour appeler la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
 [!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]  
  
## Voir aussi  
 <xref:System.TimeZoneInfo>   
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)