---
title: Utilisation de la classe StringBuilder
description: Utilisation de la classe StringBuilder
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 076e10e095b50cc96187f2ec13ade2365d83dad3
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="using-the-stringbuilder-class"></a><span data-ttu-id="2be53-104">Utilisation de la classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="2be53-104">Using the StringBuilder class</span></span>

<span data-ttu-id="2be53-105">L’objet [String](xref:System.String) est immuable.</span><span class="sxs-lookup"><span data-stu-id="2be53-105">The [String](xref:System.String) object is immutable.</span></span> <span data-ttu-id="2be53-106">Chaque fois que vous utilisez l’une des méthodes de la classe [System.String](xref:System.String), vous créez un nouvel objet String en mémoire, ce qui nécessite une nouvelle allocation d’espace pour ce nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="2be53-106">Every time you use one of the methods in the [System.String](xref:System.String) class, you create a new string object in memory, which requires a new allocation of space for that new object.</span></span> <span data-ttu-id="2be53-107">Si vous devez effectuer des modifications répétées sur une chaîne, la surcharge associée à la création d’un objet [String](xref:System.String) peut être coûteuse.</span><span class="sxs-lookup"><span data-stu-id="2be53-107">In situations where you need to perform repeated modifications to a string, the overhead associated with creating a new [String](xref:System.String) object can be costly.</span></span> <span data-ttu-id="2be53-108">Vous pouvez utiliser la classe [System.Text.StringBuilder](xref:System.Text.StringBuilder) quand vous voulez modifier une chaîne sans créer d’objet.</span><span class="sxs-lookup"><span data-stu-id="2be53-108">The [System.Text.StringBuilder](xref:System.Text.StringBuilder) class can be used when you want to modify a string without creating a new object.</span></span> <span data-ttu-id="2be53-109">Par exemple, la classe [StringBuilder](xref:System.Text.StringBuilder) permet d’améliorer les performances quand il s’agit de concaténer un grand nombre de chaînes dans une boucle.</span><span class="sxs-lookup"><span data-stu-id="2be53-109">For example, using the [StringBuilder](xref:System.Text.StringBuilder) class can boost performance when concatenating many strings together in a loop.</span></span>

## <a name="importing-the-systemtext-namespace"></a><span data-ttu-id="2be53-110">Importation de l’espace de noms System.Text</span><span class="sxs-lookup"><span data-stu-id="2be53-110">Importing the System.Text Namespace</span></span>

<span data-ttu-id="2be53-111">La classe [StringBuilder](xref:System.Text.StringBuilder) se trouve dans l’espace de noms [System.Text](xref:System.Text).</span><span class="sxs-lookup"><span data-stu-id="2be53-111">The [StringBuilder](xref:System.Text.StringBuilder) class is found in the [System.Text](xref:System.Text) namespace.</span></span> <span data-ttu-id="2be53-112">Pour éviter d’avoir à fournir un nom de type complet dans votre code, vous pouvez importer l’espace de noms [System.Text](xref:System.Text) :</span><span class="sxs-lookup"><span data-stu-id="2be53-112">To avoid having to provide a fully qualified type name in your code, you can import the [System.Text](xref:System.Text) namespace:</span></span> 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a><span data-ttu-id="2be53-113">Instanciation d’un objet StringBuilder</span><span class="sxs-lookup"><span data-stu-id="2be53-113">Instantiating a StringBuilder Object</span></span>

<span data-ttu-id="2be53-114">Vous pouvez créer une instance de la classe [StringBuilder](xref:System.Text.StringBuilder) en initialisant votre variable avec l’une des méthodes de constructeur surchargées, comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2be53-114">You can create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class by initializing your variable with one of the overloaded constructor methods, as illustrated in the following example.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a><span data-ttu-id="2be53-115">Définition de la capacité et de la longueur</span><span class="sxs-lookup"><span data-stu-id="2be53-115">Setting the Capacity and Length</span></span>

<span data-ttu-id="2be53-116">Bien que [StringBuilder](xref:System.Text.StringBuilder) soit un objet dynamique qui permet de développer le nombre de caractères contenus dans la chaîne qu’il encapsule, vous pouvez spécifier une valeur pour le nombre maximal de caractères qu’elle peut contenir.</span><span class="sxs-lookup"><span data-stu-id="2be53-116">Although the [StringBuilder](xref:System.Text.StringBuilder) is a dynamic object that allows you to expand the number of characters in the string that it encapsulates, you can specify a value for the maximum number of characters that it can hold.</span></span> <span data-ttu-id="2be53-117">Cette valeur est appelée « capacité » de l’objet et ne doit pas être confondue avec la longueur de la chaîne que l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder) contient.</span><span class="sxs-lookup"><span data-stu-id="2be53-117">This value is called the capacity of the object and should not be confused with the length of the string that the current [StringBuilder](xref:System.Text.StringBuilder) holds.</span></span> <span data-ttu-id="2be53-118">Par exemple, vous pouvez créer une instance de la classe [StringBuilder](xref:System.Text.StringBuilder) avec la chaîne « Hello», dont la longueur est de 5, et préciser que l’objet a une capacité maximale de 25.</span><span class="sxs-lookup"><span data-stu-id="2be53-118">For example, you might create a new instance of the [StringBuilder](xref:System.Text.StringBuilder) class with the string "Hello", which has a length of 5, and you might specify that the object has a maximum capacity of 25.</span></span> <span data-ttu-id="2be53-119">Quand vous modifiez l’instance de [StringBuilder](xref:System.Text.StringBuilder), elle ne se réalloue pas une taille tant que la capacité maximale n’est pas atteinte.</span><span class="sxs-lookup"><span data-stu-id="2be53-119">When you modify the [StringBuilder](xref:System.Text.StringBuilder), it does not reallocate size for itself until the capacity is reached.</span></span> <span data-ttu-id="2be53-120">Quand cela se produit, le nouvel espace est alloué automatiquement et la capacité est doublée.</span><span class="sxs-lookup"><span data-stu-id="2be53-120">When this occurs, the new space is allocated automatically and the capacity is doubled.</span></span> <span data-ttu-id="2be53-121">Vous pouvez spécifier la capacité de la classe [StringBuilder](xref:System.Text.StringBuilder) en utilisant l’un des constructeurs surchargés.</span><span class="sxs-lookup"><span data-stu-id="2be53-121">You can specify the capacity of the [StringBuilder](xref:System.Text.StringBuilder) class using one of the overloaded constructors.</span></span> <span data-ttu-id="2be53-122">L’exemple suivant spécifie que l’objet `MyStringBuilder` peut être développé en 25 espaces, au maximum.</span><span class="sxs-lookup"><span data-stu-id="2be53-122">The following example specifies that the `MyStringBuilder` object can be expanded to a maximum of 25 spaces.</span></span>

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

<span data-ttu-id="2be53-123">De plus, vous pouvez utiliser la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) en lecture/écriture pour définir la longueur maximale de votre objet.</span><span class="sxs-lookup"><span data-stu-id="2be53-123">Additionally, you can use the read/write [Capacity](xref:System.Text.StringBuilder.Capacity) property to set the maximum length of your object.</span></span> <span data-ttu-id="2be53-124">L’exemple suivant utilise la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) pour définir la longueur maximale de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2be53-124">The following example uses the [Capacity](xref:System.Text.StringBuilder.Capacity) property to define the maximum object length.</span></span>

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

<span data-ttu-id="2be53-125">La méthode [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) peut être utilisée pour vérifier la capacité de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-125">The [EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) method can be used to check the capacity of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="2be53-126">Si la capacité est supérieure à la valeur passée, aucune modification n’est apportée ; en revanche, si la capacité est inférieure à la valeur passée, la capacité actuelle est modifiée pour correspondre à la valeur passée.</span><span class="sxs-lookup"><span data-stu-id="2be53-126">If the capacity is greater than the passed value, no change is made; however, if the capacity is smaller than the passed value, the current capacity is changed to match the passed value.</span></span>

<span data-ttu-id="2be53-127">Vous pouvez aussi afficher ou définir la propriété [Length](xref:System.Text.StringBuilder.Length).</span><span class="sxs-lookup"><span data-stu-id="2be53-127">The [Length](xref:System.Text.StringBuilder.Length) property can also be viewed or set.</span></span> <span data-ttu-id="2be53-128">Si vous attribuez à la propriété [Length](xref:System.Text.StringBuilder.Length) une valeur supérieure à celle de la propriété [Capacity](xref:System.Text.StringBuilder.Capacity), la propriété [Capacity](xref:System.Text.StringBuilder.Capacity) prend automatiquement la valeur de la propriété [Length](xref:System.Text.StringBuilder.Length).</span><span class="sxs-lookup"><span data-stu-id="2be53-128">If you set the [Length](xref:System.Text.StringBuilder.Length) property to a value that is greater than the [Capacity](xref:System.Text.StringBuilder.Capacity) property, the [Capacity](xref:System.Text.StringBuilder.Capacity) property is automatically changed to the same value as the [Length](xref:System.Text.StringBuilder.Length) property.</span></span> <span data-ttu-id="2be53-129">Si vous attribuez à la propriété [Length](xref:System.Text.StringBuilder.Length) une valeur inférieure à la longueur de la chaîne dans l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder), la chaîne se raccourcit.</span><span class="sxs-lookup"><span data-stu-id="2be53-129">Setting the [Length](xref:System.Text.StringBuilder.Length) property to a value that is less than the length of the string within the current [StringBuilder](xref:System.Text.StringBuilder) shortens the string.</span></span>

## <a name="modifying-the-stringbuilder-string"></a><span data-ttu-id="2be53-130">Modification de la chaîne StringBuilder</span><span class="sxs-lookup"><span data-stu-id="2be53-130">Modifying the StringBuilder String</span></span>

<span data-ttu-id="2be53-131">Le tableau suivant répertorie les méthodes que vous pouvez utiliser pour modifier le contenu d’une instance de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-131">The following table lists the methods you can use to modify the contents of a [StringBuilder](xref:System.Text.StringBuilder).</span></span>

<span data-ttu-id="2be53-132">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="2be53-132">Method name</span></span> | <span data-ttu-id="2be53-133">Utilisation</span><span class="sxs-lookup"><span data-stu-id="2be53-133">Use</span></span>
----------- | ---
<span data-ttu-id="2be53-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span><span class="sxs-lookup"><span data-stu-id="2be53-134">[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char))</span></span> | <span data-ttu-id="2be53-135">Ajoute des informations à la fin de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-135">Appends information to the end of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="2be53-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="2be53-136">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | <span data-ttu-id="2be53-137">Remplace un spécificateur de format passé dans une chaîne avec du texte mis en forme.</span><span class="sxs-lookup"><span data-stu-id="2be53-137">Replaces a format specifier passed in a string with formatted text.</span></span>
<span data-ttu-id="2be53-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span><span class="sxs-lookup"><span data-stu-id="2be53-138">[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char))</span></span> | <span data-ttu-id="2be53-139">Insère une chaîne ou un objet dans l’index spécifié de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-139">Inserts a string or object into the specified index of the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="2be53-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2be53-140">[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32))</span></span> | <span data-ttu-id="2be53-141">Supprime un nombre de caractères spécifié de l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-141">Removes a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder).</span></span>
<span data-ttu-id="2be53-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span><span class="sxs-lookup"><span data-stu-id="2be53-142">[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char))</span></span> | <span data-ttu-id="2be53-143">Remplace un caractère spécifié au niveau d’un index spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be53-143">Replaces a specified character at a specified index.</span></span>

### <a name="append"></a><span data-ttu-id="2be53-144">Append</span><span class="sxs-lookup"><span data-stu-id="2be53-144">Append</span></span>

<span data-ttu-id="2be53-145">La méthode [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) permet d’ajouter du texte ou une représentation sous forme de chaîne d’un objet à la fin d’une chaîne représentée par l’instance actuelle de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-145">The [StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) method can be used to add text or a string representation of an object to the end of a string represented by the current [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="2be53-146">L’exemple suivant initialise une instance de [StringBuilder](xref:System.Text.StringBuilder) à « Hello World » avant d’ajouter du texte à la fin de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2be53-146">The following example initializes a [StringBuilder](xref:System.Text.StringBuilder) to "Hello World" and then appends some text to the end of the object.</span></span> <span data-ttu-id="2be53-147">L’espace est alloué automatiquement en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="2be53-147">Space is allocated automatically as needed.</span></span>

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

### <a name="appendformat"></a><span data-ttu-id="2be53-148">AppendFormat</span><span class="sxs-lookup"><span data-stu-id="2be53-148">AppendFormat</span></span>

<span data-ttu-id="2be53-149">La méthode [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) ajoute du texte à la fin de l’objet [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-149">The [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) method adds text to the end of the [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="2be53-150">Elle prend en charge la fonctionnalité de mise en forme composite (pour plus d’informations, consultez [Mise en forme composite](composite-format.md)) en appelant l’implémentation [IFormattable](xref:System.IFormattable) des objets à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="2be53-150">It supports the composite formatting feature (for more information, see [Composite Formatting](composite-format.md)) by calling the [IFormattable](xref:System.IFormattable) implementation of the object or objects to be formatted.</span></span> <span data-ttu-id="2be53-151">Par conséquent, elle accepte les chaînes de format standard pour les valeurs numériques, de date et d’heure et d’énumération, les chaînes de format personnalisé pour les valeurs numériques et de date et d’heure, ainsi que les chaînes de format définies pour des types personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2be53-151">Therefore, it accepts the standard format strings for numeric, date and time, and enumeration values, the custom format strings for numeric and date and time values, and the format strings defined for custom types.</span></span> <span data-ttu-id="2be53-152">(Pour plus d’informations sur la mise en forme, consultez [Mise en forme des types](formatting-types.md).) Vous pouvez utiliser cette méthode pour personnaliser le format des variables et ajouter ces valeurs à une instance de [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-152">(For information about formatting, see [Formatting Types](formatting-types.md).) You can use this method to customize the format of variables and append those values to a [StringBuilder](xref:System.Text.StringBuilder).</span></span> <span data-ttu-id="2be53-153">L’exemple suivant utilise la méthode AppendFormat pour placer une valeur entière mise en forme comme valeur monétaire à la fin d’un objet [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-153">The following example uses the AppendFormat method to place an integer value formatted as a currency value at the end of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="insert"></a><span data-ttu-id="2be53-154">Insert</span><span class="sxs-lookup"><span data-stu-id="2be53-154">Insert</span></span>

<span data-ttu-id="2be53-155">La méthode [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) ajoute une chaîne ou un objet à une position spécifiée dans l’objet [StringBuilder](xref:System.Text.StringBuilder) actuel.</span><span class="sxs-lookup"><span data-stu-id="2be53-155">The [StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) method adds a string or object to a specified position in the current [StringBuilder](xref:System.Text.StringBuilder) object.</span></span> <span data-ttu-id="2be53-156">L’exemple suivant utilise cette méthode pour insérer un mot à la sixième position d’un objet [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-156">The following example uses this method to insert a word into the sixth position of a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="remove"></a><span data-ttu-id="2be53-157">Remove</span><span class="sxs-lookup"><span data-stu-id="2be53-157">Remove</span></span>

<span data-ttu-id="2be53-158">Vous pouvez utiliser la méthode [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) pour supprimer un nombre spécifié de caractères dans l’objet [StringBuilder](xref:System.Text.StringBuilder) actuel, en partant d’un index de base zéro spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be53-158">You can use the [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to remove a specified number of characters from the current [StringBuilder](xref:System.Text.StringBuilder) object, beginning at a specified zero-based index.</span></span> <span data-ttu-id="2be53-159">L’exemple suivant utilise la méthode [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) pour raccourcir un objet [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="2be53-159">The following example uses the [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) method to shorten a [StringBuilder](xref:System.Text.StringBuilder) object.</span></span>

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

### <a name="replace"></a><span data-ttu-id="2be53-160">Remplacer</span><span class="sxs-lookup"><span data-stu-id="2be53-160">Replace</span></span>

<span data-ttu-id="2be53-161">La méthode [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Remplace un caractère spécifié au niveau d’un index spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be53-161">The [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="2be53-162">permet de remplacer des caractères dans l’objet [StringBuilder](xref:System.Text.StringBuilder) par un autre caractère spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be53-162">method can be used to replace characters within the [StringBuilder](xref:System.Text.StringBuilder) object with another specified character.</span></span> <span data-ttu-id="2be53-163">L’exemple suivant utilise la méthode [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Remplace un caractère spécifié au niveau d’un index spécifié.</span><span class="sxs-lookup"><span data-stu-id="2be53-163">The following example uses the [Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | Replaces a specified character at a specified index.</span></span>
<span data-ttu-id="2be53-164">pour rechercher toutes les instances du caractère point d’exclamation (!) dans un objet [StringBuilder](xref:System.Text.StringBuilder) et les remplacer par le caractère point d’interrogation (?).</span><span class="sxs-lookup"><span data-stu-id="2be53-164">method to search a [StringBuilder](xref:System.Text.StringBuilder) object for all instances of the exclamation point character (!) and replace them with the question mark character (?).</span></span>
 
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

## <a name="converting-a-stringbuilder-object-to-a-string"></a><span data-ttu-id="2be53-165">Conversion d’un objet StringBuilder en chaîne</span><span class="sxs-lookup"><span data-stu-id="2be53-165">Converting a StringBuilder Object to a String</span></span>

<span data-ttu-id="2be53-166">Vous devez convertir l’objet [StringBuilder](xref:System.Text.StringBuilder) en objet [String](xref:System.String) pour pouvoir passer la chaîne représentée par l’objet [StringBuilder](xref:System.Text.StringBuilder) à une méthode qui a un paramètre [String](xref:System.String) ou pour l’afficher dans l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2be53-166">You must convert the [StringBuilder](xref:System.Text.StringBuilder) object to a [String](xref:System.String) object before you can pass the string represented by the [StringBuilder](xref:System.Text.StringBuilder) object to a method that has a [String](xref:System.String) parameter or display it in the user interface.</span></span> <span data-ttu-id="2be53-167">Effectuez cette conversion en appelant la méthode [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString).</span><span class="sxs-lookup"><span data-stu-id="2be53-167">You do this conversion by calling the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method.</span></span> <span data-ttu-id="2be53-168">L’exemple suivant appelle plusieurs méthodes [StringBuilder](xref:System.Text.StringBuilder), puis la méthode [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) pour afficher la chaîne.</span><span class="sxs-lookup"><span data-stu-id="2be53-168">The following example calls a number of [StringBuilder](xref:System.Text.StringBuilder) methods and then calls the [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) method to display the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2be53-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2be53-169">See Also</span></span>

[<span data-ttu-id="2be53-170">System.Text.StringBuilder</span><span class="sxs-lookup"><span data-stu-id="2be53-170">System.Text.StringBuilder</span></span>](xref:System.Text.StringBuilder)

[<span data-ttu-id="2be53-171">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="2be53-171">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="2be53-172">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="2be53-172">Formatting types</span></span>](formatting-types.md)

