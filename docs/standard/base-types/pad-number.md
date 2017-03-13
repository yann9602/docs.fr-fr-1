---
title: "Guide pratique : remplir un nombre avec des zéros non significatifs"
description: "Guide pratique pour remplir un nombre avec des zéros non significatifs"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a517c066-b11e-4815-826b-9262611eac40
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 92f8796eae0f269cacfa4cf70330c5e3c0826717
ms.lasthandoff: 03/13/2017

---

# <a name="how-to-pad-a-number-with-leading-zeros"></a>Guide pratique : remplir un nombre avec des zéros non significatifs

Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](standard-numeric.md) « D » avec un spécificateur de précision. Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](custom-numeric.md). Cette rubrique montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique

1. Déterminez le nombre minimal de chiffres que la valeur entière doit afficher. Incluez des chiffres non significatifs dans ce nombre.

2. Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.

    * Pour afficher l’entier comme valeur décimale, appelez sa méthode `ToString(String)`, puis transmettez la chaîne « D*n* » comme valeur du paramètre de format, où *n* représente la longueur minimale de la chaîne.
    
    * Pour afficher l’entier comme valeur hexadécimale, appelez sa méthode `ToString(String)`, puis transmettez la chaîne « X*n* » comme valeur du paramètre de format, où *n* représente la longueur minimale de la chaîne.
    
  Vous pouvez également recourir à la chaîne de format dans une méthode, comme [Console.WriteLine](xref:System.Console.WriteLine) ou [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), qui utilise la [mise en forme composite](composite-format.md).  
  
L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.

```csharp
byte byteValue = 254;
short shortValue = 10342;
int intValue = 1023983;
long lngValue = 6985321;               
ulong ulngValue = UInt64.MaxValue;

// Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"));
Console.WriteLine();

// Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue);
// The example displays the following output:
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//       
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//         18446744073709551615       FFFFFFFFFFFFFFFF
```

```vb
Dim byteValue As Byte = 254
Dim shortValue As Short = 10342
Dim intValue As Integer = 1023983
Dim lngValue As Long = 6985321               
Dim ulngValue As ULong = UInt64.MaxValue

' Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"))
Console.WriteLine()

' Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue)
' The example displays the following output:
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
'       
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
```

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Pour remplir un entier avec un nombre spécifique de zéros non significatifs

1. Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.

2. Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale. Selon que vous souhaitez le mettre en forme en tant que valeur décimale ou que valeur hexadécimale, vous devez utiliser le spécificateur de format standard « D » ou « X ».

3. Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière. 

4. Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie. Cette opération définit la longueur totale de la chaîne remplie.

5. Appelez la méthode `ToString(String)` de la valeur entière, puis transmettez la chaîne « D*n* » pour les chaînes décimales et la chaîne « X*n* » pour les chaînes hexadécimales, où *n* représente la longueur totale de la chaîne remplie. Vous pouvez également utiliser la chaîne de format « D*n* » ou « X*n* » dans une méthode qui prend en charge la mise en forme composite.

L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.

```csharp
int value = 160934;
int decimalLength = value.ToString("D").Length + 5;
int hexLength = value.ToString("X").Length + 5;
Console.WriteLine(value.ToString("D" + decimalLength.ToString()));
Console.WriteLine(value.ToString("X" + hexLength.ToString()));
// The example displays the following output:
//       00000160934
//       00000274A6
```

```vb
Dim value As Integer = 160934
Dim decimalLength As Integer = value.ToString("D").Length + 5
Dim hexLength As Integer = value.ToString("X").Length + 5
Console.WriteLine(value.ToString("D" + decimalLength.ToString()))
Console.WriteLine(value.ToString("X" + hexLength.ToString()))
' The example displays the following output:
'       00000160934
'       00000274A6 
```

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique

1. Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne. Incluez des zéros non significatifs dans ce nombre total de chiffres.

2. Définissez une chaîne de format numérique personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour représenter le nombre minimal de zéros.

3. Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée. Vous pouvez également utiliser la chaîne de format personnalisée avec une méthode qui prend en charge la mise en forme composite.

L'exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères à gauche du séparateur décimal.

```csharp
string fmt = "00000000.##";
int intValue = 1053240;
decimal decValue = 103932.52m;
float sngValue = 1549230.10873992f;
double dblValue = 9034521202.93217412;

// Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt));
Console.WriteLine(decValue.ToString(fmt));           
Console.WriteLine(sngValue.ToString(fmt));
Console.WriteLine(dblValue.ToString(fmt));           
Console.WriteLine();

// Display the numbers using composite formatting.
string formatString = " {0,15:" + fmt + "}";
Console.WriteLine(formatString, intValue);      
Console.WriteLine(formatString, decValue);      
Console.WriteLine(formatString, sngValue);      
Console.WriteLine(formatString, dblValue);      
// The example displays the following output:
//       01053240
//       00103932.52
//       01549230
//       9034521202.93
//       
//               01053240
//            00103932.52
//               01549230
//          9034521202.93  
```

```vb
Dim fmt As String = "00000000.##"
Dim intValue As Integer = 1053240
Dim decValue As Decimal = 103932.52d
Dim sngValue As Single = 1549230.10873992
Dim dblValue As Double = 9034521202.93217412

' Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt))
Console.WriteLine(decValue.ToString(fmt))            
Console.WriteLine(sngValue.ToString(fmt))
Console.WriteLine(dblValue.ToString(fmt))            
Console.WriteLine()

' Display the numbers using composite formatting.
Dim formatString As String = " {0,15:" + fmt + "}"
Console.WriteLine(formatString, intValue)      
Console.WriteLine(formatString, decValue)      
Console.WriteLine(formatString, sngValue)      
Console.WriteLine(formatString, dblValue)      
' The example displays the following output:
'       01053240
'       00103932.52
'       01549230
'       9034521202.93
'       
'               01053240
'            00103932.52
'               01549230
'          9034521202.93
```

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs

1. Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.

2. Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie. Pour ce faire :

    a. Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.
    
    b. Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.       
    
    ou
       
    Sinon, déterminez la longueur de la chaîne. 
       
3. Créez une chaîne de format personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour chaque zéro non significatif à inclure dans la chaîne, ainsi que l'espace réservé du zéro ou l'espace réservé de chiffre (« # ») pour représenter chaque chiffre dans la chaîne par défaut. 

4. Fournissez la chaîne de format personnalisée comme paramètre à la méthode ToString(String) du nombre ou à une méthode qui prend en charge la mise en forme composite.

L’exemple suivant remplit deux valeurs [Double](xref:System.Double) avec cinq zéros non significatifs.

```csharp
double[] dblValues = { 9034521202.93217412, 9034521202 };
foreach (double dblValue in dblValues)
{
   string decSeparator = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator;
   string fmt, formatString;

   if (dblValue.ToString().Contains(decSeparator))
   {
      int digits = dblValue.ToString().IndexOf(decSeparator);
      fmt = new String('0', 5) + new String('#', digits) + ".##";
   }
   else
   {
      fmt = new String('0', dblValue.ToString().Length);   
   }
   formatString = "{0,20:" + fmt + "}";

   Console.WriteLine(dblValue.ToString(fmt));
   Console.WriteLine(formatString, dblValue);
}
// The example displays the following output:
//       000009034521202.93
//         000009034521202.93
//       9034521202
//                 9034521202 
```

```vb
Dim dblValues() As Double = { 9034521202.93217412, 9034521202 }
For Each dblValue As Double In dblValues
   Dim decSeparator As String = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator
   Dim fmt, formatString As String

   If dblValue.ToString.Contains(decSeparator) Then
      Dim digits As Integer = dblValue.ToString().IndexOf(decSeparator)
      fmt = New String("0"c, 5) + New String("#"c, digits) + ".##"
   Else
      fmt = New String("0"c, dblValue.ToString.Length)   
   End If
   formatString = "{0,20:" + fmt + "}"

   Console.WriteLine(dblValue.ToString(fmt))
   Console.WriteLine(formatString, dblValue)
Next
' The example displays the following output:
'       000009034521202.93
'         000009034521202.93
'       9034521202
'                 9034521202
```

## <a name="see-also"></a>Voir aussi

[Chaînes de format numériques standard](standard-numeric.md)

[Chaînes de format numériques personnalisées](custom-numeric.md)

[Mise en forme composite](composite-format.md)


