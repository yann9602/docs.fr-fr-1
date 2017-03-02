---
title: Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
description: Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: aeb1928be32584ee4b6acf7c9a4f4330daedc590
ms.lasthandoff: 03/02/2017

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo

Les applications .NET qui utilisent des informations de date et d’heure sont très diverses et peuvent utiliser ces informations de plusieurs façons. Les utilisations les plus courantes des informations de date et d'heure sont une ou plusieurs parmi les suivantes :

* Pour refléter seulement une date, les informations d'heure n'étant pas importantes.

* Pour refléter seulement une heure, les informations de date n'étant pas importantes.

* Pour refléter une date et une heure abstraites, qui ne sont pas liées à un moment et un endroit spécifiques (par exemple, la plupart des magasins d'une chaîne internationale ouvrent en semaine à 9h00).

* Pour récupérer des informations de date et d’heure à partir de sources externes à l’application .NET, en général lorsque les informations de date et d’heure sont stockées dans un type de données simple.

* Pour identifier de façon univoque et non ambiguë un point unique dans le temps. Certaines applications requièrent qu'une date/heure soit ambiguë seulement sur le système hôte. D'autres requièrent qu'elle soit non ambiguë entre les systèmes (autrement dit, une date sérialisée sur un système peut être désérialisée de manière significative et utilisée sur un autre système n'importe où dans le monde). 

* Pour conserver plusieurs dates/heures ayant un lien les unes avec les autres (comme la date/heure locale du demandeur et la date/heure de réception par le serveur d'une demande web).

* Pour effectuer des calculs de date et d'heure, éventuellement avec un résultat qui identifie de façon univoque et non ambiguë un point unique dans le temps. 

.NET inclut les types [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan) et [System.TimeZoneInfo](xref:System.TimeZoneInfo), qui permettent tous de créer des applications qui fonctionnent avec des dates et des heures. 

> [!NOTE]
> Cette rubrique ne traite pas du type `TimeZone` plus ancien, car ses fonctionnalités sont presque totalement intégrées dans la classe [System.TimeZoneInfo](xref:System.TimeZoneInfo). Chaque fois que possible, les développeurs doivent utiliser la classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) à la place de la classe `TimeZone`.


## <a name="the-datetime-structure"></a>La structure DateTime

Une valeur [System.DateTime](xref:System.DateTime) définit une date et une heure spécifiques. Elle inclut une propriété [Kind](xref:System.DateTime.Kind) qui fournit des informations limitées sur le fuseau horaire auquel appartiennent cette date et cette heure. La valeur [DateTimeKind](xref:System.DateTimeKind) retournée par la propriété [Kind](xref:System.DateTime.Kind) indique si la valeur [DateTime](xref:System.DateTime) représente l’heure locale [DateTimeKind.Local](xref:System.DateTimeKind.Local), le temps universel coordonné (UTC) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou une heure non spécifiée [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).

La structure [DateTime](xref:System.DateTime) convient pour les applications qui : 

* Utilisent seulement des dates.

* Utilisent seulement des heures.

* Utilisent des dates et des heures abstraites.

* Utilisent des dates et des heures pour lesquelles les informations de fuseau horaire sont manquantes. 

* Utilisent seulement des dates et des heures UTC. 

* Récupèrent des informations de date et d’heure auprès de sources externes au .NET Framework, comme des bases de données SQL. En règle générale, ces sources stockent les informations de date et d’heure dans un format simple qui est compatible avec la structure [DateTime](xref:System.DateTime).

* Effectuent des calculs de dates et d'heures, mais sont surtout concernées par des résultats d'ordre général. Par exemple, dans une opération d'addition qui ajoute six mois à une date/heure, il n'est souvent pas important que le résultat soit ajusté pour l'heure d'été.

Sauf si une valeur [DateTime](xref:System.DateTime) particulière représente le temps UTC, cette valeur de date et d’heure est souvent ambiguë ou limitée en termes de portabilité. Par exemple, si une valeur [DateTime](xref:System.DateTime) représente l’heure locale, elle est portable dans ce fuseau horaire local (c’est-à-dire que si la valeur est désérialisée sur un autre système dans le même fuseau horaire, cette valeur continue d’identifier de façon non ambiguë un point unique dans le temps). En dehors du fuseau horaire local, cette valeur [DateTime](xref:System.DateTime) peut être interprétée de plusieurs façons. Si la propriété [Kind](xref:System.DateTime.Kind) de la valeur est [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), elle est encore moins portable : elle est maintenant ambiguë dans le même fuseau horaire, voire même sur le système où elle a été sérialisée pour la première fois. Seulement dans le cas où une valeur [DateTime](xref:System.DateTime) représente le temps UTC, celle-ci identifie de façon non ambiguë un point unique dans le temps, indépendamment du système ou du fuseau horaire où la valeur est utilisée.

> [!IMPORTANT]
> Lors de l’enregistrement ou du partage de données [DateTime](xref:System.DateTime), le temps UTC doit être utilisé et la propriété [Kind](xref:System.DateTime.Kind) de la valeur [DateTime](xref:System.DateTime) doit être définie sur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

## <a name="the-datetimeoffset-structure"></a>La structure DateTimeOffset

La structure [System.DateTimeOffset](xref:System.DateTimeOffset) représente une valeur de date et d’heure, ainsi qu’un décalage qui indique de combien cette valeur diffère du temps UTC. Ainsi, la valeur toujours identifie toujours de façon non ambiguë un point unique dans le temps. 

Le type [DateTimeOffset](xref:System.DateTimeOffset) comprend toutes les fonctionnalités du type [DateTime](xref:System.DateTime), ainsi que la gestion des fuseaux horaires. Il convient donc pour les applications qui : 

* Identifient de façon univoque et non ambiguë un point unique dans le temps. Le type [DateTimeOffset](xref:System.DateTimeOffset) peut être utilisé pour définir de façon non ambiguë la signification de « maintenant », pour consigner les dates/heures des transactions, pour consigner les dates/heures des événements système ou des événements d’une application, et pour enregistrer les dates/heures de création et de modification des fichiers. 

* Effectuent des calculs de date et d'heure.

* Conservent plusieurs dates/heures ayant un lien entre elles, comme les dates/heures qui sont stockées sous la forme de deux valeurs distinctes ou de deux membres d'une structure.

> [!NOTE]
> Ces utilisations pour des valeurs [DateTimeOffset](xref:System.DateTimeOffset) sont beaucoup plus courantes que celles pour les valeurs [DateTime](xref:System.DateTime). Par conséquent, [DateTimeOffset](xref:System.DateTimeOffset) doit être considéré comme le type de date et d’heure par défaut pour le développement d’applications.

Une valeur [DateTimeOffset](xref:System.DateTimeOffset) n’est pas liée à un fuseau horaire particulier, mais peut provenir de n’importe quel fuseau horaire. Pour illustrer cela, l’exemple suivant répertorie les fuseaux horaires auxquels plusieurs valeurs [DateTimeOffset](xref:System.DateTimeOffset) (y compris une heure locale du Pacifique) peuvent appartenir.

```csharp
using System;
using System.Collections.ObjectModel;

public class TimeOffsets
{
   public static void Main()
   {
      DateTime thisDate = new DateTime(2007, 3, 10, 0, 0, 0);
      DateTime dstDate = new DateTime(2007, 6, 10, 0, 0, 0);
      DateTimeOffset thisTime;

      thisTime = new DateTimeOffset(dstDate, new TimeSpan(-7, 0, 0));
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(-6, 0, 0));  
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(+1, 0, 0));
      ShowPossibleTimeZones(thisTime);
   }

   private static void ShowPossibleTimeZones(DateTimeOffset offsetTime)
   {
      TimeSpan offset = offsetTime.Offset;
      ReadOnlyCollection<TimeZoneInfo> timeZones;

      Console.WriteLine("{0} could belong to the following time zones:", 
                        offsetTime.ToString());
      // Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones();     
      // Iterate time zones 
      foreach (TimeZoneInfo timeZone in timeZones)
      {
         // Compare offset with offset for that date in that time zone
         if (timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset))
            Console.WriteLine("   {0}", timeZone.DisplayName);
      }
      Console.WriteLine();
   } 
}
// This example displays the following output to the console:
//       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
//          (GMT-07:00) Arizona
//          (GMT-08:00) Pacific Time (US & Canada)
//          (GMT-08:00) Tijuana, Baja California
//       
//       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
//          (GMT-06:00) Central America
//          (GMT-06:00) Central Time (US & Canada)
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
//          (GMT-06:00) Saskatchewan
//       
//       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
//          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
//          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
//          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
//          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
//          (GMT+01:00) West Central Africa
```

```vb
Imports System.Collections.ObjectModel

Module TimeOffsets
   Public Sub Main()
      Dim thisTime As DateTimeOffset 

      thisTime = New DateTimeOffset(#06/10/2007#, New TimeSpan(-7, 0, 0))
      ShowPossibleTimeZones(thisTime) 

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(-6, 0, 0))  
      ShowPossibleTimeZones(thisTime)

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(+1, 0, 0))
      ShowPossibleTimeZones(thisTime)
   End Sub

   Private Sub ShowPossibleTimeZones(offsetTime As DateTimeOffset)
      Dim offset As TimeSpan = offsetTime.Offset
      Dim timeZones As ReadOnlyCollection(Of TimeZoneInfo)

      Console.WriteLine("{0} could belong to the following time zones:", _
                        offsetTime.ToString())
      ' Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones()     
      ' Iterate time zones
      For Each timeZone As TimeZoneInfo In timeZones
         ' Compare offset with offset for that date in that time zone
         If timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset) Then
            Console.WriteLine("   {0}", timeZone.DisplayName)
         End If   
      Next
      Console.WriteLine()
   End Sub
End Module
' This example displays the following output to the console:
'       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
'          (GMT-07:00) Arizona
'          (GMT-08:00) Pacific Time (US & Canada)
'          (GMT-08:00) Tijuana, Baja California
'       
'       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
'          (GMT-06:00) Central America
'          (GMT-06:00) Central Time (US & Canada)
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
'          (GMT-06:00) Saskatchewan
'       
'       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
'          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
'          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
'          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
'          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
'          (GMT+01:00) West Central Africa
```

La sortie montre que chaque valeur de date et d'heure de cet exemple peut appartenir à au moins trois fuseaux horaires différents. La valeur [DateTimeOffset](xref:System.DateTimeOffset) de 6/10/2007 indique que si une valeur de date/heure représente une heure d’été, son décalage par rapport à l’heure UTC ne correspond pas nécessairement au décalage UTC de base du fuseau horaire d’origine ni au décalage par rapport à l’heure UTC indiquée dans son nom d’affichage. Cela signifie que, comme une valeur [DateTimeOffset](xref:System.DateTimeOffset) individuelle n’est pas fortement couplée avec son fuseau horaire, elle ne peut pas refléter la transition d’un fuseau horaire vers et depuis l’heure d’été. Ceci peut être particulièrement problématique quand des calculs de date et d’heure sont utilisés pour manipuler une valeur [DateTimeOffset](xref:System.DateTimeOffset). (Pour une présentation de la façon d’effectuer des opérations arithmétiques avec des dates et des heures en prenant en compte les règles d’ajustement d’un fuseau horaire, consultez [Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md).

## <a name="the-timespan-structure"></a>La structure TimeSpan

La structure [System.TimeSpan](xref:System.TimeSpan) représente un intervalle de temps. Ses deux utilisations courantes sont : 

* Refléter un intervalle de temps entre deux valeurs de date/heure. Par exemple, la soustraction d’une valeur [DateTime](xref:System.DateTime) d’une autre retourne une valeur [TimeSpan](xref:System.TimeSpan). 

* Mesurer un temps écoulé. Par exemple, la propriété [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) retourne une valeur [TimeSpan](xref:System.TimeSpan) qui reflète l’intervalle de temps écoulé depuis l’appel à l’une des méthodes [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch), qui commence à mesurer le temps écoulé.

Une valeur [TimeSpan](xref:System.TimeSpan) peut également être utilisée en remplacement d’une valeur [DateTime](xref:System.DateTime) quand cette valeur reflète un moment sans référence à une heure précise de la journée. Cette utilisation est similaire aux propriétés [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) et [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay), qui retournent une valeur [TimeSpan](xref:System.TimeSpan) représentant l’heure sans référence à une date. Par exemple, la structure [TimeSpan](xref:System.TimeSpan) peut être utilisée pour refléter les heures d’ouverture ou de fermeture quotidiennes d’un magasin, ou elle peut être utilisée pour représenter l’heure où se produit un événement régulier.

L’exemple suivant définit une structure `StoreInfo` qui inclut des objets [TimeSpan](xref:System.TimeSpan) pour les heures d’ouverture et de fermeture d’un magasin, ainsi qu’un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire du magasin. La structure comprend également deux méthodes, `IsOpenNow` et `IsOpenAt`, qui indiquent si le magasin est ouvert à une heure spécifiée par l'utilisateur, qui est supposé être dans le fuseau horaire local.  

```csharp
using System;

public struct StoreInfo
{
   public String store;
   public TimeZoneInfo tz;
   public TimeSpan open;
   public TimeSpan close;

   public bool IsOpenNow()
   {
      return IsOpenAt(DateTime.TimeOfDay);
   }

   public bool IsOpenAt(TimeSpan time)
   {
      TimeZoneInfo local = TimeZoneInfo.Local;
      TimeSpan offset = TimeZoneInfo.BaseUtcOffset;

      // Is the store in the same time zone?
      if (tz.Equals(local)) {
         return time >= open & time <= close;
      }
   }
}
```

```vb
Public Structure StoreInfo
   Dim store As String
   Dim tz As TimeZoneInfo
   Dim open As TimeSpan
   Dim close As TimeSpan

   Public Function IsOpenNow() As Boolean
      Return IsOpenAt(Date.Now.TimeOfDay)
   End Function

   Public Function IsOpenAt(time As TimeSpan) As Boolean
      Dim local As TimeZoneInfo = TimeZoneInfo.Local
      Dim offset As TimeSpan = TimeZoneInfo.Local.BaseUtcOffset

      ' Is the store in the same time zone?
      If tz.Equals(local) Then
         Return time >= open And time <= close
      Else
         Dim delta As TimeSpan = TimeSpan.Zero
         Dim storeDelta As TimeSpan = TimeSpan.Zero

         ' Is it daylight saving time in either time zone?
         If local.IsDaylightSavingTime(Date.Now.Date + time) Then
            delta = local.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         If tz.IsDaylightSavingTime(TimeZoneInfo.ConvertTime(Date.Now.Date + time, local, tz))
            storeDelta = tz.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         Dim comparisonTime As TimeSpan = time + (offset - tz.BaseUtcOffset).Negate() + (delta - storeDelta).Negate
         Return (comparisonTime >= open And comparisonTime <= close)
      End If
   End Function
End Structure
```

La structure `StoreInfo` peut ensuite être utilisée par le code du client comme ce qui suit. 

```csharp
public class Example
{
   public static void Main()
   {
      // Instantiate a StoreInfo object.
      var store103 = new StoreInfo();
      store103.store = "Store #103";
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
      // Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0);
      // Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0);

      Console.WriteLine("Store is open now at {0}: {1}",
                        DateTime.TimeOfDay, store103.IsOpenNow());
      TimeSpan[] times = { new TimeSpan(8, 0, 0), new TimeSpan(21, 0, 0),
                           new TimeSpan(4, 59, 0), new TimeSpan(18, 31, 0) };
      foreach (var time in times)
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time));
   }
}
// The example displays the following output:
//       Store is open now at 15:29:01.6129911: True
//       Store is open at 08:00:00: True
//       Store is open at 21:00:00: False
//       Store is open at 04:59:00: False
//       Store is open at 18:31:00: False
```

```vb
Module Example
   Public Sub Main()
      ' Instantiate a StoreInfo object.
      Dim store103 As New StoreInfo()
      store103.store = "Store #103"
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
      ' Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0)
      ' Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0)

      Console.WriteLine("Store is open now at {0}: {1}",
                        Date.Now.TimeOfDay, store103.IsOpenNow())
      Dim times() As TimeSpan = { New TimeSpan(8, 0, 0),
                                  New TimeSpan(21, 0, 0),
                                  New TimeSpan(4, 59, 0),
                                  New TimeSpan(18, 31, 0) }
      For Each time In times
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time))
      Next
   End Sub
End Module
' The example displays the following output:
'       Store is open now at 15:29:01.6129911: True
'       Store is open at 08:00:00: True
'       Store is open at 21:00:00: False
'       Store is open at 04:59:00: False
'       Store is open at 18:31:00: False
```

## <a name="the-timezoneinfo-class"></a>La classe TimeZoneInfo

La classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) représente les fuseaux horaires de la terre et permet la conversion de toute date/heure dans un fuseau horaire en son équivalent dans un autre fuseau horaire. La classe [TimeZoneInfo](xref:System.TimeZoneInfo) permet de travailler avec des dates et des heures de façon à ce qu’une valeur de date/heure identifie d’une manière non ambiguë un point unique dans le temps.

Dans certains cas, tirer parti de la classe [TimeZoneInfo](xref:System.TimeZoneInfo) peut nécessiter des efforts de développement supplémentaires. Les valeurs de date et d’heure ne sont pas étroitement couplées avec les fuseaux horaires auxquels elles appartiennent. Par conséquent, à moins que votre application ne fournisse un mécanisme permettant de lier une date/heure avec son fuseau horaire associé, une valeur de date/heure peut être facilement dissociée de son fuseau horaire. Une méthode pour lier ces informations consiste à définir une classe ou une structure qui contient à la fois la date/heure et son objet de fuseau horaire associé.

Tirer parti de la prise en charge des fuseaux horaires dans .NET est possible seulement si le fuseau horaire auquel appartient une valeur de date/heure est connu quand cet objet de date/heure est instancié. Ce n'est pas souvent le cas, en particulier dans les applications web ou réseau.

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)
