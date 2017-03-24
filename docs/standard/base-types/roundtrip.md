---
title: "Guide pratique : effectuer un aller-retour de valeurs de date et d’heure"
description: "Guide pratique pour effectuer un aller-retour de valeurs de date et d’heure"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 15690f18-1bb9-4bb8-bc11-0b737e2f0859
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 79c4da0cc6b4436fcbd5b345e23b387f2ad933d1
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-round-trip-date-and-time-values"></a>Guide pratique : effectuer un aller-retour de valeurs de date et d’heure

Dans de nombreuses applications, une valeur de date et d’heure est destinée à identifier clairement un point unique dans le temps. Cette rubrique montre comment enregistrer et restaurer une valeur [DateTime](xref:System.DateTime) et une valeur [DateTimeOffset](xref:System.DateTimeOffset) afin que la valeur restaurée identifie la même heure que la valeur enregistrée.

## <a name="to-round-trip-a-datetime-value"></a>Pour effectuer un aller-retour d’une valeur DateTime

1. Convertissez la valeur [DateTime](xref:System.DateTime) en sa représentation sous forme de chaîne en appelant la méthode [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) avec le spécificateur de format « o ».

2. Enregistrez la représentation sous forme de chaîne de la valeur [DateTime](xref:System.DateTime) dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.

3. Récupérez la chaîne qui représente la valeur [DateTime](xref:System.DateTime).

4. Appelez la méthode [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)), puis passez [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) comme valeur du paramètre *DateTimeStyles*.

L’exemple suivant montre comment effectuer un aller-retour d’une valeur [DateTime](xref:System.DateTime).

```csharp
const string fileName = @".\DateFile.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTime dateToSave = DateTime.SpecifyKind(new DateTime(2008, 6, 12, 18, 45, 15), 
                                           DateTimeKind.Local);
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} ({1}) to {2}.", 
                  dateToSave.ToString(), 
                  dateToSave.Kind.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTime restoredDate;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), 
                                              fileName, 
                                              restoredDate.Kind.ToString());
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
//    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
//    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

```vb
Const fileName As String = ".\DateFile.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As Date = DateTime.SpecifyKind(#06/12/2008 6:45:15 PM#, _
                                              DateTimeKind.Local)
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} ({1}) to {2}.", dateToSave.ToString(), _
                  dateToSave.Kind.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDate As Date

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDate = DateTime.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} ({2}) from {1}.", restoredDate.ToString(), _
                  fileName, restoredDAte.Kind.ToString())
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM (Local) to 2008-06-12T18:45:15.0000000-05:00.
'    Wrote 2008-06-12T18:45:15.0000000-05:00 to .\DateFile.txt.
'    Read 6/12/2008 6:45:15 PM (Local) from .\DateFile.txt.
```

Lors de l’aller-retour d’une valeur [DateTime](xref:System.DateTime), cette technique permet de conserver correctement l’heure pour toutes les heures locales et universelles. Par exemple, si une valeur [DateTime](xref:System.DateTime) locale est enregistrée sur un système situé dans le fuseau horaire Pacifique (États-Unis) et qu’elle est restaurée sur un système situé dans le fuseau horaire Centre (États-Unis), la date et l’heure restaurées ont deux heures de retard par rapport à l’heure d’origine, ce qui reflète le décalage horaire entre ces deux fuseaux horaires. En revanche, cette technique n’est pas nécessairement exacte pour les heures non spécifiées. Toutes les valeurs [DateTime](xref:System.DateTime) dont la propriété [Kind](xref:System.DateTime.Kind) a la valeur [Unspecified](xref:System.DateTimeKind.Unspecified) sont traitées comme s’il s’agissait d’heures locales. Si ce n’est pas le cas, la valeur [DateTime](xref:System.DateTime) n’identifie pas correctement le point adéquat dans le temps. La solution pour contourner cette limitation consiste à associer étroitement une valeur de date et d’heure avec son fuseau horaire pour l’opération d’enregistrement et de restauration.

## <a name="to-round-trip-a-datetimeoffset-value"></a>Pour effectuer un aller-retour d’une valeur DateTimeOffset

Convertissez la valeur [DateTimeOffset](xref:System.DateTimeOffset) en sa représentation sous forme de chaîne en appelant la méthode [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) avec le spécificateur de format « o ».

2. Enregistrez la représentation sous forme de chaîne de la valeur [DateTimeOffset](xref:System.DateTimeOffset) dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.

3. Récupérez la chaîne qui représente la valeur [DateTimeOffset](xref:System.DateTimeOffset).

4. Appelez la méthode [DateTimeOffset.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTimeOffset.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)), puis passez [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) comme valeur du paramètre *styles*.

L’exemple suivant montre comment effectuer un aller-retour d’une valeur [DateTimeOffset](xref:System.DateTimeOffset).

```csharp
const string fileName = @".\DateOff.txt";

StreamWriter outFile = new StreamWriter(fileName);

// Save DateTime value.
DateTimeOffset dateToSave = new DateTimeOffset(2008, 6, 12, 18, 45, 15, 
                                               new TimeSpan(7, 0, 0));
string dateString = dateToSave.ToString("o");      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), 
                  dateString);      
outFile.WriteLine(dateString);
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName);
outFile.Close();

// Restore DateTime value.
DateTimeOffset restoredDateOff;

StreamReader inFile = new StreamReader(fileName);
dateString = inFile.ReadLine();
inFile.Close();
restoredDateOff = DateTimeOffset.Parse(dateString, null, 
                                       DateTimeStyles.RoundtripKind);
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), 
                  fileName);
// The example displays the following output:
//    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
//    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
//    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

```vb
Const fileName As String = ".\DateOff.txt"

Dim outFile As New StreamWriter(fileName)

' Save DateTime value.
Dim dateToSave As New DateTimeOffset(2008, 6, 12, 18, 45, 15, _
                                     New TimeSpan(7, 0, 0))
Dim dateString As String = dateToSave.ToString("o")      
Console.WriteLine("Converted {0} to {1}.", dateToSave.ToString(), dateString)      
outFile.WriteLine(dateString)
Console.WriteLine("Wrote {0} to {1}.", dateString, fileName)
outFile.Close()   

' Restore DateTime value.
Dim restoredDateOff As DateTimeOffset

Dim inFile As New StreamReader(fileName)
dateString = inFile.ReadLine()
inFile.Close()
restoredDateOff = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundTripKind)
Console.WriteLine("Read {0} from {1}.", restoredDateOff.ToString(), fileName)
' The example displays the following output:
'    Converted 6/12/2008 6:45:15 PM +07:00 to 2008-06-12T18:45:15.0000000+07:00.
'    Wrote 2008-06-12T18:45:15.0000000+07:00 to .\DateOff.txt.
'    Read 6/12/2008 6:45:15 PM +07:00 from .\DateOff.txt.
```

Cette technique identifie toujours clairement une valeur [DateTimeOffset](xref:System.DateTimeOffset) comme point unique dans le temps. La valeur peut ensuite être convertie en temps universel coordonné (UTC) en appelant la méthode [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime), ou elle peut être convertie en heure d’un fuseau horaire particulier en appelant la méthode [DateTimeOffset.ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) ou [TimeZoneInfo.ConvertTime (TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo). La principale limitation de cette technique est que les opérations arithmétiques de date et heure, effectuées sur une valeur [DateTimeOffset](xref:System.DateTimeOffset) qui représente l’heure dans un fuseau horaire particulier, risquent de ne pas produire des résultats exacts pour ce fuseau horaire. En effet, quand une valeur [DateTimeOffset](xref:System.DateTimeOffset) est instanciée, elle est dissociée de son fuseau horaire. Ainsi, les règles d’ajustement de ce fuseau horaire ne sont plus applicables quand vous effectuez des calculs de date et d’heure. Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut à la fois une valeur de date et heure et son fuseau horaire correspondant.

## <a name="see-also"></a>Voir aussi

[Exécution d’opérations de mise en forme](performing-formatting-operations.md)

[Chaînes de format de date et d’heure standard](standard-datetime.md)


