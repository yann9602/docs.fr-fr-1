---
title: "Analyse de chaînes numériques dans .NET"
description: "Analyse de chaînes numériques dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 209d24d32eb3b235ff2fde2ef11ffd0ee4e930cf

---

# <a name="parsing-numeric-strings-in-net"></a>Analyse de chaînes numériques dans .NET

Tous les types numériques disposent de deux méthodes d’analyse statiques, `Parse` et `TryParse`, que vous pouvez utiliser pour convertir la représentation sous forme de chaîne d’un nombre en type numérique. Ces méthodes vous permettent d’analyser les chaînes qui ont été générées à l’aide de chaînes de format documentées dans [Chaînes de format numériques standard](standard-numeric.md) et [Chaînes de format numériques personnalisées](custom-numeric.md). Par défaut, les méthodes `Parse` et `TryParse` peuvent convertir correctement les chaînes qui contiennent uniquement des chiffres décimaux intégraux en valeurs entières. Ils peuvent convertir correctement les chaînes qui contiennent des chiffres décimaux intégraux et fractionnaires, des séparateurs de groupe et un séparateur décimal en valeurs à virgule flottante. La méthode `Parse` lève une exception si l’opération échoue, tandis que la méthode `TryParse` retourne `false`.

## <a name="parsing-and-format-providers"></a>Analyse et fournisseurs de format

En général, les représentations sous forme de chaîne de valeurs numériques varient selon la culture. Les éléments des chaînes numériques, tels que les symboles monétaires, les séparateurs de groupes (ou de milliers) et les séparateurs décimaux, varient selon la culture. Les méthodes d’analyse utilisent implicitement ou explicitement un fournisseur de format qui identifie ces variantes spécifiques à la culture. Si aucun fournisseur de format n’est spécifié dans un appel à la méthode `Parse` ou `TryParse`, le fournisseur de format associé à la culture du thread actuel (l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) retourné par la propriété [NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo)) est utilisé. 

Un fournisseur de format est représenté par une implémentation [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo). Cette interface a un seul membre, la méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)), dont l’unique paramètre est un objet [Type](xref:System.Type) qui représente le type à mettre en forme. Cette méthode retourne l’objet qui fournit des informations de mise en forme. .NET prend en charge les deux implémentations [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) suivantes pour analyser les chaînes numériques :

* Un objet [CultureInfo](xref:System.Globalization.CultureInfo) dont la méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui fournit des informations de mise en forme propres à la culture.

* Un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) dont la méthode [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) se retourne elle-même.

L’exemple suivant essaie de convertir chaque chaîne d’un tableau en une valeur [Double](xref:System.Double). Il commence par essayer d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture anglophone (États-Unis). Si cette opération lève une exception [FormatException](xref:System.FormatException), il tente d’analyser la chaîne à l’aide d’un fournisseur de format qui reflète les conventions de la culture française (France).

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a>Analyse et valeurs NumberStyles

Les éléments de style (tels que les espaces blancs, les séparateurs de groupe et le séparateur décimal) que l’opération d’analyse peut gérer sont définis par une valeur d’énumération [NumberStyles](xref:System.Globalization.NumberStyles). Par défaut, les chaînes qui représentent des valeurs entières sont analysées à l’aide de la valeur [NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer), qui autorise uniquement les chiffres numériques, les espaces blancs de début et de fin et un signe de début. Les chaînes qui représentent des valeurs à virgule flottante sont analysées à l’aide d’une combinaison des valeurs [NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) et [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands). Ce style composite autorise les chiffres décimaux avec un espace blanc de début et de fin, un signe de début, un séparateur décimal, un séparateur de groupes et un exposant. Quand vous appelez une surcharge de la méthode `Parse` ou `TryParse` qui inclut un paramètre de type [NumberStyles](xref:System.Globalization.NumberStyles) et que vous définissez un ou plusieurs indicateurs [NumberStyles](xref:System.Globalization.NumberStyles), vous pouvez contrôler les éléments de style pouvant être présents dans la chaîne pour que l’opération d’analyse aboutisse. 

Par exemple, une chaîne qui contient un séparateur de groupes ne peut pas être convertie en valeur [Int32](xref:System.Int32) à l’aide de la méthode [Int32.Parse(String)](xref:System.Int32.Parse(System.String)). Toutefois, la conversion réussit si vous utilisez l’indicateur [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands), comme le montre l’exemple suivant.

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> **Avertissement**
>
> L’opération d’analyse utilise toujours les conventions de mise en forme d’une culture particulière. Si vous ne spécifiez pas de culture en passant un objet [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), la culture associée au thread actuel est utilisée.
 
Le tableau suivant répertorie les membres de l’énumération [NumberStyles](xref:System.Globalization.NumberStyles) et décrit l’effet qu’ils ont sur l’opération d’analyse.

Valeur NumberStyles | Effet sur la chaîne à analyser
------------------ | --------------------------------- 
[NumberStyles.None](xref:System.Globalization.NumberStyles.None) | Seuls les chiffres sont autorisés.
[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | Le séparateur décimal et les chiffres fractionnaires sont autorisés. Pour les valeurs entières, le seul chiffre fractionnaire autorisé est zéro. Les séparateurs décimaux valides sont déterminés par la propriété [NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) ou [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator).
[NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) | Les caractères « e » ou « E » peuvent être utilisés pour indiquer une notation exponentielle.
[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | L’espace blanc de début est autorisé.
[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | L’espace blanc de fin est autorisé.
[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) | Un signe positif ou négatif peut précéder les chiffres.
[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign) | Un signe positif ou négatif peut suivre les chiffres.
[NumberStyles.AllowParentheses](xref:System.Globalization.NumberStyles.AllowParentheses) | Les parenthèses peuvent être utilisées pour indiquer des valeurs négatives.
[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) | Le séparateur de groupes est autorisé. Le caractère de séparation de groupe est déterminé par la propriété [NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) ou [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator).
[NumberStyles.AllowCurrencySymbol](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | Le symbole monétaire est autorisé. Le symbole monétaire est défini par la propriété [NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol).
[NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | La chaîne à analyser est interprétée comme un nombre hexadécimal. Elle peut inclure les chiffres hexadécimaux 0-9, A-F et a-f. Cet indicateur peut être utilisé uniquement pour analyser des valeurs entières.
 
En outre, l’énumération [NumberStyles](xref:System.Globalization.NumberStyles) fournit les styles composites suivants, qui comprennent plusieurs indicateurs [NumberStyles](xref:System.Globalization.NumberStyles). 

Valeur NumberStyles composite | Membres
---------------------------- | ---------------- 
[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) | Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) et [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign). Il s’agit du style par défaut utilisé pour analyser des valeurs entières.
[NumberStyles.Number](xref:System.Globalization.NumberStyles.Number) | Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) et [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands).
[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) | Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite), [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign), [NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) et [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent).
[NumberStyles.Currency](xref:System.Globalization.NumberStyles.Currency) | Comprend tous les styles, à l’exception de [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) et [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
[NumberStyles.Any](xref:System.Globalization.NumberStyles.Any) | Comprend tous les styles, à l’exception de [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
[NumberStyles.HexNumber](xref:System.Globalization.NumberStyles.HexNumber) | Comprend les styles [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite), [NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) et [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier).
 
## <a name="parsing-and-unicode-digits"></a>Analyse et chiffres Unicode

La norme Unicode définit des points de code pour les chiffres dans différents systèmes d’écriture. Par exemple, les points de code U+0030 à U+0039 représentent les chiffres latins de base 0 à 9, les points de code de U+09E6 à U+09EF représentent les chiffres bengalis compris entre 0 et 9, et les points de code U+FF10 à U+FF19 représentent les chiffres pleine chasse compris entre 0 et 9. Toutefois, les seuls chiffres identifiés par les méthodes d’analyse sont les chiffres latins de base 0 à 9 avec des points de code compris entre U+0030 et U+0039. Si une chaîne contenant tout autre chiffre est passée à une méthode d’analyse numérique, celle-ci lève une exception [FormatException](xref:System.FormatException).

L’exemple suivant utilise la méthode [Int32.Parse](xref:System.Int32.Parse(System.String)) pour analyser des chaînes composées de chiffres dans différents systèmes d’écriture. Comme l’indique le résultat de l’exemple, la tentative d’analyse des chiffres latins de base réussit, mais la tentative d’analyse des chiffres pleine chasse, arabe-hindi et bengali échoue.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a>Voir aussi

[System.Globalization.NumberStyles](xref:System.Globalization.NumberStyles)

[Analyse de chaînes dans .NET](parsing-strings.md)

[Mise en forme des types dans .NET](formatting-types.md)




<!--HONumber=Nov16_HO3-->


