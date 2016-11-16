---
title: "Conversion d’heures entre fuseaux horaires"
description: "Conversion d’heures entre fuseaux horaires"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 051a4891336470e79bda9d7b9bb1be4e2c9187b8

---

# <a name="converting-times-between-time-zones"></a>Conversion d’heures entre fuseaux horaires

Il devient de plus en plus important pour une application qui fonctionne avec des dates et des heures de gérer les différences entre les fuseaux horaires. Une application ne peut plus supposer que toutes les heures puissent être exprimées selon l’heure locale, qui est l’heure disponible à partir de la structure [System.DateTime](xref:System.DateTime). Par exemple, une page web qui affiche l’heure actuelle dans la partie Est des États-Unis ne sera pas crédible pour un client d’Asie orientale. Cette rubrique explique comment convertir des heures d’un fuseau horaire vers un autre, et comment convertir des valeurs [System.DateTimeOffset](xref:System.DateTimeOffset) qui ne prennent pas complètement en charge les fuseaux horaires.

## <a name="converting-to-coordinated-universal-time"></a>Conversion en heure UTC

Le temps universel coordonné (UTC) est une norme d’heure atomique de haute précision. Les fuseaux horaires du monde sont exprimés comme décalages positifs ou négatifs par rapport à l’heure UTC. Par conséquent, l’heure UTC fournit une sorte d’heure neutre du point de vue des fuseaux horaires. L’utilisation de l’heure UTC est recommandée lorsque la portabilité de la date et de l’heure entre les ordinateurs est importante. La conversion de fuseaux horaires individuels en heure UTC facilite les comparaisons d’heures.

> [!NOTE]
> Vous pouvez également sérialiser une structure [DateTimeOffset](xref:System.DateTimeOffset) pour représenter de façon non ambiguë un point unique dans le temps. Étant donné que les objets [DateTimeOffset](xref:System.DateTimeOffset) stockent une valeur de date et d’heure, ainsi que son décalage par rapport à l’heure UTC, ils représentent toujours un point particulier dans le temps, associé à l’heure UTC.

Pour convertir une heure en heure UTC, le plus simple consiste à appeler la méthode `static` (`Shared` en Visual Basic) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx). 

> [!IMPORTANT]
> La méthode `TimeZoneInfo.ConvertTimeToUtc(DateTime)` n’est pas disponible dans .NET Core. 

La conversion exacte effectuée par cette méthode dépend de la valeur de la propriété [Kind](xref:System.DateTime.Kind) du paramètre `DateTime`, comme illustré dans le tableau ci-dessous.

Propriété [DateTime.Kind](xref:System.DateTimeKind) | Conversion
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | Convertit l’heure locale en heure UTC.
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | Suppose que le paramètre `DateTime` est l’heure locale et convertit l’heure locale en heure UTC.
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | Retourne le paramètre `DateTime` inchangé.

Le code suivant convertit l’heure locale actuelle en heure UTC et affiche le résultat dans la console.

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
>La méthode [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) ne produit pas nécessairement les mêmes résultats que les méthodes [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) et [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime). Si le fuseau horaire local du système hôte inclut plusieurs règles d’ajustement, [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) applique la règle appropriée à une date et une heure particulières. Les deux autres méthodes appliquent toujours la dernière règle d’ajustement.

Si la valeur de date et d’heure ne représente pas l’heure locale ni l’heure UTC, la méthode [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) retournera probablement un résultat erroné. Toutefois, vous pouvez utiliser la méthode [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) pour convertir la date et l’heure d’un fuseau horaire spécifié. (Pour plus d’informations sur la récupération d’un objet TimeZoneInfo qui représente le fuseau horaire de destination, consultez [Recherche des fuseaux horaires définis sur un système Local](finding-the-time-zones-on-local-system.md). Le code suivant utilise la méthode [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) pour convertir l’heure du fuseau horaire Est en heure UTC.

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

Notez que cette méthode lève une exception [ArgumentException](xref:System.ArgumentException) si la propriété [Kind](xref:System.DateTimeKind) de l’objet [DateTime](xref:System.DateTime) et le fuseau horaire ne correspondent pas. Une incompatibilité se produit si la propriété Kind a la valeur [DateTimeKind.Local](xref:System.DateTimeKind.Local) mais que l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) ne représente pas le fuseau horaire local, ou si la propriété Kind a la valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) mais que l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) n’est pas égal à [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).

Toutes ces méthodes prennent des valeurs [DateTime](xref:System.DateTime) comme paramètres et retournent une valeur [DateTime](xref:System.DateTime). Pour les valeurs [DateTimeOffset](xref:System.DateTimeOffset), la structure [DateTimeOffset](xref:System.DateTimeOffset) a une méthode d’instance [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) qui convertit la date et l’heure de l’instance actuelle en heure UTC. L’exemple suivant appelle la méthode [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) pour convertir une heure locale et plusieurs autres heures en temps universel coordonné (UTC).

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a>Conversion de l’heure UTC dans un fuseau horaire désigné

Pour convertir l’heure UTC en heure locale, consultez la section [Conversion de l’heure UTC en heure locale](#converting-utc-to-local-time) qui suit. 

Pour convertir l’heure UTC en heure propre à un fuseau horaire que vous désignez, appelez la méthode [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx). 

> [!IMPORTANT]
> La méthode « TimeZoneInfo.ConvertTimeFromUtc » n’est pas disponible actuellement dans .NET Core. 

Cette méthode accepte deux paramètres :

* L’heure UTC à convertir. Ce doit être une valeur [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a pour valeur [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) ou [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified). 

* Le fuseau horaire vers lequel convertir l’heure UTC. 

Le code suivant convertit l’heure UTC en heure propre au fuseau horaire Centre.

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a>Conversion de l’heure UTC en heure locale

Pour convertir une heure UTC en heure locale, appelez la méthode [DateTime.ToLocalTime](xref:System.DateTime) de l’objet [DateTime](xref:System.DateTime) dont vous souhaitez convertir l’heure. Le comportement exact de cette méthode dépend de la valeur de la propriété [Kind](xref:System.DateTime.Kind) de l’objet, comme illustré dans le tableau ci-dessous.

Propriété [DateTime.Kind](xref:System.DateTimeKind) | Conversion
---------------------------------------------------------------------------------------------- | ----------
[DateTimeKind.Local](xref:System.DateTimeKind.Local) | Retourne la valeur [DateTime](xref:System.DateTime) inchangée.
[DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) | Suppose que la valeur [DateTime](xref:System.DateTime) est une heure UTC et convertit l’heure UTC en heure locale.
[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) | Convertit la valeur [DateTime](xref:System.DateTime) en heure locale.

## <a name="converting-between-any-two-time-zones"></a>Conversion entre deux fuseaux horaires quelconques

Vous pouvez convertir une heure entre deux fuseaux horaires quelconques à l’aide de la méthode static [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)). Les paramètres de cette méthode sont la valeur [DateTime](xref:System.DateTime) à convertir, un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire de la valeur de date et d’heure, et un objet [TimeZoneInfo](xref:System.TimeZoneInfo) qui représente le fuseau horaire vers lequel convertir la valeur de date et d’heure.

La méthode exige que la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure à convertir et l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) ou l’identificateur de fuseau horaire qui représente son fuseau horaire correspondent l’une à l’autre. Sinon, une exception [ArgumentException](xref:System.ArgumentException) est levée. Par exemple, si la propriété [Kind](xref:System.DateTime.Kind) de la valeur de date et d’heure est [DateTimeKind.Local](xref:System.DateTimeKind.Local), une exception est levée si l’objet [TimeZoneInfo](xref:System.TimeZoneInfo) transmis comme paramètre à la méthode n’est pas égal à [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local). Une exception est également levée si l’identificateur transmis comme paramètre à la méthode n’est pas égal à [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id).

L’exemple suivant utilise la méthode [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) pour convertir l’heure d’Hawaï en heure locale.

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a>Conversion de valeurs DateTimeOffset

Les valeurs de date et d’heure représentées par des objets [System.DateTimeOffset](xref:System.DateTimeOffset) ne prennent pas complètement en charge les fuseaux horaires, car l’objet est dissocié de son fuseau horaire au moment où il est instancié. Toutefois, dans de nombreux cas, une application doit simplement convertir une date et une heure en fonction de deux décalages différents par rapport à l’heure UTC plutôt qu’en fonction de l’heure dans des fuseaux horaires particuliers. Pour effectuer cette conversion, vous pouvez appeler la méthode [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) de l’instance actuelle. Le seul paramètre de la méthode est [TimeSpan](xref:System.TimeSpan), qui représente le décalage de la nouvelle valeur de date et d’heure que la méthode doit retourner.  

Par exemple, si la date et l’heure d’une demande de page web de l’utilisateur sont connues et sont sérialisées comme chaîne au format MM/jj/aaaa hh:mm:ss zzzz, la méthode `ReturnTimeOnServer` qui suit convertit cette valeur de date et d’heure en date et heure sur le serveur web.

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

Si la chaîne « 1/9/2007 5:32:07 -05:00 » est transmise à la méthode, représentant la date et l’heure dans un fuseau horaire en retard de cinq heures par rapport à l’heure UTC, elle retourne 1/9/2007 3:32:07 AM -07:00 pour un serveur situé dans le fuseau horaire Pacifique.

La classe [TimeZoneInfo](xref:System.TimeZoneInfo) inclut également une méthode surchargée [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) qui effectue des conversions de fuseau horaire avec des valeurs [System.DateTimeOffset](xref:System.DateTimeOffset). Les paramètres de la méthode sont une valeur [System.DateTimeOffset](xref:System.DateTimeOffset) et une référence au fuseau horaire vers lequel l’heure doit être convertie. L’appel de la méthode retourne une valeur [System.DateTimeOffset](xref:System.DateTimeOffset). Par exemple, la méthode `ReturnTimeOnServer` de l’exemple précédent peut être réécrite comme suit pour appeler la méthode [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)).

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a>Voir aussi

[TimeZoneInfo](xref:System.TimeZoneInfo)

[Dates, heures et fuseaux horaires](index.md)

[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md)





<!--HONumber=Nov16_HO1-->


