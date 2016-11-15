---
title: "Comparaison de chaînes"
description: "Comparaison de chaînes"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 10c9ea3ebb50e8d8075d8a4e4ce007ddc29ff412

---

# <a name="comparing-strings"></a>Comparaison de chaînes

.NET fournit plusieurs méthodes permettant de comparer les valeurs de chaînes. Le tableau suivant répertorie et décrit les méthodes de comparaison de valeurs.

Nom de la méthode | Utilisation
----------- | ---
[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) | Compare les valeurs de deux chaînes. Retourne une valeur entière.
[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) | Compare deux chaînes sans tenir compte de la culture locale. Retourne une valeur entière.
[String.CompareTo](xref:System.String.CompareTo(System.String)) | Compare l'objet chaîne actif à une autre chaîne. Retourne une valeur entière.
[String.StartsWith](xref:System.String.StartsWith(System.String)) | Détermine si une chaîne commence par la chaîne passée. Retourne une valeur booléenne.
[String.EndsWith](xref:System.String.CompareTo(System.String)) | Détermine si une chaîne se termine par la chaîne passée. Retourne une valeur booléenne.
[String.Equals](xref:System.String.CompareTo(System.String)) | Détermine si deux chaînes sont identiques. Retourne une valeur booléenne.
[String.IndexOf](xref:System.String.IndexOf(System.Char)) | Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par le début de la chaîne que vous examinez. Retourne une valeur entière.
[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) | Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par la fin de la chaîne que vous examinez. Retourne une valeur entière.

## <a name="compare"></a>Comparer

La méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) statique fournit un moyen complet de comparer deux chaînes. Cette méthode prend en compte la culture. Vous pouvez utiliser cette fonction pour comparer deux chaînes ou les sous-chaînes de deux chaînes. En outre, des surcharges sont fournies, qui prennent ou non en compte les différences de casse et de culture. Le tableau suivant montre les trois valeurs entières que cette méthode peut retourner. 

Valeur de retour | Condition
------------ | ---------
Entier négatif | La première chaîne précède la seconde dans l’ordre de tri ou la première chaîne est `null`.
0 | La première chaîne et la seconde sont égales ou les deux chaînes sont `null`.
Un entier positif ou 1 | La première chaîne suit la seconde dans l’ordre de tri, ou la seconde chaîne est Null.
 
> [!IMPORTANT]
> La méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) est principalement destinée à être utilisée lors du classement ou du tri de chaînes. Vous ne devez pas utiliser la méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre). Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

L’exemple suivant utilise la méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour déterminer les valeurs relatives de deux chaînes.

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

Cet exemple affiche `-1` sur la console.

## <a name="compareordinal"></a>CompareOrdinal

La méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) compare deux objets String sans prendre en compte la culture locale. Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode `Compare` du tableau précédent.

> [!IMPORTANT]
> La méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) est principalement destinée à être utilisée pour classer ou trier des chaînes. Vous ne devez pas utiliser la méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre). Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

L’exemple suivant utilise la méthode `CompareOrdinal` pour comparer les valeurs de deux chaînes.

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

Cet exemple affiche `-32` sur la console.

## <a name="compareto"></a>CompareTo

La méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) compare la chaîne encapsulée par l’objet String actif à une autre chaîne ou un autre objet. Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode `String.Compare` du tableau précédent.

> [!IMPORTANT]
> La méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) est principalement destinée à être utilisée lors du classement ou du tri de chaînes. Vous ne devez pas utiliser la méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre). Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).

L’exemple suivant utilise la méthode `String.CompareTo` pour comparer l’objet `string1` à l’objet `string2`.

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

Cet exemple affiche `-1` sur la console.

## <a name="equals"></a>Equals

La méthode [String.Equals](xref:System.String.CompareTo(System.String)) peut facilement déterminer si deux chaînes sont identiques. Cette méthode respectant la casse retourne une valeur booléenne `true` ou `false`. Elle peut être utilisée à partir d'une classe existante, comme illustré dans l'exemple suivant. L’exemple suivant utilise la méthode `Equals` pour déterminer si un objet String contient la phrase « Hello World ».

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

Cet exemple affiche `true` sur la console.

Cette méthode peut également être utilisée comme une méthode statique. L'exemple suivant compare deux objets chaîne à l'aide d'une méthode statique.

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

Cet exemple affiche `true` sur la console.

## <a name="startswith-and-endswith"></a>StartsWith et EndsWith

Vous pouvez utiliser la méthode [String.StartsWith](xref:System.String.StartsWith(System.String)) pour déterminer si un objet String commence par les mêmes caractères que ceux qui constituent une autre chaîne. Cette méthode qui respecte la casse retourne `true` si l’objet String actif commence par la chaîne passée et `false` si ce n’est pas le cas. L'exemple suivant utilise cette méthode pour déterminer si un objet chaîne commence par "Hello".

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

Cet exemple affiche `true` sur la console.

La méthode [String.EndsWith](xref:System.String.CompareTo(System.String)) compare une chaîne passée aux caractères qui se trouvent à la fin de l’objet String actif. Elle retourne également une valeur booléenne. L’exemple suivant vérifie la fin d’une chaîne à l’aide de la méthode `EndsWith`.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

Cet exemple affiche `false` sur la console.

## <a name="indexof-and-lastindexof"></a>IndexOf et LastIndexOf

Vous pouvez utiliser la méthode [String.IndexOf](xref:System.String.IndexOf(System.Char)) pour déterminer la position de la première occurrence d’un caractère particulier dans une chaîne. Cette méthode qui respecte la casse commence à compter à partir du début d'une chaîne et retourne la position d'un caractère passé en utilisant un index de base zéro. Si le caractère est introuvable, la valeur -1 est retournée.

L’exemple suivant utilise la méthode `IndexOf` pour rechercher la première occurrence du caractère '`l`' dans une chaîne.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

Cet exemple affiche `2` sur la console.

La méthode [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) est similaire à la méthode `String.IndexOf`, sauf qu’elle retourne la position de la dernière occurrence d’un caractère particulier dans une chaîne. Elle respecte la casse et utilise un index de base zéro. 

L’exemple suivant utilise la méthode `LastIndexOf` pour rechercher la dernière occurrence du caractère '`l`' dans une chaîne.

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

Cet exemple affiche `9` sur la console.

Les deux méthodes sont utiles quand elles sont utilisées conjointement avec la méthode [String.Remove](xref:System.String.Remove(System.Int32)). Vous pouvez utiliser la méthode `IndexOf` ou la méthode `LastIndexOf` pour récupérer la position d’un caractère, puis fournir cette position à la `Remove method` pour supprimer un caractère ou un mot commençant par ce caractère.

## <a name="see-also"></a>Voir aussi

[Opérations de chaînes de base](basic-string-operations.md)















<!--HONumber=Nov16_HO1-->


