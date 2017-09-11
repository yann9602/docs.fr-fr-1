---
title: "Comparaison de chaînes"
description: "Comparaison de chaînes"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="comparing-strings"></a><span data-ttu-id="9c400-104">Comparaison de chaînes</span><span class="sxs-lookup"><span data-stu-id="9c400-104">Comparing strings</span></span>

<span data-ttu-id="9c400-105">.NET fournit plusieurs méthodes permettant de comparer les valeurs de chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="9c400-106">Le tableau suivant répertorie et décrit les méthodes de comparaison de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9c400-106">The following table lists and describes the value-comparison methods.</span></span>

<span data-ttu-id="9c400-107">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="9c400-107">Method name</span></span> | <span data-ttu-id="9c400-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="9c400-108">Use</span></span>
----------- | ---
<span data-ttu-id="9c400-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9c400-109">[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="9c400-110">Compare les valeurs de deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-110">Compares the values of two strings.</span></span> <span data-ttu-id="9c400-111">Retourne une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="9c400-111">Returns an integer value.</span></span>
<span data-ttu-id="9c400-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9c400-112">[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32))</span></span> | <span data-ttu-id="9c400-113">Compare deux chaînes sans tenir compte de la culture locale.</span><span class="sxs-lookup"><span data-stu-id="9c400-113">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="9c400-114">Retourne une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="9c400-114">Returns an integer value.</span></span>
<span data-ttu-id="9c400-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="9c400-115">[String.CompareTo](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="9c400-116">Compare l'objet chaîne actif à une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-116">Compares the current string object to another string.</span></span> <span data-ttu-id="9c400-117">Retourne une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="9c400-117">Returns an integer value.</span></span>
<span data-ttu-id="9c400-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span><span class="sxs-lookup"><span data-stu-id="9c400-118">[String.StartsWith](xref:System.String.StartsWith(System.String))</span></span> | <span data-ttu-id="9c400-119">Détermine si une chaîne commence par la chaîne passée.</span><span class="sxs-lookup"><span data-stu-id="9c400-119">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="9c400-120">Retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9c400-120">Returns a Boolean value.</span></span>
<span data-ttu-id="9c400-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="9c400-121">[String.EndsWith](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="9c400-122">Détermine si une chaîne se termine par la chaîne passée.</span><span class="sxs-lookup"><span data-stu-id="9c400-122">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="9c400-123">Retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9c400-123">Returns a Boolean value.</span></span>
<span data-ttu-id="9c400-124">[String.Equals](xref:System.String.CompareTo(System.String))</span><span class="sxs-lookup"><span data-stu-id="9c400-124">[String.Equals](xref:System.String.CompareTo(System.String))</span></span> | <span data-ttu-id="9c400-125">Détermine si deux chaînes sont identiques.</span><span class="sxs-lookup"><span data-stu-id="9c400-125">Determines whether two strings are the same.</span></span> <span data-ttu-id="9c400-126">Retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9c400-126">Returns a Boolean value.</span></span>
<span data-ttu-id="9c400-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="9c400-127">[String.IndexOf](xref:System.String.IndexOf(System.Char))</span></span> | <span data-ttu-id="9c400-128">Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par le début de la chaîne que vous examinez.</span><span class="sxs-lookup"><span data-stu-id="9c400-128">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="9c400-129">Retourne une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="9c400-129">Returns an integer value.</span></span>
<span data-ttu-id="9c400-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span><span class="sxs-lookup"><span data-stu-id="9c400-130">[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char))</span></span> | <span data-ttu-id="9c400-131">Retourne la position d'index d'un caractère ou d'une chaîne, en commençant par la fin de la chaîne que vous examinez.</span><span class="sxs-lookup"><span data-stu-id="9c400-131">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="9c400-132">Retourne une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="9c400-132">Returns an integer value.</span></span>

## <a name="compare"></a><span data-ttu-id="9c400-133">Comparer</span><span class="sxs-lookup"><span data-stu-id="9c400-133">Compare</span></span>

<span data-ttu-id="9c400-134">La méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) statique fournit un moyen complet de comparer deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-134">The static [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="9c400-135">Cette méthode prend en compte la culture.</span><span class="sxs-lookup"><span data-stu-id="9c400-135">This method is culturally aware.</span></span> <span data-ttu-id="9c400-136">Vous pouvez utiliser cette fonction pour comparer deux chaînes ou les sous-chaînes de deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-136">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="9c400-137">En outre, des surcharges sont fournies, qui prennent ou non en compte les différences de casse et de culture.</span><span class="sxs-lookup"><span data-stu-id="9c400-137">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="9c400-138">Le tableau suivant montre les trois valeurs entières que cette méthode peut retourner.</span><span class="sxs-lookup"><span data-stu-id="9c400-138">The following table shows the three integer values that this method might return.</span></span> 

<span data-ttu-id="9c400-139">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9c400-139">Return value</span></span> | <span data-ttu-id="9c400-140">Condition</span><span class="sxs-lookup"><span data-stu-id="9c400-140">Condition</span></span>
------------ | ---------
<span data-ttu-id="9c400-141">Entier négatif</span><span class="sxs-lookup"><span data-stu-id="9c400-141">A negative integer</span></span> | <span data-ttu-id="9c400-142">La première chaîne précède la seconde dans l’ordre de tri ou la première chaîne est `null`.</span><span class="sxs-lookup"><span data-stu-id="9c400-142">The first string precedes the second string in the sort order, or the first string is `null`.</span></span>
<span data-ttu-id="9c400-143">0</span><span class="sxs-lookup"><span data-stu-id="9c400-143">0</span></span> | <span data-ttu-id="9c400-144">La première chaîne et la seconde sont égales ou les deux chaînes sont `null`.</span><span class="sxs-lookup"><span data-stu-id="9c400-144">The first string and the second string are equal, or both strings are `null`.</span></span>
<span data-ttu-id="9c400-145">Un entier positif ou 1</span><span class="sxs-lookup"><span data-stu-id="9c400-145">A positive integer, or 1</span></span> | <span data-ttu-id="9c400-146">La première chaîne suit la seconde dans l’ordre de tri, ou la seconde chaîne est Null.</span><span class="sxs-lookup"><span data-stu-id="9c400-146">The first string follows the second string in the sort order, or the second string is null.</span></span>
 
> [!IMPORTANT]
> <span data-ttu-id="9c400-147">La méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) est principalement destinée à être utilisée lors du classement ou du tri de chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-147">The [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="9c400-148">Vous ne devez pas utiliser la méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre).</span><span class="sxs-lookup"><span data-stu-id="9c400-148">You should not use the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="9c400-149">Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="9c400-149">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="9c400-150">L’exemple suivant utilise la méthode [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour déterminer les valeurs relatives de deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-150">The following example uses the [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to determine the relative values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

<span data-ttu-id="9c400-151">Cet exemple affiche `-1` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-151">This example displays `-1` to the console.</span></span>

## <a name="compareordinal"></a><span data-ttu-id="9c400-152">CompareOrdinal</span><span class="sxs-lookup"><span data-stu-id="9c400-152">CompareOrdinal</span></span>

<span data-ttu-id="9c400-153">La méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) compare deux objets String sans prendre en compte la culture locale.</span><span class="sxs-lookup"><span data-stu-id="9c400-153">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="9c400-154">Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode `Compare` du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="9c400-154">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c400-155">La méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) est principalement destinée à être utilisée pour classer ou trier des chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-155">The [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="9c400-156">Vous ne devez pas utiliser la méthode [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre).</span><span class="sxs-lookup"><span data-stu-id="9c400-156">You should not use the [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="9c400-157">Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="9c400-157">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="9c400-158">L’exemple suivant utilise la méthode `CompareOrdinal` pour comparer les valeurs de deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-158">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

<span data-ttu-id="9c400-159">Cet exemple affiche `-32` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-159">This example displays `-32` to the console.</span></span>

## <a name="compareto"></a><span data-ttu-id="9c400-160">CompareTo</span><span class="sxs-lookup"><span data-stu-id="9c400-160">CompareTo</span></span>

<span data-ttu-id="9c400-161">La méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) compare la chaîne encapsulée par l’objet String actif à une autre chaîne ou un autre objet.</span><span class="sxs-lookup"><span data-stu-id="9c400-161">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="9c400-162">Les valeurs de retour de cette méthode sont identiques aux valeurs retournées par la méthode `String.Compare` du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="9c400-162">The return values of this method are identical to the values returned by the `String.Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c400-163">La méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) est principalement destinée à être utilisée lors du classement ou du tri de chaînes.</span><span class="sxs-lookup"><span data-stu-id="9c400-163">The [String.CompareTo](xref:System.String.CompareTo(System.String)) method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="9c400-164">Vous ne devez pas utiliser la méthode [String.CompareTo](xref:System.String.CompareTo(System.String)) pour tester l’égalité (c’est-à-dire rechercher explicitement une valeur de retour égale à 0 sans savoir si une chaîne est inférieure ou supérieure à l’autre).</span><span class="sxs-lookup"><span data-stu-id="9c400-164">You should not use the [String.CompareTo](xref:System.String.CompareTo(System.String)) method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="9c400-165">Pour déterminer si deux chaînes sont égales, utilisez plutôt la méthode [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)).</span><span class="sxs-lookup"><span data-stu-id="9c400-165">Instead, to determine whether two strings are equal, use the [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) method.</span></span>

<span data-ttu-id="9c400-166">L’exemple suivant utilise la méthode `String.CompareTo` pour comparer l’objet `string1` à l’objet `string2`.</span><span class="sxs-lookup"><span data-stu-id="9c400-166">The following example uses the `String.CompareTo` method to compare the `string1` object to the `string2` object.</span></span>

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

<span data-ttu-id="9c400-167">Cet exemple affiche `-1` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-167">This example displays `-1` to the console.</span></span>

## <a name="equals"></a><span data-ttu-id="9c400-168">Equals</span><span class="sxs-lookup"><span data-stu-id="9c400-168">Equals</span></span>

<span data-ttu-id="9c400-169">La méthode [String.Equals](xref:System.String.CompareTo(System.String)) peut facilement déterminer si deux chaînes sont identiques.</span><span class="sxs-lookup"><span data-stu-id="9c400-169">The [String.Equals](xref:System.String.CompareTo(System.String)) method can easily determine if two strings are the same.</span></span> <span data-ttu-id="9c400-170">Cette méthode respectant la casse retourne une valeur booléenne `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="9c400-170">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="9c400-171">Elle peut être utilisée à partir d'une classe existante, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9c400-171">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="9c400-172">L’exemple suivant utilise la méthode `Equals` pour déterminer si un objet String contient la phrase « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="9c400-172">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

<span data-ttu-id="9c400-173">Cet exemple affiche `true` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-173">This example displays `true` to the console.</span></span>

<span data-ttu-id="9c400-174">Cette méthode peut également être utilisée comme une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9c400-174">This method can also be used as a static method.</span></span> <span data-ttu-id="9c400-175">L'exemple suivant compare deux objets chaîne à l'aide d'une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="9c400-175">The following example compares two string objects using a static method.</span></span>

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

<span data-ttu-id="9c400-176">Cet exemple affiche `true` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-176">This example displays `true` to the console.</span></span>

## <a name="startswith-and-endswith"></a><span data-ttu-id="9c400-177">StartsWith et EndsWith</span><span class="sxs-lookup"><span data-stu-id="9c400-177">StartsWith and EndsWith</span></span>

<span data-ttu-id="9c400-178">Vous pouvez utiliser la méthode [String.StartsWith](xref:System.String.StartsWith(System.String)) pour déterminer si un objet String commence par les mêmes caractères que ceux qui constituent une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-178">You can use the [String.StartsWith](xref:System.String.StartsWith(System.String)) method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="9c400-179">Cette méthode qui respecte la casse retourne `true` si l’objet String actif commence par la chaîne passée et `false` si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="9c400-179">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="9c400-180">L'exemple suivant utilise cette méthode pour déterminer si un objet chaîne commence par "Hello".</span><span class="sxs-lookup"><span data-stu-id="9c400-180">The following example uses this method to determine if a string object begins with "Hello".</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

<span data-ttu-id="9c400-181">Cet exemple affiche `true` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-181">This example displays `true` to the console.</span></span>

<span data-ttu-id="9c400-182">La méthode [String.EndsWith](xref:System.String.CompareTo(System.String)) compare une chaîne passée aux caractères qui se trouvent à la fin de l’objet String actif.</span><span class="sxs-lookup"><span data-stu-id="9c400-182">The [String.EndsWith](xref:System.String.CompareTo(System.String)) method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="9c400-183">Elle retourne également une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="9c400-183">It also returns a Boolean value.</span></span> <span data-ttu-id="9c400-184">L’exemple suivant vérifie la fin d’une chaîne à l’aide de la méthode `EndsWith`.</span><span class="sxs-lookup"><span data-stu-id="9c400-184">The following example checks the end of a string using the `EndsWith` method.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

<span data-ttu-id="9c400-185">Cet exemple affiche `false` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-185">This example displays `false` to the console.</span></span>

## <a name="indexof-and-lastindexof"></a><span data-ttu-id="9c400-186">IndexOf et LastIndexOf</span><span class="sxs-lookup"><span data-stu-id="9c400-186">IndexOf and LastIndexOf</span></span>

<span data-ttu-id="9c400-187">Vous pouvez utiliser la méthode [String.IndexOf](xref:System.String.IndexOf(System.Char)) pour déterminer la position de la première occurrence d’un caractère particulier dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-187">You can use the [String.IndexOf](xref:System.String.IndexOf(System.Char)) method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="9c400-188">Cette méthode qui respecte la casse commence à compter à partir du début d'une chaîne et retourne la position d'un caractère passé en utilisant un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="9c400-188">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="9c400-189">Si le caractère est introuvable, la valeur -1 est retournée.</span><span class="sxs-lookup"><span data-stu-id="9c400-189">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="9c400-190">L’exemple suivant utilise la méthode `IndexOf` pour rechercher la première occurrence du caractère '`l`' dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-190">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

<span data-ttu-id="9c400-191">Cet exemple affiche `2` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-191">This example displays `2` to the console.</span></span>

<span data-ttu-id="9c400-192">La méthode [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) est similaire à la méthode `String.IndexOf`, sauf qu’elle retourne la position de la dernière occurrence d’un caractère particulier dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-192">The [String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="9c400-193">Elle respecte la casse et utilise un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="9c400-193">It is case-sensitive and uses a zero-based index.</span></span> 

<span data-ttu-id="9c400-194">L’exemple suivant utilise la méthode `LastIndexOf` pour rechercher la dernière occurrence du caractère '`l`' dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9c400-194">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

<span data-ttu-id="9c400-195">Cet exemple affiche `9` sur la console.</span><span class="sxs-lookup"><span data-stu-id="9c400-195">This example displays `9` to the console.</span></span>

<span data-ttu-id="9c400-196">Les deux méthodes sont utiles quand elles sont utilisées conjointement avec la méthode [String.Remove](xref:System.String.Remove(System.Int32)).</span><span class="sxs-lookup"><span data-stu-id="9c400-196">Both methods are useful when used in conjunction with the [String.Remove](xref:System.String.Remove(System.Int32)) method.</span></span> <span data-ttu-id="9c400-197">Vous pouvez utiliser la méthode `IndexOf` ou la méthode `LastIndexOf` pour récupérer la position d’un caractère, puis fournir cette position à la `Remove method` pour supprimer un caractère ou un mot commençant par ce caractère.</span><span class="sxs-lookup"><span data-stu-id="9c400-197">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove method` in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c400-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c400-198">See Also</span></span>

[<span data-ttu-id="9c400-199">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="9c400-199">Basic string operations</span></span>](basic-string-operations.md)













