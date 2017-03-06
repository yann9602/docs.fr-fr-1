---
title: "Guide pratique : instancier un objet TimeZoneInfo"
description: Guide pratique pour instancier un objet TimeZoneInfo
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Guide pratique : instancier un objet TimeZoneInfo

La façon la plus courante d’instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) consiste à récupérer les informations le concernant à partir du système d’exploitation. Cette rubrique explique comment instancier un objet [TimeZoneInfo](xref:System.TimeZoneInfo) à partir du système local.

## <a name="to-instantiate-a-timezoneinfo-object"></a>Pour instancier un objet TimeZoneInfo

1. Déclarez un objet [TimeZoneInfo](xref:System.TimeZoneInfo).

2. Appelez la méthode `static` (`Shared` en Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)).

3. Gérez toutes les exceptions éventuelles levées par la méthode.

## <a name="example"></a>Exemple

Le code suivant récupère un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire EST et affiche l’heure EST qui correspond à l’heure locale.

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

Le paramètre unique de la méthode [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) est l’identificateur du fuseau horaire que vous souhaitez récupérer, qui correspond à la propriété [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) de l’objet. L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique. Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long. Dans la plupart des cas, sa valeur correspond à la propriété [StandardName](xref:System.TimeZoneInfo.StandardName) d’un objet [TimeZoneInfo](xref:System.TimeZoneInfo), qui est utilisée pour fournir le nom de l’heure d’hiver du fuseau horaire. Toutefois, il existe des exceptions. Pour vous assurer que l’identificateur fourni est valide, il est recommandé d’énumérer les fuseaux horaires disponibles sur votre système et de noter les identificateurs associés. Pour voir une illustration, consultez [Guide pratique : énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md). La rubrique [Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md) contient également la liste des identificateurs de fuseau horaire sélectionnés.

Si le fuseau horaire est trouvé, la méthode retourne son objet [TimeZoneInfo](xref:System.TimeZoneInfo). Si le fuseau horaire est trouvé, mais que ses données sont endommagées ou incomplètes, la méthode lève une exception [InvalidTimeZoneException](xref:System.InvalidTimeZoneException). 

## <a name="see-also"></a>Voir aussi

[Dates, heures et fuseaux horaires](index.md)

[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md)
