---
title: "Guide pratique : extraire le jour de la semaine à partir d’une date spécifique"
description: "Guide pratique pour extraire le jour de la semaine à partir d’une date spécifique"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 88a8f8b9-f5c9-4503-b968-84468b52bb8e
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: f7ae17ac6dbc23e18d18561d5e5ae7efc037c63e

---

# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a>Guide pratique : extraire le jour de la semaine à partir d’une date spécifique

.NET permet de déterminer facilement le jour ordinal de la semaine pour une date particulière, et d’afficher le nom du jour de la semaine localisé pour une date particulière. Le jour de la semaine correspondant à une date particulière est indiqué par une valeur énumérée contenue dans la propriété [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) ou [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek). Par contre, la récupération du nom du jour de la semaine est une opération de mise en forme qui peut être effectuée en appelant une méthode de mise en forme, comme la méthode `ToString` d’une valeur de date et d’heure ou la méthode [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Cette rubrique montre comment effectuer ces opérations de mise en forme.

## <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a>Pour extraire un nombre indiquant le jour de la semaine d'une date spécifique

1. Si vous utilisez la représentation sous forme de chaîne d’une date, convertissez-la en une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) à l’aide de la méthode [DateTime.Parse](xref:System.DateTime.Parse(System.String)) ou [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) statique.

2. Utilisez la propriété [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) ou [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek) pour récupérer une valeur [DayOfWeek](xref:System.DayOfWeek) qui indique le jour de la semaine.

3. Si nécessaire, effectuez un cast de la valeur [DayOfWeek](xref:System.DayOfWeek) en un entier. 

L'exemple suivant affiche un entier qui représente le jour de la semaine d'une date spécifique. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      DateTime dateValue = new DateTime(2008, 6, 11);
      Console.WriteLine((int) dateValue.DayOfWeek);      
   }
}
// The example displays the following output:
//       3
```

```vb
Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#
      Console.WriteLine(dateValue.DayOfWeek)           
   End Sub
End Module
' The example displays the following output:
'    3
```

## <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a>Pour extraire le nom abrégé du jour de la semaine d'une date spécifique

1. Si vous utilisez la représentation sous forme de chaîne d’une date, convertissez-la en une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) à l’aide de la méthode [DateTime.Parse](xref:System.DateTime.Parse(System.String)) ou [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) statique.

2. Vous pouvez extraire le nom abrégé du jour de la semaine au format de la culture actuelle ou d'une culture spécifique :

    a. Pour extraire le nom abrégé du jour de la semaine pour la culture actuelle, appelez la méthode d’instance [DateTime.ToString(String)](xref:System.DateTimeSystem.DateTime.ToString(System.String) ou [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) de la valeur de date et d’heure et indiquez la chaîne "ddd" comme paramètre de *format*. L'exemple suivant illustre l'appel de la méthode `ToString(String)`.
    
    ```csharp
    using System;

    public class Example
    {
       public static void Main()
       {
          DateTime dateValue = new DateTime(2008, 6, 11);
          Console.WriteLine(dateValue.ToString("ddd"));   
       }
    }
    // The example displays the following output:
    //       Wed
    ```

    ```vb
    Module Example
       Public Sub Main()
          Dim dateValue As Date = #6/11/2008#
          Console.WriteLine(dateValue.ToString("ddd"))    
       End Sub
    End Module
    ' The example displays the following output:
    '       Wed
    ```
    
    b. Pour extraire le nom abrégé du jour de la semaine pour une culture spécifique, appelez la méthode d’instance [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) de la valeur de date et d’heure. Indiquez la chaîne "ddd" comme paramètre de *format*. Indiquez comme paramètre de *fournisseur* un objet [CultureInfo](xref:System.Globalization.CultureInfo) ou [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui représente la culture au format de laquelle vous souhaitez récupérer le nom du jour de la semaine. Le code suivant illustre un appel de la méthode [ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) à l’aide d’un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente la culture fr-FR.
    
    ```csharp
    using System;
    using System.Globalization;

    public class Example
    {
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("ddd", 
                            new CultureInfo("fr-FR")));    
    }
    }
    // The example displays the following output:
    //       mer. 
    ```

    ```vb
    Imports System.Globalization

    Module Example
       Public Sub Main()
          Dim dateValue As Date = #6/11/2008#
          Console.WriteLine(dateValue.ToString("ddd", 
                            New CultureInfo("fr-FR")))    
       End Sub
    End Module
    ' The example displays the following output:
    '       mer.
    ```
    
## <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a>Pour extraire le nom complet du jour de la semaine d'une date spécifique

1. Si vous utilisez la représentation sous forme de chaîne d’une date, convertissez-la en une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) à l’aide de la méthode [DateTime.Parse](xref:System.DateTime.Parse(System.String)) ou [DateTimeOffset.Parse](xref:System.DateTimeOffset.Parse(System.String)) statique.

2. Vous pouvez extraire le nom abrégé du jour de la semaine au format de la culture actuelle ou d'une culture spécifique :

    a. Pour extraire le nom abrégé du jour de la semaine pour la culture actuelle, appelez la méthode d’instance [DateTime.ToString(String)](xref:System.DateTimeSystem.DateTime.ToString(System.String) ou [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) de la valeur de date et d’heure et indiquez la chaîne "dddd" comme paramètre de *format*. L'exemple suivant illustre l'appel de la méthode `ToString(String)`.
    
    ```csharp
    using System;

    public class Example
    {
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("dddd"));    
    }
    }
    // The example displays the following output:
    //       Wednesday
    ```

    ```vb
    Module Example
       Public Sub Main()
          Dim dateValue As Date = #6/11/2008#
          Console.WriteLine(dateValue.ToString("dddd"))
       End Sub
    End Module
    ' The example displays the following output:
    '       Wednesday
    ```
    
    b. Pour extraire le nom du jour de la semaine pour une culture spécifique, appelez la méthode d’instance [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) de la valeur de date et d’heure. Indiquez la chaîne "dddd" comme paramètre de *format*. Indiquez comme paramètre de *fournisseur* un objet [CultureInfo](xref:System.Globalization.CultureInfo) ou [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui représente la culture au format de laquelle vous souhaitez récupérer le nom du jour de la semaine. Le code suivant illustre un appel de la méthode [ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) à l’aide d’un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente la culture es-ES.
    
    ```csharp
    using System;
    using System.Globalization;

    public class Example
    {
    public static void Main()
    {
        DateTime dateValue = new DateTime(2008, 6, 11);
        Console.WriteLine(dateValue.ToString("dddd", 
                            new CultureInfo("es-ES")));    
    }
    }
    // The example displays the following output:
    //       miércoles.
    ```

    ```vb
    Imports System.Globalization

    Module Example
       Public Sub Main()
          Dim dateValue As Date = #6/11/2008#
          Console.WriteLine(dateValue.ToString("dddd", _
                            New CultureInfo("es-ES")))     
       End Sub
    End Module
    ' The example displays the following output:
    '       miércoles.
    ```
    
## <a name="example"></a>Exemple

L’exemple illustre des appels aux propriétés [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) et [DateTimeOffset.DayOfWeek](xref:System.DateTimeOffset.DayOfWeek) et aux méthodes [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String) ou [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) pour récupérer le nombre qui représente le jour de la semaine, le nom abrégé du jour de la semaine et le nom complet du jour de la semaine pour une date particulière. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string dateString = "6/11/2007";
      DateTime dateValue;
      DateTimeOffset dateOffsetValue;

      try
      {
         DateTimeFormatInfo dateTimeFormats;
         // Convert date representation to a date value
         dateValue = DateTime.Parse(dateString, CultureInfo.InvariantCulture);
         dateOffsetValue = new DateTimeOffset(dateValue, 
                                      TimeZoneInfo.Local.GetUtcOffset(dateValue));         

         // Convert date representation to a number indicating the day of week
         Console.WriteLine((int) dateValue.DayOfWeek);
         Console.WriteLine((int) dateOffsetValue.DayOfWeek);

         // Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"));
         Console.WriteLine(dateOffsetValue.ToString("ddd"));

         // Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"));
         Console.WriteLine(dateOffsetValue.ToString("dddd"));

         // Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", new CultureInfo("de-DE")));
         Console.WriteLine(dateOffsetValue.ToString("ddd", 
                                                     new CultureInfo("de-DE")));

         // Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = new CultureInfo("de-DE").DateTimeFormat;
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats));
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats));

         // Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", new CultureInfo("fr-FR")));
         Console.WriteLine(dateOffsetValue.ToString("ddd", 
                                                    new CultureInfo("fr-FR")));

         // Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = new CultureInfo("fr-FR").DateTimeFormat;
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats));
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats));
      }
      catch (FormatException)
      {
         Console.WriteLine("Unable to convert {0} to a date.", dateString);
      }
   }
}
// The example displays the following output:
//       1
//       1
//       Mon
//       Mon
//       Monday
//       Monday
//       Mo
//       Mo
//       Mo
//       Mo
//       lun.
//       lun.
//       lundi
//       lundi
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateString As String = "6/11/2007"
      Dim dateValue As Date
      Dim dateOffsetValue As DateTimeOffset

      Try
         Dim dateTimeFormats As DateTimeFormatInfo
         ' Convert date representation to a date value
         dateValue = Date.Parse(dateString, CultureInfo.InvariantCulture)
         dateOffsetValue = New DateTimeOffset(dateValue, _
                                     TimeZoneInfo.Local.GetUtcOffset(dateValue))            
         ' Convert date representation to a number indicating the day of week
         Console.WriteLine(dateValue.DayOfWeek)
         Console.WriteLine(dateOffsetValue.DayOfWeek)

         ' Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"))
         Console.WriteLine(dateOffsetValue.ToString("ddd"))

         ' Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"))
         Console.WriteLine(dateOffsetValue.ToString("dddd"))

         ' Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("de-DE")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("de-DE")))

         ' Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("de-DE").DateTimeFormat
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats))

         ' Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("fr-FR")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("fr-FR")))

         ' Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("fr-FR").DateTimeFormat
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'       1
'       1
'       Mon
'       Mon
'       Monday
'       Monday
'       Mo
'       Mo
'       Mo
'       Mo
'       lun.
'       lun.
'       lundi
'       lundi
```

Des langages spécifiques peuvent fournir des fonctionnalités similaires aux fonctionnalités offertes par .NET, ou complémentaires de celles-ci. Par exemple, Visual Basic comprend deux de ces fonctions :

* `Weekday`, qui retourne un nombre qui indique le jour de la semaine d'une date particulière. Il considère que la valeur ordinale du premier jour de la semaine est un, tandis que la propriété [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) considère que cette valeur est égale à zéro.

* `WeekdayName`, qui retourne, dans la culture actuelle, le nom du jour de la semaine correspondant au nombre d'un jour de la semaine.

L'exemple suivant illustre l'utilisation des fonctions Visual Basic `Weekday` et `WeekdayName`.

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim dateValue As Date = #6/11/2008#

      ' Get weekday number using Visual Basic Weekday function
      Console.WriteLine(Weekday(dateValue))                 ' Displays 4
      ' Compare with .NET DateTime.DayOfWeek property
      Console.WriteLine(dateValue.DayOfWeek)                ' Displays 3

      ' Get weekday name using Weekday and WeekdayName functions
      Console.WriteLine(WeekdayName(Weekday(dateValue)))    ' Displays Wednesday

      ' Change culture to de-DE
      Dim originalCulture As CultureInfo = Thread.CurrentThread.CurrentCulture
      Thread.CurrentThread.CurrentCulture = New CultureInfo("de-DE")
      ' Get weekday name using Weekday and WeekdayName functions
      Console.WriteLine(WeekdayName(Weekday(dateValue)))   ' Displays Donnerstag

      ' Restore original culture
      Thread.CurrentThread.CurrentCulture = originalCulture   
   End Sub
End Module
``` 

Vous pouvez également recourir à la valeur retournée par la propriété [Datetime.DayOfWeek](xref:System.DateTime.DayOfWeek) pour récupérer le nom du jour de la semaine d’une date particulière. Pour ce faire, vous avez uniquement besoin d’appeler la méthode [Enum.ToString](xref:System.Enum.ToString(System.String)) sur la valeur [DayOfWeek](xref:System.DayOfWeek) retournée par la propriété. Toutefois, cette technique ne génère pas un nom de jour de la semaine localisé dans la culture actuelle, comme l'illustre l'exemple suivant. 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      // Change current culture to fr-FR
      CultureInfo originalCulture = Thread.CurrentThread.CurrentCulture;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("fr-FR");

      DateTime dateValue = new DateTime(2008, 6, 11);
      // Display the DayOfWeek string representation
      Console.WriteLine(dateValue.DayOfWeek.ToString());   
      // Restore original current culture
      Thread.CurrentThread.CurrentCulture = originalCulture;
   }
}
// The example displays the following output:
//       Wednesday
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateString As String = "6/11/2007"
      Dim dateValue As Date
      Dim dateOffsetValue As DateTimeOffset

      Try
         Dim dateTimeFormats As DateTimeFormatInfo
         ' Convert date representation to a date value
         dateValue = Date.Parse(dateString, CultureInfo.InvariantCulture)
         dateOffsetValue = New DateTimeOffset(dateValue, _
                                     TimeZoneInfo.Local.GetUtcOffset(dateValue))            
         ' Convert date representation to a number indicating the day of week
         Console.WriteLine(dateValue.DayOfWeek)
         Console.WriteLine(dateOffsetValue.DayOfWeek)

         ' Display abbreviated weekday name using current culture
         Console.WriteLine(dateValue.ToString("ddd"))
         Console.WriteLine(dateOffsetValue.ToString("ddd"))

         ' Display full weekday name using current culture
         Console.WriteLine(dateValue.ToString("dddd"))
         Console.WriteLine(dateOffsetValue.ToString("dddd"))

         ' Display abbreviated weekday name for de-DE culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("de-DE")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("de-DE")))

         ' Display abbreviated weekday name with de-DE DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("de-DE").DateTimeFormat
         Console.WriteLine(dateValue.ToString("ddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("ddd", dateTimeFormats))

         ' Display full weekday name for fr-FR culture
         Console.WriteLine(dateValue.ToString("ddd", New CultureInfo("fr-FR")))
         Console.WriteLine(dateOffsetValue.ToString("ddd", _
                                                    New CultureInfo("fr-FR")))

         ' Display abbreviated weekday name with fr-FR DateTimeFormatInfo object
         dateTimeFormats = New CultureInfo("fr-FR").DateTimeFormat
         Console.WriteLine(dateValue.ToString("dddd", dateTimeFormats))
         Console.WriteLine(dateOffsetValue.ToString("dddd", dateTimeFormats))
      Catch e As FormatException
         Console.WriteLine("Unable to convert {0} to a date.", dateString)
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'       1
'       1
'       Mon
'       Mon
'       Monday
'       Monday
'       Mo
'       Mo
'       Mo
'       Mo
'       lun.
'       lun.
'       lundi
'       lundi
```

## <a name="see-also"></a>Voir aussi

[Exécution d’opérations de mise en forme](performing-formatting-operations.md)

[Chaînes de format de date et d’heure standard](standard-datetime.md)

[Chaînes de format de date et d’heure personnalisées](custom-datetime.md)
    



<!--HONumber=Nov16_HO1-->


