---
title: "Chaînes de format numériques standard"
description: "Chaînes de format numériques standard"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 285faf73-466a-4af0-8eba-7e509958f240
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 5f5ee73c7c9e0ecdce8aa0d75a630decea57704b

---

# <a name="standard-numeric-format-strings"></a>Chaînes de format numériques standard

Les chaînes de format numériques standard sont utilisées pour mettre en forme des types numériques courants. Une chaîne de format numérique standard se présente sous la forme **A**_xx_, où : 

* **A** est un caractère alphabétique unique appelé *spécificateur de format*. Toute chaîne de format numérique contenant plusieurs caractères alphabétiques, y compris un espace blanc, est interprétée comme une chaîne de format numérique personnalisée. Pour plus d’informations, consultez [Chaînes de format numériques personnalisées](custom-numeric.md). 

* *xx* est un entier facultatif appelé *spécificateur de précision*. Le spécificateur de précision est compris entre 0 et 99 ; il affecte le nombre de chiffres dans le résultat. Notez que le spécificateur de précision contrôle le nombre de chiffres dans la représentation sous forme de chaîne d'un nombre. Il n'arrondit pas le nombre lui-même. Pour effectuer une opération d’arrondi, utilisez les méthodes [Math.Ceiling](xref:System.Math), [Math.Floor](xref:System.Math) ou [Math.Round](xref:System.Math). 

Quand un *spécificateur de précision* contrôle le nombre de décimales dans la chaîne de résultat, celle-ci donne des nombres arrondis vers le haut, en s’éloignant de zéro (c’est-à-dire avec [MidpointRounding.AwayFromZero](xref:System.MidpointRounding.AwayFromZero)). 

> [!NOTE]
> Le spécificateur de précision détermine le nombre de chiffres dans la chaîne de résultat. Pour remplir une chaîne de résultat avec des espaces de début ou de fin, utilisez la fonctionnalité de [mise en forme composite](composite-format.md) et définissez un *composant d’alignement* dans l’élément de mise en forme. 

Les chaînes de format numérique standard sont prises en charge par certaines surcharges de la méthode `ToString` de tous les types numériques. Par exemple, vous pouvez fournir une chaîne de format numérique aux méthodes [ToString(String)](xref:System.Int32.ToString(System.String)) et [ToString(String,IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) du type [Int32](xref:System.Int32). Les chaînes de format numériques standard sont également prises en charge par la fonctionnalité de [mise en forme composite](composite-format.md) .NET, utilisée par certaines méthodes `Write` et `WriteLine` des classes [Console](xref:System.Console) et [StreamWriter](xref:System.IO.StreamWriter), la méthode [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) et la méthode [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)). La fonctionnalité de mise en forme composite vous permet d’inclure la représentation sous forme de chaîne de plusieurs éléments de données dans une même chaîne, de spécifier la largeur d’un champ et d’aligner les nombres dans un champ. Pour plus d’informations, consultez [Mise en forme composite](composite-format.md). 

Le tableau suivant décrit les spécificateurs de format numériques standard et affiche une sortie produite par chaque spécificateur de format. Consultez la section [Remarques](#notes) pour plus d’informations sur l’utilisation de chaînes de format numériques standard, et la section [Exemple](#example) pour obtenir une illustration complète de leur utilisation.

|Spécificateur de format|Nom|Description|Exemples|  
|----------------------|----------|-----------------|--------------|  
|"C" ou "c"|Devise|Résultat : une valeur monétaire.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : défini par [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits).<br /><br /> |123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|"D" ou "d"|Decimal|Résultat : chiffres entiers avec un signe négatif facultatif.<br /><br /> Pris en charge par : les types intégraux uniquement.<br /><br /> Spécificateur de précision : nombre minimal de chiffres.<br /><br /> Spécificateur de précision par défaut : nombre minimal de chiffres requis.<br /><br /> |1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|"E" ou "e"|Exponentiel (scientifique)|Résultat : notation exponentielle.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : 6.<br /><br /> |1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1,05E+003|  
|"F" ou "f"|Virgule fixe|Résultat : chiffres intégraux et décimaux avec un signe négatif facultatif.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres décimaux.<br /><br /> Spécificateur de précision par défaut : défini par [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits).<br /><br /> |1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|  
|"G" ou "g"|Général|Résultat : format le plus compact (notation à virgule fixe ou scientifique).<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre de chiffres significatifs.<br /><br /> Spécificateur de précision par défaut : dépend du type numérique.<br /><br /> |-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|"N" ou "n"|Nombre|Résultat : chiffres intégraux et décimaux, séparateurs de groupes et séparateur décimal avec un signe négatif facultatif.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre souhaité de décimales.<br /><br /> Spécificateur de précision par défaut : défini par [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits).<br /><br /> |1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|  
|"P" ou "p"|Pourcentage|Résultat : nombre multiplié par 100 et affiché avec un symbole de pourcentage.<br /><br /> Pris en charge par : tous les types numériques.<br /><br /> Spécificateur de précision : nombre souhaité de décimales.<br /><br /> Spécificateur de précision par défaut : défini par [NumberFormatInfo.PercentDecimalDigits](assetId:///P:System.Globalization.NumberFormatInfo.PercentDecimalDigits?qualifyHint=True&autoUpgrade=True).<br /><br /> |1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|  
|"R" ou "r"|Aller-retour|Résultat : chaîne qui peut effectuer un aller-retour vers un nombre identique.<br /><br /> Pris en charge par : [Single](xref:System.Single), [Double](xref:System.Double) et [BigInteger](xref:System.Numerics.BigInteger).<br /><br /> Spécificateur de précision : ignoré.<br /><br /> |123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|"X" ou "x"|Hexadécimal|Résultat : chaîne hexadécimale.<br /><br /> Pris en charge par : les types intégraux uniquement.<br /><br /> Spécificateur de précision : nombre de chiffres dans la chaîne de résultat.<br /><br /> |255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|N'importe quel caractère|Spécificateur inconnu|Résultat : lève une exception [FormatException](xref:System.FormatException) au moment de l’exécution.|| 

## <a name="using-standard-numeric-format-strings"></a>Utilisation de chaînes de format numériques standard

Une chaîne de format numérique standard peut être utilisée pour définir la mise en forme d'une valeur numérique de l'une des deux manières suivantes :

* Elle peut être passée à une surcharge de la méthode `ToString` qui a un paramètre *format*. L'exemple suivant met en forme une valeur numérique en tant que chaîne monétaire dans la culture actuelle (dans le cas présent, la culture en-US). 

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine(value.ToString("C2"));
  // Displays $123.46
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine(value.ToString("C2"))         
  ' Displays $123.46
  ```
  
* Elle peut être fournie comme argument *formatString* dans un élément de mise en forme utilisé avec des méthodes telles que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), [Console.WriteLine](xref:System.Console.WriteLine) et [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)). Pour plus d’informations, consultez [Mise en forme composite](composite-format.md). L'exemple suivant utilise un élément de mise en forme pour insérer une valeur monétaire dans une chaîne.

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine("Your account balance is {0:C2}.", value);
  // Displays "Your account balance is $123.46."
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine("Your account balance is {0:C2}.", value)
  ' Displays "Your account balance is $123.46."
  ```
  
  Vous pouvez éventuellement fournir un argument d’alignement pour spécifier la largeur du champ numérique et si sa valeur est alignée à droite ou à gauche. L’exemple suivant aligne à gauche une valeur monétaire dans un champ de 28 caractères et aligne à droite une valeur monétaire dans un champ de 14 caractères.
  
  ```csharp
  decimal[] amounts = { 16305.32m, 18794.16m };
  Console.WriteLine("   Beginning Balance           Ending Balance");
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts[0], amounts[1]);
  // Displays:
  //        Beginning Balance           Ending Balance
  //        $16,305.32                      $18,794.16
  ```

  ```vb
  Dim amounts() As Decimal = { 16305.32d, 18794.16d }
  Console.WriteLine("   Beginning Balance           Ending Balance")
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts(0), amounts(1))
  ' Displays:
  '        Beginning Balance           Ending Balance
  '        $16,305.32                      $18,794.16
  ```
  
Les sections suivantes fournissent des informations détaillées sur chacune des chaînes de format numériques standard.

## <a name="the-currency-c-format-specifier"></a>Spécificateur de format de devise ("C")

Le spécificateur de format "C" (ou monétaire) convertit un nombre en une chaîne qui représente un montant en devise. Le spécificateur de précision indique le nombre souhaité de décimales dans la chaîne de résultat. Si le spécificateur de précision est omis, la précision par défaut est définie par la propriété [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits).

Si la valeur à mettre en forme contient un nombre de décimales supérieur au nombre spécifié ou au nombre par défaut, la valeur fractionnaire est arrondie dans la chaîne de résultat. Si la valeur à droite du nombre de décimales est égale à 5 ou supérieure, le dernier chiffre dans la chaîne de résultat est arrondi à une valeur différente de zéro.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) | Définit la position du symbole monétaire pour les valeurs positives.
[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) | Définit la position du symbole monétaire pour les valeurs négatives, et spécifie si le signe négatif est représenté par des parenthèses ou par la propriété [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign).
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit le signe négatif utilisé si [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) indique que les parenthèses ne sont pas utilisées. 
[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) | Définit le symbole monétaire.
[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) | Définit le nombre par défaut de chiffres décimaux dans une valeur monétaire. Cette valeur peut être substituée à l'aide du spécificateur de précision.
[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) | Définit la chaîne qui sépare les groupes de nombres de la partie entière. 
[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) | Définit le nombre de chiffres entiers qui s'affichent dans un groupe.

L’exemple suivant met en forme une valeur [Double](xref:System.Double) avec le spécificateur de format monétaire. 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", 
                  CultureInfo.CreateSpecificCulture("da-DK")));
// The example displays the following output on a system whose
// current culture is English (United States):
//       $12,345.68
//       $12,345.679
//       kr 12.345,679
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", _
                  CultureInfo.CreateSpecificCulture("da-DK")))
' The example displays the following output on a system whose
' current culture is English (United States):
'       $12,345.68
'       $12,345.679
'       kr 12.345,679
```

## <a name="the-decimal-d-format-specifier"></a>Spécificateur de format décimal ("D")

Le spécificateur de format "D" (ou décimal) convertit un nombre en une chaîne de chiffres décimaux (0-9), préfixée par un signe moins si le nombre est négatif. Ce format est pris en charge par les types intégraux uniquement.

Le spécificateur de précision indique le nombre minimal de chiffres voulu dans la chaîne résultante. Le cas échéant, des zéros sont ajoutés à la gauche du nombre afin de fournir le nombre de chiffres déterminé par le spécificateur de précision. Si aucun spécificateur de précision n'est spécifié, la valeur par défaut est la valeur minimale requise pour représenter l'entier sans zéros non significatifs.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Comme le montre le tableau suivant, une seule propriété affecte la mise en forme de la chaîne de résultat. 

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif. 

L’exemple suivant met en forme une valeur [Int32](xref:System.Int32) avec le spécificateur de format décimal.

```csharp
int value; 

value = 12345;
Console.WriteLine(value.ToString("D"));
// Displays 12345
Console.WriteLine(value.ToString("D8"));
// Displays 00012345

value = -12345;
Console.WriteLine(value.ToString("D"));
// Displays -12345
Console.WriteLine(value.ToString("D8"));
// Displays -00012345
```

```vb
Dim value As Integer 

value = 12345
Console.WriteLine(value.ToString("D"))
' Displays 12345   
Console.WriteLine(value.ToString("D8"))
' Displays 00012345

value = -12345
Console.WriteLine(value.ToString("D"))
' Displays -12345
Console.WriteLine(value.ToString("D8"))
' Displays -00012345
```

## <a name="the-exponential-e-format-specifier"></a>Spécificateur de format exponentiel ("E")

Le spécificateur de format exponentiel ("E") convertit un nombre en une chaîne au format "-d.ddd…E+ddd" ou "-d.ddd…e+ddd", où chaque "d" correspond à un chiffre (0-9). La chaîne commence par un signe moins si le nombre est négatif. Un chiffre exactement précède toujours la virgule décimale. 

Le spécificateur de précision indique le nombre de chiffres voulu après la virgule décimale. Si vous avez omis le spécificateur de précision, une précision par défaut de six chiffres après la virgule décimale est utilisée. 

La casse du spécificateur de format indique si le préfixe "E" ou "e" doit être ajouté à l'exposant. L'exposant est toujours constitué d'un signe plus ou moins et d'un minimum de trois chiffres. Le cas échéant, des zéros sont ajoutés à l'exposant pour respecter ce minimum.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif à la fois pour le coefficient et pour l'exposant. 
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Définit la chaîne qui sépare le chiffre intégral des chiffres décimaux dans le coefficient.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Définit la chaîne qui indique qu'un exposant est positif.

L’exemple suivant met en forme une valeur [Double](xref:System.Double) avec le spécificateur de format exponentiel. 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture));
// Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture));
// Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture));
// Displays 1.2346e+004

Console.WriteLine(value.ToString("E", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 1,234568E+004
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture))
' Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture))
' Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture))
' Displays 1.2346e+004

Console.WriteLine(value.ToString("E", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 1,234568E+004
```

## <a name="the-fixedpoint-f-format-specifier"></a>Spécificateur de format à virgule fixe ("F")

Le spécificateur de format à virgule fixe ("F) convertit un nombre en chaîne sous la forme « -ddd.ddd… » où chaque « d » indique un chiffre (0-9). La chaîne commence par un signe moins si le nombre est négatif. 

Le spécificateur de précision indique le nombre de décimales voulu. Si le spécificateur de précision est omis, la propriété [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) actuelle fournit la précision numérique.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui peuvent contrôler la mise en forme de la chaîne de résultat.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | Définit le nombre par défaut de chiffres décimaux. Cette valeur peut être substituée à l'aide du spécificateur de précision.

L’exemple suivant met en forme une valeur [Double](xref:System.Double) et une valeur [Int32](xref:System.Int32) avec le spécificateur de format à virgule fixe.

```csharp
int integerNumber;
integerNumber = 17843;
Console.WriteLine(integerNumber.ToString("F", 
                  CultureInfo.InvariantCulture));
// Displays 17843.00

integerNumber = -29541;
Console.WriteLine(integerNumber.ToString("F3", 
                  CultureInfo.InvariantCulture));
// Displays -29541.000

double doubleNumber;
doubleNumber = 18934.1879;
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture));
// Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture));
// Displays 18934

doubleNumber = -1898300.1987;
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture));  
// Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays -1898300,199 
```

```vb
Dim integerNumber As Integer
integerNumber = 17843
Console.WriteLine(integerNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 17843.00

integerNumber = -29541
Console.WriteLine(integerNumber.ToString("F3", CultureInfo.InvariantCulture))
' Displays -29541.000

Dim doubleNumber As Double
doubleNumber = 18934.1879
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture))
' Displays 18934

doubleNumber = -1898300.1987
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture))  
' Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", _ 
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays -1898300,199                        
```

## <a name="the-general-g-format-specifier"></a>Spécificateur de format général ("G")

Le spécificateur de format général (« G ») convertit un nombre dans le format le plus compact (notation à virgule fixe ou notation scientifique), en fonction du type du nombre et de la présence d'un spécificateur de précision. Le spécificateur de précision définit le nombre maximal des chiffres significatifs qui peuvent s'afficher dans la chaîne de résultat. Si le spécificateur de précision est omis ou est égal à zéro, le type du nombre détermine la précision par défaut, comme indiqué dans le tableau suivant. 

Type numérique | Précision par défaut
------------ | -----------------
[Byte](xref:System.Byte) ou [SByte](xref:System.SByte) | 3 chiffres
[Int16](xref:System.Int16) ou [UInt16](xref:System.UInt16) | 5 chiffres
[Int32](xref:System.Int32) ou [UInt32](xref:System.UInt32) | 10 chiffres
[Int64](xref:System.Int64) | 19 chiffres
[UInt64](xref:System.UInt64) | 20 chiffres
[BigInteger](xref:System.Numerics.BigInteger) | Illimité (identique à « R »)
[Single](xref:System.Single) | 7 chiffres
[Double](xref:System.Double) | 15 chiffres
[Decimal](xref:System.Decimal) | 29 chiffres

La notation à virgule fixe est utilisée si l'exposant résultant de l'expression du nombre en notation scientifique est supérieur à -5 et inférieur au spécificateur de précision ; dans le cas contraire, la notation scientifique est utilisée. Le résultat contient un séparateur décimal si nécessaire et les zéros non significatifs situés après le séparateur décimal sont omis. Si le spécificateur de précision est présent et que le nombre de chiffres significatifs dans le résultat est supérieur à la précision indiquée, les chiffres de fin en trop sont supprimés par arrondi. 

Toutefois, si le nombre est un [Decimal](xref:System.Decimal) et que le spécificateur de précision est omis, la notation à virgule fixe est toujours utilisée et les zéros de fin sont conservés.

Si la notation scientifique est utilisée, l'exposant du résultat est précédé de "E" si le spécificateur de format est "G", ou de "e" si le spécificateur de format est "g". L'exposant contient au minimum deux chiffres. Cela diffère du format utilisé pour la notation scientifique produite par le spécificateur de format exponentiel, lequel inclut un minimum de trois chiffres dans l'exposant.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne de résultat.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Définit la chaîne qui indique qu'un exposant est positif. 

L'exemple suivant met en forme des valeurs à virgule flottante assorties avec le spécificateur de format général.

```csharp
double number;

number = 12345.6789;      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays  12345.6789
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture));
// Displays 12345.68 

number = .0000023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 2.3E-06       
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 2,3E-06

number = .0023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 0.0023

number = 1234;
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture));
// Displays 1.2E+03

number = Math.PI;
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture));
// Displays 3.1416    
```

```vb
Dim number As Double

number = 12345.6789      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays  12345.6789
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture))
' Displays 12345.68 

number = .0000023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 2.3E-06       
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 2,3E-06

number = .0023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 0.0023

number = 1234
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture))
' Displays 1.2E+03

number = Math.Pi
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture))
' Displays 3.1416
```

## <a name="the-numeric-n-format-specifier"></a>Spécificateur de format numérique ("N")

Le spécificateur de format numérique ("N") convertit un nombre en une chaîne au format "-d,ddd,ddd.ddd…", où "-" correspond, le cas échéant, à un symbole de nombre négatif, "d" indique un chiffre (0-9), "," indique un séparateur de groupes et "." correspond à une virgule décimale. Le spécificateur de précision indique le nombre de chiffres voulu après la virgule décimale. Si le spécificateur de précision est omis, le nombre de décimales est défini par la propriété [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) actuelle.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne de résultat.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif.
[NumberNegativePattern](xref:System.Globalization.NumberFormatInfo.NumberNegativePattern) | Définit le format des valeurs négatives, et spécifie si le signe négatif est représenté par des parenthèses ou par la propriété [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign).
[NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) | Définit le nombre de chiffres intégraux qui s'affichent entre les séparateurs de groupes.
[NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) | Définit la chaîne qui sépare les groupes de nombres de la partie entière.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | Définit le nombre par défaut de chiffres décimaux. Cette valeur peut être substituée à l'aide d'un spécificateur de précision.

L'exemple suivant met en forme des valeurs à virgule flottante assorties avec le spécificateur de format de nombre.

```csharp
double dblValue = -12445.6789;
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture));
// Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", 
                  CultureInfo.CreateSpecificCulture("sv-SE")));
// Displays -12 445,7

int intValue = 123456789;
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture));
// Displays 123,456,789.0 
```

```vb
Dim dblValue As Double = -12445.6789
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture))
' Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", _
                  CultureInfo.CreateSpecificCulture("sv-SE")))
' Displays -12 445,7

Dim intValue As Integer = 123456789
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture))
' Displays 123,456,789.0 
```

## <a name="the-percent-p-format-specifier"></a>Spécificateur de format pourcentage ("P")

Le spécificateur de format pourcentage ("P") multiplie un nombre par 100 et le convertit en une chaîne qui représente un pourcentage. Le spécificateur de précision indique le nombre de décimales voulu. Si le spécificateur de précision est omis, la précision numérique par défaut fournie par la propriété [PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) actuelle est utilisée.

Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne retournée.

Propriété NumberFormatInfo | Description
------------------------- | -----------
[PercentPositivePattern](xref:System.Globalization.NumberFormatInfo.PercentPositivePattern) | Définit la position du symbole de pourcentage pour les valeurs positives.
[PercentNegativePattern](xref:System.Globalization.NumberFormatInfo.PercentNegativePattern) | 
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif.
[PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) | Définit le symbole de pourcentage.
[PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) | Définit le nombre par défaut de chiffres décimaux dans une valeur de pourcentage. Cette valeur peut être substituée à l'aide du spécificateur de précision.
[PercentDecimalSeparator](xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[PercentGroupSeparator](xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator) | Définit la chaîne qui sépare les groupes de nombres de la partie entière. 
[PercentGroupSizes](xref:System.Globalization.NumberFormatInfo.PercentGroupSizes) | Définit le nombre de chiffres entiers qui s'affichent dans un groupe.

L'exemple suivant met en forme des valeurs à virgule flottante assorties avec le spécificateur de format pourcentage.

```csharp
double number = .2468013;
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture));
// Displays 24.68 %
Console.WriteLine(number.ToString("P", 
                  CultureInfo.CreateSpecificCulture("hr-HR")));
// Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture));
// Displays 24.7 %
```

```vb
Dim number As Double = .2468013
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture))
' Displays 24.68 %
Console.WriteLine(number.ToString("P", _
                  CultureInfo.CreateSpecificCulture("hr-HR")))
' Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture))
' Displays 24.7 %
```

## <a name="the-roundtrip-r-format-specifier"></a>Spécificateur de format aller-retour ("R")

Le spécificateur de format aller-retour ("R") est utilisé pour garantir qu'une valeur numérique qui est convertie en chaîne sera de nouveau analysée en aboutissant à la même valeur numérique. Ce format est pris en charge uniquement pour les types [Single](xref:System.Single), [Double](xref:System.Double) et [BigInteger](xref:System.Numerics.BigInteger). 

Quand une valeur [BitInteger](xref:System.Numerics.BigInteger) est mise en forme à l’aide de ce spécificateur, sa représentation sous forme de chaîne contient tous les chiffres significatifs dans la valeur [BigInteger](xref:System.Numerics.BigInteger). Quand une valeur [Single](xref:System.Single) ou [Double](xref:System.Double) est mise en forme à l’aide de ce spécificateur, elle est tout d’abord testée à l’aide du format général, avec 15 chiffres de précision pour une valeur [Double](xref:System.Double) et 7 chiffres de précision pour une valeur [Single](xref:System.Single). Si la valeur est correctement analysée pour la même valeur numérique, elle est mise en forme à l'aide du spécificateur de format général. Si la valeur n’est pas analysée correctement dans la même valeur numérique, elle est mise en forme à l’aide de 17 chiffres de précision pour une valeur [Double](xref:System.Double) et de 9 chiffres de précision pour une valeur [Single](xref:System.Single). 

Bien que vous puissiez inclure un spécificateur de précision, il est ignoré. Les allers-retours prévalent sur la précision lorsque vous utilisez ce spécificateur. 

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif affectent la chaîne de résultat. Le tableau suivant répertorie les propriétés [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui contrôlent la mise en forme de la chaîne de résultat.

Propriété de NumberFormatInfo | Description
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | Définit la chaîne qui indique qu'un nombre est négatif.
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | Définit la chaîne qui sépare les chiffres de la partie entière des chiffres de la partie décimale.
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | Définit la chaîne qui indique qu'un exposant est positif.

 L’exemple suivant met en forme des valeurs [Double](xref:System.Double) avec le spécificateur de format aller-retour.

```csharp
double value;

value = Math.PI;
Console.WriteLine(value.ToString("r"));
// Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 3,1415926535897931
value = 1.623e-21;
Console.WriteLine(value.ToString("r"));
// Displays 1.623E-21
```

```vb
Dim value As Double

value = Math.Pi
Console.WriteLine(value.ToString("r"))
' Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 3,1415926535897931
value = 1.623e-21
Console.WriteLine(value.ToString("r"))
' Displays 1.623E-21
```

## <a name="the-hexadecimal-x-format-specifier"></a>Spécificateur de format hexadécimal ("X")

Le spécificateur de format hexadécimal ("X") convertit un nombre en une chaîne de chiffres hexadécimaux. La casse du spécificateur de format indique s'il convient d'utiliser des caractères majuscules ou minuscules pour les chiffres hexadécimaux supérieurs à 9. Par exemple, utilisez "X" pour produire "ABCDEF" et "x" pour produire "abcdef". Ce format est pris en charge par les types intégraux uniquement.

Le spécificateur de précision indique le nombre minimal de chiffres voulu dans la chaîne résultante. Le cas échéant, des zéros sont ajoutés à la gauche du nombre afin de fournir le nombre de chiffres déterminé par le spécificateur de précision.

Les informations de mise en forme de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif n’affectent pas la chaîne de résultat. 

L’exemple suivant met en forme des valeurs [Int32](xref:System.Int32) avec le spécificateur de format hexadécimal.

```csharp
int value; 

value = 0x2045e;
Console.WriteLine(value.ToString("x"));
// Displays 2045e
Console.WriteLine(value.ToString("X"));
// Displays 2045E
Console.WriteLine(value.ToString("X8"));
// Displays 0002045E

value = 123456789;
Console.WriteLine(value.ToString("X"));
// Displays 75BCD15
Console.WriteLine(value.ToString("X2"));
// Displays 75BCD15
```

```vb
Dim value As Integer 

value = &h2045e
Console.WriteLine(value.ToString("x"))
' Displays 2045e
Console.WriteLine(value.ToString("X"))
' Displays 2045E
Console.WriteLine(value.ToString("X8"))
' Displays 0002045E

value = 123456789
Console.WriteLine(value.ToString("X"))
' Displays 75BCD15
Console.WriteLine(value.ToString("X2"))
' Displays 75BCD15
```

## <a name="notes"></a>Remarques

### <a name="numberformatinfo-properties"></a>Propriétés NumberFormatInfo

La mise en forme dépend des propriétés de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actif, qui est fourni implicitement par la culture actuelle du thread ou explicitement par le paramètre [IFormatProvider](xref:System.IFormatProvider) de la méthode qui appelle la mise en forme. Spécifiez un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) ou [CultureInfo](xref:System.Globalization.CultureInfo) pour ce paramètre. 

### <a name="integral-and-floatingpoint-numeric-types"></a>Types numériques intégraux et à virgule flottante

Certaines descriptions de spécificateurs de format numériques standard font référence à des types numériques intégraux ou à virgule flottante. Les types numériques intégraux sont [Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) et [BigInteger](xref:System.Numerics.BigInteger). Les types numériques à virgule flottante sont [Decimal](xref:System.Decimal), [Single](xref:System.Single) et [Double](xref:System.Double). 

### <a name="floatingpoint-infinities-and-nan"></a>Infinis à virgule flottante et NaN

Quelle que soit la chaîne de format, si la valeur d’un type virgule flottante [Single](xref:System.Single) ou [Double](xref:System.Double) est l’infini positif, l’infini négatif ou une valeur qui n’est pas un nombre, la chaîne mise en forme est, respectivement, la valeur de la propriété [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol), [NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) ou [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) qui est spécifiée par l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) actuellement applicable.

## <a name="example"></a>Exemple

L'exemple suivant met en forme une valeur numérique intégrale et à virgule flottante en utilisant la culture en-US et tous les spécificateurs de format numériques standard. Cet exemple utilise deux types numériques particuliers ([Double](xref:System.Double) et [Int32](xref:System.Int32)), mais produirait des résultats similaires pour les autres types numériques de base ([Byte](xref:System.Byte), [SByte](xref:System.SByte), [Int16](xref:System.Int16), [Int64](xref:System.Int64), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64), [BigInteger](xref:System.Numerics.BigInteger), [Decimal](xref:System.Decimal) et [Single](xref:System.Single)). 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class NumericFormats
{
   public static void Main()
   {
      // Display string representations of numbers for en-us culture
      CultureInfo ci = new CultureInfo("en-us");

      // Output floating point values
      double floating = 10761.937554;
      Console.WriteLine("C: {0}", 
              floating.ToString("C", ci));           // Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", 
              floating.ToString("E03", ci));         // Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", 
              floating.ToString("F04", ci));         // Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}",  
              floating.ToString("G", ci));           // Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", 
              floating.ToString("N03", ci));         // Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", 
              (floating/10000).ToString("P02", ci)); // Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", 
              floating.ToString("R", ci));           // Displays "R: 10761.937554"            
      Console.WriteLine();

      // Output integral values
      int integral = 8395;
      Console.WriteLine("C: {0}", 
              integral.ToString("C", ci));           // Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", 
              integral.ToString("D6", ci));          // Displays "D: 008395" 
      Console.WriteLine("E: {0}", 
              integral.ToString("E03", ci));         // Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", 
              integral.ToString("F01", ci));         // Displays "F: 8395.0"    
      Console.WriteLine("G: {0}",  
              integral.ToString("G", ci));           // Displays "G: 8395"
      Console.WriteLine("N: {0}", 
              integral.ToString("N01", ci));         // Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", 
              (integral/10000.0).ToString("P02", ci)); // Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", 
              integral.ToString("X", ci));           // Displays "X: 0x20CB"
      Console.WriteLine();
   }
}
```

```vb
Option Strict On

Imports System.Globalization
Imports System.Threading

Module NumericFormats
   Public Sub Main()
      ' Display string representations of numbers for en-us culture
      Dim ci As New CultureInfo("en-us")

      ' Output floating point values
      Dim floating As Double = 10761.937554
      Console.WriteLine("C: {0}", _
              floating.ToString("C", ci))           ' Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", _
              floating.ToString("E03", ci))         ' Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", _
              floating.ToString("F04", ci))         ' Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}", _ 
              floating.ToString("G", ci))           ' Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", _
              floating.ToString("N03", ci))         ' Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", _
              (floating/10000).ToString("P02", ci)) ' Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", _
              floating.ToString("R", ci))           ' Displays "R: 10761.937554"            
      Console.WriteLine()

      ' Output integral values
      Dim integral As Integer = 8395
      Console.WriteLine("C: {0}", _
              integral.ToString("C", ci))           ' Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", _
              integral.ToString("D6"))              ' Displays "D: 008395" 
      Console.WriteLine("E: {0}", _
              integral.ToString("E03", ci))         ' Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", _
              integral.ToString("F01", ci))         ' Displays "F: 8395.0"    
      Console.WriteLine("G: {0}", _ 
              integral.ToString("G", ci))           ' Displays "G: 8395"
      Console.WriteLine("N: {0}", _
              integral.ToString("N01", ci))         ' Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", _
              (integral/10000).ToString("P02", ci)) ' Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", _
              integral.ToString("X", ci))           ' Displays "X: 0x20CB"
      Console.WriteLine()
   End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[Chaînes de format numériques personnalisées](custom-numeric.md)

[Mise en forme des types](formatting-types.md)

[Guide pratique pour remplir un nombre avec des zéros non significatifs](pad-number.md)

[Mise en forme composite](composite-format.md)



<!--HONumber=Nov16_HO1-->


