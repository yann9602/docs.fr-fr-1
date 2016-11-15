---
title: Utilisation de la classe StringBuilder
description: Utilisation de la classe StringBuilder
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 1e8453b78827d8c02f29135ddfb832956ab40f3c

---

# <a name="using-the-stringbuilder-class"></a>Utilisation de la classe StringBuilder

L’objet [String](xref:System.String) est immuable. Chaque fois que vous utilisez l’une des méthodes de la classe [System.String](xref:System.String), vous créez un nouvel objet String en mémoire, ce qui nécessite une nouvelle allocation d’espace pour ce nouvel objet. Si vous devez effectuer des modifications répétées sur une chaîne, la surcharge associée à la création d’un objet [String](xref:System.String) peut être coûteuse. Vous pouvez utiliser la classe [System.Text.StringBuilder](xref:System.Text.StringBuilder) quand vous voulez modifier une chaîne sans créer d’objet. Par exemple, la classe [StringBuilder](xref:System.Text.StringBuilder) permet d’améliorer les performances quand il s’agit de concaténer un grand nombre de chaînes dans une boucle.

## <a name="importing-the-systemtext-namespace"></a>Importation de l’espace de noms System.Text

La classe [StringBuilder](xref:System.Text.StringBuilder) se trouve dans l’espace de noms [System.Text](xref:System.Text). Pour éviter d’avoir à fournir un nom de type complet dans votre code, vous pouvez importer l’espace de noms [System.Text](xref:System.Text) : 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a>Instanciation d’un objet StringBuilder

Vous pouvez créer une instance de la classe [StringBuilder](xref:System.Text.StringBuilder) en initialisant votre variable avec l’une des méthodes de constructeur surchargées, comme l’illustre l’exemple suivant.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a>Définition de la capacité et de la longueur

Bien que [StringBuilder](xref:System.Text.StringBuilder) soit un objet dynamique qui permet de développer le nombre de caractères contenus dans la chaîne qu’il encapsule, vous pouvez spécifier une valeur pour le nombre maximal de caractères qu’elle peut contenir. Cette valeur est appelée « capacité » de l’objet et ne doit pas être confondue avec la longueur de la chaîne que l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder) contient. Par exemple, vous pouvez créer une instance de la classe [StringBuilder](xref:System.Text.StringBuilder) avec la chaîne « Hello», dont la longueur est de 5, et préciser que l’objet a une capacité maximale de 25. Quand vous modifiez l’instance de [StringBuilder](xref:System.Text.StringBuilder), elle ne se réalloue pas une taille tant que la capacité maximale n’est pas atteinte. Quand cela se produit, le nouvel espace est alloué automatiquement et la capacité est doublée. Vous pouvez spécifier la capacité de la classe [StringBuilder](xref:System.Text.StringBuilder) en utilisant l’un des constructeurs surchargés. L’exemple suivant spécifie que l’objet `MyStringBuilder` peut être développé en 25 espaces, au maximum.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

De plus, vous pouvez utiliser la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) en lecture/écriture pour définir la longueur maximale de votre objet. L’exemple suivant utilise la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) pour définir la longueur maximale de l’objet.

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

La méthode [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) peut être utilisée pour vérifier la capacité de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder). Si la capacité est supérieure à la valeur passée, aucune modification n’est apportée ; en revanche, si la capacité est inférieure à la valeur passée, la capacité actuelle est modifiée pour correspondre à la valeur passée.

Vous pouvez aussi afficher ou définir la propriété [Length](xref:System.Text.StringBuilder.Length). Si vous attribuez à la propriété [Length](xref:System.Text.StringBuilder.Length) une valeur supérieure à celle de la propriété [Capacity](xref:System.Text.StringBuilder.Capacity), la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) prend automatiquement la valeur de la propriété [Length](xref:System.Text.StringBuilder.Length). Si vous attribuez à la propriété [Length](xref:System.Text.StringBuilder.Length) une valeur inférieure à la longueur de la chaîne dans l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder), la chaîne se raccourcit.

## <a name="modifying-the-stringbuilder-string"></a>Modification de la chaîne StringBuilder

Le tableau suivant répertorie les méthodes que vous pouvez utiliser pour modifier le contenu d’une instance de [StringBuilder](xref:System.Text.StringBuilder).

Nom de la méthode | Utilisation
----------- | ---
[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) | Ajoute des informations à la fin de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | Remplace un spécificateur de format passé dans une chaîne avec du texte mis en forme.
[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) | Insère une chaîne ou un objet dans l’index spécifié de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).
[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) | Supprime un nombre de caractères spécifié de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).
[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Remplace un caractère spécifié au niveau d’un index spécifié.

### <a name="append"></a>Append

La méthode [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) permet d’ajouter du texte ou une représentation sous forme de chaîne d’un objet à la fin d’une chaîne représentée par l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder). L’exemple suivant initialise une instance de [StringBuilder](xref:System.Text.StringBuilder) à « Hello World » avant d’ajouter du texte à la fin de l’objet. L’espace est alloué automatiquement en fonction des besoins.

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Append(" What a beautiful day.");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World! What a beautiful day.
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Append(" What a beautiful day.")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World! What a beautiful day.
```

### <a name="appendformat"></a>AppendFormat

La méthode [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) ajoute du texte à la fin de l’objet [StringBuilder](xref:System.Text.StringBuilder). Elle prend en charge la fonctionnalité de mise en forme composite (pour plus d’informations, consultez [Mise en forme composite](composite-format.md)) en appelant l’implémentation [IFormattable](xref:System.IFormattable) des objets à mettre en forme. Par conséquent, elle accepte les chaînes de format standard pour les valeurs numériques, de date et d’heure et d’énumération, les chaînes de format personnalisé pour les valeurs numériques et de date et d’heure, ainsi que les chaînes de format définies pour des types personnalisés. (Pour plus d’informations sur la mise en forme, consultez [Mise en forme des types](formatting-types.md).) Vous pouvez utiliser cette méthode pour personnaliser le format des variables et ajouter ces valeurs à une instance de [StringBuilder](xref:System.Text.StringBuilder). L’exemple suivant utilise la méthode AppendFormat pour placer une valeur entière mise en forme comme valeur monétaire à la fin d’un objet [StringBuilder](xref:System.Text.StringBuilder).

```csharp
int MyInt = 25; 
StringBuilder MyStringBuilder = new StringBuilder("Your total is ");
MyStringBuilder.AppendFormat("{0:C} ", MyInt);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Your total is $25.00
```

```vb
Dim MyInt As Integer = 25
Dim MyStringBuilder As New StringBuilder("Your total is ")
MyStringBuilder.AppendFormat("{0:C} ", MyInt)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'     Your total is $25.00 
```

### <a name="insert"></a>Insert

La méthode [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) ajoute une chaîne ou un objet à une position spécifiée dans l’objet [StringBuilder](xref:System.Text.StringBuilder) actuel. L’exemple suivant utilise cette méthode pour insérer un mot à la sixième position d’un objet [StringBuilder](xref:System.Text.StringBuilder).

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Insert(6,"Beautiful ");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello Beautiful World!
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Insert(6, "Beautiful ")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'      Hello Beautiful World!
```

### <a name="remove"></a>Remove

Vous pouvez utiliser la méthode [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) pour supprimer un nombre spécifié de caractères dans l’objet [StringBuilder](xref:System.Text.StringBuilder) actuel, en partant d’un index de base zéro spécifié. L’exemple suivant utilise la méthode [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) pour raccourcir un objet [StringBuilder](xref:System.Text.StringBuilder).

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Remove(5,7);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Remove(5, 7)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello
```

### <a name="replace"></a>Remplacer

La méthode [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Remplace un caractère spécifié au niveau d’un index spécifié.
permet de remplacer des caractères dans l’objet [StringBuilder](xref:System.Text.StringBuilder) par un autre caractère spécifié. L’exemple suivant utilise la méthode [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Remplace un caractère spécifié au niveau d’un index spécifié.
pour rechercher toutes les instances du caractère point d’exclamation (!) dans un objet [StringBuilder](xref:System.Text.StringBuilder) et les remplacer par le caractère point d’interrogation (?).
 
 ```csharp
 StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Replace('!', '?');
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World?
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Replace("!"c, "?"c)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World?
```

## <a name="converting-a-stringbuilder-object-to-a-string"></a>Conversion d’un objet StringBuilder en chaîne

Vous devez convertir l’objet [StringBuilder](xref:System.Text.StringBuilder) en objet [String](xref:System.String) pour pouvoir passer la chaîne représentée par l’objet [StringBuilder](xref:System.Text.StringBuilder) à une méthode qui a un paramètre [String](xref:System.String) ou pour l’afficher dans l’interface utilisateur. Effectuez cette conversion en appelant la méthode [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString). L’exemple suivant appelle plusieurs méthodes [StringBuilder](xref:System.Text.StringBuilder), puis la méthode [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) pour afficher la chaîne.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      StringBuilder sb = new StringBuilder();
      bool flag = true;
      string[] spellings = { "recieve", "receeve", "receive" };
      sb.AppendFormat("Which of the following spellings is {0}:", flag);
      sb.AppendLine();
      for (int ctr = 0; ctr <= spellings.GetUpperBound(0); ctr++) {
         sb.AppendFormat("   {0}. {1}", ctr, spellings[ctr]);
         sb.AppendLine();
      }
      sb.AppendLine();
      Console.WriteLine(sb.ToString());
   }
}
// The example displays the following output:
//       Which of the following spellings is True:
//          0. recieve
//          1. receeve
//          2. receive
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim sb As New StringBuilder()
      Dim flag As Boolean = True
      Dim spellings() As String = { "recieve", "receeve", "receive" }
      sb.AppendFormat("Which of the following spellings is {0}:", flag)
      sb.AppendLine()
      For ctr As Integer = 0 To spellings.GetUpperBound(0)
         sb.AppendFormat("   {0}. {1}", ctr, spellings(ctr))
         sb.AppendLine()
      Next
      sb.AppendLine()
      Console.WriteLine(sb.ToString())
   End Sub
End Module
' The example displays the following output:
'       Which of the following spellings is True:
'          0. recieve
'          1. receeve
'          2. receive
```

## <a name="see-also"></a>Voir aussi

[System.Text.StringBuilder](xref:System.Text.StringBuilder)

[Opérations de chaînes de base](basic-string-operations.md)

[Mise en forme des types](formatting-types.md)



<!--HONumber=Nov16_HO1-->


