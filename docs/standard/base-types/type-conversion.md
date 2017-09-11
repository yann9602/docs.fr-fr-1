---
title: Conversion de type
description: Conversion de type
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c9a53222-89cb-47e5-983d-4f0f204e31ba
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="type-conversion"></a><span data-ttu-id="2c5b2-104">Conversion de type</span><span class="sxs-lookup"><span data-stu-id="2c5b2-104">Type conversion</span></span>

<span data-ttu-id="2c5b2-105">Chaque valeur a un type associé qui définit des attributs, tels la quantité d'espace allouée à la valeur, la plage de valeurs possibles et les membres qu'il rend disponibles.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-105">Every value has an associated type, which defines attributes such as the amount of space allocated to the value, the range of possible values it can have, and the members that it makes available.</span></span> <span data-ttu-id="2c5b2-106">De nombreuses valeurs peuvent être exprimées sous forme de plusieurs types.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-106">Many values can be expressed as more than one type.</span></span> <span data-ttu-id="2c5b2-107">Par exemple, la valeur `4` peut être exprimée sous forme d’entier ou de valeur à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-107">For example, the value `4` can be expressed as an integer or a floating-point value.</span></span> <span data-ttu-id="2c5b2-108">La conversion de type crée une valeur dans un nouveau type qui est équivalente à la valeur d'un ancien type, mais ne préserve pas nécessairement l'identité (ou la valeur exacte) de l'objet d'origine.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-108">Type conversion creates a value in a new type that is equivalent to the value of an old type, but does not necessarily preserve the identity (or exact value) of the original object.</span></span>

<span data-ttu-id="2c5b2-109">.NET prend automatiquement en charge les conversions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c5b2-109">.NET automatically supports the following conversions:</span></span>

* <span data-ttu-id="2c5b2-110">Conversion d’une classe dérivée vers une classe de base.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-110">Conversion from a derived class to a base class.</span></span> <span data-ttu-id="2c5b2-111">Cela signifie, par exemple, qu’une instance d’une classe ou d’une structure peut être convertie en instance [Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-111">This means, for example, that an instance of any class or structure can be converted to an [Object](xref:System.Object) instance.</span></span> <span data-ttu-id="2c5b2-112">Cette conversion ne nécessite pas d’opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-112">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="2c5b2-113">Reconversion d’une classe de base vers la classe dérivée d’origine.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-113">Conversion from a base class back to the original derived class.</span></span> <span data-ttu-id="2c5b2-114">En C#, cette conversion nécessite un opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-114">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="2c5b2-115">En Visual Basic, elle nécessite l’opérateur `CType` si `Option Strict` est activée.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-115">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

* <span data-ttu-id="2c5b2-116">Conversion d’un type qui implémente une interface vers un objet d’interface qui représente cette interface.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-116">Conversion from a type that implements an interface to an interface object that represents that interface.</span></span> <span data-ttu-id="2c5b2-117">Cette conversion ne nécessite pas d’opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-117">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="2c5b2-118">Reconversion d’un objet d’interface vers le type d’origine qui implémente cette interface.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-118">Conversion from an interface object back to the original type that implements that interface.</span></span> <span data-ttu-id="2c5b2-119">En C#, cette conversion nécessite un opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-119">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="2c5b2-120">En Visual Basic, elle nécessite l’opérateur `CType` si `Option Strict` est activée.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-120">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

<span data-ttu-id="2c5b2-121">En plus de ces conversions automatiques, .NET fournit plusieurs fonctionnalités qui prennent en charge la conversion de type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-121">In addition to these automatic conversions, .NET provides several features that support custom type conversion.</span></span> <span data-ttu-id="2c5b2-122">Notamment :</span><span class="sxs-lookup"><span data-stu-id="2c5b2-122">These include the following:</span></span> 

* <span data-ttu-id="2c5b2-123">L'opérateur `Implicit`, qui définit les conversions étendues disponibles entre des types.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-123">The `Implicit` operator, which defines the available widening conversions between types.</span></span> <span data-ttu-id="2c5b2-124">Pour plus d’informations, consultez la section [Conversion implicite avec l’opérateur Implicit](#implicit-conversion-with-the-implicit-operator).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-124">For more information, see the [Implicit conversion with the Implicit operator](#implicit-conversion-with-the-implicit-operator) section.</span></span>

* <span data-ttu-id="2c5b2-125">L'opérateur `Explicit`, qui définit les conversions restrictives entre des types.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-125">The `Explicit` operator, which defines the available narrowing conversions between types.</span></span> <span data-ttu-id="2c5b2-126">Pour plus d’informations, consultez la section [Conversion explicite avec l’opérateur Explicit](#explicit-conversion-with-the-explicit-operator).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-126">For more information, see the [Explicit conversion with the Explicit operator](#explicit-conversion-with-the-explicit-operator) section.</span></span>

* <span data-ttu-id="2c5b2-127">L’interface [IConvertible](xref:System.IConvertible), qui définit les conversions vers chacun des types de données .NET de base.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-127">The [IConvertible](xref:System.IConvertible) interface, which defines conversions to each of the base .NET data types.</span></span> <span data-ttu-id="2c5b2-128">Pour plus d’informations, consultez la section [Interface IConvertible](#the-iconvertible-interface).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-128">For more information, see the [The IConvertible interface](#the-iconvertible-interface) section.</span></span>

* <span data-ttu-id="2c5b2-129">La classe [Convert`IConvertible`, qui fournit un ensemble de méthodes qui implémentent les méthodes dans l’interface ](xref:System.Convert).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-129">The [Convert](xref:System.Convert) class, which provides a set of methods that implement the methods in the `IConvertible` interface.</span></span> <span data-ttu-id="2c5b2-130">Pour plus d’informations, consultez la section [Classe Convert](#the-convert-class).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-130">For more information, see the [The Convert class](#the-convert-class) section.</span></span>

* <span data-ttu-id="2c5b2-131">La classe [TypeConverter](xref:System.ComponentModel.TypeConverter), qui est une classe de base qui peut être étendue pour prendre en charge la conversion d’un type spécifié vers un autre type.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-131">The [TypeConverter](xref:System.ComponentModel.TypeConverter) class, which is a base class that can be extended to support the conversion of a specified type to any other type.</span></span> <span data-ttu-id="2c5b2-132">Pour plus d’informations, consultez la section [Classe TypeConverter](#the-typeconverter-class).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-132">For more information, see the [The TypeConverter class](#the-typeconverter-class) section.</span></span>

## <a name="implicit-conversion-with-the-implicit-operator"></a><span data-ttu-id="2c5b2-133">Conversion implicite avec l’opérateur Implicit</span><span class="sxs-lookup"><span data-stu-id="2c5b2-133">Implicit conversion with the Implicit operator</span></span>

<span data-ttu-id="2c5b2-134">Les conversions étendues impliquent la création d'une valeur à partir de la valeur d'un type existant dont la plage est plus restrictive ou qui contient une liste de membres plus restreinte que le type cible.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-134">Widening conversions involve the creation of a new value from the value of an existing type that has either a more restrictive range or a more restricted member list than the target type.</span></span> <span data-ttu-id="2c5b2-135">Les conversions étendues ne peuvent pas entraîner de perte de données (bien qu'elles puissent produire un résultat de moindre précision).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-135">Widening conversions cannot result in data loss (although they may result in a loss of precision).</span></span> <span data-ttu-id="2c5b2-136">Étant donné qu'aucune donnée ne peut être perdue, les compilateurs peuvent gérer la conversion de façon implicite ou transparente, sans exiger l'utilisation d'une méthode de conversion explicite ou d'un opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-136">Because data cannot be lost, compilers can handle the conversion implicitly or transparently, without requiring the use of an explicit conversion method or a casting operator.</span></span>

> [!NOTE]
> <span data-ttu-id="2c5b2-137">Même si le code qui exécute une conversion implicite peut appeler une méthode de conversion ou utiliser un opérateur de cast, son utilisation n'est pas requise par les compilateurs qui prennent en charge les conversions implicites.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-137">Although code that performs an implicit conversion can call a conversion method or use a casting operator, their use is not required by compilers that support implicit conversions.</span></span>

<span data-ttu-id="2c5b2-138">Par exemple, le type [Decimal](xref:System.Decimal) prend en charge les conversions implicites des valeurs [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) et [UInt64](xref:System.UInt64).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-138">For example, the [Decimal](xref:System.Decimal) type supports implicit conversions from [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64) values.</span></span> <span data-ttu-id="2c5b2-139">L'exemple suivant illustre certaines de ces conversions implicites en assignant des valeurs à une variable `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-139">The following example illustrates some of these implicit conversions in assigning values to a `Decimal` variable.</span></span>

```csharp
byte byteValue = 16;
short shortValue = -1024;
int intValue = -1034000;
long longValue = 1152921504606846976;
ulong ulongValue = UInt64.MaxValue;

decimal decimalValue;

decimalValue = byteValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  byteValue.GetType().Name, decimalValue); 

decimalValue = shortValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  shortValue.GetType().Name, decimalValue); 

decimalValue = intValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  intValue.GetType().Name, decimalValue); 

decimalValue = longValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 

decimalValue = ulongValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 
// The example displays the following output:
//    After assigning a Byte value, the Decimal value is 16.
//    After assigning a Int16 value, the Decimal value is -1024.
//    After assigning a Int32 value, the Decimal value is -1034000.
//    After assigning a Int64 value, the Decimal value is 1152921504606846976.
//    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

```vb
Dim byteValue As Byte = 16
Dim shortValue As Short = -1024
Dim intValue As Integer = -1034000
Dim longValue As Long = CLng(1024^6)
Dim ulongValue As ULong = ULong.MaxValue

Dim decimalValue As Decimal

decimalValue = byteValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  byteValue.GetType().Name, decimalValue) 

decimalValue = shortValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  shortValue.GetType().Name, decimalValue) 

decimalValue = intValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  intValue.GetType().Name, decimalValue) 

decimalValue = longValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 

decimalValue = ulongValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 
' The example displays the following output:
'    After assigning a Byte value, the Decimal value is 16.
'    After assigning a Int16 value, the Decimal value is -1024.
'    After assigning a Int32 value, the Decimal value is -1034000.
'    After assigning a Int64 value, the Decimal value is 1152921504606846976.
'    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

<span data-ttu-id="2c5b2-140">Si un compilateur de langage particulier prend en charge des opérateurs personnalisés, vous pouvez également définir des conversions implicites dans vos propres types personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-140">If a particular language compiler supports custom operators, you can also define implicit conversions in your own custom types.</span></span> <span data-ttu-id="2c5b2-141">L'exemple suivant fournit une implémentation partielle d'un type de données d'octets signés nommé `ByteWithSign` qui utilise la représentation « signe et magnitude ».</span><span class="sxs-lookup"><span data-stu-id="2c5b2-141">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="2c5b2-142">Il prend en charge la conversion implicite des valeurs [Byte](xref:System.Byte) et [SByte](xref:System.SByte) en valeurs `ByteWithSign`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-142">It supports implicit conversion of [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values to `ByteWithSign` values.</span></span>

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   public static implicit operator ByteWithSign(SByte value) 
   {
      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static implicit operator ByteWithSign(Byte value)
   {
      ByteWithSign  newValue;
      newValue.signValue = 1;
      newValue.value = value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Public Overloads Shared Widening Operator CType(value As SByte) As ByteWithSign
      Dim newValue As ByteWithSign
      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator  

   Public Overloads Shared Widening Operator CType(value As Byte) As ByteWithSign
      Dim NewValue As ByteWithSign
      newValue.signValue = 1
      newValue.value = value
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

<span data-ttu-id="2c5b2-143">Le code client peut ensuite déclarer une variable `ByteWithSign` et lui assigner des valeurs [Byte](xref:System.Byte) et [SByte](xref:System.SByte) sans exécuter de conversion explicite ni utiliser d’opérateur de cast, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-143">Client code can then declare a `ByteWithSign` variable and assign it [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values without performing any explicit conversions or using any casting operators, as the following example shows.</span></span>

```csharp
SByte sbyteValue = -120;
ByteWithSign value = sbyteValue;
Console.WriteLine(value);
value = Byte.MaxValue;
Console.WriteLine(value);
// The example displays the following output:
//       -120
//       255
```

```vb
Dim sbyteValue As SByte = -120
Dim value As ByteWithSign = sbyteValue
Console.WriteLine(value.ToString()) 
value = Byte.MaxValue
Console.WriteLine(value.ToString()) 
' The example displays the following output:
'       -120
'       255
```

## <a name="explicit-conversion-with-the-explicit-operator"></a><span data-ttu-id="2c5b2-144">Conversion explicite avec l’opérateur Explicit</span><span class="sxs-lookup"><span data-stu-id="2c5b2-144">Explicit conversion with the Explicit operator</span></span>

<span data-ttu-id="2c5b2-145">Les conversions restrictives impliquent la création d'une valeur à partir de la valeur d'un type existant dont la plage est plus étendue ou qui contient une liste de membres plus étendue que le type cible.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-145">Narrowing conversions involve the creation of a new value from the value of an existing type that has either a greater range or a larger member list than the target type.</span></span> <span data-ttu-id="2c5b2-146">Une conversion restrictive pouvant entraîner une perte de données, les compilateurs exigent souvent que la conversion soit effectuée de façon implicite via un appel à une méthode de conversion ou à un opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-146">Because a narrowing conversion can result in a loss of data, compilers often require that the conversion be made explicit through a call to a conversion method or a casting operator.</span></span> <span data-ttu-id="2c5b2-147">En d'autres termes, la conversion doit être gérée de manière explicite dans le code du développeur.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-147">That is, the conversion must be handled explicitly in developer code.</span></span> 

> [!NOTE]
> <span data-ttu-id="2c5b2-148">Exiger une méthode de conversion ou un opérateur de cast pour les conversions restrictives a pour principal objectif que le développeur soit conscient des risques de perte de données ou d’un [OverflowException](xref:System.OverflowException) et puisse les gérer dans le code.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-148">The major purpose of requiring a conversion method or casting operator for narrowing conversions is to make the developer aware of the possibility of data loss or an [OverflowException](xref:System.OverflowException) so that it can be handled in code.</span></span> <span data-ttu-id="2c5b2-149">Toutefois, certains compilateurs peuvent assouplir cette exigence.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-149">However, some compilers can relax this requirement.</span></span> <span data-ttu-id="2c5b2-150">Par exemple, en Visual Basic, si `Option Strict` est désactivé (paramètre par défaut), le compilateur Visual Basic essaie d'exécuter des conversions restrictives de manière implicite.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-150">For example, in Visual Basic, if `Option Strict` is off (its default setting), the Visual Basic compiler tries to perform narrowing conversions implicitly.</span></span>

<span data-ttu-id="2c5b2-151">Par exemple, les types de données [UInt32](xref:System.UInt32), [Int64](xref:System.Int64) et [UInt64](xref:System.UInt64) ont tous des plages qui dépassent celle du type de données [Int32](xref:System.Int32), comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-151">For example, the [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), and [UInt64](xref:System.UInt64) data types have ranges that exceed that the [Int32](xref:System.Int32) data type, as the following table shows.</span></span>

<span data-ttu-id="2c5b2-152">Type</span><span class="sxs-lookup"><span data-stu-id="2c5b2-152">Type</span></span> | <span data-ttu-id="2c5b2-153">Comparaison avec la plage de Int32</span><span class="sxs-lookup"><span data-stu-id="2c5b2-153">Comparison with range of Int32</span></span>
---- | ------------------------------
[<span data-ttu-id="2c5b2-154">Int64</span><span class="sxs-lookup"><span data-stu-id="2c5b2-154">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="2c5b2-155">[Int64.MaxValue](xref:System.Int64.MaxValue) est supérieur à [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue) et [Int64.MinValue](xref:System.Int64.MinValue) est inférieur à (a une plage plus négative que) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-155">[Int64.MaxValue](xref:System.Int64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue), and [Int64.MinValue](xref:System.Int64.MinValue) is less than (has a greater negative range than) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span></span>
[<span data-ttu-id="2c5b2-156">UInt32</span><span class="sxs-lookup"><span data-stu-id="2c5b2-156">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="2c5b2-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) est supérieur à [Int32.MaxValue](xref:System.Int32.MaxValue).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>
[<span data-ttu-id="2c5b2-158">UInt64</span><span class="sxs-lookup"><span data-stu-id="2c5b2-158">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="2c5b2-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) est supérieur à [Int32.MaxValue](xref:System.Int32.MaxValue).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>

<span data-ttu-id="2c5b2-160">Pour gérer ces conversions restrictives, .NET permet aux types de définir un opérateur `Explicit`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-160">To handle such narrowing conversions, .NET allows types to define an `Explicit` operator.</span></span> <span data-ttu-id="2c5b2-161">Chaque compilateur de langage peut ensuite implémenter cet opérateur à l’aide de sa propre syntaxe, ou un membre de la classe [Convert](xref:System.Convert) peut être appelé pour effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-161">Individual language compilers can then implement this operator using their own syntax, or a member of the [Convert](xref:System.Convert) class can be called to perform the conversion.</span></span> <span data-ttu-id="2c5b2-162">(Pour plus d’informations sur la classe `Convert`, consultez [Classe Convert](#the-convert-class) plus loin dans cette rubrique.) L’exemple suivant illustre l’utilisation de fonctionnalités de langage pour gérer la conversion explicite de ces valeurs entières potentiellement hors limites en valeurs [Int32](xref:System.Int32).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-162">(For more information about the `Convert` class, see [The Convert class](#the-convert-class) later in this topic.) The following example illustrates the use of language features to handle the explicit conversion of these potentially out-of-range integer values to [Int32](xref:System.Int32) values.</span></span> 

```csharp
long number1 = int.MaxValue + 20L;
uint number2 = int.MaxValue - 1000;
ulong number3 = int.MaxValue;

int intNumber;

try {
   intNumber = checked((int) number1);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number1.GetType().Name, intNumber); 
}
catch (OverflowException) {
   if (number1 > int.MaxValue)
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                        number1, int.MaxValue);
   else
      Console.WriteLine("Conversion failed: {0} is less than {1}.", 
                        number1, int.MinValue);
}

try {
   intNumber = checked((int) number2);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number2.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number2, int.MaxValue);
}

try {
   intNumber = checked((int) number3);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number3.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number1, int.MaxValue);
}

// The example displays the following output:
//    Conversion failed: 2147483667 exceeds 2147483647.
//    After assigning a UInt32 value, the Integer value is 2147482647.
//    After assigning a UInt64 value, the Integer value is 2147483647.
```

```vb
Dim number1 As Long = Integer.MaxValue + 20L
Dim number2 As UInteger = Integer.MaxValue - 1000
Dim number3 As ULong = Integer.MaxValue

Dim intNumber As Integer

Try
   intNumber = CInt(number1)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number1.GetType().Name, intNumber)
Catch e As OverflowException
   If number1 > Integer.MaxValue Then
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                        number1, Integer.MaxValue)
   Else
      Console.WriteLine("Conversion failed: {0} is less than {1}.\n", 
                                        number1, Integer.MinValue)
   End If
End Try

Try
   intNumber = CInt(number2)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number2.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                     number2, Integer.MaxValue)
End Try

Try
   intNumber = CInt(number3)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number3.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.",
                                     number1, Integer.MaxValue)
End Try
' The example displays the following output:
'    Conversion failed: 2147483667 exceeds 2147483647.
'    After assigning a UInt32 value, the Integer value is 2147482647.
'    After assigning a UInt64 value, the Integer value is 2147483647.
```

<span data-ttu-id="2c5b2-163">Les conversions explicites peuvent produire des résultats différents selon les langages, et ces résultats peuvent différer de la valeur retournée par la méthode [Convert](xref:System.Convert) correspondante.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-163">Explicit conversions can produce different results in different languages, and these results can differ from the value returned by the corresponding [Convert](xref:System.Convert) method.</span></span> <span data-ttu-id="2c5b2-164">Par exemple, si la valeur [Double](xref:System.Double) **12.63251** est convertie en valeur [Int32](xref:System.Int32), les méthodes .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) et Visual Basic `CInt` arrondissent la valeur [Double](xref:System.Double) pour retourner une valeur de **13**, mais l’opérateur `(int)` C# tronque la valeur [Double](xref:System.Double) pour retourner une valeur de **12**.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-164">For example, if the [Double](xref:System.Double) value **12.63251** is converted to an [Int32](xref:System.Int32), both the .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) and the Visual Basic `CInt` method method rounds the [Double](xref:System.Double) to return a value of **13**, but the C# `(int)` operator truncates the [Double](xref:System.Double) to return a value of **12**.</span></span> <span data-ttu-id="2c5b2-165">De même, l’opérateur `(int)` C# ne prend pas en charge la conversion de valeurs booléennes en valeurs entières, mais la méthode `CInt` Visual Basic convertit une valeur `true` en **-1**.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-165">Similarly, the C# `(int)` operator does not support Boolean-to-integer conversion, but the Visual Basic `CInt` method converts a value of `true` to **-1**.</span></span> <span data-ttu-id="2c5b2-166">Quant à elle, la méthode [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) convertit une valeur `true` en **1**.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-166">On the other hand, the [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) method converts a value of `true` to **1**.</span></span>

<span data-ttu-id="2c5b2-167">La plupart des compilateurs autorisent les conversions explicites contrôlées ou non contrôlées.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-167">Most compilers allow explicit conversions to be performed in a checked or unchecked manner.</span></span> <span data-ttu-id="2c5b2-168">Quand une conversion contrôlée est effectuée, un [OverflowException](xref:System.OverflowException) est levé lorsque la valeur du type à convertir se situe en dehors de la plage du type cible.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-168">When a checked conversion is performed, an [OverflowException](xref:System.OverflowException) is thrown when the value of the type to be converted is outside the range of the target type.</span></span> <span data-ttu-id="2c5b2-169">Lorsqu'une conversion non contrôlée est effectuée dans les mêmes circonstances, la conversion n'entraîne pas nécessairement la levée d'une exception, mais le comportement exact devient indéfini et la valeur obtenue peut être incorrecte.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-169">When an unchecked conversion is performed under the same conditions, the conversion might not throw an exception, but the exact behavior becomes undefined and an incorrect value might result.</span></span>

> [!NOTE]
> <span data-ttu-id="2c5b2-170">En C#, vous pouvez effectuer des conversions contrôlées à l'aide du mot clé `checked` et d'un opérateur de cast, ou en spécifiant l'option de compilateur `/checked+`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-170">In C#, checked conversions can be performed by using the `checked` keyword together with a casting operator, or by specifying the `/checked+` compiler option.</span></span> <span data-ttu-id="2c5b2-171">Vous pouvez également effectuer des conversions non contrôlées à l'aide du mot clé `unchecked` et de l'opérateur de cast ou en spécifiant l'option de compilateur `/checked-`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-171">Conversely, unchecked conversions can be performed by using the `unchecked` keyword together with the casting operator, or by specifying the `/checked-` compiler option.</span></span> <span data-ttu-id="2c5b2-172">Par défaut, les conversions explicites ne sont pas contrôlées.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-172">By default, explicit conversions are unchecked.</span></span> <span data-ttu-id="2c5b2-173">Dans Visual Basic, les conversions contrôlées peuvent être effectuées en spécifiant l’option du compilateur `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-173">In Visual Basic, checked conversions can be performed by specifying the `/removeintchecks-` compiler option.</span></span> <span data-ttu-id="2c5b2-174">À l’inverse, les conversions non contrôlées peuvent être effectuées en spécifiant l’option du compilateur `/removeintchecks+`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-174">Conversely, unchecked conversions can be performed by specifying the `/removeintchecks+` compiler option.</span></span> <span data-ttu-id="2c5b2-175">Par défaut, les conversions explicites sont contrôlées.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-175">By default, explicit conversions are checked.</span></span>

<span data-ttu-id="2c5b2-176">L'exemple C# suivant utilise les mots clés `checked` et `unchecked` pour illustrer la différence de comportement lorsqu’une valeur en dehors de la plage d’une valeur [Byte](xref:System.Byte) est convertie en `Byte`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-176">The following C# example uses the `checked` and `unchecked` keywords to illustrate the difference in behavior when a value outside the range of a [Byte](xref:System.Byte) is converted to a `Byte`.</span></span> <span data-ttu-id="2c5b2-177">La conversion contrôlée lève une exception, mais la conversion non contrôlée assigne [Byte.MaxValue](xref:System.Byte.MaxValue) à la variable `Byte`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-177">The checked conversion throws an exception, but the unchecked conversion assigns [Byte.MaxValue](xref:System.Byte.MaxValue) to the `Byte` variable.</span></span>

```csharp
int largeValue = Int32.MaxValue;
byte newValue;

try {
   newValue = unchecked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}

try {
   newValue = checked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}
// The example displays the following output:
//    Converted the Int32 value 2147483647 to the Byte value 255.
//    2147483647 is outside the range of the Byte data type.
```

<span data-ttu-id="2c5b2-178">Si un compilateur de langage particulier prend en charge des opérateurs surchargés personnalisés, vous pouvez également définir des conversions explicites dans vos propres types personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-178">If a particular language compiler supports custom overloaded operators, you can also define explicit conversions in your own custom types.</span></span> <span data-ttu-id="2c5b2-179">L'exemple suivant fournit une implémentation partielle d'un type de données d'octets signés nommé `ByteWithSign` qui utilise la représentation « signe et magnitude ».</span><span class="sxs-lookup"><span data-stu-id="2c5b2-179">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="2c5b2-180">Il prend en charge la conversion explicite de valeurs [Int32](xref:System.Int32) et [UInt32](xref:System.UInt32) en valeurs `ByteWithSign`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-180">It supports explicit conversion of [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values to `ByteWithSign` values.</span></span>

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   private const byte MaxValue = byte.MaxValue;
   private const int MinValue = -1 * byte.MaxValue;

   public static explicit operator ByteWithSign(int value) 
   {
      // Check for overflow.
      if (value > ByteWithSign.MaxValue || value < ByteWithSign.MinValue)
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static explicit operator ByteWithSign(uint value)
   {
      if (value > ByteWithSign.MaxValue) 
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = 1;
      newValue.value = (byte) value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Private Const MaxValue As Byte = Byte.MaxValue
   Private Const MinValue As Integer = -1 * Byte.MaxValue

   Public Overloads Shared Narrowing Operator CType(value As Integer) As ByteWithSign
      ' Check for overflow.
      If value > ByteWithSign.MaxValue Or value < ByteWithSign.MinValue Then
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim newValue As ByteWithSign

      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator

   Public Overloads Shared Narrowing Operator CType(value As UInteger) As ByteWithSign
      If value > ByteWithSign.MaxValue Then 
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim NewValue As ByteWithSign

      newValue.signValue = 1
      newValue.value = CByte(value)
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

<span data-ttu-id="2c5b2-181">Le code client peut ensuite déclarer une variable `ByteWithSign` et lui assigner des valeurs [Int32](xref:System.Int32) et [UInt32](xref:System.UInt32) si les assignations incluent un opérateur de cast, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-181">Client code can then declare a `ByteWithSign` variable and assign it [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values if the assignments include a casting operator, as the following example shows.</span></span>

```csharp
ByteWithSign value;

try {
   int intValue = -120;
   value = (ByteWithSign) intValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
   Console.WriteLine(e.Message);
}

try {
   uint uintValue = 1024;
   value = (ByteWithSign) uintValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
    Console.WriteLine(e.Message);
}
// The example displays the following output:
//       -120
//       '1024' is out of range of the ByteWithSign data type.
```

```vb
Dim value As ByteWithSign

Try  
   Dim intValue As Integer = -120
   value = CType(intValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try

Try
   Dim uintValue As UInteger = 1024
   value = CType(uintValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try
' The example displays the following output:
'       -120
'       '1024' is out of range of the ByteWithSign data type.
```

## <a name="the-iconvertible-interface"></a><span data-ttu-id="2c5b2-182">Interface IConvertible</span><span class="sxs-lookup"><span data-stu-id="2c5b2-182">The IConvertible interface</span></span>

<span data-ttu-id="2c5b2-183">Pour prendre en charge la conversion d’un type vers un type de base du Common Language Runtime (CLR), .NET fournit l’interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-183">To support the conversion of any type to a common language runtime base type, .NET provides the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="2c5b2-184">Le type d'implémentation est requis pour fournir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2c5b2-184">The implementing type is required to provide the following:</span></span>

* <span data-ttu-id="2c5b2-185">une méthode qui retourne le [TypeCode](xref:System.TypeCode) du type d’implémentation ;</span><span class="sxs-lookup"><span data-stu-id="2c5b2-185">A method that returns the [TypeCode](xref:System.TypeCode) of the implementing type.</span></span>

* <span data-ttu-id="2c5b2-186">des méthodes pour convertir le type d’implémentation dans chaque type de base du Common Language Runtime ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), et ainsi de suite) ;</span><span class="sxs-lookup"><span data-stu-id="2c5b2-186">Methods to convert the implementing type to each common language runtime base type ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), and so on).</span></span>

* <span data-ttu-id="2c5b2-187">une méthode de conversion généralisée pour convertir une instance du type d'implémentation dans un autre type spécifié.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-187">A generalized conversion method to convert an instance of the implementing type to another specified type.</span></span> <span data-ttu-id="2c5b2-188">Les conversions qui ne sont pas prises en charge doivent lever un [InvalidCastException](xref:System.InvalidCastException).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-188">Conversions that are not supported should throw an [InvalidCastException](xref:System.InvalidCastException).</span></span>

<span data-ttu-id="2c5b2-189">Chaque type de base du Common Language Runtime (autrement dit, les types [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) et [UInt64](xref:System.UInt64), ainsi que les types [DBNull](xref:System.DBNull) et [Enum](xref:System.Enum), implémentent l’interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-189">Each common language runtime base type (that is, the [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64), as well as the [DBNull](xref:System.DBNull) and [Enum](xref:System.Enum) types, implement the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="2c5b2-190">Il s’agit toutefois d’implémentations d’interface explicites. La méthode de conversion ne peut être appelée que via une variable d’interface [IConvertible](xref:System.IConvertible), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-190">However, these are explicit interface implementations; the conversion method can be called only through an [IConvertible](xref:System.IConvertible) interface variable, as the following example shows.</span></span> <span data-ttu-id="2c5b2-191">Cet exemple convertit une valeur [Int32](xref:System.Int32) en sa valeur [Char](xref:System.Char) équivalente.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-191">This example converts an [Int32](xref:System.Int32) value to its equivalent [Char](xref:System.Char) value.</span></span>

```csharp
int codePoint = 1067;
IConvertible iConv = codePoint;
char ch = iConv.ToChar(null);
Console.WriteLine("Converted {0} to {1}.", codePoint, ch);
```

```vb
Dim codePoint As Integer = 1067
Dim iConv As IConvertible = codePoint
Dim ch As Char = iConv.ToChar(Nothing)
Console.WriteLine("Converted {0} to {1}.", codePoint, ch)
```

<span data-ttu-id="2c5b2-192">L’exigence visant à appeler la méthode de conversion sur son interface plutôt que sur le type d’implémentation rend les implémentations d’interface explicites relativement coûteuse.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-192">The requirement to call the conversion method on its interface rather than on the implementing type makes explicit interface implementations relatively expensive.</span></span> <span data-ttu-id="2c5b2-193">En lieu et place, nous vous recommandons d’appeler le membre approprié de la classe [Convert](xref:System.Convert) pour effectuer des conversions entre des types de base du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-193">Instead, we recommend that you call the appropriate member of the [Convert](xref:System.Convert) class to convert between common language runtime base types.</span></span> <span data-ttu-id="2c5b2-194">Pour plus d’informations, consultez la section suivante, [Classe Convert](#the-convert-class).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-194">For more information, see the next section, [The Convert class](#the-convert-class).</span></span> 

> [!NOTE]
> <span data-ttu-id="2c5b2-195">Outre l’interface [IConvertible](xref:System.IConvertible) et la classe [Convert](xref:System.Convert) fournie par .NET, chaque langage peut également offrir des moyens d’effectuer des conversions.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-195">In addition to the [IConvertible](xref:System.IConvertible) interface and the [Convert](xref:System.Convert) class provided by .NET, individual languages may also provide ways to perform conversions.</span></span> <span data-ttu-id="2c5b2-196">Par exemple, C# utilise des opérateurs de casting et Visual Basic fait appel à des fonctions de conversion implémentées par compilateur, telles que `CType`, `CInt` et `DirectCast`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-196">For example, C# uses casting operators; Visual Basic uses compiler-implemented conversion functions such as `CType`, `CInt`, and `DirectCast`.</span></span>

<span data-ttu-id="2c5b2-197">Pour l’essentiel, l’interface [IConvertible](xref:System.IConvertible) est conçue pour prendre en charge la conversion entre les types de base dans .NET.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-197">For the most part, the [IConvertible](xref:System.IConvertible) interface is designed to support conversion between the base types in .NET.</span></span> <span data-ttu-id="2c5b2-198">Toutefois, l'interface peut également être implémentée par un type personnalisé pour prendre en charge la conversion de ce type vers d'autres types personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-198">However, the interface can also be implemented by a custom type to support conversion of that type to other custom types.</span></span> <span data-ttu-id="2c5b2-199">Pour plus d’informations, consultez la section [Conversions personnalisées avec la méthode ChangeType](#custom-conversions-with-the-changetype-method), plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-199">For more information, see the section [Custom conversions with the ChangeType method](#custom-conversions-with-the-changetype-method) later in this topic.</span></span>

## <a name="the-convert-class"></a><span data-ttu-id="2c5b2-200">Classe Convert</span><span class="sxs-lookup"><span data-stu-id="2c5b2-200">The Convert class</span></span>

<span data-ttu-id="2c5b2-201">L’implémentation de l’interface [IConvertible](xref:System.IConvertible) de chaque type de base peut être appelée pour effectuer une conversion de type. Toutefois, l’appel des méthodes de la classe [System.Convert](xref:System.Convert) est recommandé pour effectuer une conversion d’un type de base vers un autre, car il est indépendant du langage.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-201">Although each base type's [IConvertible](xref:System.IConvertible) interface implementation can be called to perform a type conversion, calling the methods of the [System.Convert](xref:System.Convert) class is the recommended language-neutral way to convert from one base type to another.</span></span> <span data-ttu-id="2c5b2-202">En outre, la méthode [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) peut être utilisée pour convertir un type personnalisé spécifié en un autre type.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-202">In addition, the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method can be used to convert from a specified custom type to another type.</span></span> 

### <a name="conversions-between-base-types"></a><span data-ttu-id="2c5b2-203">Conversions entre types de base</span><span class="sxs-lookup"><span data-stu-id="2c5b2-203">Conversions between base types</span></span>

<span data-ttu-id="2c5b2-204">La classe [Convert](xref:System.Convert) constitue une façon indépendante du langage d’effectuer des conversions entre des types de base, et est disponible pour tous les langages qui ciblent le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-204">The [Convert](xref:System.Convert) class provides a language-neutral way to perform conversions between base types and is available to all languages that target the common language runtime.</span></span> <span data-ttu-id="2c5b2-205">Elle fournit un ensemble complet de méthodes pour les conversions étendues et restrictives, et lève un [InvalidCastException](xref:System.InvalidCastException) pour les conversions qui ne sont pas prises en charge (telles que la conversion d’une valeur [DateTime](xref:System.DateTime) en valeur entière).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-205">It provides a complete set of methods for both widening and narrowing conversions, and throws an [InvalidCastException](xref:System.InvalidCastException) for conversions that are not supported (such as the conversion of a [DateTime](xref:System.DateTime) value to an integer value).</span></span> <span data-ttu-id="2c5b2-206">Les conversions restrictives sont effectuées dans un contexte vérifié (checked), et un [OverflowException](xref:System.OverflowException) est levé en cas d’échec de la conversion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-206">Narrowing conversions are performed in a checked context, and an [OverflowException](xref:System.OverflowException) is thrown if the conversion fails.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c5b2-207">Étant donné que la classe [Convert](xref:System.Convert) inclut des méthodes permettant d’effectuer des conversions pour chaque type de base, elle évite de devoir appeler l’implémentation d’interface explicite [IConvertible](xref:System.IConvertible) de chaque type de base.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-207">Because the [Convert](xref:System.Convert) class includes methods to convert to and from each base type, it eliminates the need to call each base type's [IConvertible](xref:System.IConvertible) explicit interface implementation.</span></span>

<span data-ttu-id="2c5b2-208">L’exemple suivant illustre l’utilisation de la classe [System.Convert](xref:System.Convert) pour effectuer plusieurs conversions étendues et restrictives entre des types de base .NET.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-208">The following example illustrates the use of the [System.Convert](xref:System.Convert) class to perform several widening and narrowing conversions between .NET base types.</span></span>

```csharp
// Convert an Int32 value to a Decimal (a widening conversion).
int integralValue = 12534;
decimal decimalValue = Convert.ToDecimal(integralValue);
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:N2}.", 
                                  integralValue.GetType().Name, 
                                  integralValue, 
                                  decimalValue.GetType().Name, 
                                  decimalValue);
// Convert a Byte value to an Int32 value (a widening conversion).
byte byteValue = Byte.MaxValue;
int integralValue2 = Convert.ToInt32(byteValue);                                  
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:G}.", 
                                  byteValue.GetType().Name, 
                                  byteValue, 
                                  integralValue2.GetType().Name, 
                                  integralValue2);

// Convert a Double value to an Int32 value (a narrowing conversion).
double doubleValue = 16.32513e12;
try {
   long longValue = Convert.ToInt64(doubleValue);
   Console.WriteLine("Converted the {0} value {1:E} to " +  
                                     "the {2} value {3:N0}.", 
                                     doubleValue.GetType().Name, 
                                     doubleValue, 
                                     longValue.GetType().Name, 
                                     longValue);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0:E} value {1}.", 
                                     doubleValue.GetType().Name, doubleValue);
}

// Convert a signed byte to a byte (a narrowing conversion).     
sbyte sbyteValue = -16;
try {
   byte byteValue2 = Convert.ToByte(sbyteValue);
   Console.WriteLine("Converted the {0} value {1} to " +  
                                     "the {2} value {3:G}.", 
                                     sbyteValue.GetType().Name, 
                                     sbyteValue, 
                                     byteValue2.GetType().Name, 
                                     byteValue2);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0} value {1}.", 
                                     sbyteValue.GetType().Name, sbyteValue);
}                                         
// The example displays the following output:
//       Converted the Int32 value 12534 to the Decimal value 12,534.00.
//       Converted the Byte value 255 to the Int32 value 255.
//       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
//       Unable to convert the SByte value -16.
```

```vb
' Convert an Int32 value to a Decimal (a widening conversion).
Dim integralValue As Integer = 12534
Dim decimalValue As Decimal = Convert.ToDecimal(integralValue)
Console.WriteLine("Converted the {0} value {1} to the {2} value {3:N2}.", 
                  integralValue.GetType().Name,
                  integralValue,
                  decimalValue.GetType().Name,
                  decimalValue)

' Convert a Byte value to an Int32 value (a widening conversion).
Dim byteValue As Byte = Byte.MaxValue
Dim integralValue2 As Integer = Convert.ToInt32(byteValue)                                  
Console.WriteLine("Converted the {0} value {1} to " + 
                                  "the {2} value {3:G}.",
                                  byteValue.GetType().Name,
                                  byteValue,
                                  integralValue2.GetType().Name,
                                  integralValue2)

' Convert a Double value to an Int32 value (a narrowing conversion).
Dim doubleValue As Double = 16.32513e12
Try
   Dim longValue As Long = Convert.ToInt64(doubleValue)
   Console.WriteLine("Converted the {0} value {1:E} to " + 
                                     "the {2} value {3:N0}.",
                                     doubleValue.GetType().Name,
                                     doubleValue,
                                     longValue.GetType().Name,
                                     longValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0:E} value {1}.",
                                     doubleValue.GetType().Name, doubleValue)
End Try                                                             

' Convert a signed byte to a byte (a narrowing conversion).     
Dim sbyteValue As SByte = -16
Try
   Dim byteValue2 As Byte = Convert.ToByte(sbyteValue)
   Console.WriteLine("Converted the {0} value {1} to " + 
                                     "the {2} value {3:G}.",
                                     sbyteValue.GetType().Name,
                                     sbyteValue,
                                     byteValue2.GetType().Name,
                                     byteValue2)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0} value {1}.",
                                     sbyteValue.GetType().Name, sbyteValue)
End Try 
' The example displays the following output:
'       Converted the Int32 value 12534 to the Decimal value 12,534.00.
'       Converted the Byte value 255 to the Int32 value 255.
'       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
'       Unable to convert the SByte value -16.
```

<span data-ttu-id="2c5b2-209">Dans certains cas, particulièrement lors de la conversion entre des valeurs à virgule flottante, une conversion peut impliquer une perte de précision, bien qu’elle ne lève pas d’[OverflowException](xref:System.OverflowException).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-209">In some cases, particularly when converting to and from floating-point values, a conversion may involve a loss of precision, even though it does not throw an [OverflowException](xref:System.OverflowException).</span></span> <span data-ttu-id="2c5b2-210">L'exemple suivant illustre cette perte de précision.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-210">The following example illustrates this loss of precision.</span></span> <span data-ttu-id="2c5b2-211">Dans le premier cas, une valeur [Decimal](xref:System.Decimal) a moins de précision (moins de chiffres significatifs) lorsqu’elle est convertie en valeur [Double](xref:System.Double).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-211">In the first case, a [Decimal](xref:System.Decimal) value has less precision (fewer significant digits) when it is converted to a [Double](xref:System.Double).</span></span> <span data-ttu-id="2c5b2-212">Dans le second cas, une valeur [Double](xref:System.Double) est arrondie de **42,72** à **43** afin de terminer la conversion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-212">In the second case, a [Double](xref:System.Double) value is rounded from **42.72** to **43** in order to complete the conversion.</span></span>

```csharp
double doubleValue; 

// Convert a Double to a Decimal.
decimal decimalValue = 13956810.96702888123451471211m;
doubleValue = Convert.ToDouble(decimalValue);
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue);

doubleValue = 42.72;
try {
   int integerValue = Convert.ToInt32(doubleValue);
   Console.WriteLine("{0} converted to {1}.", 
                                     doubleValue, integerValue);
}
catch (OverflowException) {      
   Console.WriteLine("Unable to convert {0} to an integer.", 
                                     doubleValue);
}   
// The example displays the following output:
//       13956810.96702888123451471211 converted to 13956810.9670289.
//       42.72 converted to 43.
```

```vb
Dim doubleValue As Double 

' Convert a Double to a Decimal.
Dim decimalValue As Decimal = 13956810.96702888123451471211d
doubleValue = Convert.ToDouble(decimalValue)
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue)

doubleValue = 42.72
Try
   Dim integerValue As Integer = Convert.ToInt32(doubleValue)
   Console.WriteLine("{0} converted to {1}.",
                                     doubleValue, integerValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert {0} to an integer.",
                                     doubleValue)
End Try   
' The example displays the following output:
'       13956810.96702888123451471211 converted to 13956810.9670289.
'       42.72 converted to 43.
```

<span data-ttu-id="2c5b2-213">Pour obtenir un tableau qui répertorie les conversions étendues et restrictives prises en charge par la classe [Convert](xref:System.Convert), consultez [Tableaux de conversion de types](conversion-tables.md).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-213">For a table that lists both the widening and narrowing conversions supported by the [Convert](xref:System.Convert) class, see [Type conversion tables](conversion-tables.md).</span></span>

### <a name="custom-conversions-with-the-changetype-method"></a><span data-ttu-id="2c5b2-214">Conversions personnalisées avec la méthode ChangeType</span><span class="sxs-lookup"><span data-stu-id="2c5b2-214">Custom conversions with the ChangeType method</span></span>

<span data-ttu-id="2c5b2-215">Outre la prise en charge des conversions vers chacun des types de base, la classe [Convert](xref:System.Convert) peut être utilisée pour convertir un type personnalisé vers un ou plusieurs types prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-215">In addition to supporting conversions to each of the base types, the [Convert](xref:System.Convert) class can be used to convert a custom type to one or more predefined types.</span></span> <span data-ttu-id="2c5b2-216">Cette conversion est effectuée par la méthode [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)), qui à son tour encapsule un appel à la méthode [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) du paramètre value.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-216">This conversion is performed by the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method, which in turn wraps a call to the [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) method of the value parameter.</span></span> <span data-ttu-id="2c5b2-217">Ainsi, l'objet représenté par le paramètre value doit fournir une implémentation de l’interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-217">This means that the object represented by the value parameter must provide an implementation of the [IConvertible](xref:System.IConvertible) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="2c5b2-218">Étant donné que les méthodes [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) et [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) utilisent un objet [Type](xref:System.Type) pour spécifier le type cible dans lequel la valeur est convertie, elles peuvent servir à effectuer une conversion dynamique en objet dont le type n’est pas connu au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-218">Because the [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) and [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) methods use a [Type](xref:System.Type) object to specify the target type to which value is converted, they can be used to perform a dynamic conversion to an object whose type is not known at compile time.</span></span> <span data-ttu-id="2c5b2-219">Toutefois, notez que l’implémentation [IConvertible](xref:System.IConvertible) de la valeur doit toujours prendre en charge cette conversion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-219">However, note that the [IConvertible](xref:System.IConvertible) implementation of value must still support this conversion.</span></span> 

<span data-ttu-id="2c5b2-220">L’exemple suivant illustre une implémentation possible de l’interface [IConvertible](xref:System.IConvertible) qui permet de convertir un objet `TemperatureCelsius` en objet `TemperatureFahrenheit`, et inversement.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-220">The following example illustrates a possible implementation of the [IConvertible](xref:System.IConvertible) interface that allows a `TemperatureCelsius` object to be converted to a `TemperatureFahrenheit` object and vice versa.</span></span> <span data-ttu-id="2c5b2-221">L’exemple définit une classe de base, `Temperature`, qui implémente l’interface [IConvertible](xref:System.IConvertible) et remplace la méthode [Object.ToString](xref:System.Object.ToString).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-221">The example defines a base class, `Temperature`, that implements the [IConvertible](xref:System.IConvertible) interface and overrides the [Object.ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="2c5b2-222">Les classes dérivées `TemperatureCelsius` et `TemperatureFahrenheit` substituent chacune les méthodes `ToType` et `ToString` de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-222">The derived `TemperatureCelsius` and `TemperatureFahrenheit` classes each override the `ToType` and the `ToString` methods of the base class.</span></span> 

```csharp
using System;

public abstract class Temperature : IConvertible
{
   protected decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;
   }

   public decimal Value
   { 
      get { return this.temp; } 
      set { this.temp = Value; }        
   }

   public override string ToString()
   {
      return temp.ToString(null as IFormatProvider) + "º";
   }

   // IConvertible implementations.
   public TypeCode GetTypeCode() { 
      return TypeCode.Object;
   }   

   public bool ToBoolean(IFormatProvider provider) {
      throw new InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."));
   }

   public byte ToByte(IFormatProvider provider) {
      if (temp < Byte.MinValue || temp > Byte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Byte data type.", temp));
      else
         return (byte) temp;
   }

   public char ToChar(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-Char conversion is not supported.");
   }

   public DateTime ToDateTime(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-DateTime conversion is not supported.");
   }

   public decimal ToDecimal(IFormatProvider provider) {
      return temp;
   }

   public double ToDouble(IFormatProvider provider) {
      return (double) temp;
   }

   public short ToInt16(IFormatProvider provider) {
      if (temp < Int16.MinValue || temp > Int16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp));
      else
         return (short) Math.Round(temp);
   }

   public int ToInt32(IFormatProvider provider) {
      if (temp < Int32.MinValue || temp > Int32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp));
      else
         return (int) Math.Round(temp);
   }

   public long ToInt64(IFormatProvider provider) {
      if (temp < Int64.MinValue || temp > Int64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp));
      else
         return (long) Math.Round(temp);
   }

   public sbyte ToSByte(IFormatProvider provider) {
      if (temp < SByte.MinValue || temp > SByte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the SByte data type.", temp));
      else
         return (sbyte) temp;
   }

   public float ToSingle(IFormatProvider provider) {
      return (float) temp;
   }

   public virtual string ToString(IFormatProvider provider) {
      return temp.ToString(provider) + "°";
   }

   // If conversionType is implemented by another IConvertible method, call it.
   public virtual object ToType(Type conversionType, IFormatProvider provider) {
      switch (Type.GetTypeCode(conversionType))
      {
         case TypeCode.Boolean:
            return this.ToBoolean(provider);
         case TypeCode.Byte:
            return this.ToByte(provider);
         case TypeCode.Char:
            return this.ToChar(provider);
         case TypeCode.DateTime:
            return this.ToDateTime(provider);
         case TypeCode.Decimal:
            return this.ToDecimal(provider);
         case TypeCode.Double:
            return this.ToDouble(provider);
         case TypeCode.Empty:
            throw new NullReferenceException("The target type is null.");
         case TypeCode.Int16:
            return this.ToInt16(provider);
         case TypeCode.Int32:
            return this.ToInt32(provider);
         case TypeCode.Int64:
            return this.ToInt64(provider);
         case TypeCode.Object:
            // Leave conversion of non-base types to derived classes.
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
         case TypeCode.SByte:
            return this.ToSByte(provider);
         case TypeCode.Single:
            return this.ToSingle(provider);
         case TypeCode.String:
            IConvertible iconv = this;
            return iconv.ToString(provider);
         case TypeCode.UInt16:
            return this.ToUInt16(provider);
         case TypeCode.UInt32:
            return this.ToUInt32(provider);
         case TypeCode.UInt64:
            return this.ToUInt64(provider);
         default:
            throw new InvalidCastException("Conversion not supported.");
      }
   }

   public ushort ToUInt16(IFormatProvider provider) {
      if (temp < UInt16.MinValue || temp > UInt16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp));
      else
         return (ushort) Math.Round(temp);
   }

   public uint ToUInt32(IFormatProvider provider) {
      if (temp < UInt32.MinValue || temp > UInt32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp));
      else
         return (uint) Math.Round(temp);
   }

   public ulong ToUInt64(IFormatProvider provider) {
      if (temp < UInt64.MinValue || temp > UInt64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp));
      else
         return (ulong) Math.Round(temp);
   }
}

public class TemperatureCelsius : Temperature, IConvertible
{
   public TemperatureCelsius(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°C"; 
   }

   // If conversionType is a implemented by another IConvertible method, call it.
   public override object ToType(Type conversionType, IFormatProvider provider) {
      // For non-objects, call base method.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         if (conversionType.Equals(typeof(TemperatureCelsius)))
            return this;
         else if (conversionType.Equals(typeof(TemperatureFahrenheit)))
            return new TemperatureFahrenheit((decimal) this.temp * 9 / 5 + 32);
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }
   }
}

public class TemperatureFahrenheit : Temperature, IConvertible 
{
   public TemperatureFahrenheit(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°F"; 
   }

   public override object ToType(Type conversionType, IFormatProvider provider)
   { 
      // For non-objects, call base methood.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         // Handle conversion between derived classes.
         if (conversionType.Equals(typeof(TemperatureFahrenheit))) 
            return this;
         else if (conversionType.Equals(typeof(TemperatureCelsius)))
            return new TemperatureCelsius((decimal) (this.temp - 32) * 5 / 9);
         // Unspecified object type: throw an InvalidCastException.
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }                                 
   }
}
```

```vb
Public MustInherit Class Temperature
   Implements IConvertible

   Protected temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Property Value As Decimal
      Get 
         Return Me.temp
      End Get
      Set
         Me.temp = Value
      End Set   
   End Property

   Public Overrides Function ToString() As String
      Return temp.ToString() & "º"
   End Function

   ' IConvertible implementations.
   Public Function GetTypeCode() As TypeCode Implements IConvertible.GetTypeCode
      Return TypeCode.Object
   End Function   

   Public Function ToBoolean(provider As IFormatProvider) As Boolean Implements IConvertible.ToBoolean
      Throw New InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."))
   End Function

   Public Function ToByte(provider As IFormatProvider) As Byte Implements IConvertible.ToByte
      If temp < Byte.MinValue Or temp > Byte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Byte data type.", temp))
      Else
         Return CByte(temp)
      End If    
   End Function

   Public Function ToChar(provider As IFormatProvider) As Char Implements IConvertible.ToChar
      Throw New InvalidCastException("Temperature-to-Char conversion is not supported.")
   End Function

   Public Function ToDateTime(provider As IFormatProvider) As DateTime Implements IConvertible.ToDateTime
      Throw New InvalidCastException("Temperature-to-DateTime conversion is not supported.")
   End Function

   Public Function ToDecimal(provider As IFormatProvider) As Decimal Implements IConvertible.ToDecimal
      Return temp
   End Function

   Public Function ToDouble(provider As IFormatProvider) As Double Implements IConvertible.ToDouble
      Return CDbl(temp)
   End Function

   Public Function ToInt16(provider As IFormatProvider) As Int16 Implements IConvertible.ToInt16
      If temp < Int16.MinValue Or temp > Int16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp))
      End If
      Return CShort(Math.Round(temp))
   End Function

   Public Function ToInt32(provider As IFormatProvider) As Int32 Implements IConvertible.ToInt32
      If temp < Int32.MinValue Or temp > Int32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp))
      End If
      Return CInt(Math.Round(temp))
   End Function

   Public Function ToInt64(provider As IFormatProvider) As Int64 Implements IConvertible.ToInt64
      If temp < Int64.MinValue Or temp > Int64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp))
      End If
      Return CLng(Math.Round(temp))
   End Function

   Public Function ToSByte(provider As IFormatProvider) As SByte Implements IConvertible.ToSByte
      If temp < SByte.MinValue Or temp > SByte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the SByte data type.", temp))
      Else
         Return CSByte(temp)
      End If    
   End Function

   Public Function ToSingle(provider As IFormatProvider) As Single Implements IConvertible.ToSingle
      Return CSng(temp)
   End Function

   Public Overridable Overloads Function ToString(provider As IFormatProvider) As String Implements IConvertible.ToString
      Return temp.ToString(provider) & " °C"
   End Function

   ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overridable Function ToType(conversionType As Type, provider As IFormatProvider) As Object Implements IConvertible.ToType
      Select Case Type.GetTypeCode(conversionType)
         Case TypeCode.Boolean
            Return Me.ToBoolean(provider)
         Case TypeCode.Byte
            Return Me.ToByte(provider)
         Case TypeCode.Char
            Return Me.ToChar(provider)   
         Case TypeCode.DateTime
            Return Me.ToDateTime(provider)
         Case TypeCode.Decimal
            Return Me.ToDecimal(provider)
         Case TypeCode.Double
            Return Me.ToDouble(provider)
         Case TypeCode.Empty
            Throw New NullReferenceException("The target type is null.")
         Case TypeCode.Int16
            Return Me.ToInt16(provider)
         Case TypeCode.Int32
            Return Me.ToInt32(provider)
         Case TypeCode.Int64
            Return Me.ToInt64(provider)
         Case TypeCode.Object
            ' Leave conversion of non-base types to derived classes.
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         Case TypeCode.SByte
            Return Me.ToSByte(provider)
         Case TypeCode.Single
            Return Me.ToSingle(provider)
         Case TypeCode.String
            Return Me.ToString(provider)
         Case TypeCode.UInt16
            Return Me.ToUInt16(provider)
         Case TypeCode.UInt32
            Return Me.ToUInt32(provider)
         Case TypeCode.UInt64
            Return Me.ToUInt64(provider)
         Case Else
            Throw New InvalidCastException("Conversion not supported.")   
      End Select
   End Function

   Public Function ToUInt16(provider As IFormatProvider) As UInt16 Implements IConvertible.ToUInt16
      If temp < UInt16.MinValue Or temp > UInt16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp))
      End If
      Return CUShort(Math.Round(temp))
   End Function

   Public Function ToUInt32(provider As IFormatProvider) As UInt32 Implements IConvertible.ToUInt32
      If temp < UInt32.MinValue Or temp > UInt32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp))
      End If
      Return CUInt(Math.Round(temp))
   End Function

   Public Function ToUInt64(provider As IFormatProvider) As UInt64 Implements IConvertible.ToUInt64
      If temp < UInt64.MinValue Or temp > UInt64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp))
      End If
      Return CULng(Math.Round(temp))
   End Function
End Class

Public Class TemperatureCelsius : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°C" 
   End Function

  ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base method.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         If conversionType.Equals(GetType(TemperatureCelsius)) Then
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureFahrenheit))
            Return New TemperatureFahrenheit(CDec(Me.temp * 9 / 5 + 32))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _ 
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class

Public Class TemperatureFahrenheit : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°F" 
   End Function

   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base methood.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         ' Handle conversion between derived classes.
         If conversionType.Equals(GetType(TemperatureFahrenheit)) Then 
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureCelsius))
            Return New TemperatureCelsius(CDec((MyBase.temp - 32) * 5 / 9))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class
```

<span data-ttu-id="2c5b2-223">L’exemple suivant illustre plusieurs appels à ces implémentations [IConvertible](xref:System.IConvertible) pour convertir des objets `TemperatureCelsius` en objets `TemperatureFahrenheit`, et inversement.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-223">The following example illustrates several calls to these [IConvertible](xref:System.IConvertible) implementations to convert `TemperatureCelsius` objects to `TemperatureFahrenheit` objects and vice versa.</span></span>

```csharp
TemperatureCelsius tempC1 = new TemperatureCelsius(0);
TemperatureFahrenheit tempF1 = (TemperatureFahrenheit) Convert.ChangeType(tempC1, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempF1);
TemperatureCelsius tempC2 = (TemperatureCelsius) Convert.ChangeType(tempC1, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempC2);
TemperatureFahrenheit tempF2 = new TemperatureFahrenheit(212);
TemperatureCelsius tempC3 = (TemperatureCelsius) Convert.ChangeType(tempF2, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempC3);
TemperatureFahrenheit tempF3 = (TemperatureFahrenheit) Convert.ChangeType(tempF2, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempF3);
// The example displays the following output:
//       0°C equals 32°F.
//       0°C equals 0°C.
//       212°F equals 100°C.
//       212°F equals 212°F.
```

```vb
Dim tempC1 As New TemperatureCelsius(0)
Dim tempF1 As TemperatureFahrenheit = CType(Convert.ChangeType(tempC1, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempC1, tempF1) 
Dim tempC2 As TemperatureCelsius = CType(Convert.ChangeType(tempC1, GetType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempC1, tempC2) 
Dim tempF2 As New TemperatureFahrenheit(212)
Dim tempC3 As TEmperatureCelsius = CType(Convert.ChangeType(tempF2, GEtType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempF2, tempC3) 
Dim tempF3 As TemperatureFahrenheit = CType(Convert.ChangeType(tempF2, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempF2, tempF3)
' The example displays the following output:
'       0°C equals 32°F.
'       0°C equals 0°C.
'       212°F equals 100°C.
'       212°F equals 212°F.
```

## <a name="the-typeconverter-class"></a><span data-ttu-id="2c5b2-224">Classe TypeConverter</span><span class="sxs-lookup"><span data-stu-id="2c5b2-224">The TypeConverter class</span></span>

<span data-ttu-id="2c5b2-225">.NET vous permet également de définir un convertisseur de type pour un type personnalisé en étendant la classe [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) et en associant le convertisseur de type au type par le biais d’un attribut [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-225">.NET also allows you to define a type converter for a custom type by extending the [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) class and associating the type converter with the type through a [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> <span data-ttu-id="2c5b2-226">Le tableau suivant met en évidence les différences entre cette approche et l’implémentation de l’interface [IConvertible](xref:System.IConvertible) pour un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-226">The following table highlights the differences between this approach and implementing the [IConvertible](xref:System.IConvertible) interface for a custom type.</span></span>

> [!NOTE]
> <span data-ttu-id="2c5b2-227">La prise en charge au moment du design ne peut être fournie pour un type personnalisé que si un convertisseur de type est défini pour ce dernier.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-227">Design-time support can be provided for a custom type only if it has a type converter defined for it.</span></span>

<span data-ttu-id="2c5b2-228">Conversion à l'aide de TypeConverter</span><span class="sxs-lookup"><span data-stu-id="2c5b2-228">Conversion using TypeConverter</span></span> | <span data-ttu-id="2c5b2-229">Conversion à l'aide de IConvertible</span><span class="sxs-lookup"><span data-stu-id="2c5b2-229">Conversion using IConvertible</span></span>
------------------------------ | -----------------------------
<span data-ttu-id="2c5b2-230">Est implémentée pour un type personnalisé en dérivant une classe distincte de [TypeConverter](xref:System.ComponentModel.TypeConverter).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-230">Is implemented for a custom type by deriving a separate class from [TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span> <span data-ttu-id="2c5b2-231">Cette classe dérivée est associée au type personnalisé en appliquant un attribut [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-231">This derived class is associated with the custom type by applying a [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> | <span data-ttu-id="2c5b2-232">Est implémentée par un type personnalisé pour effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-232">Is implemented by a custom type to perform conversion.</span></span> <span data-ttu-id="2c5b2-233">Un utilisateur du type appelle une méthode de conversion [IConvertible](xref:System.IConvertible) sur le type.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-233">A user of the type invokes an [IConvertible](xref:System.IConvertible) conversion method on the type.</span></span>
<span data-ttu-id="2c5b2-234">Peut être utilisée à la fois au moment du design et au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-234">Can be used both at design time and at run time.</span></span> | <span data-ttu-id="2c5b2-235">Ne peut être utilisée qu'au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-235">Can be used only at run time.</span></span>
<span data-ttu-id="2c5b2-236">Utilise la réflexion, et est donc plus lente que la conversion à l’aide d’[IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-236">Uses reflection; therefore, is slower than conversion enabled by [IConvertible](xref:System.IConvertible).</span></span> | <span data-ttu-id="2c5b2-237">N'utilise pas la réflexion.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-237">Does not use reflection.</span></span>
<span data-ttu-id="2c5b2-238">Permet les conversions de type bilatérales du type personnalisé en d'autres types de données, et d'autres types de données en type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-238">Allows two-way type conversions from the custom type to other data types, and from other data types to the custom type.</span></span> <span data-ttu-id="2c5b2-239">Par exemple, un [TypeConverter](xref:System.ComponentModel.TypeConverter) défini pour `MyType` permet les conversions de `MyType` en [String](xref:System.String) et de [String](xref:System.String) en `MyType`.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-239">For example, a [TypeConverter](xref:System.ComponentModel.TypeConverter) defined for `MyType` allows conversions from `MyType` to [String](xref:System.String), and from [String](xref:System.String) to `MyType`.</span></span> | <span data-ttu-id="2c5b2-240">Permet la conversion d'un type personnalisé en d'autres types de données, mais pas d'autres types de données en type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2c5b2-240">Allows conversion from a custom type to other data types, but not from other data types to the custom type.</span></span>

<span data-ttu-id="2c5b2-241">Pour plus d’informations sur l’utilisation de convertisseurs de type pour effectuer des conversions, consultez [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span><span class="sxs-lookup"><span data-stu-id="2c5b2-241">For more information about using type converters to perform conversions, see [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c5b2-242">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c5b2-242">See also</span></span>

[<span data-ttu-id="2c5b2-243">System.Convert</span><span class="sxs-lookup"><span data-stu-id="2c5b2-243">System.Convert</span></span>](xref:System.Convert)

[<span data-ttu-id="2c5b2-244">IConvertible</span><span class="sxs-lookup"><span data-stu-id="2c5b2-244">IConvertible</span></span>](xref:System.IConvertible)

[<span data-ttu-id="2c5b2-245">Tables de conversion de type</span><span class="sxs-lookup"><span data-stu-id="2c5b2-245">Type conversion tables</span></span>](conversion-tables.md)
