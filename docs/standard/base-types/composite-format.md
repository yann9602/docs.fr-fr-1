---
title: Mise en forme composite
description: Mise en forme composite
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a01efc8f-c242-4535-bd32-acd0032d9590
translationtype: Human Translation
ms.sourcegitcommit: 90ade65e167770bdbcbbf79707fe48e6fbc030c0
ms.openlocfilehash: 5b61b4736880d57f02070150d8613d860505b268

---

# <a name="composite-formatting"></a>Mise en forme composite

La fonctionnalité de mise en forme composite du .NET utilise une liste d’objets et une chaîne de format composite comme entrée. Une chaîne de format composite se compose de texte fixe mélangé à des espaces réservés indexés, appelés éléments de format, qui correspondent aux objets de la liste. L'opération de mise en forme produit une chaîne résultante qui se compose du texte fixe d'origine mélangé à la représentation sous forme de chaîne des objets de la liste. 

La fonctionnalité de mise en forme composite est prise en charge par les méthodes suivantes : 

* [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), qui retourne une chaîne de résultat mise en forme. 

* [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), qui ajoute une chaîne de résultat mise en forme à un objet [StringBuilder](xref:System.Text.StringBuilder).

* Certaines surcharges de la méthode [Console](xref:System.Console) `WriteLine`, qui affichent une chaîne de résultat mise en forme sur la console.  

* Certaines surcharges de la méthode [TextWriter](xref:System.IO.TextWriter) `WriteLine`, qui écrivent la chaîne de résultat mise en forme dans un flux ou un fichier. Les classes dérivées de [TextWriter](xref:System.IO.TextWriter), telles que [StreamWriter](xref:System.IO.StreamWriter), partagent également ces fonctionnalités.

* [Debug.WriteLine(String, Object[])](xref:System.Diagnostics.Debug.WriteLine(System.String,System.Object[])), qui génère un message mis en forme pour les écouteurs Trace. 

* Les méthodes [Trace.TraceError (String, Object[])](xref:System.Diagnostics.Trace.TraceError(System.String,System.Object[])), [Trace.TraceInformation (String, Object[])](xref:System.Diagnostics.Trace.TraceInformation(System.String,System.Object[])) et [Trace.TraceWarning (String, Object[])](xref:System.Diagnostics.Trace.TraceWarning(System.String,System.Object[])), qui génèrent des messages mis en forme pour les écouteurs Trace. 

* La méthode [TraceSource.TraceInformation (String, Object[])](xref:System.Diagnostics.TraceSource.TraceInformation(System.String,System.Object[])), qui écrit une méthode à caractère informatif pour les écouteurs Trace. 

## <a name="composite-format-string"></a>Chaîne de format composite

Une chaîne de format composite et une liste d'objets sont utilisées comme arguments des méthodes qui prennent en charge la fonctionnalité de mise en forme composite. Une chaîne de format composite est constituée de zéro, une ou plusieurs séquences de texte fixe mélangées à un ou plusieurs éléments de format. Le texte fixe correspond à toute chaîne que vous choisissez, et chaque élément de format correspond à un objet ou une structure boxed dans la liste. La fonctionnalité de mise en forme composite retourne une nouvelle chaîne résultante, dans laquelle chaque élément de format est remplacé par la représentation sous forme de chaîne de l’objet correspondant dans la liste.

Prenons le fragment de code [Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) suivant.

```csharp
string name = "Fred";
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now);
```

```vb
Dim name As String = "Fred"
String.Format("Name = {0}, hours = {1:hh}", name, DateTime.Now)
```

Le texte fixe est `"Name = "` et `", hours = "`. Les éléments de format sont `"{0}"`, dont l’index est 0, ce qui correspond à l’objet `name`, et `"{1:hh}"`, dont l’index est 1, ce qui correspond à l’objet `DateTime.Now`.

## <a name="format-item-syntax"></a>Syntaxe des éléments de format

Chaque élément de format prend la forme suivante et comprend les composants suivants :

__{__*index*[,*alignment*][:*formatString*]__}__

Les accolades correspondantes (« { » et « } ») sont nécessaires. 
 
### <a name="index-component"></a>Composant d'index

Le composant obligatoire *index*, également appelé « spécificateur de paramètre », est un nombre à partir de 0 qui permet d’identifier un élément correspondant dans la liste des objets. En d'autres termes, l'élément de format dont le spécificateur de format est 0 met en forme le premier objet de la liste, l'élément de format dont le spécificateur de paramètres est 1 met en forme le deuxième objet de la liste, etc. L’exemple suivant comprend quatre spécificateurs de paramètres, numérotés de 0 à 3, pour représenter les nombres premiers inférieurs à 10 : 

```csharp
string primes;
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 );
Console.WriteLine(primes);
// The example displays the following output:
//      Prime numbers less than 10: 2, 3, 5, 7
```

```vb
Dim primes As String
primes = String.Format("Prime numbers less than 10: {0}, {1}, {2}, {3}",
                       2, 3, 5, 7 )
Console.WriteLine(primes)
' The example displays the following output:
'      Prime numbers less than 10: 2, 3, 5, 7
```

Plusieurs éléments de format peuvent faire référence au même élément de la liste d'objets en indiquant le même spécificateur de paramètre. Par exemple, vous pouvez mettre en forme la même valeur numérique au format hexadécimal, scientifique et numérique en spécifiant une chaîne de format composite comme "0x{0:X} {0:E} {0:N}", comme dans l'exemple suivant. 

```csharp
string multiple = String.Format("0x{0:X} {0:E} {0:N}",
                                Int64.MaxValue);
Console.WriteLine(multiple);
// The example displays the following output:
//      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

```vb
Dim multiple As String = String.Format("0x{0:X} {0:E} {0:N}",
                                       Int64.MaxValue)
Console.WriteLine(multiple)
' The example displays the following output:
'      0x7FFFFFFFFFFFFFFF 9.223372E+018 9,223,372,036,854,775,807.00
```

Chaque élément de format peut faire référence à n'importe quel objet de la liste. Par exemple, si vous disposez de trois objets à mettre en forme, vous pouvez mettre en forme le deuxième, le premier et le troisième en spécifiant une chaîne de format composite telle que : « {1} {0} {2} ». Un objet qui n'est pas référencé par un élément de format est ignoré. Un [FormatException](xref:System.FormatException) est levé au moment de l’exécution si un spécificateur de paramètres désigne un élément situé en dehors des limites de la liste d’objets.

### <a name="alignment-component"></a>Composant d'alignement

Le composant facultatif *alignment* est un entier signé indiquant la largeur préférée du champ mis en forme. Si la valeur du composant *alignment* est inférieure à la longueur de la chaîne mise en forme, *alignment*est ignoré et la longueur de la chaîne mise en forme est utilisée comme largeur de champ. Les données mises en forme dans le champ sont alignées à droite si *alignment* est positif et alignées à gauche si *alignment* est négatif. Si un remplissage est nécessaire, des espaces blancs sont utilisés. La virgule est obligatoire si *alignment* est spécifié.

L'exemple suivant définit deux tableaux, l'un contenant les noms des employés et l'autre contenant les heures qu'ils ont prestées sur une période de deux semaines. La chaîne de format composite aligne les noms à gauche dans un champ de 20 caractères et aligne leurs heures à droite dans un champ de 5 caractères. Notez que la chaîne de format standard "N1" est également utilisée pour mettre les heures sous la forme d'un nombre avec une décimale. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string[] names = { "Adam", "Bridgette", "Carla", "Daniel",
                         "Ebenezer", "Francine", "George" };
      decimal[] hours = { 40, 6.667m, 40.39m, 82, 40.333m, 80,
                                 16.75m };

      Console.WriteLine("{0,-20} {1,5}\n", "Name", "Hours");
      for (int ctr = 0; ctr < names.Length; ctr++)
         Console.WriteLine("{0,-20} {1,5:N1}", names[ctr], hours[ctr]);

   }
}
// The example displays the following output:
//       Name                 Hours
//
//       Adam                  40.0
//       Bridgette              6.7
//       Carla                 40.4
//       Daniel                82.0
//       Ebenezer              40.3
//       Francine              80.0
//       George                16.8
```

```vb
Module Example
   Public Sub Main()
      Dim names() As String = { "Adam", "Bridgette", "Carla", "Daniel",
                                "Ebenezer", "Francine", "George" }
      Dim hours() As Decimal = { 40, 6.667d, 40.39d, 82, 40.333d, 80,
                                 16.75d }

      Console.WriteLine("{0,-20} {1,5}", "Name", "Hours")
      Console.WriteLine()
      For ctr As Integer = 0 To names.Length - 1
         Console.WriteLine("{0,-20} {1,5:N1}", names(ctr), hours(ctr))
      Next
   End Sub
End Module
' The example displays the following output:
'       Name                 Hours
'
'       Adam                  40.0
'       Bridgette              6.7
'       Carla                 40.4
'       Daniel                82.0
'       Ebenezer              40.3
'       Francine              80.0
'       George                16.8
```

### <a name="format-string-component"></a>Composant de chaîne de format

Le composant facultatif *formatString* est une chaîne de format appropriée pour le type d’objet mis en forme. Spécifiez une chaîne de format numérique standard ou personnalisée si l’objet correspondant est une valeur numérique, une chaîne de format de date et d’heure standard ou personnalisée si l’objet correspondant est un objet [DateTime](xref:System.DateTime), ou une [chaîne de format d’énumération](enumeration-format.md) si l’objet correspondant est une valeur d’énumération. Si *formatString* n’est pas spécifié, le spécificateur de format général (« G ») pour un type numérique, de date et d’heure ou d’énumération est utilisé. Le point est obligatoire si *formatString* est spécifié.

Le tableau suivant répertorie les types ou les catégories de types dans la bibliothèque de classes .NET Framework qui prennent en charge un ensemble prédéfini de chaînes de format, et fournit des liens vers les rubriques qui répertorient les chaînes de format prises en charge. Notez que la mise en forme de chaînes est un mécanisme extensible qui permet de définir de nouvelles chaînes de format pour tous les types existants et de définir un ensemble de chaînes de format pris en charge par un type défini par l'application. Pour plus d’informations, consultez les rubriques sur l’interface [IFormattable](xref:System.IFormattable) et [ICustomFormatter](xref:System.ICustomFormatter). 

Type ou catégorie de type | Voir
--------------------- | ---
Types de date et d’heure ([DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset)) | [Chaînes de format de date et d’heure standard ](standard-datetime.md), [Chaînes de format de date et d’heure personnalisées](custom-datetime.md)
Types d’énumération (tous les types dérivés de [System.Enum](xref:System.Enum)) | [Chaînes de format d’énumération](enumeration-format.md)
Types numériques ([BigInteger](xref:System.Numerics.BigInteger), [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64)) | [Chaînes de format numériques standard](standard-numeric.md), [Chaînes de format numériques personnalisées](custom-numeric.md)
[Guid](xref:System.Guid) | [Guid.ToString(String)](xref:System.Guid.ToString(System.String))
[TimeSpan](xref:System.TimeSpan) | [Chaînes de format TimeSpan standard](standard-timespan.md), [Chaînes de format TimeSpan personnalisées](custom-timespan.md)

### <a name="escaping-braces"></a>Accolades d'échappement

Les accolades ouvrantes et fermantes sont interprétées comme le début et la fin d'un élément de format. Par conséquent, vous devez utiliser une séquence d'échappement pour afficher une accolade ouvrante ou fermante littérale. Spécifiez deux accolades ouvrantes (« {{ ») dans le texte fixe pour afficher une accolade ouvrante (« { ») ou deux accolades fermantes (« }} ») pour afficher une accolade fermante (« } »). Les accolades d'un élément de format sont interprétées séquentiellement dans l'ordre dans lequel elles sont rencontrées. L'interprétation des accolades imbriquées n'est pas prise en charge. 

La façon dont les accolades d'échappement sont interprétées peut générer des résultats inattendus. Par exemple, considérez l'élément de format « {{{0:D}}} » destiné à afficher une accolade ouvrante, une valeur numérique mise en forme en tant que nombre décimal et une accolade fermante. Toutefois, l'élément de format est réellement interprété de la manière suivante : 

1. Les deux premières accolades ouvrantes (« {{ ») font l'objet d'un échappement et produisent une accolade ouvrante. 

2. Les trois caractères suivants (« {0: ») sont interprétés comme le début d'un élément de format.

3. Le caractère suivant (« D ») devrait être interprété comme le spécificateur de format numérique standard Decimal, mais les deux accolades d'échappement suivantes (« }} ») produisent une seule accolade. Comme la chaîne résultante (« D} ») n'est pas un spécificateur de format numérique standard, elle est interprétée comme une chaîne de mise en forme personnalisée qui sous-entend l'affichage de la chaîne littérale « D} ». 

4. La dernière accolade (« } ») est interprétée comme la fin de l'élément de format. 

5. Le résultat final affiché est la chaîne littérale, « {D} ». La valeur numérique qui devait être mise en forme n'est pas affichée.

Pour éviter une mauvaise interprétation des accolades d'échappement et des éléments de format, mettez en forme séparément les accolades et l'élément de format. Autrement dit, dans la première opération de formatage, affichez une accolade ouvrante littérale, dans l'opération suivante, affichez le résultat de l'élément de format, puis dans la dernière opération, affichez une accolade fermante littérale. L'exemple suivant illustre cette approche.

```csharp
int value = 6324;
string output = string.Format("{0}{1:D}{2}", 
                             "{", value, "}");
Console.WriteLine(output);
// The example displays the following output:
//       {6324} 
```

```vb
Dim value As Integer = 6324
Dim output As String = String.Format("{0}{1:D}{2}", _
                                     "{", value, "}")
Console.WriteLine(output)   
' The example displays the following output:
'       {6324}
```

### <a name="processing-order"></a>Ordre de traitement

Si l’appel à la méthode de mise en forme composite comprend un argument [IFormatProvider](xref:System.IFormatProvider) dont la valeur n’est pas null, le runtime appelle sa méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) pour demander une implémentation de [ICustomFormatter](xref:System.ICustomFormatter). Si la méthode peut retourner une implémentation de [ICustomFormatter](xref:System.ICustomFormatter), elle est mise en cache pour une utilisation ultérieure. 

Chaque valeur de la liste de paramètres qui correspond à un élément de mise en forme peut être convertie en une chaîne en exécutant les étapes suivantes. Si une condition présente dans l'une des trois premières étapes est remplie, la représentation sous forme de chaîne de la valeur est retournée dans cette étape et les étapes suivantes ne sont pas effectuées.

1. Si la valeur à mettre en forme est `null`, une chaîne vide ("") est retournée. 

2. Si une implémentation de [ICustomFormatter](xref:System.ICustomFormatter) est disponible, le runtime appelle sa méthode [Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)). Il passe à la méthode la valeur *formatString* de l’élément de mise en forme, s’il en existe un, ou `null` si ce n’est pas le cas, ainsi que l’implémentation de [IFormatProvider](xref:System.IFormatProvider). 

3. Si la valeur implémente l’interface [IFormattable](xref:System.IFormattable), la méthode [ToString(String,IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)) de l’interface est appelée. La valeur *formatString*, s’il en existe une dans l’élément de mise en forme, est passée à la méthode, ou bien la valeur `null` dans le cas contraire. L’argument [IFormatProvider](xref:System.IFormatProvider)est déterminé comme suit :

    *   Pour une valeur numérique, si une méthode de mise en forme composite avec l’argument non null [IFormatProvider](xref:System.IFormatProvider) est appelée, le runtime demande un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) de sa méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). Si elle ne peut pas en fournir un, si la valeur de l’argument est `null` ou si la méthode de mise en forme composite n’a pas de paramètre [IFormatProvider](xref:System.IFormatProvider), l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) de la culture de thread actuelle est utilisé. 
    
    * Pour une valeur de date et d’heure, si une méthode de mise en forme composite avec l’argument non null [IFormatProvider](xref:System.IFormatProvider) est appelée, le runtime demande un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) auprès de sa méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). S’il ne peut pas en fournir un, si la valeur de l’argument est `null` ou si la méthode de mise en forme composite n’a pas de paramètre [IFormatProvider](xref:System.IFormatProvider), l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) de la culture de thread actuelle est utilisé. 
    
    * Pour les objets d’autres types, si la mise en forme composite est appelée avec un argument [IFormatProvider](xref:System.IFormatProvider), sa valeur (notamment un `null` si aucun objet [IFormatProvider](xref:System.IFormatProvider) n’est fourni) est transmise directement à l’implémentation de [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)). Sinon, un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente la culture de thread actuelle est passé à l’implémentation de [IFormattable.ToString](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)). 
    
4. La méthode `ToString` sans paramètre du type, qui remplace [Object.ToString()](xref:System.Object.ToString) ou hérite du comportement de sa classe de base, est appelée. Dans ce cas, la chaîne de format spécifiée par le composant *formatString* dans l’élément de mise en forme, si elle est présente, est ignorée.

L'alignement est appliqué une fois les précédentes étapes effectuées. 

## <a name="code-examples"></a>Exemples de code

L'exemple suivant illustre une chaîne créée à l'aide de la mise en forme composite et une autre chaîne créée à l'aide de la méthode `ToString` d'un objet. Les deux types de mise en forme produisent des résultats équivalents. 

```csharp
string FormatString1 = String.Format("{0:dddd MMMM}", DateTime.Now);
string FormatString2 = DateTime.Now.ToString("dddd MMMM");
```

```vb
Dim FormatString1 As String = String.Format("{0:dddd MMMM}", DateTime.Now)
Dim FormatString2 As String = DateTime.Now.ToString("dddd MMMM")
```

En supposant que le jour actuel soit un jeudi du mois de mai, la valeur des deux chaînes de l'exemple précédent est `Thursday May` dans la culture Anglais (États-Unis).

[Console.WriteLine](xref:System.Console.WriteLine) présente les mêmes fonctionnalités que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). La seule différence entre les deux méthodes est que [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))retourne son résultat sous la forme d’une chaîne, alors que [Console.WriteLine](xref:System.Console.WriteLine) écrit le résultat dans le flux de sortie associé à l’objet [Console](xref:System.Console). L’exemple suivant utilise la méthode [Console.WriteLine](xref:System.Console.WriteLine) pour mettre en forme la valeur de `MyInt` en une valeur monétaire.

```csharp
int MyInt = 100;
Console.WriteLine("{0:C}", MyInt);
// The example displays the following output 
// if en-US is the current culture:
//        $100.00
```

```vb
Dim MyInt As Integer = 100
Console.WriteLine("{0:C}", MyInt)
' The example displays the following output
' if en-US is the current culture:
'        $100.00
```

L'exemple suivant illustre la mise en forme de plusieurs objets, y compris la mise en forme d'un objet de deux manières différentes.

```csharp
string myName = "Fred";
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}",
      myName, DateTime.Now));
// Depending on the current time, the example displays output like the following:
//    Name = Fred, hours = 11, minutes = 30                 
```

```vb
Dim myName As String = "Fred"
Console.WriteLine(String.Format("Name = {0}, hours = {1:hh}, minutes = {1:mm}", _
                  myName, DateTime.Now))
' Depending on the current time, the example displays output like the following:
'    Name = Fred, hours = 11, minutes = 30
```

L'exemple suivant illustre l'utilisation de l'alignement lors de la mise en forme. Les arguments mis en forme sont placés entre des barres verticales (« | ») pour mettre en évidence l’alignement en résultant.

```csharp
string myFName = "Fred";
string myLName = "Opals";
int myInt = 100;
string FormatFName = String.Format("First Name = |{0,10}|", myFName);
string FormatLName = String.Format("Last Name = |{0,10}|", myLName);
string FormatPrice = String.Format("Price = |{0,10:C}|", myInt); 
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
Console.WriteLine();

FormatFName = String.Format("First Name = |{0,-10}|", myFName);
FormatLName = String.Format("Last Name = |{0,-10}|", myLName);
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt);
Console.WriteLine(FormatFName);
Console.WriteLine(FormatLName);
Console.WriteLine(FormatPrice);
// The example displays the following output on a system whose current
// culture is en-US:
//          First Name = |      Fred|
//          Last Name = |     Opals|
//          Price = |   $100.00|
//
//          First Name = |Fred      |
//          Last Name = |Opals     |
//          Price = |$100.00   |
```

```vb
Dim myFName As String = "Fred"
Dim myLName As String = "Opals"

Dim myInt As Integer = 100
Dim FormatFName As String = String.Format("First Name = |{0,10}|", myFName)
Dim FormatLName As String = String.Format("Last Name = |{0,10}|", myLName)
Dim FormatPrice As String = String.Format("Price = |{0,10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
Console.WriteLine()

FormatFName = String.Format("First Name = |{0,-10}|", myFName)
FormatLName = String.Format("Last Name = |{0,-10}|", myLName)
FormatPrice = String.Format("Price = |{0,-10:C}|", myInt)
Console.WriteLine(FormatFName)
Console.WriteLine(FormatLName)
Console.WriteLine(FormatPrice)
' The example displays the following output on a system whose current
' culture is en-US:
'          First Name = |      Fred|
'          Last Name = |     Opals|
'          Price = |   $100.00|
'
'          First Name = |Fred      |
'          Last Name = |Opals     |
'          Price = |$100.00   |
```

## <a name="see-also"></a>Voir aussi

[Console.WriteLine](xref:System.Console.WriteLine)

[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))

[Mise en forme des types](formatting-types.md)

[Chaînes de format de date et d’heure standard](standard-datetime.md)

[Chaînes de format de date et d’heure personnalisées](custom-datetime.md)

[Chaînes de format d’énumération](enumeration-format.md)

[Chaînes de format numériques standard](standard-numeric.md)

[Chaînes de format numériques personnalisées](custom-numeric.md)

[Chaînes de format TimeSpan standard](standard-timespan.md)

[Chaînes de format TimeSpan personnalisées](custom-timespan.md)



<!--HONumber=Feb17_HO1-->


