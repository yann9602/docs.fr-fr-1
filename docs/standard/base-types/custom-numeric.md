---
title: "Chaînes de format numériques personnalisées"
description: "Chaînes de format numériques personnalisées"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 7b1c16ee-956f-4e9c-8502-c3dd6598c51d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: e36c0117f6f011589299fa59a8abd139870c2257

---

# <a name="custom-numeric-format-strings"></a>Chaînes de format numériques personnalisées

Vous pouvez créer une chaîne de format numérique personnalisée, qui est composée d'un ou de plusieurs spécificateurs de format numériques personnalisés, pour définir la mise en forme des données numériques. Une chaîne de format numérique personnalisée est toute chaîne de format autre qu’une [chaîne de format numérique standard](standard-numeric.md). 

Les chaînes de format numérique personnalisées sont prises en charge par certaines surcharges de la méthode `ToString` de tous les types numériques. Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes [ToString (String)](xref:System.Int32.ToString(System.String)) et [ToString (String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) du type [Int32](xref:System.Int32). Les chaînes de format numériques personnalisées sont également prises en charge par la fonctionnalité de [mise en forme composite](composite-format.md) .NET Framework, utilisée par certaines méthodes `Write` et `WriteLine` des classes [Console](xref:System.Console) et [StreamWriter](xref:System.IO.StreamWriter), la méthode [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) et la méthode [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)).

Le tableau suivant décrit les spécificateurs de format numériques personnalisés et affiche un exemple de sortie produite par chaque spécificateur de format. Consultez la section [Remarques](#notes) pour plus d’informations sur l’utilisation de chaînes de format numériques personnalisées, et la section [Exemple](#example) pour obtenir une illustration complète de leur utilisation.

Spécificateur de format | Nom | Description | Exemples
---------------- | ---- | ----------- | --------
"0" | Espace réservé du zéro | Remplace le zéro par le chiffre correspondant, le cas échéant ; sinon, le zéro s'affiche dans la chaîne de résultat. | `1234.5678 ("00000") -> 01235`; `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"#" | Espace réservé de chiffre | Remplace le symbole « # » par le chiffre correspondant, le cas échéant ; sinon, aucun chiffre ne s'affiche dans la chaîne de résultat. Notez qu’aucun chiffre n’apparaît dans la chaîne de résultat si le chiffre correspondant dans la chaîne d’entrée est un 0 non significatif. Exemple : 0003 ("####") -> 3. | `1234.5678 ("#####") -> 1235`; `0.45678 ("#.##", en-US) -> .46`; `0.45678 ("#.##", fr-FR) -> ,46`
"." | Virgule décimale | Détermine l'emplacement du séparateur décimal dans la chaîne de résultat. | `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"," | Séparateur de groupes et mise à l'échelle des nombres | Sert à la fois de séparateur de groupes et de spécificateur de mise à l'échelle des nombres. En tant que séparateur de groupes, il insère un caractère de séparation des groupes localisé entre chaque groupe. En tant que spécificateur de mise à l'échelle des nombres, il divise un nombre par 1000 pour chaque virgule spécifiée. | Spécificateur de séparateur de groupes : `2147483647 ("##,#", en-US) -> 2,147,483,647` ; `2147483647 ("##,#", es-ES) -> 2.147.483.647`. Spécificateur de mise à l’échelle : `2147483647 ("#,#,,", en-US) -> 2,147` ; `2147483647 ("#,#,,", es-ES) -> 2.147`
"%" | Espace réservé de pourcentage | Multiplie un nombre par 100 et insère un symbole de pourcentage localisé dans la chaîne de résultat. | `0.3697 ("%#0.00", en-US) -> %36.97`; `0.3697 ("%#0.00", el-GR) -> %36,97`; `0.3697 ("##.0 %", en-US) -> 37.0 %`; `0.3697 ("##.0 %", el-GR) -> 37,0 %`
"‰" | Espace réservé « pour mille » | Multiplie un nombre par 1000 et insère un symbole « pour mille » localisé dans la chaîne de résultat. | `0.03697 ("#0.00‰", en-US) -> 36.97‰`; `0.03697 ("#0.00‰", ru-RU) -> 36,97‰`
"E0", "E+0", "E-0", "e0", "e+0", "e-0" | Notation exponentielle | Si le spécificateur est suivi d'au moins un zéro (0), met en forme le résultat à l'aide de la notation exponentielle. La casse de « E » ou « e » indique la casse du symbole d'exposant dans la chaîne de résultat. Le nombre des zéros qui suivent le caractère « E » ou « e » détermine le nombre minimal de chiffres dans l'exposant. Un signe plus (+) indique qu'un caractère de signe précède toujours l'exposant. Un signe moins (-) indique qu'un caractère de signe précède uniquement les exposants négatifs. | `987654 ("#0.0e0") -> 98.8e4`; `1503.92311 ("0.0##e+00") -> 1.504e+03`; `1.8901385E-16 ("0.0e+00") -> 1.9e-16`
\ | Caractère d'échappement | Entraîne l'interprétation du caractère suivant comme un littéral plutôt que comme un spécificateur de format personnalisé. | `987654 ("\###00\#") -> #987654#`
'chaîne', "chaîne" | Délimiteur de chaîne littérale | Indique que les caractères encadrés doivent être copiés inchangés dans la chaîne de résultat. | `68 ("# ' degrees'") -> 68 degrees`
; | Séparateur de section | Définit des sections avec des chaînes de format distinctes pour les nombres positifs, négatifs et nuls. | `12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35`; `0 ("#0.0#;(#0.0#);-\0-") -> -0-`; `-12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)`; `12.345 ("#0.0#;(#0.0#)") -> 12.35`; `0 ("#0.0#;(#0.0#)") -> 0.0 ; -12.345 ("#0.0#;(#0.0#)") -> (12.35)`
Autre | Tous les autres caractères | Le caractère est copié inchangé dans la chaîne de résultat. | `68 ("# °") -> 68 °`

Les sections suivantes fournissent des informations détaillées sur chacun des spécificateurs de format numériques personnalisés.

## <a name="the-0-custom-specifier"></a>Spécificateur personnalisé "0"

Le spécificateur de format personnalisé "0" sert de symbole d'espace réservé du zéro. Si la valeur qui est mise en forme comprend un chiffre à l'emplacement le zéro apparaît dans la chaîne de format, ce chiffre est copié dans la chaîne de résultant ; sinon, un zéro apparaît dans la chaîne de résultat. L'emplacement du zéro situé à l'extrême gauche avant le séparateur décimal et du zéro situé à l'extrême droite après le séparateur décimal détermine la plage des chiffres qui sont toujours présents dans la chaîne de résultat. 

Le spécificateur « 00 » provoque l'arrondissement de la valeur au chiffre le plus proche précédant la virgule ; l'arrondissement à une valeur différente de zéro est toujours utilisé. Par exemple, la mise en forme de 34,5 avec « 00 » produit la valeur 35.

L'exemple suivant affiche plusieurs valeurs qui sont mises en forme à l'aide de chaînes de format personnalisées incluant des espaces réservés du zéro.

```csharp
double value;

value = 123;
Console.WriteLine(value.ToString("00000"));
Console.WriteLine(String.Format("{0:00000}", value));
// Displays 00123

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

CultureInfo daDK = CultureInfo.CreateSpecificCulture("da-DK");
Console.WriteLine(value.ToString("00.00", daDK)); 
Console.WriteLine(String.Format(daDK, "{0:00.00}", value));
// Displays 01,20

value = .56;
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value));
// Displays 0.6

value = 1234567890;
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value)); 
// Displays 1,234,567,890      

CultureInfo elGR = CultureInfo.CreateSpecificCulture("el-GR");
Console.WriteLine(value.ToString("0,0", elGR)); 
Console.WriteLine(String.Format(elGR, "{0:0,0}", value));   
// Displays 1.234.567.890

value = 1234567890.123456;
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture));   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value));   
// Displays 1,234,567,890.1  

value = 1234.567890;
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture));  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value));  
// Displays 1,234.57
```

```vb
Dim value As Double

value = 123
Console.WriteLine(value.ToString("00000"))
Console.WriteLine(String.Format("{0:00000}", value))
' Displays 00123

value = 1.2
Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                  "{0:0.00}", value))
' Displays 1.20
Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value))
' Displays 01.20
Dim daDK As CultureInfo = CultureInfo.CreateSpecificCulture("da-DK")
Console.WriteLine(value.ToString("00.00", daDK))
Console.WriteLine(String.Format(daDK, "{0:00.00}", value))
' Displays 01,20

value = .56
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value))
' Displays 0.6

value = 1234567890
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture))  
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value))  
' Displays 1,234,567,890      
Dim elGR As CultureInfo = CultureInfo.CreateSpecificCulture("el-GR")
Console.WriteLine(value.ToString("0,0", elGR))
Console.WriteLine(String.Format(elGR, "{0:0,0}", value))    
' Displays 1.234.567.890

value = 1234567890.123456
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value))    
' Displays 1,234,567,890.1  

value = 1234.567890
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture))   
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value))   
' Displays 1,234.57
```

## <a name="the-custom-specifier"></a>Spécificateur personnalisé "#"

Le spécificateur de format personnalisé "#" sert de symbole d'espace réservé des chiffres. Si la valeur qui est mise en forme comprend un chiffre à l'emplacement où le symbole « # » apparaît dans la chaîne de format, ce chiffre est copié dans la chaîne de résultat. Sinon, rien n'est stocké à cet emplacement dans la chaîne résultante. 

Notez que ce spécificateur n'affiche jamais un zéro qui n'est pas un chiffre significatif, même si le zéro est le seul chiffre de la chaîne. Il affichera zéro uniquement s'il s'agit d'un chiffre significatif dans le nombre affiché. 

La chaîne de format « ## » provoque l'arrondissement de la valeur au chiffre le plus proche précédant la virgule ; l'arrondissement à une valeur différente de zéro est toujours utilisé. Par exemple, la mise en forme de 34,5 avec « ## » produit la valeur 35.

L'exemple suivant affiche plusieurs valeurs qui sont mises en forme à l'aide de chaînes de format personnalisées incluant des espaces réservés de chiffres.

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value));
// Displays 1.2

value = 123;
Console.WriteLine(value.ToString("#####"));
Console.WriteLine(String.Format("{0:#####}", value));
// Displays 123

value = 123456;
Console.WriteLine(value.ToString("[##-##-##]"));      
Console.WriteLine(String.Format("{0:[##-##-##]}", value));      
// Displays [12-34-56]

value = 1234567890;
Console.WriteLine(value.ToString("#"));
Console.WriteLine(String.Format("{0:#}", value));
// Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"));
Console.WriteLine(String.Format("{0:(###) ###-####}", value));
// Displays (123) 456-7890
```

```vb
Dim value As Double

value = 1.2
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value))
' Displays 1.2

value = 123
Console.WriteLine(value.ToString("#####"))
Console.WriteLine(String.Format("{0:#####}", value))
' Displays 123

value = 123456
Console.WriteLine(value.ToString("[##-##-##]"))      
Console.WriteLine(String.Format("{0:[##-##-##]}", value))      
' Displays [12-34-56]

value = 1234567890
Console.WriteLine(value.ToString("#"))
Console.WriteLine(String.Format("{0:#}", value))
' Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"))
Console.WriteLine(String.Format("{0:(###) ###-####}", value))
' Displays (123) 456-7890
```

Pour retourner une chaîne de résultat dans laquelle les chiffres absents ou les zéros non significatifs sont remplacés par des espaces, utilisez la fonctionnalité de [mise en forme composite](composite-format.md) et spécifiez une largeur de champ, comme l’illustre l’exemple suivant.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double value = .324;
      Console.WriteLine("The value is: '{0,5:#.###}'", value);
   }
}
// The example displays the following output if the current culture
// is en-US:
//      The value is: ' .324'
```

```vb
Module Example
   Public Sub Main()
      Dim value As Double = .324
      Console.WriteLine("The value is: '{0,5:#.###}'", value)
   End Sub
End Module
' The example displays the following output if the current culture
' is en-US:
'      The value is: ' .324'
```

## <a name="the-custom-specifier"></a>Le spécificateur personnalisé "."

Le spécificateur de format personnalisé "." insère un séparateur décimal localisé dans la chaîne de résultat. Le premier point de la chaîne de format détermine l'emplacement du séparateur décimal dans la valeur mise en forme. Tout autre point est ignoré. 

Le caractère qui est utilisé comme séparateur décimal dans la chaîne de résultat n’est pas toujours un point ; il est déterminé par la propriété [NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôle la mise en forme.

L'exemple suivant utilise le spécificateur de format "." pour définir l'emplacement de la virgule décimale dans plusieurs chaînes de résultat.

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

Console.WriteLine(value.ToString("00.00", 
                CultureInfo.CreateSpecificCulture("da-DK")));
Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                "{0:00.00}", value));
// Displays 01,20

value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value)); 
// Displays 8.6%

value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.###E+0}", value));
// Displays 8.6E+4
```

```vb
Dim value As Double

  value = 1.2
  Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
  Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:0.00}", value))
  ' Displays 1.20

  Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:00.00}", value))
  ' Displays 01.20

  Console.WriteLine(value.ToString("00.00", _
                    CultureInfo.CreateSpecificCulture("da-DK")))
  Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                    "{0:00.00}", value))
  ' Displays 01,20

  value = .086
  Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)) 
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#0.##%}", value)) 
  ' Displays 8.6%

  value = 86000
  Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                    "{0:0.###E+0}", value))
' Displays 8.6E+4
```

## <a name="the-custom-specifier"></a>Spécificateur personnalisé ","

Le caractère "," sert à la fois de séparateur de groupes et de spécificateur de mise à l'échelle des nombres. 

* Séparateur de groupes : si une ou plusieurs virgules sont spécifiées entre deux espaces réservés de chiffres (0 ou #) qui mettent en forme les chiffres intégraux d'un nombre, un caractère de séparation des groupes est inséré entre chaque groupe de nombres dans la partie intégrale de la sortie. 

  Les propriétés [NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) et [NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actuel déterminent le caractère utilisé comme séparateur de groupes de nombres et la taille de chaque groupe de nombres. Par exemple, si la chaîne « #,# » et la culture indifférente sont utilisées pour mettre en forme le nombre 1000, la sortie est « 1,000 ».
  
* Spécificateur de mise à l'échelle des nombres : si une ou plusieurs virgules sont spécifiées immédiatement à gauche du séparateur décimal explicite ou implicite, le nombre à mettre en forme est divisé par 1000 pour chaque virgule. Par exemple, si la chaîne « 0,, » est utilisée pour mettre en forme le nombre 100 millions, la sortie est « 100 ». 

Vous pouvez utiliser des spécificateurs de séparateur de groupes et de mise à l'échelle des nombres dans la même chaîne de format. Par exemple, si la chaîne « #,0,, » et la culture indifférente sont utilisées pour mettre en forme le nombre 1 milliard, la sortie est « 1,000 ». 

L'exemple suivant illustre l'utilisation de la virgule comme séparateur de groupes.

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value));
// Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));
// Displays 1,235
```

```vb
Dim value As Double = 1234567890
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value))
' Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value))
' Displays 1,235
```

L'exemple suivant illustre l'utilisation de la virgule comme spécificateur pour la mise à l'échelle des nombres.

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,}", value)); 
// Displays 1235   

Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,,}", value));
// Displays 1  

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));       
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));       
// Displays 1,235
```  

```vb
Dim value As Double = 1234567890
  Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture))    
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, "{0:#,,}", value))  
  ' Displays 1235   

  Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,,,}", value))
' Displays 1  

  Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))       
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,##0,,}", value))       
' Displays 1,235
```

## <a name="the-custom-specifier"></a>Spécificateur personnalisé "%"

Un signe de pourcentage (%) dans une chaîne de format entraîne la multiplication d'un nombre par 100 avant sa mise en forme. Le symbole de pourcentage localisé est inséré dans le nombre à l'emplacement où le caractère % apparaît dans la chaîne de format. Le caractère de pourcentage utilisé est défini par la propriété [PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actuel.

L'exemple suivant définit plusieurs chaînes de format personnalisées qui incluent le spécificateur personnalisé "%".

```csharp
double value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value));
// Displays 8.6%     
```

```vb
Dim value As Double = .086
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value))
' Displays 8.6% 
```

## <a name="the-custom-specifier"></a>Spécificateur personnalisé "‰"

Un caractère « pour mille » (‰ ou \u2030) dans une chaîne de format entraîne la multiplication d'un nombre par 1 000 avant sa mise en forme. Le symbole « pour mille » approprié est inséré dans la chaîne retournée, à l'emplacement où le symbole ‰ apparaît dans la chaîne de format. Le caractère « pour mille » utilisé est défini par la propriété [NumberFormatInfo.PerMilleSymbol](xref:System.Globalization.NumberFormatInfo.PerMilleSymbol) de l’objet qui fournit les informations de mise en forme spécifique à la culture.

L'exemple suivant définit une chaîne de format personnalisée qui inclut le spécificateur personnalisé "‰".

```csharp
double value = .00354;
string perMilleFmt = "#0.## " + '\u2030';
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value));
// Displays 3.54‰   
```

```vb
Dim value As Double = .00354
Dim perMilleFmt As String = "#0.## " & ChrW(&h2030)
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value))
' Displays 3.54 ‰
```

## <a name="the-e-and-e-custom-specifiers"></a>Spécificateurs personnalisés « E » et « e »

Si l'une des chaînes "E", "E+", "E-", "e", "e+" ou "e-" est présente dans la chaîne de format et immédiatement suivie d'au moins un zéro, le nombre est mis en forme à l'aide de la notation scientifique, avec un "E" ou un "e" inséré entre le nombre et l'exposant. Le nombre de zéros qui suivent l'indicateur de notation scientifique détermine le nombre minimal de chiffres à afficher pour l'exposant. Les formats "E+" et "e+" indiquent qu'un signe plus ou un signe moins doit toujours précéder l'exposant. Les formats "E", "E-", "e" ou "e-" indiquent qu'un signe ne doit précéder que les exposants négatifs.

L'exemple suivant met en forme plusieurs valeurs numériques à l'aide des spécificateurs pour la notation scientifique.

```csharp
double value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value));
// Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value));
// Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value));
// Displays 8.6E004
```

```vb
Dim value As Double = 86000
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value))
' Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value))
' Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value))
' Displays 8.6E004
```

## <a name="the-escape-character"></a>Caractère d’échappement "\"

Les symboles "#", "0", ".", ",", "%" et "‰" dans une chaîne de format sont interprétés comme des spécificateurs de format plutôt que comme des caractères littéraux. En fonction de leur position dans une chaîne de format personnalisée, les "E" majuscules et minuscules ainsi que les symboles + et - peuvent également être interprétés comme des spécificateurs de format. 

Pour éviter qu'un caractère soit interprété comme un spécificateur de format, vous pouvez le faire précéder d'une barre oblique inverse, qui est le caractère d'échappement. Le caractère d'échappement signifie que le caractère suivant est un caractère littéral qui doit être inclus inchangé dans la chaîne de résultat.

Pour inclure une barre oblique inverse dans une chaîne de résultat, vous devez la placer dans une séquence d'échappement avec une autre barre oblique inverse (\\). 

> [!NOTE]
> Certains compilateurs, tels que le compilateur C#, peuvent également interpréter une barre oblique inverse unique comme un caractère d’échappement. Pour garantir l’interprétation correcte d’une chaîne durant la mise en forme, vous pouvez utiliser le caractère littéral de chaîne textuelle (le caractère @) avant la chaîne en C#, ou ajouter une autre barre oblique inverse avant chaque barre oblique inverse. L'exemple C# suivant illustre ces deux approches.

L’exemple suivant utilise le caractère d’échappement pour empêcher l’opération de mise en forme d’interpréter les caractères "#", "0" et "\" comme des caractères d’échappement ou des spécificateurs de format. L’exemple utilise une barre oblique inverse supplémentaire pour garantir qu’une barre oblique inverse est interprétée comme un caractère littéral.

```csharp
int value = 123;
Console.WriteLine(value.ToString("\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#"));
Console.WriteLine(String.Format("{0:\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString(xref:"\#\#\# ##0 dollars and \0\0 cents \#\#\#"));
Console.WriteLine(String.Format(xref:"{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\"));
Console.WriteLine(String.Format("{0:\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\

Console.WriteLine(value.ToString(xref:"\\\\\\ ##0 dollars and \0\0 cents \\\\\\"));
Console.WriteLine(String.Format(xref:"{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\
```

```vb
Dim value As Integer = 123
Console.WriteLine(value.ToString("\#\#\# ##0 dollars and \0\0 cents \#\#\#"))
Console.WriteLine(String.Format("{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}", 
                                value))
' Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\ ##0 dollars and \0\0 cents \\\\\\"))
Console.WriteLine(String.Format("{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}", 
                                value))
' Displays \\\ 123 dollars and 00 cents \\\
```

## <a name="the-section-separator"></a>Séparateur de section ";"

Le point-virgule (;) est un spécificateur de format conditionnel qui applique une mise en forme différente à un nombre suivant que sa valeur est positive, négative ou nulle. Pour entraîner ce comportement, une chaîne de format personnalisée peut contenir jusqu'à trois sections séparées par des points-virgules. Ces sections sont décrites dans le tableau suivant. 

Nombre de sections | Description
------------------ | -----------
Une section | La chaîne de format s'applique à toutes les valeurs.
Deux sections | La première section s'applique aux valeurs positives et aux zéros, et la deuxième section s'applique aux valeurs négatives. Si le nombre à mettre en forme est négatif, mais devient nul après l'arrondissement au format de la deuxième section, le zéro résultant est mis en forme en fonction de la première section.
Trois sections | La première section s'applique aux valeurs positives, la deuxième section s'applique aux valeurs négatives et la troisième section s'applique aux zéros. La deuxième section peut rester vide (en n'insérant aucune valeur entre les points-virgules), auquel cas la première section s'applique à toutes les valeurs différentes de zéro. Si le nombre à mettre en forme est différent de zéro, mais devient nul après l'arrondissement au format de la première ou deuxième section, le zéro résultant est mis en forme en fonction de la troisième section.

Les séparateurs de section ignorent toute mise en forme préexistante associée à un nombre lorsque la valeur finale est mise en forme. Par exemple, les valeurs négatives sont toujours affichées sans signe moins lorsque des séparateurs de section sont utilisés. Si vous souhaitez que la valeur mise en forme finale soit précédée d'un signe moins, vous devez inclure ce signe explicitement comme élément du spécificateur de format personnalisé. 

L'exemple suivant utilise le spécificateur de format ";" pour mettre en forme différemment les nombres positifs, négatifs et nuls.

```csharp
double posValue = 1234;
double negValue = -1234;
double zeroValue = 0;

string fmt2 = "##;(##)";
string fmt3 = "##;(##);**Zero**";

Console.WriteLine(posValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue));    
// Displays 1234

Console.WriteLine(negValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue));    
// Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3)); 
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue));
// Displays **Zero**
```

```vb
Dim posValue As Double = 1234
Dim negValue As Double = -1234
Dim zeroValue As Double = 0

Dim fmt2 As String = "##;(##)"
Dim fmt3 As String = "##;(##);**Zero**"

Console.WriteLine(posValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue))    
' Displays 1234

Console.WriteLine(negValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue))    
' Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3))  
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue))
' Displays **Zero**
```

## <a name="notes"></a>Notes

### <a name="floatingpoint-infinities-and-nan"></a>Infinis à virgule flottante et NaN

Quelle que soit la chaîne de format, si la valeur d’un type virgule flottante [Single](xref:System.Single) ou [Double](xref:System.Double) est l’infini positif, l’infini négatif ou une valeur qui n’est pas un nombre, la chaîne mise en forme est, respectivement, la valeur de la propriété [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol), [NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) ou [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) qui est spécifiée par l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actuellement applicable. 

### <a name="rounding-and-fixedpoint-format-strings"></a>Arrondi et chaînes de format à virgule fixe

Pour les chaînes de format à virgule fixe (c'est-à-dire les chaînes de format ne contenant pas de caractères de format de notation scientifique), les nombres sont arrondis au même nombre de décimales que d'espaces réservés de chiffres à droite du séparateur décimal. Si la chaîne de format ne contient pas de virgule décimale, le nombre est arrondi à l'entier le plus proche. Si le nombre possède plus de chiffres que d'espaces réservés de chiffres à gauche de la virgule décimale, les chiffres supplémentaires sont copiés dans la chaîne résultante immédiatement avant le premier espace réservé de chiffre.

## <a name="example"></a>Exemple

L'exemple suivant présente deux chaînes de format numériques personnalisées. Dans les deux cas, l’espace réservé de chiffre (#) affiche les données numériques, et tous les autres caractères sont copiés dans la chaîne de résultat.

```csharp
double number1 = 1234567890;
string value1 = number1.ToString("(###) ###-####");
Console.WriteLine(value1);

int number2 = 42;
string value2 = number2.ToString("My Number = #");
Console.WriteLine(value2);
// The example displays the following output:
//       (123) 456-7890
//       My Number = 42
```

```vb
Dim number1 As Double = 1234567890
Dim value1 As String = number1.ToString("(###) ###-####")
Console.WriteLine(value1)

Dim number2 As Integer = 42
Dim value2 As String = number2.ToString("My Number = #")
Console.WriteLine(value2)
' The example displays the following output:
'       (123) 456-7890
'       My Number = 42
```

## <a name="see-also"></a>Voir aussi

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[Mise en forme des types](formatting-types.md)

[Chaînes de format numériques standard](standard-numeric.md)

[Guide pratique pour remplir un nombre avec des zéros non significatifs](pad-number.md)

[Mise en forme composite](composite-format.md)




<!--HONumber=Nov16_HO1-->


