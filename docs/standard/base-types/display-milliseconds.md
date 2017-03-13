---
title: "Guide pratique : afficher les millisecondes dans les valeurs de date et d’heure"
description: "Guide pratique pour afficher les millisecondes dans les valeurs de date et d’heure"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 78599e33-1c3f-4335-b320-751e35906338
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 7a110cf28ac8de558cd1460c61a650fc8a80e51a
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Guide pratique : afficher les millisecondes dans les valeurs de date et d’heure

Les méthodes de mise en forme de date et d’heure par défaut, telles que [DateTime.ToString()](xref:System.DateTime.ToString), incluent les heures, les minutes et les secondes d’une valeur d’heure, mais excluent son composant « millisecondes ». Cette rubrique montre comment inclure le composant « millisecondes » d’une date et d’une heure dans des chaînes de date et d’heure mises en forme.

## <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Pour afficher le composant « millisecondes » d’une valeur DateTime

1. Si vous utilisez la représentation sous forme de chaîne d’une date, convertissez-la en une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) à l’aide de la méthode [DateTime.Parse(String)](xref:System.DateTime.Parse(System.String)) ou [DateTimeOffset.Parse(String)](xref:System.DateTimeOffset.Parse(System.String)) statique.

2. Pour extraire la représentation sous forme de chaîne du composant « millisecondes » d’une heure, appelez la méthode [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String)) de la valeur de date et d’heure, puis transmettez le modèle de format personnalisé `fff` ou `FFF` seul ou avec d’autres spécificateurs de format personnalisé comme paramètre de format.

## <a name="example"></a>Exemple

L’exemple affiche le composant « milliseconde » d’une valeur [DateTime](xref:System.DateTime) et d’une valeur [DateTimeOffset](xref:System.DateTimeOffset) sur la console, à la fois seul et inclus dans une chaîne de date et d’heure plus longue. 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class MillisecondDisplay
{
   public static void Main()
   {
      string dateString = "7/16/2008 8:32:45.126 AM";

      try
      {
         DateTime dateValue = DateTime.Parse(dateString);
         DateTimeOffset dateOffsetValue = DateTimeOffset.Parse(dateString);

         // Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", 
                           dateValue.ToString("fff"));
         Console.WriteLine("Millisecond component only: {0}", 
                           dateOffsetValue.ToString("fff"));

         // Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", 
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"));

         // Append millisecond pattern to current culture's full date time pattern
         string fullPattern = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern;
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff");

         // Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", 
                           dateValue.ToString(fullPattern));
         Console.WriteLine("Modified full date time pattern: {0}",
                           dateOffsetValue.ToString(fullPattern));
      }
      catch (FormatException)
      {
         Console.WriteLine("Unable to convert {0} to a date.", dateString);
      }
   }
}
// The example displays the following output if the current culture is en-US:
//    Millisecond component only: 126
//    Millisecond component only: 126
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
//    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

```vb
Imports System.Globalization
Imports System.Text.REgularExpressions

Module MillisecondDisplay
   Public Sub Main()

      Dim dateString As String = "7/16/2008 8:32:45.126 AM"

      Try
         Dim dateValue As Date = Date.Parse(dateString)
         Dim dateOffsetValue As DateTimeOffset = DateTimeOffset.Parse(dateString)

         ' Display Millisecond component alone.
         Console.WriteLine("Millisecond component only: {0}", _
                           dateValue.ToString("fff"))
         Console.WriteLine("Millisecond component only: {0}", _
                           dateOffsetValue.ToString("fff"))

         ' Display Millisecond component with full date and time.
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))                        
         Console.WriteLine("Date and Time with Milliseconds: {0}", _
                           dateOffsetValue.ToString("MM/dd/yyyy hh:mm:ss.fff tt"))

         ' Append millisecond pattern to current culture's full date time pattern
         Dim fullPattern As String = DateTimeFormatInfo.CurrentInfo.FullDateTimePattern
         fullPattern = Regex.Replace(fullPattern, "(:ss|:s)", "$1.fff")

         ' Display Millisecond component with modified full date and time pattern.
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateValue.ToString(fullPattern))                        
         Console.WriteLine("Modified full date time pattern: {0}", _
                           dateOffsetValue.ToString(fullPattern))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)      
      End Try
   End Sub
End Module
' The example displays the following output if the current culture is en-US:
'    Millisecond component only: 126
'    Millisecond component only: 126
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Date and Time with Milliseconds: 07/16/2008 08:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
'    Modified full date time pattern: Wednesday, July 16, 2008 8:32:45.126 AM
```

Le modèle de format `fff` inclut les zéros de fin éventuels dans la valeur en millisecondes. Le modèle de format `FFF` les supprime. L’exemple suivant illustre cette différence.

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine(dateValue.ToString("fff"));    
Console.WriteLine(dateValue.ToString("FFF"));
// The example displays the following output to the console:
//    180
//    18 
```

```vb
Dim dateValue As New Date(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLIne(dateValue.ToString("fff"))    
Console.WriteLine(dateValue.ToString("FFF"))
' The example displays the following output to the console:
'    180
'    18
```

Quand vous définissez un spécificateur de format personnalisé complet qui inclut le composant « millisecondes » d’une date et d’une heure, vous pouvez être confronté au problème suivant : le format défini peut être un format codé en dur qui ne correspond pas à la disposition des éléments d’heure dans la culture actuelle de l’application. Une meilleure solution consiste à récupérer l’un des modèles d’affichage de la date et de l’heure définis par l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) de la culture actuelle et à le modifier pour inclure les millisecondes. L’exemple illustre également cette approche. Il récupère de la propriété [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) le modèle de date et d’heure complet de la culture actuelle, puis insère le modèle personnalisé `.ffff` après son modèle des secondes. Notez que l’exemple utilise une expression régulière pour effectuer cette opération dans un seul appel de méthode.

Vous pouvez également utiliser un spécificateur de format personnalisé pour afficher une partie fractionnaire des secondes autre que les millisecondes. Par exemple, le spécificateur de format personnalisé `f` ou `F` affiche les dixièmes de seconde, le spécificateur de format personnalisé `ff` ou `FF` affiche les centièmes de seconde, tandis que le spécificateur de format personnalisé `ffff` ou `FFFF` affiche les dix millièmes de seconde. La partie fractionnaire d’une milliseconde est tronquée au lieu d’être arrondie dans la chaîne retournée. Ces spécificateurs de format sont utilisés dans l’exemple suivant.

```csharp
DateTime dateValue = new DateTime(2008, 7, 16, 8, 32, 45, 180); 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"));
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"));      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"));
// The example displays the following output to the console:
//    45.1 seconds
//    45.18 seconds
//    45.1800 seconds
```

```vb
Dim dateValue As New DateTime(2008, 7, 16, 8, 32, 45, 180) 
Console.WriteLine("{0} seconds", dateValue.ToString("s.f"))
Console.WriteLine("{0} seconds", dateValue.ToString("s.ff"))      
Console.WriteLine("{0} seconds", dateValue.ToString("s.ffff"))
' The example displays the following output to the console:
'    45.1 seconds
'    45.18 seconds
'    45.1800 seconds
```

> [!NOTE]
> Il est possible d’afficher de très petites unités fractionnaires d’une seconde, telles que les dix millièmes de seconde ou les cent millièmes de seconde. Toutefois, ces valeurs peuvent ne pas être significatives. La précision des valeurs de date et d’heure dépend de la résolution de l’horloge système.

## <a name="see-also"></a>Voir aussi

[System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)

[Chaînes de format de date et d’heure personnalisées](custom-datetime.md)


