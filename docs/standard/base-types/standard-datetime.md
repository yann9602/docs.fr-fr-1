---
title: "Chaînes de format de date et d’heure standard"
description: "Chaînes de format de date et d’heure standard"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: be239871-10cc-4949-b548-200bb260630a
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: f9247bae0d290db570b8cd8885e654524ea2f36b
ms.lasthandoff: 03/13/2017

---

# <a name="standard-date-and-time-format-strings"></a>Chaînes de format de date et d’heure standard

Une chaîne de format de date et d'heure standard utilise un spécificateur de format unique pour définir la représentation textuelle d'une valeur de date et d'heure. Toute chaîne de format de date et d’heure contenant plusieurs caractères, notamment un espace, est interprétée comme une chaîne de format de date et d’heure personnalisée. Pour plus d’informations, consultez [Chaînes de format de date et d’heure personnalisées](custom-datetime.md). Une chaîne de format standard ou personnalisée peut être utilisée de deux façons :

* Pour définir la chaîne qui résulte d'une opération de mise en forme.

* Pour définir la représentation textuelle d’une valeur de date et d’heure pouvant être convertie en valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset) par une opération d’analyse.

Les chaînes de format de date et d'heure standard sont utilisables avec des valeurs [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset). 

Le tableau suivant décrit les spécificateurs de format de date et d'heure standard. Sauf indication contraire, un spécificateur de format de date et d'heure standard particulier produit une représentation sous forme de chaîne identique, qu'il soit utilisé avec une valeur [DateTime](xref:System.DateTime) ou [DateTimeOffset](xref:System.DateTimeOffset). Pour plus d’informations sur l’utilisation de chaînes de format de date et d’heure standard, consultez la section [Remarques](#notes).

Spécificateur de format | Description | Exemples
---------------- | ----------- | --------
"d" | Modèle de date courte. | `2009-06-15T13:45:30 -> 6/15/2009 (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)`; `2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)`
"D" | Modèle de date longue. | `2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)`; `2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)`; `2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)`
"f" | Modèle de date/heure complet (heure courte). | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)`
"F" | Modèle de date/heure complet (heure longue). | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)`
"g" | Modèle de date/heure général (heure courte). | `2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)`
"G" | Modèle de date/heure général (heure longue). | `2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)`
"M", "m' | Modèle de mois/jour. | `2009-06-15T13:45:30 -> June 15 (en-US)`; `2009-06-15T13:45:30 -> 15. juni (da-DK)`; `2009-06-15T13:45:30 -> 15 Juni (id-ID)`
"O", "o" | Modèle de date/heure aller-retour. | Valeurs [DateTime](xref:System.DateTime) : `2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00`; `2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z`; `2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000`. Valeurs [DateTimeOffset](xref:System.DateTimeOffset) : `2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00`
"R", "r" | Modèle RFC1123. | `2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT`
"s" | Modèle de date/heure pouvant être trié. | `2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30`; `2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30`
"t" | Modèle d’heure courte. | `2009-06-15T13:45:30 -> 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45 م (ar-EG)` 
"T" | Modèle d’heure longue. | `2009-06-15T13:45:30 -> 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45:30 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)`
"u" | Modèle de date/heure universel pouvant être trié. | Avec une valeur [DateTime](xref:System.DateTime) : `2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z`. Avec une valeur [DateTimeOffset](xref:System.DateTimeOffset) : `2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z`
"U" | Modèle de date/heure complet universel. | `2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)`
"Y", "y" | Modèle d’année/mois. | `2009-06-15T13:45:30 -> June, 2009 (en-US)`; `2009-06-15T13:45:30 -> juni 2009 (da-DK)`; `2009-06-15T13:45:30 -> Juni 2009 (id-ID)`
N'importe quel caractère | Spécificateur inconnu. | Lève une exception [FormatException](xref:System.FormatException) d’exécution.

## <a name="how-standard-format-strings-work"></a>Fonctionnement des chaînes de format standard

Dans une opération de mise en forme, une chaîne de format standard constitue simplement un alias d'une chaîne de format personnalisée. L'utilisation d'un alias pour faire référence à une chaîne de format personnalisée présente l'avantage suivant : bien que l'alias reste invariant, la chaîne de format personnalisée peut varier. Ce point est important car les représentations sous forme de chaîne de valeurs de date et d'heure varient généralement selon la culture. Par exemple, la chaîne de format standard "d" indique qu'une valeur de date et d'heure sera affichée à l'aide d'un modèle de date courte. Pour la culture dite indifférente, ce modèle est "MM/dd/yyyy". Pour la culture fr-FR, il s'agit de "dd/MM/yyyy". Pour la culture ja-JP, il s'agit de "yyyy/MM/dd".

Si, dans une opération de mise en forme, une chaîne de format standard est mappée à une chaîne de format personnalisée d'une culture particulière, votre application peut définir la culture spécifique dont les chaînes de format personnalisées sont utilisées de l'une des manières suivantes :

* Vous pouvez utiliser la culture par défaut (ou actuelle). L'exemple suivant affiche une date à l'aide du format de date courte de la culture actuelle. Dans ce cas, la culture actuelle est en-US. 

  ```csharp
  // Display using current (en-us) culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  Console.WriteLine(thisDate.ToString("d"));           // Displays 3/15/2008
  ```

  ```vb
  ' Display using current (en-us) culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Console.WriteLine(thisDate.ToString("d"))     ' Displays 3/15/2008
  ```
  
* Vous pouvez passer un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont la mise en forme sera utilisée à une méthode qui a un paramètre [IFormatProvider](xref:System.IFormatProvider). L'exemple suivant affiche une date à l'aide du format de date courte de la culture pt-BR.
  
  ```csharp
  // Display using pt-BR culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  CultureInfo culture = new CultureInfo("pt-BR");      
  Console.WriteLine(thisDate.ToString("d", culture));  // Displays 15/3/2008
  ```

  ```vb
  ' Display using pt-BR culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Dim culture As New CultureInfo("pt-BR")      
  Console.WriteLine(thisDate.ToString("d", culture))   ' Displays 15/3/2008
  ```
  
* Vous pouvez passer un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objet qui fournit des informations de mise en forme à une méthode qui a un paramètre [IFormatProvider](xref:System.IFormatProvider). L’exemple suivant affiche une date à l’aide du format de date courte d’un objet DateTimeFormatInfo pour la culture hr-HR.  

  ```csharp
  // Display using date format information from hr-HR culture
  DateTime thisDate = new DateTime(2008, 3, 15);
  DateTimeFormatInfo fmt = (new CultureInfo("hr-HR")).DateTimeFormat;
  Console.WriteLine(thisDate.ToString("d", fmt));      // Displays 15.3.2008
  ```

  ```vb
  ' Display using date format information from hr-HR culture
  Dim thisDate As Date = #03/15/2008#
  Dim fmt As DateTimeFormatInfo = (New CultureInfo("hr-HR")).DateTimeFormat
  Console.WriteLine(thisDate.ToString("d", fmt))   ' Displays 15.3.2008
  ```
  
Dans certains cas, il est pratique d'utiliser la chaîne de format standard comme abréviation pour les chaînes de format personnalisées plus longues et indifférentes. Quatre chaînes de format standard appartiennent à cette catégorie : "O" (ou "o"), "R" (ou "r"), "s" et "u". Ces chaînes correspondent aux chaînes de format personnalisées définies par la culture dite indifférente. Elles produisent des représentations sous forme de chaîne de valeurs de date et d'heure destinées à être identiques dans toutes les cultures. Le tableau suivant fournit des informations sur ces quatre chaînes de format de date et d'heure standard.

Chaîne de format standard | Défini par la propriété DateTimeFormatInfo.InvariantInfo | Chaîne de format personnalisée
---------------------- | ---------------------------------------------------- | --------------------
"O" ou "o" | Aucun | yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz
"R" ou "r" | [RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
"s" | [SortableDateTime](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) | yyyy'-'MM'-'dd'T'HH':'mm':'ss
"u" | [UniversalSortableDateTime](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) | yyyy'-'MM'-'dd HH':'mm':'ss'Z'

Les sections suivantes décrivent les spécificateurs de format standard pour les valeurs [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset).

## <a name="the-short-date-d-format-specifier"></a>Spécificateur de format de date courte ("d")

Le spécificateur de format standard « d » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) d’une culture spécifique. Par exemple, la chaîne de format personnalisée qui est retournée par la propriété [ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) de la culture dite indifférente est « MM/dd/yyyy ». 

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.
L'exemple suivant utilise le spécificateur de format "d" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008,4, 10);
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-NZ")));
// Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("de-DE")));
// Displays 10.04.2008 
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-NZ")))
' Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("de-DE")))
' Displays 10.04.2008 
```

## <a name="the-long-date-d-format-specifier"></a>Spécificateur de format de date longue ("D")

Le spécificateur de format standard « D » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "dddd, dd MMMM yyyy".

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété | Description
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | Définit le format global de la chaîne de résultat.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.

L'exemple suivant utilise le spécificateur de format "D" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10);
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("pt-BR")));
// Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays jueves, 10 de abril de 2008
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("pt-BR")))
' Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays jueves, 10 de abril de 2008
```

## <a name="the-full-date-short-time-f-format-specifier"></a>Spécificateur de format de date complet et d’heure courte ("f")

Le spécificateur de format standard "f" représente une combinaison des modèles de date longue ("D") et d’heure courte ("t"), séparés par un espace.

Les informations de mise en forme d’un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé retourné par les propriétés [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) et [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de certaines cultures peuvent ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | Définit le format du composant « date » de la chaîne de résultat.
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Définit le format du composant « heure » de la chaîne de résultat.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "f" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30 
```

## <a name="the-full-date-long-time-f-format-specifier"></a>Spécificateur de format de date complet et d’heure longue ("F")

Le spécificateur de format standard « F » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "dddd, dd MMMM yyyy HH:mm:ss".

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) de certaines cultures peut ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | Définit le format global de la chaîne de résultat.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "F" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30:00 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30:00 
```

## <a name="the-general-date-short-time-g-format-specifier"></a>Spécificateur de format de date général et d’heure courte ("g")

Le spécificateur de format standard "g" représente une combinaison des modèles de date courte ("d") et d’heure courte ("t"), séparés par un espace.

Les informations de mise en forme d’un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé retourné par les propriétés [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) et [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de certaines cultures peuvent ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | Définit le format du composant « date » de la chaîne de résultat.
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Définit le format du composant « heure » de la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "g" pour afficher une valeur de date et d'heure. 

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("g", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("fr-BE")));
// Displays 10/04/2008 6:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("g", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("fr-BE")))
' Displays 10/04/2008 6:30  
```

## <a name="the-general-date-long-time-g-format-specifier"></a>Spécificateur de format de date général et d’heure longue ("G")

Le spécificateur de format standard "G" représente une combinaison des modèles de date courte ("d") et d’heure longue ("T"), séparés par un espace.

Les informations de mise en forme d’un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé retourné par les propriétés [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) et [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) de certaines cultures peuvent ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | Définit le format du composant « date » de la chaîne de résultat.
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | Définit le format du composant « heure » de la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "G" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("G", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("nl-BE")));
// Displays 10/04/2008 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("G", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("nl-BE")))
' Displays 10/04/2008 6:30:00                       
```

## <a name="the-month-m-m-format-specifier"></a>Spécificateur de format de mois ("M", "m")

Le spécificateur de format standard « M » ou « m » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "MMMM dd".

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété | Description
-------- | -----------
[MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) | Définit le format global de la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.

L'exemple suivant utilise le spécificateur de format "m" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays April 10                        
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("ms-MY")));
// Displays 10 April  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays April 10                        
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("ms-MY")))
' Displays 10 April
```

## <a name="the-round-trip-o-o-format-specifier"></a>Spécificateur de format aller-retour ("O", "o")

Le spécificateur de format standard "O" ou "o" représente une chaîne de format de date et d’heure personnalisée à l’aide d’un modèle qui conserve les informations de fuseau horaire et génère une chaîne de résultat conforme à la norme ISO 8601. Pour les valeurs [DateTime](xref:System.DateTime), ce spécificateur de format est conçu pour conserver des valeurs de date et d’heure avec la propriété [DateTime.Kind](xref:System.DateTime.Kind) dans le texte. La chaîne mise en forme peut être analysée de nouveau à l’aide de la méthode [DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) ou [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) si le paramètre styles a la valeur [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind). 

Le spécificateur de format standard « O » ou « o » correspond à la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" pour les valeurs DateTime et à la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" pour les valeurs [DateTimeOffset](xref:System.DateTimeOffset). Dans cette chaîne, les paires de guillemets simples qui délimitent des caractères individuels, comme les traits d'union, les deux-points et la lettre "T", indiquent que le caractère individuel est un littéral qui ne peut pas être modifié. Les apostrophes n'apparaissent pas dans la chaîne de sortie. 

Le spécificateur de format standard « O » ou « o » et la chaîne de format personnalisée "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" tirent parti des trois façons dont la norme ISO 8601 représente les informations de fuseau horaire pour conserver la propriété [Kind](xref:System.DateTime.Kind) des valeurs [DateTime](xref:System.DateTime) : 

* Le composant de fuseau horaire des valeurs de date et d’heure [DateTimeKind.Local](xref:System.DateTimeKind.Local) est un décalage par rapport à l’heure UTC (par exemple, +01:00, -07:00). Toutes les valeurs DateTimeOffset sont également représentées dans ce format. 

* Le composant de fuseau horaire des valeurs de date et d’heure [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) utilise « Z » (soit zéro décalage) pour représenter l’heure UTC. 

* Les valeurs de date et d’heure [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) ne possèdent aucune information de fuseau horaire. 

Comme le spécificateur de format standard O" ou "o" est conforme à une norme internationale, l'opération de mise en forme ou d'analyse qui recourt au spécificateur utilise toujours la culture dite indifférente et le calendrier grégorien. 

Les chaînes transmises aux méthodes `Parse`, `TryParse`, `ParseExact` et `TryParseExact` de [DateTime](xref:System.DateTime) et [DateTimeOffset](xref:System.DateTimeOffset) peuvent être analysées à l’aide du spécificateur de format « O » ou « o » si elles sont définies dans l’un de ces formats. Dans le cas des objets [DateTime](xref:System.DateTime), la surcharge d’analyse que vous appelez doit également inclure un paramètre styles avec une valeur [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind). Notez que si vous appelez une méthode d'analyse avec la chaîne de format personnalisée qui correspond au spécificateur de format "O" ou "o", vous n'obtenez pas les mêmes résultats que "O" ou "o". En effet, les méthodes d'analyse qui utilisent une chaîne de format personnalisée ne peuvent pas analyser la représentation sous forme de chaîne des valeurs de date et d'heure auxquelles fait défaut un composant de fuseau horaire ou qui recourent à "Z" pour indiquer l'heure UTC. 

L’exemple suivant utilise le spécificateur de format « o » pour afficher une série de valeurs [DateTime](xref:System.DateTime) et une valeur [DateTimeOffset](xref:System.DateTimeOffset) sur un système situé dans le fuseau horaire Pacifique (États-Unis). 

```csharp
using System;

public class Example
{
   public static void Main()
   {
       DateTime dat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                   DateTimeKind.Unspecified);
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind); 

       DateTime uDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Utc);
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind);

       DateTime lDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Local);
       Console.WriteLine("{0} ({1}) --> {0:O}\n", lDat, lDat.Kind);

       DateTimeOffset dto = new DateTimeOffset(lDat);
       Console.WriteLine("{0} --> {0:O}", dto);
   }
}
// The example displays the following output:
//    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
//    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
//    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
//    
//    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

```vb
Module Example
   Public Sub Main()
       Dim dat As New Date(2009, 6, 15, 13, 45, 30, 
                           DateTimeKind.Unspecified)
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind) 

       Dim uDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Utc)
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind)

       Dim lDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Local)
       Console.WriteLine("{0} ({1}) --> {0:O}", lDat, lDat.Kind)
       Console.WriteLine()

       Dim dto As New DateTimeOffset(lDat)
       Console.WriteLine("{0} --> {0:O}", dto)
   End Sub
End Module
' The example displays the following output:
'    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
'    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
'    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
'    
'    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

L'exemple suivant utilise le spécificateur de format "o" pour créer une chaîne mise en forme, puis restaure la valeur de date et d'heure d'origine en appelant une méthode `Parse` de date et d'heure.

```csharp
// Round-trip DateTime values.
DateTime originalDate, newDate;
string dateString;
// Round-trip a local time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 10, 6, 30, 0), DateTimeKind.Local);
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip a UTC time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 12, 9, 30, 0), DateTimeKind.Utc);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip time in an unspecified time zone.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 13, 12, 30, 0), DateTimeKind.Unspecified);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);

// Round-trip a DateTimeOffset value.
DateTimeOffset originalDTO = new DateTimeOffset(2008, 4, 12, 9, 30, 0, new TimeSpan(-8, 0, 0));
dateString = originalDTO.ToString("o");
DateTimeOffset newDTO = DateTimeOffset.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO);
// The example displays the following output:
//    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
//    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
//    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
//    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

```vb
' Round-trip DateTime values.
Dim originalDate, newDate As Date
Dim dateString As String
' Round-trip a local time.
originalDate = Date.SpecifyKind(#4/10/2008 6:30AM#, DateTimeKind.Local)
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip a UTC time.
originalDate = Date.SpecifyKind(#4/12/2008 9:30AM#, DateTimeKind.Utc)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip time in an unspecified time zone.
originalDate = Date.SpecifyKind(#4/13/2008 12:30PM#, DateTimeKind.Unspecified)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)

' Round-trip a DateTimeOffset value.
Dim originalDTO As New DateTimeOffset(#4/12/2008 9:30AM#, New TimeSpan(-8, 0, 0))
dateString = originalDTO.ToString("o")
Dim newDTO As DateTimeOffset = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO)
' The example displays the following output:
'    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
'    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
'    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
'    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

## <a name="the-rfc1123-r-r-format-specifier"></a>Spécificateur de format RFC1123 ("R", "r")

Le spécificateur de format standard « R » ou « r » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern). Le modèle reflète une norme définie, et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "ddd, dd MMM yyyy HH':'mm':'ss 'GMT'". Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente.

La chaîne de résultat est affectée par les propriétés suivantes de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) retourné par la propriété [DateTimeFormatInfo.InvariantInfo](xref:System.Globalization.DateTimeFormatInfo.InvariantInfo) qui représente la culture dite indifférente.

Propriété | Description
-------- | -----------
[RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | Définit le format de la chaîne de résultat.
[AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) | Définit les noms de jours abrégés qui peuvent s'afficher dans la chaîne de résultat.
[AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) | Définit les noms de mois abrégés qui peuvent s'afficher dans la chaîne de résultat.

Bien que la norme RFC 1123 exprime une heure au format de temps universel coordonné (UTC, Coordinated Universal Time), l’opération de mise en forme ne modifie pas la valeur de l’objet [DateTime](xref:System.DateTime) qui est mis en forme. Par conséquent, vous devez convertir la valeur [DateTime](xref:System.DateTime) en temps UTC en appelant la méthode [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) avant d’exécuter l’opération de mise en forme. En revanche, les valeurs [DateTimeOffset](xref:System.DateTimeOffset) effectuent cette conversion automatiquement ; il n’est pas nécessaire d’appeler la méthode [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) avant l’opération de mise en forme. 

L’exemple suivant utilise le spécificateur de format « r » pour afficher une valeur [DateTime](xref:System.DateTime) et une valeur [DateTimeOffset](xref:System.DateTimeOffset) sur un système situé dans le fuseau horaire Pacifique (États-Unis).

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
DateTimeOffset dateOffset = new DateTimeOffset(date1, 
                            TimeZoneInfo.Local.GetUtcOffset(date1));
Console.WriteLine(date1.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Dim dateOffset As New DateTimeOffset(date1, TimeZoneInfo.Local.GetUtcOFfset(date1))
Console.WriteLine(date1.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT
```

## <a name="the-sortable-s-format-specifier"></a>Spécificateur de format pouvant être trié ("s")

Le spécificateur de format standard « s » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.SortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern). Le modèle reflète une norme définie (ISO 8601), et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "yyyy'-'MM'-'dd'T'HH':'mm':'ss".

L'objectif du spécificateur de format "s" est de produire des chaînes de résultats qui trient de façon cohérente par ordre croissant ou décroissant en fonction des valeurs de date et d'heure. Par conséquent, bien que le spécificateur de format standard « s » représente une valeur de date et d’heure dans un format cohérent, l’opération de mise en forme ne modifie pas la valeur de l’objet de date et d’heure qui est mis en forme de façon à refléter sa propriété [DateTime.Kind](xref:System.DateTime.Kind) ou sa valeur [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset). Par exemple, les chaînes de résultat produites par la mise en forme des valeurs de date et d'heure 2014-11-15T18:32:17 + 00:00 et 2014-11-15T18:32:17 + 08:00 sont identiques. 

Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente. 

L’exemple suivant utilise le spécificateur de format « s » pour afficher une valeur [DateTime](xref:System.DateTime) et une valeur [DateTimeOffset](xref:System.DateTimeOffset) sur un système situé dans le fuseau horaire Pacifique (États-Unis).

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("s"));
// Displays 2008-04-10T06:30:00
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("s"))
' Displays 2008-04-10T06:30:00 
```

## <a name="the-short-time-t-format-specifier"></a>Spécificateur de format d’heure courte ("t")

Le spécificateur de format standard « t » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) actuelle. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "HH:mm".

Les informations de mise en forme d’un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) spécifique affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) de certaines cultures peut ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | Définit le format du composant « heure » de la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "t" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30
```

## <a name="the-long-time-t-format-specifier"></a>Spécificateur de format d’heure longue ("T")

Le spécificateur de format standard « T » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) d’une culture spécifique. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "HH:mm:ss".

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) de certaines cultures peut ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | Définit le format du composant « heure » de la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

L'exemple suivant utilise le spécificateur de format "T" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30:00 
```

## <a name="the-universal-sortable-u-format-specifier"></a>Spécificateur de format universel pouvant être trié ("u")

Le spécificateur de format standard « u » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.UniversalSortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern). Le modèle reflète une norme définie, et la propriété est en lecture seule. Par conséquent, il s'agit toujours du même, quels que soient la culture utilisée ou le fournisseur de format spécifié. La chaîne de format personnalisée est "yyyy'-'MM'-'dd HH':'mm':'ss'Z'". Lorsque ce spécificateur de format standard est utilisé, l'opération de mise en forme ou d'analyse utilise toujours la culture dite indifférente. 

Bien que la chaîne de résultat doive exprimer une heure au format du temps universel coordonné (UTC, Coordinated Universal Time), aucune conversion de la valeur [DateTime](xref:System.DateTime) d’origine n’est effectuée pendant l’opération de mise en forme. Par conséquent, vous devez convertir une valeur [DateTime](xref:System.DateTime) en temps UTC en appelant la méthode [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) avant de la mettre en forme. En revanche, les valeurs [DateTimeOffset](xref:System.DateTimeOffset) effectuent cette conversion automatiquement ; il n’est pas nécessaire d’appeler la méthode [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) avant l’opération de mise en forme.   

L'exemple suivant utilise le spécificateur de format « u » pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToUniversalTime().ToString("u"));
// Displays 2008-04-10 13:30:00Z
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToUniversalTime.ToString("u"))
' Displays 2008-04-10 13:30:00Z                       
```

## <a name="the-universal-full-u-format-specifier"></a>Spécificateur de format complet universel ("U")

Le spécificateur de format standard « U » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) d’une culture spécifiée. Le modèle est identique au modèle "F". Toutefois, la valeur [DateTime](xref:System.DateTime) est automatiquement convertie en temps UTC avant d’être mise en forme.

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui peuvent contrôler la mise en forme de la chaîne retournée. Le spécificateur de format personnalisé qui est retourné par la propriété [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) de certaines cultures peut ne pas utiliser toutes les propriétés.

Propriété | Description
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | Définit le format global de la chaîne de résultat.
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | Définit les noms de jours localisés qui peuvent apparaître dans la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | Définit la chaîne qui indique les heures de minuit à avant midi sur une horloge au format 12 heures.
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | Définit la chaîne qui indique les heures de midi à avant minuit sur une horloge au format 12 heures.

Le spécificateur de format « U » n’est pas pris en charge par le type [DateTimeOffset](xref:System.DateTimeOffset) et lève une exception [FormatException](xref:System.FormatException) s’il est utilisé pour mettre en forme une valeur [DateTimeOffset](xref:System.DateTimeOffset).

L'exemple suivant utilise le spécificateur de format "U" pour afficher une valeur de date et d'heure.

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("sv-FI")));
// Displays den 10 april 2008 13:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("sv-FI")))
' Displays den 10 april 2008 13:30:00                       
```

## <a name="the-year-month-y-y-format-specifier"></a>Spécificateur de format Année Mois ("Y", "y")

Le spécificateur de format standard « Y » ou « y » représente une chaîne de format de date et d’heure personnalisée définie par la propriété [DateTimeFormatInfo.YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) d’une culture spécifiée. Par exemple, la chaîne de format personnalisée pour la culture dite indifférente est "yyyy MMMM".

Le tableau suivant répertorie les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété | Description
-------- | -----------
[YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) | Définit le format global de la chaîne de résultat.
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | Définit les noms de mois localisés qui peuvent apparaître dans la chaîne de résultat.

L'exemple suivant utilise le spécificateur de format "y" pour afficher une valeur de date et d'heure.

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("Y", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays April, 2008                       
Console.WriteLine(date1.ToString("y", 
                  CultureInfo.CreateSpecificCulture("af-ZA")));
// Displays April 2008 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("Y", CultureInfo.CreateSpecificCulture("en-US")))
' Displays April, 2008                       
Console.WriteLine(date1.ToString("y", CultureInfo.CreateSpecificCulture("af-ZA")))
' Displays April 2008
```                       

## <a name="notes"></a>Remarques

### <a name="datetimeformatinfo-properties"></a>Propriétés DateTimeFormatInfo

La mise en forme dépend des propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actif, qui est fourni implicitement par la culture de thread actuelle ou explicitement par le paramètre [IFormatProvider](xref:System.IFormatProvider) de la méthode qui appelle la mise en forme. Pour le paramètre [IFormatProvider](xref:System.IFormatProvider), votre application doit spécifier un objet [CultureInfo](xref:System.Globalization.CultureInfo), qui représente une culture, ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), qui représente les conventions de présentation de la date et de l’heure d’une culture particulière. La plupart des spécificateurs de format de date et d’heure standard sont des alias des modèles de mise en forme définis par les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) actuel. Votre application peut modifier le résultat produit par certains spécificateurs de format de date et d’heure standard en modifiant les modèles de format de date et d’heure correspondants de la propriété [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) correspondante.

## <a name="see-also"></a>Voir aussi

[Mise en forme des types](formatting-types.md)

[Chaînes de format de date et d’heure personnalisées](custom-datetime.md)


