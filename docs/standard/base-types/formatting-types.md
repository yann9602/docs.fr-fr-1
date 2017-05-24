---
title: Mise en forme des types
description: Mise en forme des types
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: e9b8ad13a48dd43236769b130d6f8a75b7b023ca
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="formatting-types"></a>Mise en forme des types

La mise en forme est le processus de conversion d'une instance d'une classe, d'une structure ou d'une valeur d'énumération en représentation sous forme de chaîne, généralement pour exposer la chaîne obtenue aux utilisateurs ou pour qu'elle soit désérialisée afin de restaurer le type de données d'origine. Cette conversion peut présenter plusieurs difficultés :

* La manière dont les valeurs sont stockées en interne ne reflète pas nécessairement celle dont les utilisateurs souhaitent les voir. Par exemple, un numéro de téléphone peut être stocké sous la forme **8009999999**, ce qui n’est pas convivial. Il devrait plutôt être affiché sous la forme **800-999-9999**. Consultez la section [Chaînes de format personnalisées](#custom-format-strings) pour obtenir un exemple d’une telle mise en forme d’un nombre. 

* La conversion d'un objet en sa représentation sous forme de chaîne n'est pas toujours intuitive. Par exemple, il n’est pas évident de savoir comment doit s’afficher la représentation sous forme de chaîne d’un objet **Temperature** ou **Person**. Pour obtenir un exemple illustrant la mise en forme d’un objet **Temperature** selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings).

* Les valeurs requièrent souvent une mise en forme qui tient compte de la culture. Par exemple, dans une application qui utilise des nombre pour refléter des valeurs monétaires, les chaînes numériques doivent inclure le symbole monétaire, le séparateur de groupes (qui, dans la plupart des cultures, est le séparateur des milliers) et le symbole décimal qui correspondent à la culture actuelle. Pour obtenir un exemple, consultez la section [Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface). 

* Une application peut avoir à afficher la même valeur de différentes manières. Par exemple, une application peut représenter un membre d'énumération en affichant une représentation sous forme de chaîne de son nom ou en affichant sa valeur sous-jacente. Pour obtenir un exemple illustrant la mise en forme d’un membre de l’énumération [DayOfWeek](xref:System.DayOfWeek) selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings).

.NET assure une prise en charge évoluée de la mise en forme qui permet aux développeurs de surmonter ces difficultés. 

> [!NOTE]
> La mise en forme convertit la valeur d'un type en une représentation sous forme de chaîne. L'analyse est l'opération inverse de la mise en forme. Une opération d'analyse crée une instance d'un type de données à partir de sa représentation sous forme de chaîne. Pour plus d’informations sur la conversion de chaînes en d’autres types de données, consultez [Analyse de chaînes](parsing-strings.md).

Cette vue d'ensemble contient les sections suivantes :

* [Mise en forme dans .NET](#formatting-in-net)

* [Mise en forme par défaut à l’aide de la méthode ToString](#default-formatting-using-the-tostring-method)

* [Substitution de la méthode ToString](#overriding-the-tostring-method)

* [Méthode ToString et chaînes de format](#the-tostring-method-and-format-strings)

    * [Chaînes de format standard](#standard-format-strings)
    
    * [Chaînes de format personnalisées](#custom-format-strings)
    
    * [Chaînes de format et types .NET](#format-strings-and-net-types)
    
* [Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [Mise en forme dépendante de la culture des valeurs numériques](#culture-sensitive-formatting-of-numeric-values)
    
    * [Mise en forme dépendante de la culture des valeurs de date et d’heure](#culture-sensitive-formatting-of-date-and-time-values)
    
* [Interface IFormattable](#the-iformattable-interface)

* [Mise en forme composite](#composite-formatting)

* [Mise en forme personnalisée avec ICustomFormatter](#custom-formatting-with-icustomformatter)

* [Rubriques connexes](#related-topics)

* [Référence](#reference)

## <a name="formatting-in-net"></a>Mise en forme dans .NET

Le mécanisme de base de la mise en forme est l’implémentation par défaut de la méthode [Object.ToString](xref:System.Object.ToString), décrite dans la section [Mise en forme par défaut à l’aide de la méthode ToString](#default-formatting-using-the-tostring-method), plus loin dans cette rubrique. Toutefois, .NET propose différentes manières de modifier et d’étendre sa prise en charge par défaut de la mise en forme. Notamment :

* Substitution de la méthode [Object.ToString](xref:System.Object.ToString) pour définir une représentation sous forme de chaîne personnalisée de la valeur d’un objet. Pour plus d’informations, consultez la section [Substitution de la méthode ToString](#overriding-the-tostring-method), plus loin dans cette rubrique.

* Définition de spécificateurs de format qui permettent à la représentation sous forme de chaîne de la valeur d'un objet de prendre plusieurs formes. Par exemple, dans l'instruction suivante, le spécificateur de format "X" convertit un entier en la représentation sous forme de chaîne d'une valeur hexadécimale.

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  Pour plus d’informations sur les spécificateurs de format, consultez la section [Méthode ToString et chaînes de format](#the-tostring-method-and-format-strings).
  
* Utilisation de fournisseurs de format pour tirer parti des conventions de mise en forme d'une culture spécifique. Par exemple, l'instruction suivante affiche une valeur monétaire en utilisant les conventions de mise en forme de la culture en-US. 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  Pour plus d’informations sur la mise en forme avec des fournisseurs de format, consultez la section [Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).  
  
* Implémentation de l’interface [IFormattable](xref:System.IFormattable) pour prendre en charge la conversion de chaînes avec la classe [Convert](xref:System.Convert) et la mise en forme composite. Pour plus d’informations, consultez la section [Interface IFormattable](#the-iformattable-interface).

* Utilisation de la mise en forme composite pour incorporer la représentation sous forme de chaîne d'une valeur dans une chaîne plus grande. Pour plus d’informations, consultez la section [Mise en forme composite](#composite-formatting).

* Implémentation des interfaces [ICustomFormatter](xref:System.ICustomFormatter) et [IFormatProvider](xref:System.IFormatProvider) pour fournir une solution de mise en forme personnalisée. Pour plus d’informations, consultez la section [Mise en forme personnalisée avec ICustomFormatter](#custom-formatting-with-icustomformatter).

Les sections suivantes étudient ces méthodes de conversion d'un objet en sa représentation sous forme de chaîne.

## <a name="default-formatting-using-the-tostring-method"></a>Mise en forme par défaut à l’aide de la méthode ToString

Chaque type qui est dérivé de [System.Object](xref:System.Object) hérite automatiquement d’une méthode [ToString](xref:System.Object.ToString) sans paramètre, laquelle retourne le nom du type par défaut. L’exemple suivant illustre la méthode [ToString](xref:System.Object.ToString) par défaut. Il définit une classe nommée `Automobile` qui n'a pas d'implémentation. Quand cette classe est instanciée et que sa méthode [ToString](xref:System.Object.ToString) est appelée, elle affiche son nom de type. Notez que la méthode [ToString](xref:System.Object.ToString) n’est pas appelée explicitement dans cet exemple. La méthode [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) appelle implicitement la méthode [ToString](xref:System.Object.ToString) de l’objet qui lui est passé comme argument. 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

Étant donné que tous les types autres que les interfaces sont dérivés d’[Object](xref:System.Object), ces fonctionnalités sont fournies automatiquement à vos classes ou structures personnalisées. Toutefois, les fonctionnalités offertes par la méthode [ToString](xref:System.Object.ToString) par défaut sont limitées : bien qu’elle identifie le type, elle ne fournit aucune information relative à une instance du type. Pour fournir une représentation sous forme de chaîne d’un objet qui donne des informations sur cet objet, vous devez substituer la méthode [ToString](xref:System.Object.ToString).

> [!NOTE]
> Les structures héritent de [ValueType](xref:System.ValueType), qui, à son tour, est dérivé d’[Object](xref:System.Object). Bien que [ValueType](xref:System.ValueType) substitue [Object.ToString](xref:System.Object.ToString), son implémentation est identique.

## <a name="overriding-the-tostring-method"></a>Substitution de la méthode ToString

L'utilité de l'affichage du nom d'un type est souvent limitée et ne permet pas aux consommateurs de vos types de différencier une instance d'une autre. Toutefois, vous pouvez substituer la méthode [ToString](xref:System.Object.ToString) pour fournir une représentation plus utile de la valeur d’un objet. L’exemple suivant définit un objet `Temperature` et substitue sa méthode [ToString](xref:System.Object.ToString) pour afficher la température en degrés Celsius.

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

Dans .NET, la méthode [ToString](xref:System.Object.ToString) de chaque type valeur primitif a été substituée de façon à afficher la valeur de l’objet au lieu de son nom. Le tableau suivant montre la substitution pour chaque type primitif. Notez que la plupart des méthodes substituées appellent une autre surcharge de la méthode [ToString](xref:System.Object.ToString) et lui passent le spécificateur de format "G", qui définit le format général pour son type, ainsi qu’un objet [IFormatProvider](xref:System.IFormatProvider) qui représente la culture actuelle.

Type | Substitution de ToString
---- | -----------------
[Boolean](xref:System.Boolean) | Retourne [Boolean.TrueString](xref:System.Boolean.TrueString) ou [Boolean.FalseString](xref:System.Boolean.FalseString).
[Byte](xref:System.Byte) | Appelle `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Byte](xref:System.Byte) pour la culture actuelle.
[Char](xref:System.Char) | Retourne le caractère sous forme de chaîne.
[DateTime](xref:System.DateTime) | Appelle `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` afin de mettre en forme la valeur de date et d'heure pour la culture actuelle. 
[Decimal](xref:System.Decimal) | Appelle `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Decimal](xref:System.Decimal) pour la culture actuelle.
[Double](xref:System.Double) | Appelle `Double.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Double](xref:System.Double) pour la culture actuelle.
[Int16](xref:System.Int16) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int16](xref:System.Int16) pour la culture actuelle.
[Int32](xref:System.Int32) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int32](xref:System.Int32) pour la culture actuelle.
[Int64](xref:System.Int64) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int64](xref:System.Int64) pour la culture actuelle.
[SByte](xref:System.SByte) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [SByte](xref:System.SByte) | pour la culture actuelle.
[Single](xref:System.Single) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Single](xref:System.Single) pour la culture actuelle.
[UInt32](xref:System.UInt32) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt32](xref:System.UInt32) pour la culture actuelle.
[UInt32](xref:System.UInt32) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt32](xref:System.UInt32) pour la culture actuelle.
[UInt64](xref:System.UInt64) | Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt64](xref:System.UInt64) pour la culture actuelle.

## <a name="the-tostring-method-and-format-strings"></a>Méthode ToString et chaînes de format

Le recours à la méthode [ToString](xref:System.Object.ToString) par défaut ou la substitution de [ToString](xref:System.Object.ToString) ne valent que quand un objet a une seule représentation sous forme de chaîne possible. Toutefois, la valeur d'un objet a souvent plusieurs représentations. Par exemple, une température peut être exprimée en degrés Fahrenheit, Celsius ou Kelvin. De même, la valeur entière 10 peut être représentée de plusieurs façons, dont 10, 10,0, 1,0e01 ou $10,00.

Pour permettre à une même valeur d’avoir plusieurs représentations sous forme de chaîne, .NET utilise des chaînes de format. Une chaîne de format est une chaîne qui contient un ou plusieurs spécificateurs de format prédéfinis, constitués d’un ou de plusieurs caractères servant à définir la manière dont la méthode [ToString](xref:System.Object.ToString) doit mettre en forme sa sortie. La chaîne de format est ensuite passée comme paramètre à la méthode [ToString](xref:System.Object.ToString) de l’objet et détermine la manière dont la représentation sous forme de chaîne de la valeur de cet objet doit apparaître.

Dans .NET, tous les types numériques, types de date et d’heure et types énumération prennent en charge un jeu prédéfini de spécificateurs de format. Vous pouvez aussi utiliser des chaînes de format pour définir plusieurs représentations sous forme de chaîne de vos types de données définis par l'application.

### <a name="standard-format-strings"></a>Chaînes de format standard

Une chaîne de format standard comprend un spécificateur de format unique, qui est un caractère alphabétique définissant la représentation sous forme de chaîne de l'objet auquel il s'applique, ainsi qu'un spécificateur de précision facultatif qui affecte le nombre de chiffres affichés dans la chaîne de résultat. Si le spécificateur de précision est omis ou n'est pas pris en charge, un spécificateur de format standard équivaut à une chaîne de format standard. 

.NET définit un jeu de spécificateurs de format standard pour tous les types numériques, types de date et d’heure et types énumération. Par exemple, chacune de ces catégories prend en charge un spécificateur de format standard "G", lequel définit une représentation sous forme de chaîne générale d'une valeur de ce type.

Les chaînes de format standard pour les types énumération contrôlent directement la représentation sous forme de chaîne d'une valeur. Les chaînes de format passées à la méthode [ToString](xref:System.Object.ToString) d’une valeur d’énumération déterminent si la valeur est affichée en utilisant son nom de chaîne (spécificateurs de format "G" et "F"), sa valeur intégrale sous-jacente (spécificateur de format "D") ou sa valeur hexadécimale (spécificateur de format "X"). L’exemple suivant illustre l’utilisation de chaînes de format standard pour mettre en forme une valeur d’énumération [DayOfWeek](xref:System.DayOfWeek). 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

Pour plus d’informations sur les chaînes de format d’énumération, consultez [Chaînes de format d’énumération](enumeration-format.md).

Les chaînes de format standard pour les types numériques définissent généralement une chaîne de résultat dont l'apparence précise est contrôlée par une ou plusieurs valeurs de propriété. Par exemple, le spécificateur de format "C" met en forme un nombre en tant que valeur monétaire. Quand vous appelez la méthode [ToString](xref:System.Object.ToString) avec, comme seul paramètre, le spécificateur de format "C", les valeurs des propriétés suivantes de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) de la culture actuelle sont utilisées pour définir la représentation sous forme de chaîne de la valeur numérique :

* Propriété [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol), qui spécifie le symbole monétaire de la culture actuelle.

* Propriété [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) ou [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern), qui retourne un entier déterminant les éléments suivants : 

    * la position du symbole monétaire ;
    
    * si les valeurs négatives sont indiquées par un signe négatif devant, par un signe négatif derrière ou par des parenthèses ;
    
    * si un espace apparaît entre la valeur numérique et le symbole monétaire.
    
* Propriété [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits), qui définit le nombre de chiffres fractionnaires dans la chaîne de résultat.

* Propriété [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator), qui définit le symbole de séparateur décimal dans la chaîne de résultat.

* Propriété [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator), qui définit le symbole du séparateur de groupes.

* Propriété [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes), qui définit le nombre de chiffres de chaque groupe situé à gauche du séparateur décimal.

* Propriété [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign), qui détermine le signe négatif utilisé dans la chaîne de résultat si les parenthèses ne sont pas utilisées pour indiquer des valeurs négatives.

De plus, les chaînes de format numériques peuvent inclure un spécificateur de précision. La signification de ce spécificateur dépend de la chaîne de format avec laquelle il est utilisé, mais il indique généralement le nombre total de chiffres ou le nombre de chiffres fractionnaires qui doivent s'afficher dans la chaîne de résultat. Par exemple, le code suivant utilise la chaîne numérique standard "X4" et un spécificateur de précision pour créer une valeur de chaîne qui comprend quatre chiffres hexadécimaux.

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

Pour plus d’informations sur les chaînes de format numériques standard, consultez [Chaînes de format numériques standard](standard-numeric.md). 

Les chaînes de format standard pour les valeurs de date et d’heure sont des alias de chaînes de format personnalisées stockées par une classe [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) particulière. Par exemple, appeler la méthode [ToString](xref:System.Object.ToString) d’une valeur de date et d’heure avec le spécificateur de format "D" affiche la date et l’heure en utilisant la chaîne de format personnalisée stockée dans la propriété [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) de la culture actuelle. (Pour plus d’informations sur les chaînes de format personnalisées, consultez la section [Chaînes de format personnalisées](#custom-format-strings).) L'exemple suivant illustre cette relation.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

Pour plus d’informations sur les chaînes de format de date et d’heure standard, consultez [Chaînes de format de date et d’heure standard](standard-datetime.md).

Vous pouvez aussi utiliser des chaînes de format standard pour définir la représentation sous forme de chaîne produite par la méthode `ToString(String)` d'un objet défini par l'application. Vous pouvez définir les spécificateurs de format standard spécifiques que votre objet prend en charge, et déterminer s'ils respectent la casse. Votre implémentation de la méthode `ToString(String)` doit prendre en charge les éléments suivants :

* Spécificateur de format "G" qui représente un format habituel ou commun de l'objet. La surcharge sans paramètre de la méthode `ToString` de votre objet doit appeler sa surcharge `ToString(String)` et lui passer la chaîne de format standard "G".

* Prise en charge d’un spécificateur de format qui est égal à une référence null. Un spécificateur de format qui est égal à une référence null doit être considéré comme équivalent au spécificateur de format "G".

Par exemple, une classe `Temperature` peut stocker en interne la température en degrés Celsius et utiliser des spécificateurs de format pour représenter la valeur de l'objet `Temperature` en degrés Celsius, Fahrenheit et Kelvin. L'exemple suivant illustre cette situation.

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a>Chaînes de format personnalisées

Outre les chaînes de format standard, .NET définit des chaînes de format personnalisées pour les valeurs numériques et les valeurs de date et d’heure. Une chaîne de format personnalisée se compose d'un ou de plusieurs spécificateurs de format personnalisés qui définissent la représentation sous forme de chaîne d'une valeur. Par exemple, la chaîne de format de date et d'heure personnalisée "yyyy\mm\dd hh:mm:ffff t zzz" convertit une date en sa représentation sous forme de chaîne "2008/11/15 07:45:00.0000 P -08:00" pour la culture en-US. De même, la chaîne de format personnalisée "0000" convertit la valeur entière 12 en "0012". Pour une liste complète des chaînes de format personnalisées, consultez [Chaînes de format de date et d’heure personnalisées](custom-datetime.md) et [Chaînes de format numériques personnalisées](custom-numeric.md).

Si une chaîne de format se compose d'un seul spécificateur de format personnalisé, le spécificateur de format doit être précédé du symbole de pourcentage (%) pour éviter toute confusion avec un spécificateur de format standard. L'exemple suivant utilise le spécificateur de format personnalisé "M" pour afficher un nombre à un chiffre ou à deux chiffres du mois d'une date particulière.

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

De nombreuses chaînes de format standard pour les valeurs de date et d’heure sont des alias de chaînes de format personnalisées qui sont définies par les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo). Les chaînes de format personnalisées offrent également une souplesse considérable en matière de mise en forme définie par l'application pour les valeurs numériques ou les valeurs de date et d'heure. Vous pouvez définir vos propres chaînes de résultat personnalisées à la fois pour les valeurs numériques et pour les valeurs de date et d'heure en combinant plusieurs spécificateurs de format personnalisés dans une chaîne de format personnalisée unique. L'exemple suivant définit une chaîne de format personnalisée qui affiche le jour de la semaine entre parenthèses après le nom du mois, le jour et l'année.

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

L’exemple ci-dessous définit une chaîne de format personnalisée qui affiche une valeur [Int64](xref:System.Int64) sous la forme d’un numéro de téléphone américain standard à sept chiffres avec son indicatif régional. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

Bien que les chaînes de format standard puissent généralement gérer la plupart des besoins de mise en forme pour vos types définis par l'application, vous pouvez également définir des spécificateurs de format personnalisés pour mettre en forme vos types. 

### <a name="format-strings-and-net-types"></a>Chaînes de format et types .NET

Tous les types numériques (à savoir les types [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) et [BigInteger](xref:System.Numerics.BigInteger)), ainsi que les types [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid) et tous les types énumération prennent en charge la mise en forme avec des chaînes de format. Pour plus d’informations sur les chaînes de format spécifiques prises en charge par chaque type, consultez les rubriques suivantes : 

Titre | Définition
----- | ----------
[Chaînes de format numériques standard](standard-numeric.md) | Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques. 
[Chaînes de format numériques personnalisées](custom-numeric.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.
[Chaînes de format de date et d’heure standard](standard-datetime.md) | Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs [DateTime](xref:System.DateTime).
[Chaînes de format de date et d’heure personnalisées](custom-datetime.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l’application pour les valeurs [DateTime](xref:System.DateTime).
[Chaînes de format TimeSpan standard](standard-timespan.md) | Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.
[Chaînes de format TimeSpan personnalisées](custom-timespan.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.
[Chaînes de format d’énumération](enumeration-format.md) | Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.
[Guid.ToString(String)](xref:System.Guid.ToString(System.String)) | Décrit les chaînes de format standard pour les valeurs [Guid](xref:System.Guid).

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a>Mise en forme dépendante de la culture avec les fournisseurs de format et l'interface IFormatProvider

Si les spécificateurs de format vous permettent de personnaliser la mise en forme d'objets, la production, pour ces derniers, d'une représentation sous forme de chaîne explicite requiert souvent des informations de mise en forme supplémentaires. Par exemple, la mise en forme d'un nombre en tant que valeur monétaire en utilisant la chaîne de format standard "C" ou une chaîne de format personnalisée telle que "$ #, #.00" requiert au minimum l'existence d'informations à inclure dans la chaîne mise en forme concernant le symbole monétaire, le séparateur de groupes et le séparateur décimal appropriés. Dans .NET, ces informations de mise en forme supplémentaires sont disponibles via l’interface [IFormatProvider](xref:System.IFormatProvider), laquelle est fournie comme paramètre à une ou plusieurs surcharges de la méthode `ToString` de types numériques et de types de date et d’heure. Des implémentations de l’interface [IFormatProvider](xref:System.IFormatProvider) sont utilisées dans .NET pour prendre en charge la mise en forme spécifique à la culture. L’exemple suivant montre comment la représentation d’un objet sous forme de chaîne évolue quand il est mis en forme avec trois objets [IFormatProvider](xref:System.IFormatProvider) représentant des cultures différentes.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

L’interface [IFormatProvider](xref:System.IFormatProvider) inclut une méthode, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), qui a un seul paramètre spécifiant le type d’objet qui fournit les informations de mise en forme. Si la méthode peut fournir un objet de ce type, elle le retourne. Autrement, elle retourne une référence Null.

[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) est une méthode de rappel. Quand vous appelez une surcharge de méthode `ToString` qui inclut un paramètre [IFormatProvider](xref:System.IFormatProvider), elle appelle la méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) de cet objet [IFormatProvider](xref:System.IFormatProvider). La méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) est chargée de retourner les informations de mise en forme requises, spécifiées par son paramètre *formatType*, à la méthode `ToString`. 

Certaines méthodes de mise en forme ou de conversion de chaînes incluent un paramètre de type [IFormatProvider](xref:System.IFormatProvider), mais la valeur de ce paramètre est souvent ignorée quand la méthode est appelée. Le tableau suivant répertorie certaines des méthodes de mise en forme qui utilisent le paramètre et le type de l’objet [Type](xref:System.Type) qu’elles passent à la méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). 

Méthode | Type de paramètre *formatType*
------ | ------------------------------
Méthode `ToString` de types numériques | [System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)
Méthode `ToString` de types de date et d'heure | [System.Globalization.DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo)
[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | [System.ICustomFormatter](xref:System.ICustomFormatter)

.NET propose trois classes qui implémentent [IFormatProvider](xref:System.IFormatProvider) : 

* [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), une classe qui fournit des informations de mise en forme pour les valeurs de date et d’heure pour une culture spécifique. Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne une instance d’elle-même.

* [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), une classe qui fournit des informations de mise en forme des nombres pour une culture spécifique. Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne une instance d’elle-même.

* [CultureInfo](xref:System.Globalization.CultureInfo). Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) peut retourner un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour fournir des informations de mise en forme des nombres ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) pour fournir des informations de mise en forme des valeurs de date et d’heure. 

Vous pouvez aussi implémenter votre propre fournisseur de format en remplacement de l'une de ces classes. Toutefois, la méthode `GetFormat` de votre implémentation doit retourner un objet du type répertorié dans le tableau précédent s'il doit fournir des informations de mise en forme à la méthode `ToString`.

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Mise en forme dépendante de la culture des valeurs numériques

Par défaut, la mise en forme des valeurs numériques est dépendante de la culture. Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées. Ceci est illustré dans l’exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) soit appelée. Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle. Ceci tient au fait que les méthodes `ToString` et `ToString(String)` encapsulent les appels à la méthode `ToString(String, IFormatProvider)` de chaque type numérique. 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

Vous pouvez également mettre en forme une valeur numérique pour une culture spécifique en appelant une surcharge `ToString` dotée d’un paramètre de *fournisseur* et en lui passant l’un ou l’autre des éléments suivants : 

* Un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont les conventions de mise en forme doivent être utilisées. Sa méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne la valeur de la propriété [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), qui est l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui fournit des informations de mise en forme propres à la culture pour les valeurs numériques.

* Un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) définissant les conventions de mise en forme propres à la culture qui doivent être utilisées. Sa méthode [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retourne une instance d’elle-même.

L’exemple suivant utilise des objets [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui représentent les cultures Anglais (États-Unis) et Anglais (Grande-Bretagne), ainsi que les cultures neutres Français et Russe pour mettre en forme un nombre à virgule flottante.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Mise en forme dépendante de la culture des valeurs de date et d’heure

Par défaut, la mise en forme des valeurs de date et d'heure est dépendante de la culture. Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées. Ceci est illustré dans l’exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) soit appelée. Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle. En effet, les méthodes [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) et [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) incluent les appels aux méthodes [DateTime.ToString (String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) et [DateTimeOffset.ToString (String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) dans un wrapper.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

Vous pouvez également mettre en forme une valeur de date et d’heure pour une culture spécifique en appelant une surcharge [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) dotée d’un paramètre de fournisseur et en lui passant l’un ou l’autre des éléments suivants : 

* Un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont les conventions de mise en forme doivent être utilisées. Sa méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne la valeur de la propriété [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), qui est l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui fournit des informations de mise en forme propres à la culture pour les valeurs numériques.

* Un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) définissant les conventions de mise en forme propres à la culture qui doivent être utilisées. Sa méthode [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) retourne une instance d’elle-même.

L’exemple suivant utilise des objets [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui représentent les cultures Anglais (États-Unis) et Anglais (Grande-Bretagne), ainsi que les cultures neutres Français et Russe pour mettre en forme une date. 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a>Interface IFormattable

En règle générale, les types qui surchargent la méthode `ToString` avec une chaîne de format et un paramètre [IFormatProvider](xref:System.IFormatProvider) implémentent également l’interface [IFormattable](xref:System.IFormattable). Cette interface comprend un seul membre, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), qui inclut comme paramètres une chaîne de format et un fournisseur de format.

L’implémentation de l’interface [IFormattable](xref:System.IFormattable) pour votre classe définie par l’application présente deux avantages : 

* Prise en charge de la conversion de chaînes par la classe [Convert](xref:System.Convert). Les appels aux méthodes [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) et [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) appellent automatiquement votre implémentation d’[IFormattable](xref:System.IFormattable).

* Prise en charge de la mise en forme composite. Si un élément de mise en forme qui inclut une chaîne de format est utilisé pour mettre en forme votre type personnalisé, le Common Language Runtime appelle automatiquement votre implémentation d’[IFormattable](xref:System.IFormattable) et lui passe la chaîne de format. Pour plus d’informations sur la mise en forme composite avec des méthodes telles que `String.Format` ou `Console.WriteLine`, consultez la section [Mise en forme composite](#composite-formatting).

L’exemple suivant définit une classe `Temperature` qui implémente l’interface [IFormattable](xref:System.IFormattable). Il prend en charge les spécificateurs de format "C" ou "G" pour afficher la température en Celsius, le spécificateur de format "F" pour afficher la température en Fahrenheit et le spécificateur de format "K" pour afficher la température en Kelvin.

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

L'exemple suivant instancie un objet `Temperature`. Il appelle ensuite la méthode [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) et utilise plusieurs chaînes de format composites pour obtenir des représentations sous forme de chaîne différentes d’un objet `Temperature`. Chacun de ces appels de méthode appelle, à son tour, l’implémentation d’[IFormattable](xref:System.IFormattable) de la classe `Temperature`.

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a>Mise en forme composite

Certaines méthodes, telles que `String.Format` et `StringBuilder.AppendFormat`, prennent en charge la mise en forme composite. Une chaîne de format composite est un genre de modèle retournant une seule chaîne qui incorpore la représentation sous forme de chaîne de zéro, un ou plusieurs objets. Chaque objet est représenté dans la chaîne de format composite par un élément de mise en forme indexé. L'index de l'élément de mise en forme correspond à la position de l'objet qu'il représente dans la liste de paramètres de la méthode. Les index sont de base zéro. Par exemple, dans l'appel suivant à la méthode `String.Format`, le premier élément de mise en forme, `{0:D}`, est remplacé par la représentation sous forme de chaîne de `thatDate` ; le deuxième élément de mise en forme, `{1}`, est remplacé par la représentation sous forme de chaîne `item1` ; le troisième élément de mise en forme, `{2:C2}`, est remplacé par la représentation sous forme de chaîne de `item1.Value`.

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

En plus de remplacer un élément de format par la représentation sous forme de chaîne de l'objet correspondant, les éléments de format vous permettent également de contrôler les éléments suivants : 

* La façon spécifique dont un objet est représenté sous forme de chaîne, si l’objet implémente l’interface [IFormattable](xref:System.IFormattable) et prend en charge les chaînes de format. Ceci se fait en faisant suivre l’index de l’élément de format d’un caractère « : » (deux-points), suivi d’une chaîne de format valide. L’exemple précédent a fait cela en mettant en forme une valeur de date avec la chaîne de format "d" (modèle de date courte) (par exemple `{0:d}`) et en mettant en forme une valeur numérique avec la chaîne de format "C2" (par exemple `{2:C2}` pour représenter le nombre comme valeur monétaire avec deux décimales). 

* La largeur du champ qui contient la représentation sous forme de chaîne de l'objet, et l'alignement de la représentation sous forme de chaîne de ce champ. Ceci se fait en faisant suivre l’index de l’élément de format d’un caractère « , » (virgule), suivie de la largeur du champ. La chaîne est alignée à droite dans le champ si la largeur du champ est une valeur positive, et elle est alignée à gauche si la largeur du champ est une valeur négative. L'exemple suivant aligne à gauche des valeurs de date dans un champ de 20 caractères, et aligne à droite des valeurs décimales avec une décimale dans un champ de 11 caractères. 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

Notez que si le composant de chaîne d'alignement et le composant de chaîne de format sont présents, le premier a priorité sur le deuxième (par exemple `{0,-20:g}`. 

Pour plus d’informations sur la mise en forme composite, consultez [Mise en forme composite](composite-format.md).

## <a name="custom-formatting-with-icustomformatter"></a>Mise en forme personnalisée avec ICustomFormatter

Deux méthodes de mise en forme composites, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) et [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), incluent un paramètre de fournisseur de format qui prend en charge la mise en forme personnalisée. Quand l’une de ces méthodes de mise en forme est appelée, elle passe à la méthode `GetFormat` du fournisseur de format un objet [Type](xref:System.Type) qui représente une interface [ICustomFormatter](xref:System.ICustomFormatter). La méthode `GetFormat` est alors chargée de retourner l’implémentation d’[ICustomFormatter](xref:System.ICustomFormatter) qui fournit la mise en forme personnalisée.

L’interface [ICustomFormatter](xref:System.ICustomFormatter) a une méthode unique, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), qui est appelée automatiquement par une méthode de mise en forme composite, une fois pour chaque élément de mise en forme dans une chaîne de format composite. La méthode [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) a trois paramètres : une chaîne de format, qui représente l’argument *formatString* dans un élément de mise en forme, un objet à mettre en forme et un objet [IFormatProvider](xref:System.IFormatProvider) qui fournit des services de mise en forme. En général, la classe qui implémente [ICustomFormatter](xref:System.ICustomFormatter) implémente également [IFormatProvider](xref:System.IFormatProvider) ; ce dernier paramètre est donc une référence à la classe de mise en forme personnalisée elle-même. La méthode retourne une représentation sous forme de chaîne mise en forme personnalisée de l'objet à mettre en forme. Si la méthode ne peut pas mettre en forme l’objet, elle doit retourner une référence null.

L’exemple suivant fournit une implémentation d’[ICustomFormatter](xref:System.ICustomFormatter) nommée `ByteByByteFormatter` qui affiche des valeurs entières sous la forme d’une séquence de valeurs hexadécimales à deux chiffres suivie d’un espace.

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

L'exemple suivant utilise la classe `ByteByByteFormatter` pour mettre en forme des valeurs entières. Notez que la méthode [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) est appelée plusieurs fois dans le deuxième appel de méthode [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), et que le fournisseur [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) par défaut est utilisé dans le troisième appel de méthode, car la méthode `.ByteByByteFormatter.Format` ne reconnaît pas la chaîne de format "N0" et retourne une référence null.

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a>Rubriques connexes

Titre | Définition
----- | ----------
[Chaînes de format numériques standard](standard-numeric.md) | Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques. 
[Chaînes de format numériques personnalisées](custom-numeric.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.
[Chaînes de format de date et d’heure standard](standard-datetime.md) |  Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs [DateTime](xref:System.DateTime).
[Chaînes de format de date et d’heure personnalisées](custom-datetime.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l’application pour les valeurs [DateTime](xref:System.DateTime).
[Chaînes de format TimeSpan standard](standard-timespan.md) | Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.
[Chaînes de format TimeSpan personnalisées](custom-timespan.md) | Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.
[Chaînes de format d’énumération](enumeration-format.md) | Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.
[Mise en forme composite](composite-format.md) | Explique comment incorporer une ou plusieurs valeurs mises en forme dans une chaîne. La chaîne peut ensuite être affichée dans la console ou écrite dans un flux.
[Exécution d’opérations de mise en forme](performing-formatting-operations.md) | Répertorie les rubriques qui fournissent des instructions pas à pas pour effectuer des opérations de mise en forme spécifiques.
[Analyse de chaînes](parsing-strings.md) | Décrit comment initialiser des objets aux valeurs décrites par des représentations sous forme de chaîne de ces objets. L'analyse est l'opération inverse de la mise en forme.

## <a name="reference"></a>Référence

[System.IFormattable](xref:System.IFormattable)

[System.IFormatProvider](xref:System.IFormatProvider)

[System.ICustomFormatter](xref:System.ICustomFormatter)

