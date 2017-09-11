---
title: Mise en forme des types
description: Mise en forme des types
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
ms.translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: e9b8ad13a48dd43236769b130d6f8a75b7b023ca
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---

# <a name="formatting-types"></a><span data-ttu-id="cb28e-104">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="cb28e-104">Formatting types</span></span>

<span data-ttu-id="cb28e-105">La mise en forme est le processus de conversion d'une instance d'une classe, d'une structure ou d'une valeur d'énumération en représentation sous forme de chaîne, généralement pour exposer la chaîne obtenue aux utilisateurs ou pour qu'elle soit désérialisée afin de restaurer le type de données d'origine.</span><span class="sxs-lookup"><span data-stu-id="cb28e-105">Formatting is the process of converting an instance of a class, structure, or enumeration value to its string representation, often so that the resulting string can be displayed to users or deserialized to restore the original data type.</span></span> <span data-ttu-id="cb28e-106">Cette conversion peut présenter plusieurs difficultés :</span><span class="sxs-lookup"><span data-stu-id="cb28e-106">This conversion can pose a number of challenges:</span></span>

* <span data-ttu-id="cb28e-107">La manière dont les valeurs sont stockées en interne ne reflète pas nécessairement celle dont les utilisateurs souhaitent les voir.</span><span class="sxs-lookup"><span data-stu-id="cb28e-107">The way that values are stored internally does not necessarily reflect the way that users want to view them.</span></span> <span data-ttu-id="cb28e-108">Par exemple, un numéro de téléphone peut être stocké sous la forme **8009999999**, ce qui n’est pas convivial.</span><span class="sxs-lookup"><span data-stu-id="cb28e-108">For example, a telephone number might be stored in the form **8009999999**, which is not user-friendly.</span></span> <span data-ttu-id="cb28e-109">Il devrait plutôt être affiché sous la forme **800-999-9999**.</span><span class="sxs-lookup"><span data-stu-id="cb28e-109">It should instead be displayed as **800-999-9999**.</span></span> <span data-ttu-id="cb28e-110">Consultez la section [Chaînes de format personnalisées](#custom-format-strings) pour obtenir un exemple d’une telle mise en forme d’un nombre.</span><span class="sxs-lookup"><span data-stu-id="cb28e-110">See the [Custom format strings](#custom-format-strings) section for an example that formats a number in this way.</span></span> 

* <span data-ttu-id="cb28e-111">La conversion d'un objet en sa représentation sous forme de chaîne n'est pas toujours intuitive.</span><span class="sxs-lookup"><span data-stu-id="cb28e-111">Sometimes the conversion of an object to its string representation is not intuitive.</span></span> <span data-ttu-id="cb28e-112">Par exemple, il n’est pas évident de savoir comment doit s’afficher la représentation sous forme de chaîne d’un objet **Temperature** ou **Person**.</span><span class="sxs-lookup"><span data-stu-id="cb28e-112">For example, it is not clear how the string representation of a **Temperature** object or a **Person** object should appear.</span></span> <span data-ttu-id="cb28e-113">Pour obtenir un exemple illustrant la mise en forme d’un objet **Temperature** selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings).</span><span class="sxs-lookup"><span data-stu-id="cb28e-113">For an example that formats a **Temperature** object in a variety of ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

* <span data-ttu-id="cb28e-114">Les valeurs requièrent souvent une mise en forme qui tient compte de la culture.</span><span class="sxs-lookup"><span data-stu-id="cb28e-114">Values often require culture-sensitive formatting.</span></span> <span data-ttu-id="cb28e-115">Par exemple, dans une application qui utilise des nombre pour refléter des valeurs monétaires, les chaînes numériques doivent inclure le symbole monétaire, le séparateur de groupes (qui, dans la plupart des cultures, est le séparateur des milliers) et le symbole décimal qui correspondent à la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-115">For example, in an application that uses numbers to reflect monetary values, numeric strings should include the current culture’s currency symbol, group separator (which, in most cultures, is the thousands separator), and decimal symbol.</span></span> <span data-ttu-id="cb28e-116">Pour obtenir un exemple, consultez la section [Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).</span><span class="sxs-lookup"><span data-stu-id="cb28e-116">For an example, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span> 

* <span data-ttu-id="cb28e-117">Une application peut avoir à afficher la même valeur de différentes manières.</span><span class="sxs-lookup"><span data-stu-id="cb28e-117">An application may have to display the same value in different ways.</span></span> <span data-ttu-id="cb28e-118">Par exemple, une application peut représenter un membre d'énumération en affichant une représentation sous forme de chaîne de son nom ou en affichant sa valeur sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="cb28e-118">For example, an application may represent an enumeration member by displaying a string representation of its name or by displaying its underlying value.</span></span> <span data-ttu-id="cb28e-119">Pour obtenir un exemple illustrant la mise en forme d’un membre de l’énumération [DayOfWeek](xref:System.DayOfWeek) selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings).</span><span class="sxs-lookup"><span data-stu-id="cb28e-119">For an example that formats a member of the [DayOfWeek](xref:System.DayOfWeek) enumeration in different ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

<span data-ttu-id="cb28e-120">.NET assure une prise en charge évoluée de la mise en forme qui permet aux développeurs de surmonter ces difficultés.</span><span class="sxs-lookup"><span data-stu-id="cb28e-120">.NET provides rich formatting support that enables developers to address these requirements.</span></span> 

> [!NOTE]
> <span data-ttu-id="cb28e-121">La mise en forme convertit la valeur d'un type en une représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-121">Formatting converts the value of a type into a string representation.</span></span> <span data-ttu-id="cb28e-122">L'analyse est l'opération inverse de la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-122">Parsing is the inverse of formatting.</span></span> <span data-ttu-id="cb28e-123">Une opération d'analyse crée une instance d'un type de données à partir de sa représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-123">A parsing operation creates an instance of a data type from its string representation.</span></span> <span data-ttu-id="cb28e-124">Pour plus d’informations sur la conversion de chaînes en d’autres types de données, consultez [Analyse de chaînes](parsing-strings.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-124">For information about converting strings to other data types, see [Parsing strings](parsing-strings.md).</span></span>

<span data-ttu-id="cb28e-125">Cette vue d'ensemble contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb28e-125">This overview contains the following sections:</span></span>

* [<span data-ttu-id="cb28e-126">Mise en forme dans .NET</span><span class="sxs-lookup"><span data-stu-id="cb28e-126">Formatting in .NET</span></span>](#formatting-in-net)

* [<span data-ttu-id="cb28e-127">Mise en forme par défaut à l’aide de la méthode ToString</span><span class="sxs-lookup"><span data-stu-id="cb28e-127">Default formatting using the ToString method</span></span>](#default-formatting-using-the-tostring-method)

* [<span data-ttu-id="cb28e-128">Substitution de la méthode ToString</span><span class="sxs-lookup"><span data-stu-id="cb28e-128">Overriding the ToString method</span></span>](#overriding-the-tostring-method)

* [<span data-ttu-id="cb28e-129">Méthode ToString et chaînes de format</span><span class="sxs-lookup"><span data-stu-id="cb28e-129">The ToString method and format strings</span></span>](#the-tostring-method-and-format-strings)

    * [<span data-ttu-id="cb28e-130">Chaînes de format standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-130">Standard format strings</span></span>](#standard-format-strings)
    
    * [<span data-ttu-id="cb28e-131">Chaînes de format personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-131">Custom format strings</span></span>](#custom-format-strings)
    
    * [<span data-ttu-id="cb28e-132">Chaînes de format et types .NET</span><span class="sxs-lookup"><span data-stu-id="cb28e-132">Format strings and .NET types</span></span>](#format-strings-and-net-types)
    
* [<span data-ttu-id="cb28e-133">Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="cb28e-133">Culture-sensitive formatting with format providers and the IFormatProvider interface</span></span>](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [<span data-ttu-id="cb28e-134">Mise en forme dépendante de la culture des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="cb28e-134">Culture-sensitive formatting of numeric values</span></span>](#culture-sensitive-formatting-of-numeric-values)
    
    * [<span data-ttu-id="cb28e-135">Mise en forme dépendante de la culture des valeurs de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="cb28e-135">Culture-sensitive formatting of date and time values</span></span>](#culture-sensitive-formatting-of-date-and-time-values)
    
* [<span data-ttu-id="cb28e-136">Interface IFormattable</span><span class="sxs-lookup"><span data-stu-id="cb28e-136">The IFormattable interface</span></span>](#the-iformattable-interface)

* [<span data-ttu-id="cb28e-137">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="cb28e-137">Composite formatting</span></span>](#composite-formatting)

* [<span data-ttu-id="cb28e-138">Mise en forme personnalisée avec ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="cb28e-138">Custom formatting with ICustomFormatter</span></span>](#custom-formatting-with-icustomformatter)

* [<span data-ttu-id="cb28e-139">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="cb28e-139">Related topics</span></span>](#related-topics)

* [<span data-ttu-id="cb28e-140">Référence</span><span class="sxs-lookup"><span data-stu-id="cb28e-140">Reference</span></span>](#reference)

## <a name="formatting-in-net"></a><span data-ttu-id="cb28e-141">Mise en forme dans .NET</span><span class="sxs-lookup"><span data-stu-id="cb28e-141">Formatting in .NET</span></span>

<span data-ttu-id="cb28e-142">Le mécanisme de base de la mise en forme est l’implémentation par défaut de la méthode [Object.ToString](xref:System.Object.ToString), décrite dans la section [Mise en forme par défaut à l’aide de la méthode ToString](#default-formatting-using-the-tostring-method), plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-142">The basic mechanism for formatting is the default implementation of the [Object.ToString](xref:System.Object.ToString) method, which is discussed in the [Default formatting using the ToString method](#default-formatting-using-the-tostring-method) section later in this topic.</span></span> <span data-ttu-id="cb28e-143">Toutefois, .NET propose différentes manières de modifier et d’étendre sa prise en charge par défaut de la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-143">However, .NET provides several ways to modify and extend its default formatting support.</span></span> <span data-ttu-id="cb28e-144">Notamment :</span><span class="sxs-lookup"><span data-stu-id="cb28e-144">These include the following:</span></span>

* <span data-ttu-id="cb28e-145">Substitution de la méthode [Object.ToString](xref:System.Object.ToString) pour définir une représentation sous forme de chaîne personnalisée de la valeur d’un objet.</span><span class="sxs-lookup"><span data-stu-id="cb28e-145">Overriding the [Object.ToString](xref:System.Object.ToString) method to define a custom string representation of an object’s value.</span></span> <span data-ttu-id="cb28e-146">Pour plus d’informations, consultez la section [Substitution de la méthode ToString](#overriding-the-tostring-method), plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-146">For more information, see the [Overriding the ToString method](#overriding-the-tostring-method) section later in this topic.</span></span>

* <span data-ttu-id="cb28e-147">Définition de spécificateurs de format qui permettent à la représentation sous forme de chaîne de la valeur d'un objet de prendre plusieurs formes.</span><span class="sxs-lookup"><span data-stu-id="cb28e-147">Defining format specifiers that enable the string representation of an object’s value to take multiple forms.</span></span> <span data-ttu-id="cb28e-148">Par exemple, dans l'instruction suivante, le spécificateur de format "X" convertit un entier en la représentation sous forme de chaîne d'une valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="cb28e-148">For example, the "X" format specifier in the following statement converts an integer to the string representation of a hexadecimal value.</span></span>

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  <span data-ttu-id="cb28e-149">Pour plus d’informations sur les spécificateurs de format, consultez la section [Méthode ToString et chaînes de format](#the-tostring-method-and-format-strings).</span><span class="sxs-lookup"><span data-stu-id="cb28e-149">For more information about format specifiers, see the [The ToString method and format strings](#the-tostring-method-and-format-strings) section.</span></span>
  
* <span data-ttu-id="cb28e-150">Utilisation de fournisseurs de format pour tirer parti des conventions de mise en forme d'une culture spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-150">Using format providers to take advantage of the formatting conventions of a specific culture.</span></span> <span data-ttu-id="cb28e-151">Par exemple, l'instruction suivante affiche une valeur monétaire en utilisant les conventions de mise en forme de la culture en-US.</span><span class="sxs-lookup"><span data-stu-id="cb28e-151">For example, the following statement displays a currency value by using the formatting conventions of the en-US culture.</span></span> 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  <span data-ttu-id="cb28e-152">Pour plus d’informations sur la mise en forme avec des fournisseurs de format, consultez la section [Mise en forme dépendante de la culture avec les fournisseurs de format et l’interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).</span><span class="sxs-lookup"><span data-stu-id="cb28e-152">For more information about formatting with format providers, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span>  
  
* <span data-ttu-id="cb28e-153">Implémentation de l’interface [IFormattable](xref:System.IFormattable) pour prendre en charge la conversion de chaînes avec la classe [Convert](xref:System.Convert) et la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="cb28e-153">Implementing the [IFormattable](xref:System.IFormattable) interface to support both string conversion with the [Convert](xref:System.Convert) class and composite formatting.</span></span> <span data-ttu-id="cb28e-154">Pour plus d’informations, consultez la section [Interface IFormattable](#the-iformattable-interface).</span><span class="sxs-lookup"><span data-stu-id="cb28e-154">For more information, see the [The IFormattable interface](#the-iformattable-interface) section.</span></span>

* <span data-ttu-id="cb28e-155">Utilisation de la mise en forme composite pour incorporer la représentation sous forme de chaîne d'une valeur dans une chaîne plus grande.</span><span class="sxs-lookup"><span data-stu-id="cb28e-155">Using composite formatting to embed the string representation of a value in a larger string.</span></span> <span data-ttu-id="cb28e-156">Pour plus d’informations, consultez la section [Mise en forme composite](#composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="cb28e-156">For more information, see the [Composite formatting](#composite-formatting) section.</span></span>

* <span data-ttu-id="cb28e-157">Implémentation des interfaces [ICustomFormatter](xref:System.ICustomFormatter) et [IFormatProvider](xref:System.IFormatProvider) pour fournir une solution de mise en forme personnalisée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-157">Implementing [ICustomFormatter](xref:System.ICustomFormatter) and [IFormatProvider](xref:System.IFormatProvider) to provide a complete custom formatting solution.</span></span> <span data-ttu-id="cb28e-158">Pour plus d’informations, consultez la section [Mise en forme personnalisée avec ICustomFormatter](#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="cb28e-158">For more information, see the [Custom formatting with ICustomFormatter](#custom-formatting-with-icustomformatter) section.</span></span>

<span data-ttu-id="cb28e-159">Les sections suivantes étudient ces méthodes de conversion d'un objet en sa représentation sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-159">The following sections examine these methods for converting an object to its string representation.</span></span>

## <a name="default-formatting-using-the-tostring-method"></a><span data-ttu-id="cb28e-160">Mise en forme par défaut à l’aide de la méthode ToString</span><span class="sxs-lookup"><span data-stu-id="cb28e-160">Default formatting using the ToString method</span></span>

<span data-ttu-id="cb28e-161">Chaque type qui est dérivé de [System.Object](xref:System.Object) hérite automatiquement d’une méthode [ToString](xref:System.Object.ToString) sans paramètre, laquelle retourne le nom du type par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb28e-161">Every type that is derived from [System.Object](xref:System.Object) automatically inherits a parameterless [ToString](xref:System.Object.ToString) method, which returns the name of the type by default.</span></span> <span data-ttu-id="cb28e-162">L’exemple suivant illustre la méthode [ToString](xref:System.Object.ToString) par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb28e-162">The following example illustrates the default [ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="cb28e-163">Il définit une classe nommée `Automobile` qui n'a pas d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="cb28e-163">It defines a class named `Automobile` that has no implementation.</span></span> <span data-ttu-id="cb28e-164">Quand cette classe est instanciée et que sa méthode [ToString](xref:System.Object.ToString) est appelée, elle affiche son nom de type.</span><span class="sxs-lookup"><span data-stu-id="cb28e-164">When the class is instantiated and its [ToString](xref:System.Object.ToString) method is called, it displays its type name.</span></span> <span data-ttu-id="cb28e-165">Notez que la méthode [ToString](xref:System.Object.ToString) n’est pas appelée explicitement dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="cb28e-165">Note that the [ToString](xref:System.Object.ToString) method is not explicitly called in the example.</span></span> <span data-ttu-id="cb28e-166">La méthode [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) appelle implicitement la méthode [ToString](xref:System.Object.ToString) de l’objet qui lui est passé comme argument.</span><span class="sxs-lookup"><span data-stu-id="cb28e-166">The [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) method implicitly calls the [ToString](xref:System.Object.ToString) method of the object passed to it as an argument.</span></span> 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

<span data-ttu-id="cb28e-167">Étant donné que tous les types autres que les interfaces sont dérivés d’[Object](xref:System.Object), ces fonctionnalités sont fournies automatiquement à vos classes ou structures personnalisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-167">Because all types other than interfaces are derived from [Object](xref:System.Object), this functionality is automatically provided to your custom classes or structures.</span></span> <span data-ttu-id="cb28e-168">Toutefois, les fonctionnalités offertes par la méthode [ToString](xref:System.Object.ToString) par défaut sont limitées : bien qu’elle identifie le type, elle ne fournit aucune information relative à une instance du type.</span><span class="sxs-lookup"><span data-stu-id="cb28e-168">However, the functionality offered by the default [ToString](xref:System.Object.ToString) method, is limited: Although it identifies the type, it fails to provide any information about an instance of the type.</span></span> <span data-ttu-id="cb28e-169">Pour fournir une représentation sous forme de chaîne d’un objet qui donne des informations sur cet objet, vous devez substituer la méthode [ToString](xref:System.Object.ToString).</span><span class="sxs-lookup"><span data-stu-id="cb28e-169">To provide a string representation of an object that provides information about that object, you must override the [ToString](xref:System.Object.ToString) method.</span></span>

> [!NOTE]
> <span data-ttu-id="cb28e-170">Les structures héritent de [ValueType](xref:System.ValueType), qui, à son tour, est dérivé d’[Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="cb28e-170">Structures inherit from [ValueType](xref:System.ValueType), which in turn is derived from [Object](xref:System.Object).</span></span> <span data-ttu-id="cb28e-171">Bien que [ValueType](xref:System.ValueType) substitue [Object.ToString](xref:System.Object.ToString), son implémentation est identique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-171">Although [ValueType](xref:System.ValueType) overrides [Object.ToString](xref:System.Object.ToString), its implementation is identical.</span></span>

## <a name="overriding-the-tostring-method"></a><span data-ttu-id="cb28e-172">Substitution de la méthode ToString</span><span class="sxs-lookup"><span data-stu-id="cb28e-172">Overriding the ToString method</span></span>

<span data-ttu-id="cb28e-173">L'utilité de l'affichage du nom d'un type est souvent limitée et ne permet pas aux consommateurs de vos types de différencier une instance d'une autre.</span><span class="sxs-lookup"><span data-stu-id="cb28e-173">Displaying the name of a type is often of limited use and does not allow consumers of your types to differentiate one instance from another.</span></span> <span data-ttu-id="cb28e-174">Toutefois, vous pouvez substituer la méthode [ToString](xref:System.Object.ToString) pour fournir une représentation plus utile de la valeur d’un objet.</span><span class="sxs-lookup"><span data-stu-id="cb28e-174">However, you can override the [ToString](xref:System.Object.ToString) method to provide a more useful representation of an object’s value.</span></span> <span data-ttu-id="cb28e-175">L’exemple suivant définit un objet `Temperature` et substitue sa méthode [ToString](xref:System.Object.ToString) pour afficher la température en degrés Celsius.</span><span class="sxs-lookup"><span data-stu-id="cb28e-175">The following example defines a `Temperature` object and overrides its [ToString](xref:System.Object.ToString) method to display the temperature in degrees Celsius.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

<span data-ttu-id="cb28e-176">Dans .NET, la méthode [ToString](xref:System.Object.ToString) de chaque type valeur primitif a été substituée de façon à afficher la valeur de l’objet au lieu de son nom.</span><span class="sxs-lookup"><span data-stu-id="cb28e-176">In .NET, the [ToString](xref:System.Object.ToString) method of each primitive value type has been overridden to display the object’s value instead of its name.</span></span> <span data-ttu-id="cb28e-177">Le tableau suivant montre la substitution pour chaque type primitif.</span><span class="sxs-lookup"><span data-stu-id="cb28e-177">The following table shows the override for each primitive type.</span></span> <span data-ttu-id="cb28e-178">Notez que la plupart des méthodes substituées appellent une autre surcharge de la méthode [ToString](xref:System.Object.ToString) et lui passent le spécificateur de format "G", qui définit le format général pour son type, ainsi qu’un objet [IFormatProvider](xref:System.IFormatProvider) qui représente la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-178">Note that most of the overridden methods call another overload of the [ToString](xref:System.Object.ToString) method and pass it the "G" format specifier, which defines the general format for its type, and an [IFormatProvider](xref:System.IFormatProvider) object that represents the current culture.</span></span>

<span data-ttu-id="cb28e-179">Type</span><span class="sxs-lookup"><span data-stu-id="cb28e-179">Type</span></span> | <span data-ttu-id="cb28e-180">Substitution de ToString</span><span class="sxs-lookup"><span data-stu-id="cb28e-180">ToString override</span></span>
---- | -----------------
[<span data-ttu-id="cb28e-181">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb28e-181">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="cb28e-182">Retourne [Boolean.TrueString](xref:System.Boolean.TrueString) ou [Boolean.FalseString](xref:System.Boolean.FalseString).</span><span class="sxs-lookup"><span data-stu-id="cb28e-182">Returns either [Boolean.TrueString](xref:System.Boolean.TrueString) or [Boolean.FalseString](xref:System.Boolean.FalseString).</span></span>
[<span data-ttu-id="cb28e-183">Byte</span><span class="sxs-lookup"><span data-stu-id="cb28e-183">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="cb28e-184">Appelle `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Byte](xref:System.Byte) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-184">Calls `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Byte](xref:System.Byte) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-185">Char</span><span class="sxs-lookup"><span data-stu-id="cb28e-185">Char</span></span>](xref:System.Char) | <span data-ttu-id="cb28e-186">Retourne le caractère sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-186">Returns the character as a string.</span></span>
[<span data-ttu-id="cb28e-187">DateTime</span><span class="sxs-lookup"><span data-stu-id="cb28e-187">DateTime</span></span>](xref:System.DateTime) | <span data-ttu-id="cb28e-188">Appelle `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` afin de mettre en forme la valeur de date et d'heure pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-188">Calls `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` to format the date and time value for the current culture.</span></span> 
[<span data-ttu-id="cb28e-189">Decimal</span><span class="sxs-lookup"><span data-stu-id="cb28e-189">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="cb28e-190">Appelle `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Decimal](xref:System.Decimal) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-190">Calls `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Decimal](xref:System.Decimal) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-191">Double</span><span class="sxs-lookup"><span data-stu-id="cb28e-191">Double</span></span>](xref:System.Double) | <span data-ttu-id="cb28e-192">Appelle `Double.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Double](xref:System.Double) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-192">Calls `Double.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Double](xref:System.Double) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-193">Int16</span><span class="sxs-lookup"><span data-stu-id="cb28e-193">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="cb28e-194">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int16](xref:System.Int16) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-194">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int16](xref:System.Int16) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-195">Int32</span><span class="sxs-lookup"><span data-stu-id="cb28e-195">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="cb28e-196">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int32](xref:System.Int32) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-196">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int32](xref:System.Int32) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-197">Int64</span><span class="sxs-lookup"><span data-stu-id="cb28e-197">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="cb28e-198">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Int64](xref:System.Int64) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-198">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int64](xref:System.Int64) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-199">SByte</span><span class="sxs-lookup"><span data-stu-id="cb28e-199">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="cb28e-200">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [SByte](xref:System.SByte)</span><span class="sxs-lookup"><span data-stu-id="cb28e-200">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [SByte](xref:System.SByte)</span></span> | <span data-ttu-id="cb28e-201">pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-201">value for the current culture.</span></span>
[<span data-ttu-id="cb28e-202">Single</span><span class="sxs-lookup"><span data-stu-id="cb28e-202">Single</span></span>](xref:System.Single) | <span data-ttu-id="cb28e-203">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [Single](xref:System.Single) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-203">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Single](xref:System.Single) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-204">UInt32</span><span class="sxs-lookup"><span data-stu-id="cb28e-204">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="cb28e-205">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt32](xref:System.UInt32) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-205">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32)value for the current culture.</span></span>
[<span data-ttu-id="cb28e-206">UInt32</span><span class="sxs-lookup"><span data-stu-id="cb28e-206">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="cb28e-207">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt32](xref:System.UInt32) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-207">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32) value for the current culture.</span></span>
[<span data-ttu-id="cb28e-208">UInt64</span><span class="sxs-lookup"><span data-stu-id="cb28e-208">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="cb28e-209">Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur [UInt64](xref:System.UInt64) pour la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-209">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt64](xref:System.UInt64)  value for the current culture.</span></span>

## <a name="the-tostring-method-and-format-strings"></a><span data-ttu-id="cb28e-210">Méthode ToString et chaînes de format</span><span class="sxs-lookup"><span data-stu-id="cb28e-210">The ToString method and format strings</span></span>

<span data-ttu-id="cb28e-211">Le recours à la méthode [ToString](xref:System.Object.ToString) par défaut ou la substitution de [ToString](xref:System.Object.ToString) ne valent que quand un objet a une seule représentation sous forme de chaîne possible.</span><span class="sxs-lookup"><span data-stu-id="cb28e-211">Relying on the default [ToString](xref:System.Object.ToString) method or overriding [ToString](xref:System.Object.ToString) is appropriate when an object has a single string representation.</span></span> <span data-ttu-id="cb28e-212">Toutefois, la valeur d'un objet a souvent plusieurs représentations.</span><span class="sxs-lookup"><span data-stu-id="cb28e-212">However, the value of an object often has multiple representations.</span></span> <span data-ttu-id="cb28e-213">Par exemple, une température peut être exprimée en degrés Fahrenheit, Celsius ou Kelvin.</span><span class="sxs-lookup"><span data-stu-id="cb28e-213">For example, a temperature can be expressed in degrees Fahrenheit, degrees Celsius, or kelvins.</span></span> <span data-ttu-id="cb28e-214">De même, la valeur entière 10 peut être représentée de plusieurs façons, dont 10, 10,0, 1,0e01 ou $10,00.</span><span class="sxs-lookup"><span data-stu-id="cb28e-214">Similarly, the integer value 10 can be represented in numerous ways, including 10, 10.0, 1.0e01, or $10.00.</span></span>

<span data-ttu-id="cb28e-215">Pour permettre à une même valeur d’avoir plusieurs représentations sous forme de chaîne, .NET utilise des chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-215">To enable a single value to have multiple string representations, .NET uses format strings.</span></span> <span data-ttu-id="cb28e-216">Une chaîne de format est une chaîne qui contient un ou plusieurs spécificateurs de format prédéfinis, constitués d’un ou de plusieurs caractères servant à définir la manière dont la méthode [ToString](xref:System.Object.ToString) doit mettre en forme sa sortie.</span><span class="sxs-lookup"><span data-stu-id="cb28e-216">A format string is a string that contains one or more predefined format specifiers, which are single characters or groups of characters that define how the [ToString](xref:System.Object.ToString) method should format its output.</span></span> <span data-ttu-id="cb28e-217">La chaîne de format est ensuite passée comme paramètre à la méthode [ToString](xref:System.Object.ToString) de l’objet et détermine la manière dont la représentation sous forme de chaîne de la valeur de cet objet doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="cb28e-217">The format string is then passed as a parameter to the object's [ToString](xref:System.Object.ToString) method and determines how the string representation of that object's value should appear.</span></span>

<span data-ttu-id="cb28e-218">Dans .NET, tous les types numériques, types de date et d’heure et types énumération prennent en charge un jeu prédéfini de spécificateurs de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-218">All numeric types, date and time types, and enumeration types in .NET support a predefined set of format specifiers.</span></span> <span data-ttu-id="cb28e-219">Vous pouvez aussi utiliser des chaînes de format pour définir plusieurs représentations sous forme de chaîne de vos types de données définis par l'application.</span><span class="sxs-lookup"><span data-stu-id="cb28e-219">You can also use format strings to define multiple string representations of your application-defined data types.</span></span>

### <a name="standard-format-strings"></a><span data-ttu-id="cb28e-220">Chaînes de format standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-220">Standard format strings</span></span>

<span data-ttu-id="cb28e-221">Une chaîne de format standard comprend un spécificateur de format unique, qui est un caractère alphabétique définissant la représentation sous forme de chaîne de l'objet auquel il s'applique, ainsi qu'un spécificateur de précision facultatif qui affecte le nombre de chiffres affichés dans la chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="cb28e-221">A standard format string contains a single format specifier, which is an alphabetic character that defines the string representation of the object to which it is applied, along with an optional precision specifier that affects how many digits are displayed in the result string.</span></span> <span data-ttu-id="cb28e-222">Si le spécificateur de précision est omis ou n'est pas pris en charge, un spécificateur de format standard équivaut à une chaîne de format standard.</span><span class="sxs-lookup"><span data-stu-id="cb28e-222">If the precision specifier is omitted or is not supported, a standard format specifier is equivalent to a standard format string.</span></span> 

<span data-ttu-id="cb28e-223">.NET définit un jeu de spécificateurs de format standard pour tous les types numériques, types de date et d’heure et types énumération.</span><span class="sxs-lookup"><span data-stu-id="cb28e-223">.NET defines a set of standard format specifiers for all numeric types, all date and time types, and all enumeration types.</span></span> <span data-ttu-id="cb28e-224">Par exemple, chacune de ces catégories prend en charge un spécificateur de format standard "G", lequel définit une représentation sous forme de chaîne générale d'une valeur de ce type.</span><span class="sxs-lookup"><span data-stu-id="cb28e-224">For example, each of these categories supports a "G" standard format specifier, which defines a general string representation of a value of that type.</span></span>

<span data-ttu-id="cb28e-225">Les chaînes de format standard pour les types énumération contrôlent directement la représentation sous forme de chaîne d'une valeur.</span><span class="sxs-lookup"><span data-stu-id="cb28e-225">Standard format strings for enumeration types directly control the string representation of a value.</span></span> <span data-ttu-id="cb28e-226">Les chaînes de format passées à la méthode [ToString](xref:System.Object.ToString) d’une valeur d’énumération déterminent si la valeur est affichée en utilisant son nom de chaîne (spécificateurs de format "G" et "F"), sa valeur intégrale sous-jacente (spécificateur de format "D") ou sa valeur hexadécimale (spécificateur de format "X").</span><span class="sxs-lookup"><span data-stu-id="cb28e-226">The format strings passed to an enumeration value’s [ToString](xref:System.Object.ToString) method determine whether the value is displayed using its string name (the "G" and "F" format specifiers), its underlying integral value (the "D" format specifier), or its hexadecimal value (the "X" format specifier).</span></span> <span data-ttu-id="cb28e-227">L’exemple suivant illustre l’utilisation de chaînes de format standard pour mettre en forme une valeur d’énumération [DayOfWeek](xref:System.DayOfWeek).</span><span class="sxs-lookup"><span data-stu-id="cb28e-227">The following example illustrates the use of standard format strings to format a [DayOfWeek](xref:System.DayOfWeek) enumeration value.</span></span> 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

<span data-ttu-id="cb28e-228">Pour plus d’informations sur les chaînes de format d’énumération, consultez [Chaînes de format d’énumération](enumeration-format.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-228">For information about enumeration format strings, see [Enumeration format strings](enumeration-format.md).</span></span>

<span data-ttu-id="cb28e-229">Les chaînes de format standard pour les types numériques définissent généralement une chaîne de résultat dont l'apparence précise est contrôlée par une ou plusieurs valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="cb28e-229">Standard format strings for numeric types usually define a result string whose precise appearance is controlled by one or more property values.</span></span> <span data-ttu-id="cb28e-230">Par exemple, le spécificateur de format "C" met en forme un nombre en tant que valeur monétaire.</span><span class="sxs-lookup"><span data-stu-id="cb28e-230">For example, the "C" format specifier formats a number as a currency value.</span></span> <span data-ttu-id="cb28e-231">Quand vous appelez la méthode [ToString](xref:System.Object.ToString) avec, comme seul paramètre, le spécificateur de format "C", les valeurs des propriétés suivantes de l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) de la culture actuelle sont utilisées pour définir la représentation sous forme de chaîne de la valeur numérique :</span><span class="sxs-lookup"><span data-stu-id="cb28e-231">When you call the [ToString](xref:System.Object.ToString) method with the "C" format specifier as the only parameter, the following property values from the current culture’s [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object are used to define the string representation of the numeric value:</span></span>

* <span data-ttu-id="cb28e-232">Propriété [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol), qui spécifie le symbole monétaire de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-232">The [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property, which specifies the current culture’s currency symbol.</span></span>

* <span data-ttu-id="cb28e-233">Propriété [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) ou [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern), qui retourne un entier déterminant les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb28e-233">The [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) or [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) property, which returns an integer that determines the following:</span></span> 

    * <span data-ttu-id="cb28e-234">la position du symbole monétaire ;</span><span class="sxs-lookup"><span data-stu-id="cb28e-234">The placement of the currency symbol.</span></span>
    
    * <span data-ttu-id="cb28e-235">si les valeurs négatives sont indiquées par un signe négatif devant, par un signe négatif derrière ou par des parenthèses ;</span><span class="sxs-lookup"><span data-stu-id="cb28e-235">Whether negative values are indicated by a leading negative sign, a trailing negative sign, or parentheses.</span></span>
    
    * <span data-ttu-id="cb28e-236">si un espace apparaît entre la valeur numérique et le symbole monétaire.</span><span class="sxs-lookup"><span data-stu-id="cb28e-236">Whether a space appears between the numeric value and the currency symbol.</span></span>
    
* <span data-ttu-id="cb28e-237">Propriété [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits), qui définit le nombre de chiffres fractionnaires dans la chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="cb28e-237">The [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) property, which defines the number of fractional digits in the result string.</span></span>

* <span data-ttu-id="cb28e-238">Propriété [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator), qui définit le symbole de séparateur décimal dans la chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="cb28e-238">The [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property, which defines the decimal separator symbol in the result string.</span></span>

* <span data-ttu-id="cb28e-239">Propriété [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator), qui définit le symbole du séparateur de groupes.</span><span class="sxs-lookup"><span data-stu-id="cb28e-239">The [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property, which defines the group separator symbol.</span></span>

* <span data-ttu-id="cb28e-240">Propriété [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes), qui définit le nombre de chiffres de chaque groupe situé à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="cb28e-240">The [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) property, which defines the number of digits in each group to the left of the decimal.</span></span>

* <span data-ttu-id="cb28e-241">Propriété [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign), qui détermine le signe négatif utilisé dans la chaîne de résultat si les parenthèses ne sont pas utilisées pour indiquer des valeurs négatives.</span><span class="sxs-lookup"><span data-stu-id="cb28e-241">The [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) property, which determines the negative sign used in the result string if parentheses are not used to indicate negative values.</span></span>

<span data-ttu-id="cb28e-242">De plus, les chaînes de format numériques peuvent inclure un spécificateur de précision.</span><span class="sxs-lookup"><span data-stu-id="cb28e-242">In addition, numeric format strings may include a precision specifier.</span></span> <span data-ttu-id="cb28e-243">La signification de ce spécificateur dépend de la chaîne de format avec laquelle il est utilisé, mais il indique généralement le nombre total de chiffres ou le nombre de chiffres fractionnaires qui doivent s'afficher dans la chaîne de résultat.</span><span class="sxs-lookup"><span data-stu-id="cb28e-243">The meaning of this specifier depends on the format string with which it is used, but it typically indicates either the total number of digits or the number of fractional digits that should appear in the result string.</span></span> <span data-ttu-id="cb28e-244">Par exemple, le code suivant utilise la chaîne numérique standard "X4" et un spécificateur de précision pour créer une valeur de chaîne qui comprend quatre chiffres hexadécimaux.</span><span class="sxs-lookup"><span data-stu-id="cb28e-244">For example, the following example uses the "X4" standard numeric string and a precision specifier to create a string value that has four hexadecimal digits.</span></span>

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

<span data-ttu-id="cb28e-245">Pour plus d’informations sur les chaînes de format numériques standard, consultez [Chaînes de format numériques standard](standard-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-245">For more information about standard numeric formatting strings, see [Standard numeric format strings](standard-numeric.md).</span></span> 

<span data-ttu-id="cb28e-246">Les chaînes de format standard pour les valeurs de date et d’heure sont des alias de chaînes de format personnalisées stockées par une classe [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) particulière.</span><span class="sxs-lookup"><span data-stu-id="cb28e-246">Standard format strings for date and time values are aliases for custom format strings stored by a particular [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) class.</span></span> <span data-ttu-id="cb28e-247">Par exemple, appeler la méthode [ToString](xref:System.Object.ToString) d’une valeur de date et d’heure avec le spécificateur de format "D" affiche la date et l’heure en utilisant la chaîne de format personnalisée stockée dans la propriété [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-247">For example, calling the [ToString](xref:System.Object.ToString) method of a date and time value with the "D" format specifier displays the date and time by using the custom format string stored in the current culture’s [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) property.</span></span> <span data-ttu-id="cb28e-248">(Pour plus d’informations sur les chaînes de format personnalisées, consultez la section [Chaînes de format personnalisées](#custom-format-strings).) L'exemple suivant illustre cette relation.</span><span class="sxs-lookup"><span data-stu-id="cb28e-248">(For more information about custom format strings, see the [Custom format strings](#custom-format-strings) section.) The following example illustrates this relationship.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

<span data-ttu-id="cb28e-249">Pour plus d’informations sur les chaînes de format de date et d’heure standard, consultez [Chaînes de format de date et d’heure standard](standard-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-249">For more information about standard date and time format strings, see [Standard date and time format strings](standard-datetime.md).</span></span>

<span data-ttu-id="cb28e-250">Vous pouvez aussi utiliser des chaînes de format standard pour définir la représentation sous forme de chaîne produite par la méthode `ToString(String)` d'un objet défini par l'application.</span><span class="sxs-lookup"><span data-stu-id="cb28e-250">You can also use standard format strings to define the string representation of an application-defined object that is produced by the object’s `ToString(String)` method.</span></span> <span data-ttu-id="cb28e-251">Vous pouvez définir les spécificateurs de format standard spécifiques que votre objet prend en charge, et déterminer s'ils respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="cb28e-251">You can define the specific standard format specifiers that your object supports, and you can determine whether they are case-sensitive or case-insensitive.</span></span> <span data-ttu-id="cb28e-252">Votre implémentation de la méthode `ToString(String)` doit prendre en charge les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb28e-252">Your implementation of the `ToString(String)` method should support the following:</span></span>

* <span data-ttu-id="cb28e-253">Spécificateur de format "G" qui représente un format habituel ou commun de l'objet.</span><span class="sxs-lookup"><span data-stu-id="cb28e-253">A "G" format specifier that represents a customary or common format of the object.</span></span> <span data-ttu-id="cb28e-254">La surcharge sans paramètre de la méthode `ToString` de votre objet doit appeler sa surcharge `ToString(String)` et lui passer la chaîne de format standard "G".</span><span class="sxs-lookup"><span data-stu-id="cb28e-254">The parameterless overload of your object's `ToString` method should call its `ToString(String)` overload and pass it the "G" standard format string.</span></span>

* <span data-ttu-id="cb28e-255">Prise en charge d’un spécificateur de format qui est égal à une référence null.</span><span class="sxs-lookup"><span data-stu-id="cb28e-255">Support for a format specifier that is equal to a null reference.</span></span> <span data-ttu-id="cb28e-256">Un spécificateur de format qui est égal à une référence null doit être considéré comme équivalent au spécificateur de format "G".</span><span class="sxs-lookup"><span data-stu-id="cb28e-256">A format specifier that is equal to a null reference should be considered equivalent to the "G" format specifier.</span></span>

<span data-ttu-id="cb28e-257">Par exemple, une classe `Temperature` peut stocker en interne la température en degrés Celsius et utiliser des spécificateurs de format pour représenter la valeur de l'objet `Temperature` en degrés Celsius, Fahrenheit et Kelvin.</span><span class="sxs-lookup"><span data-stu-id="cb28e-257">For example, a `Temperature` class can internally store the temperature in degrees Celsius and use format specifiers to represent the value of the `Temperature` object in degrees Celsius, degrees Fahrenheit, and kelvins.</span></span> <span data-ttu-id="cb28e-258">L'exemple suivant illustre cette situation.</span><span class="sxs-lookup"><span data-stu-id="cb28e-258">The following example provides an illustration.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a><span data-ttu-id="cb28e-259">Chaînes de format personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-259">Custom format strings</span></span>

<span data-ttu-id="cb28e-260">Outre les chaînes de format standard, .NET définit des chaînes de format personnalisées pour les valeurs numériques et les valeurs de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="cb28e-260">In addition to the standard format strings, .NET defines custom format strings for both numeric values and date and time values.</span></span> <span data-ttu-id="cb28e-261">Une chaîne de format personnalisée se compose d'un ou de plusieurs spécificateurs de format personnalisés qui définissent la représentation sous forme de chaîne d'une valeur.</span><span class="sxs-lookup"><span data-stu-id="cb28e-261">A custom format string consists of one or more custom format specifiers that define the string representation of a value.</span></span> <span data-ttu-id="cb28e-262">Par exemple, la chaîne de format de date et d'heure personnalisée "yyyy\mm\dd hh:mm:ffff t zzz" convertit une date en sa représentation sous forme de chaîne "2008/11/15 07:45:00.0000 P -08:00" pour la culture en-US.</span><span class="sxs-lookup"><span data-stu-id="cb28e-262">For example, the custom date and time format string "yyyy/mm/dd hh:mm:ss.ffff t zzz" converts a date to its string representation in the form "2008/11/15 07:45:00.0000 P -08:00" for the en-US culture.</span></span> <span data-ttu-id="cb28e-263">De même, la chaîne de format personnalisée "0000" convertit la valeur entière 12 en "0012".</span><span class="sxs-lookup"><span data-stu-id="cb28e-263">Similarly, the custom format string "0000" converts the integer value 12 to "0012".</span></span> <span data-ttu-id="cb28e-264">Pour une liste complète des chaînes de format personnalisées, consultez [Chaînes de format de date et d’heure personnalisées](custom-datetime.md) et [Chaînes de format numériques personnalisées](custom-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-264">For a complete list of custom format strings, see [Custom date and time format strings](custom-datetime.md) and [Custom numeric format strings](custom-numeric.md).</span></span>

<span data-ttu-id="cb28e-265">Si une chaîne de format se compose d'un seul spécificateur de format personnalisé, le spécificateur de format doit être précédé du symbole de pourcentage (%) pour éviter toute confusion avec un spécificateur de format standard.</span><span class="sxs-lookup"><span data-stu-id="cb28e-265">If a format string consists of a single custom format specifier, the format specifier should be preceded by the percent (%) symbol to avoid confusion with a standard format specifier.</span></span> <span data-ttu-id="cb28e-266">L'exemple suivant utilise le spécificateur de format personnalisé "M" pour afficher un nombre à un chiffre ou à deux chiffres du mois d'une date particulière.</span><span class="sxs-lookup"><span data-stu-id="cb28e-266">The following example uses the "M" custom format specifier to display a one-digit or two-digit number of the month of a particular date.</span></span>

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

<span data-ttu-id="cb28e-267">De nombreuses chaînes de format standard pour les valeurs de date et d’heure sont des alias de chaînes de format personnalisées qui sont définies par les propriétés de l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo).</span><span class="sxs-lookup"><span data-stu-id="cb28e-267">Many standard format strings for date and time values are aliases for custom format strings that are defined by properties of the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> <span data-ttu-id="cb28e-268">Les chaînes de format personnalisées offrent également une souplesse considérable en matière de mise en forme définie par l'application pour les valeurs numériques ou les valeurs de date et d'heure.</span><span class="sxs-lookup"><span data-stu-id="cb28e-268">Custom format strings also offer considerable flexibility in providing application-defined formatting for numeric values or date and time values.</span></span> <span data-ttu-id="cb28e-269">Vous pouvez définir vos propres chaînes de résultat personnalisées à la fois pour les valeurs numériques et pour les valeurs de date et d'heure en combinant plusieurs spécificateurs de format personnalisés dans une chaîne de format personnalisée unique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-269">You can define your own custom result strings for both numeric values and date and time values by combining multiple custom format specifiers into a single custom format string.</span></span> <span data-ttu-id="cb28e-270">L'exemple suivant définit une chaîne de format personnalisée qui affiche le jour de la semaine entre parenthèses après le nom du mois, le jour et l'année.</span><span class="sxs-lookup"><span data-stu-id="cb28e-270">The following example defines a custom format string that displays the day of the week in parentheses after the month name, day, and year.</span></span>

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

<span data-ttu-id="cb28e-271">L’exemple ci-dessous définit une chaîne de format personnalisée qui affiche une valeur [Int64](xref:System.Int64) sous la forme d’un numéro de téléphone américain standard à sept chiffres avec son indicatif régional.</span><span class="sxs-lookup"><span data-stu-id="cb28e-271">The following example defines a custom format string that displays an [Int64](xref:System.Int64) value as a standard, seven-digit U.S. telephone number along with its area code.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

<span data-ttu-id="cb28e-272">Bien que les chaînes de format standard puissent généralement gérer la plupart des besoins de mise en forme pour vos types définis par l'application, vous pouvez également définir des spécificateurs de format personnalisés pour mettre en forme vos types.</span><span class="sxs-lookup"><span data-stu-id="cb28e-272">Although standard format strings can generally handle most of the formatting needs for your application-defined types, you may also define custom format specifiers to format your types.</span></span> 

### <a name="format-strings-and-net-types"></a><span data-ttu-id="cb28e-273">Chaînes de format et types .NET</span><span class="sxs-lookup"><span data-stu-id="cb28e-273">Format strings and .NET types</span></span>

<span data-ttu-id="cb28e-274">Tous les types numériques (à savoir les types [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) et [BigInteger](xref:System.Numerics.BigInteger)), ainsi que les types [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid) et tous les types énumération prennent en charge la mise en forme avec des chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-274">All numeric types (that is, the [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64), and [BigInteger](xref:System.Numerics.BigInteger) types), as well as the [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid), and all enumeration types, support formatting with format strings.</span></span> <span data-ttu-id="cb28e-275">Pour plus d’informations sur les chaînes de format spécifiques prises en charge par chaque type, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb28e-275">For information on the specific format strings supported by each type, see the following topics:</span></span> 

<span data-ttu-id="cb28e-276">Titre</span><span class="sxs-lookup"><span data-stu-id="cb28e-276">Title</span></span> | <span data-ttu-id="cb28e-277">Définition</span><span class="sxs-lookup"><span data-stu-id="cb28e-277">Definition</span></span>
----- | ----------
[<span data-ttu-id="cb28e-278">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-278">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="cb28e-279">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-279">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="cb28e-280">Chaînes de format numériques personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-280">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="cb28e-281">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-281">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="cb28e-282">Chaînes de format de date et d’heure standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-282">Standard date and time format strings</span></span>](standard-datetime.md) | <span data-ttu-id="cb28e-283">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="cb28e-283">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="cb28e-284">Chaînes de format de date et d’heure personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-284">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="cb28e-285">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l’application pour les valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="cb28e-285">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="cb28e-286">Chaînes de format TimeSpan standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-286">Standard TimeSpan format Strings</span></span>](standard-timespan.md) | <span data-ttu-id="cb28e-287">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.</span><span class="sxs-lookup"><span data-stu-id="cb28e-287">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="cb28e-288">Chaînes de format TimeSpan personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-288">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="cb28e-289">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.</span><span class="sxs-lookup"><span data-stu-id="cb28e-289">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="cb28e-290">Chaînes de format d’énumération</span><span class="sxs-lookup"><span data-stu-id="cb28e-290">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="cb28e-291">Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.</span><span class="sxs-lookup"><span data-stu-id="cb28e-291">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
<span data-ttu-id="cb28e-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span><span class="sxs-lookup"><span data-stu-id="cb28e-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span></span> | <span data-ttu-id="cb28e-293">Décrit les chaînes de format standard pour les valeurs [Guid](xref:System.Guid).</span><span class="sxs-lookup"><span data-stu-id="cb28e-293">Describes standard format strings for [Guid](xref:System.Guid) values.</span></span>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a><span data-ttu-id="cb28e-294">Mise en forme dépendante de la culture avec les fournisseurs de format et l'interface IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="cb28e-294">Culture-Sensitive Formatting with Format Providers and the IFormatProvider Interface</span></span>

<span data-ttu-id="cb28e-295">Si les spécificateurs de format vous permettent de personnaliser la mise en forme d'objets, la production, pour ces derniers, d'une représentation sous forme de chaîne explicite requiert souvent des informations de mise en forme supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cb28e-295">Although format specifiers let you customize the formatting of objects, producing a meaningful string representation of objects often requires additional formatting information.</span></span> <span data-ttu-id="cb28e-296">Par exemple, la mise en forme d'un nombre en tant que valeur monétaire en utilisant la chaîne de format standard "C" ou une chaîne de format personnalisée telle que "$ #, #.00" requiert au minimum l'existence d'informations à inclure dans la chaîne mise en forme concernant le symbole monétaire, le séparateur de groupes et le séparateur décimal appropriés.</span><span class="sxs-lookup"><span data-stu-id="cb28e-296">For example, formatting a number as a currency value by using either the "C" standard format string or a custom format string such as "$ #,#.00" requires, at a minimum, information about the correct currency symbol, group separator, and decimal separator to be available to include in the formatted string.</span></span> <span data-ttu-id="cb28e-297">Dans .NET, ces informations de mise en forme supplémentaires sont disponibles via l’interface [IFormatProvider](xref:System.IFormatProvider), laquelle est fournie comme paramètre à une ou plusieurs surcharges de la méthode `ToString` de types numériques et de types de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="cb28e-297">In .NET, this additional formatting information is made available through the [IFormatProvider](xref:System.IFormatProvider) interface, which is provided as a parameter to one or more overloads of the `ToString` method of numeric types and date and time types.</span></span> <span data-ttu-id="cb28e-298">Des implémentations de l’interface [IFormatProvider](xref:System.IFormatProvider) sont utilisées dans .NET pour prendre en charge la mise en forme spécifique à la culture.</span><span class="sxs-lookup"><span data-stu-id="cb28e-298">[IFormatProvider](xref:System.IFormatProvider) implementations are used in .NET to support culture-specific formatting.</span></span> <span data-ttu-id="cb28e-299">L’exemple suivant montre comment la représentation d’un objet sous forme de chaîne évolue quand il est mis en forme avec trois objets [IFormatProvider](xref:System.IFormatProvider) représentant des cultures différentes.</span><span class="sxs-lookup"><span data-stu-id="cb28e-299">The following example illustrates how the string representation of an object changes when it is formatted with three [IFormatProvider](xref:System.IFormatProvider) objects that represent different cultures.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

<span data-ttu-id="cb28e-300">L’interface [IFormatProvider](xref:System.IFormatProvider) inclut une méthode, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), qui a un seul paramètre spécifiant le type d’objet qui fournit les informations de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-300">The [IFormatProvider](xref:System.IFormatProvider) interface includes one method, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), which has a single parameter that specifies the type of object that provides formatting information.</span></span> <span data-ttu-id="cb28e-301">Si la méthode peut fournir un objet de ce type, elle le retourne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-301">If the method can provide an object of that type, it returns it.</span></span> <span data-ttu-id="cb28e-302">Autrement, elle retourne une référence Null.</span><span class="sxs-lookup"><span data-stu-id="cb28e-302">Otherwise, it returns a null reference.</span></span>

<span data-ttu-id="cb28e-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) est une méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="cb28e-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) is a callback method.</span></span> <span data-ttu-id="cb28e-304">Quand vous appelez une surcharge de méthode `ToString` qui inclut un paramètre [IFormatProvider](xref:System.IFormatProvider), elle appelle la méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) de cet objet [IFormatProvider](xref:System.IFormatProvider).</span><span class="sxs-lookup"><span data-stu-id="cb28e-304">When you call a `ToString` method overload that includes an [IFormatProvider](xref:System.IFormatProvider) parameter, it calls the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method of that [IFormatProvider](xref:System.IFormatProvider) object.</span></span> <span data-ttu-id="cb28e-305">La méthode [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) est chargée de retourner les informations de mise en forme requises, spécifiées par son paramètre *formatType*, à la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-305">The [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method is responsible for returning an object that provides the necessary formatting information, as specified by its *formatType* parameter, to the `ToString` method.</span></span> 

<span data-ttu-id="cb28e-306">Certaines méthodes de mise en forme ou de conversion de chaînes incluent un paramètre de type [IFormatProvider](xref:System.IFormatProvider), mais la valeur de ce paramètre est souvent ignorée quand la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-306">A number of formatting or string conversion methods include a parameter of type [IFormatProvider](xref:System.IFormatProvider), but in many cases the value of the parameter is ignored when the method is called.</span></span> <span data-ttu-id="cb28e-307">Le tableau suivant répertorie certaines des méthodes de mise en forme qui utilisent le paramètre et le type de l’objet [Type](xref:System.Type) qu’elles passent à la méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)).</span><span class="sxs-lookup"><span data-stu-id="cb28e-307">The following table lists some of the formatting methods that use the parameter and the type of the [Type](xref:System.Type) object that they pass to the [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method.</span></span> 

<span data-ttu-id="cb28e-308">Méthode</span><span class="sxs-lookup"><span data-stu-id="cb28e-308">Method</span></span> | <span data-ttu-id="cb28e-309">Type de paramètre *formatType*</span><span class="sxs-lookup"><span data-stu-id="cb28e-309">Type of *formatType* parameter</span></span>
------ | ------------------------------
<span data-ttu-id="cb28e-310">Méthode `ToString` de types numériques</span><span class="sxs-lookup"><span data-stu-id="cb28e-310">`ToString` method of numeric types</span></span> | [<span data-ttu-id="cb28e-311">System.Globalization.NumberFormatInfo</span><span class="sxs-lookup"><span data-stu-id="cb28e-311">System.Globalization.NumberFormatInfo</span></span>](xref:System.Globalization.NumberFormatInfo)
<span data-ttu-id="cb28e-312">Méthode `ToString` de types de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="cb28e-312">`ToString` method of date and time types</span></span> | [<span data-ttu-id="cb28e-313">System.Globalization.DateTimeFormatInfo</span><span class="sxs-lookup"><span data-stu-id="cb28e-313">System.Globalization.DateTimeFormatInfo</span></span>](xref:System.Globalization.DateTimeFormatInfo)
<span data-ttu-id="cb28e-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="cb28e-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="cb28e-315">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="cb28e-315">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)
<span data-ttu-id="cb28e-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="cb28e-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="cb28e-317">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="cb28e-317">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

<span data-ttu-id="cb28e-318">.NET propose trois classes qui implémentent [IFormatProvider](xref:System.IFormatProvider) :</span><span class="sxs-lookup"><span data-stu-id="cb28e-318">.NET provides three classes that implement [IFormatProvider](xref:System.IFormatProvider):</span></span> 

* <span data-ttu-id="cb28e-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), une classe qui fournit des informations de mise en forme pour les valeurs de date et d’heure pour une culture spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), a class that provides formatting information for date and time values for a specific culture.</span></span> <span data-ttu-id="cb28e-320">Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne une instance d’elle-même.</span><span class="sxs-lookup"><span data-stu-id="cb28e-320">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="cb28e-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), une classe qui fournit des informations de mise en forme des nombres pour une culture spécifique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a class that provides numeric formatting information for a specific culture.</span></span> <span data-ttu-id="cb28e-322">Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne une instance d’elle-même.</span><span class="sxs-lookup"><span data-stu-id="cb28e-322">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="cb28e-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span><span class="sxs-lookup"><span data-stu-id="cb28e-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span></span> <span data-ttu-id="cb28e-324">Son implémentation d’[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) peut retourner un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour fournir des informations de mise en forme des nombres ou un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) pour fournir des informations de mise en forme des valeurs de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="cb28e-324">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation can return either a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to provide numeric formatting information or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object to provide formatting information for date and time values.</span></span> 

<span data-ttu-id="cb28e-325">Vous pouvez aussi implémenter votre propre fournisseur de format en remplacement de l'une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="cb28e-325">You can also implement your own format provider to replace any one of these classes.</span></span> <span data-ttu-id="cb28e-326">Toutefois, la méthode `GetFormat` de votre implémentation doit retourner un objet du type répertorié dans le tableau précédent s'il doit fournir des informations de mise en forme à la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-326">However, your implementation’s `GetFormat` method must return an object of the type listed in the previous table if it has to provide formatting information to the `ToString` method.</span></span>

### <a name="culture-sensitive-formatting-of-numeric-values"></a><span data-ttu-id="cb28e-327">Mise en forme dépendante de la culture des valeurs numériques</span><span class="sxs-lookup"><span data-stu-id="cb28e-327">Culture-sensitive formatting of numeric values</span></span>

<span data-ttu-id="cb28e-328">Par défaut, la mise en forme des valeurs numériques est dépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="cb28e-328">By default, the formatting of numeric values is culture-sensitive.</span></span> <span data-ttu-id="cb28e-329">Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-329">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="cb28e-330">Ceci est illustré dans l’exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) soit appelée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-330">This is illustrated in the following example, which changes the current thread culture four times and then calls the [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) method.</span></span> <span data-ttu-id="cb28e-331">Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-331">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="cb28e-332">Ceci tient au fait que les méthodes `ToString` et `ToString(String)` encapsulent les appels à la méthode `ToString(String, IFormatProvider)` de chaque type numérique.</span><span class="sxs-lookup"><span data-stu-id="cb28e-332">This is because the `ToString` and `ToString(String)` methods wrap calls to each numeric type's `ToString(String, IFormatProvider)` method.</span></span> 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

<span data-ttu-id="cb28e-333">Vous pouvez également mettre en forme une valeur numérique pour une culture spécifique en appelant une surcharge `ToString` dotée d’un paramètre de *fournisseur* et en lui passant l’un ou l’autre des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb28e-333">You can also format a numeric value for a specific culture by calling a `ToString` overload that has a *provider* parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="cb28e-334">Un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont les conventions de mise en forme doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-334">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="cb28e-335">Sa méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne la valeur de la propriété [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), qui est l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui fournit des informations de mise en forme propres à la culture pour les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-335">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="cb28e-336">Un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) définissant les conventions de mise en forme propres à la culture qui doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-336">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="cb28e-337">Sa méthode [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retourne une instance d’elle-même.</span><span class="sxs-lookup"><span data-stu-id="cb28e-337">Its [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="cb28e-338">L’exemple suivant utilise des objets [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui représentent les cultures Anglais (États-Unis) et Anglais (Royaume-Uni), ainsi que les cultures neutres Français et Russe pour mettre en forme un nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="cb28e-338">The following example uses [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a floating-point number.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a><span data-ttu-id="cb28e-339">Mise en forme dépendante de la culture des valeurs de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="cb28e-339">Culture-sensitive formatting of date and time values</span></span>

<span data-ttu-id="cb28e-340">Par défaut, la mise en forme des valeurs de date et d'heure est dépendante de la culture.</span><span class="sxs-lookup"><span data-stu-id="cb28e-340">By default, the formatting of date and time values is culture-sensitive.</span></span> <span data-ttu-id="cb28e-341">Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-341">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="cb28e-342">Ceci est illustré dans l’exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) soit appelée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-342">This is illustrated in the following example, which changes the current thread culture four times and then calls the [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) method.</span></span> <span data-ttu-id="cb28e-343">Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="cb28e-343">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="cb28e-344">En effet, les méthodes [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) et [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) incluent les appels aux méthodes [DateTime.ToString (String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) et [DateTimeOffset.ToString (String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) dans un wrapper.</span><span class="sxs-lookup"><span data-stu-id="cb28e-344">This is because the [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)), and [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) methods wrap calls to the [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) methods.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

<span data-ttu-id="cb28e-345">Vous pouvez également mettre en forme une valeur de date et d’heure pour une culture spécifique en appelant une surcharge [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) dotée d’un paramètre de fournisseur et en lui passant l’un ou l’autre des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb28e-345">You can also format a date and time value for a specific culture by calling a [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) overload that has a provider parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="cb28e-346">Un objet [CultureInfo](xref:System.Globalization.CultureInfo) représentant la culture dont les conventions de mise en forme doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-346">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="cb28e-347">Sa méthode [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retourne la valeur de la propriété [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), qui est l’objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui fournit des informations de mise en forme propres à la culture pour les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-347">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="cb28e-348">Un objet [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) définissant les conventions de mise en forme propres à la culture qui doivent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="cb28e-348">A [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="cb28e-349">Sa méthode [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) retourne une instance d’elle-même.</span><span class="sxs-lookup"><span data-stu-id="cb28e-349">Its [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="cb28e-350">L’exemple suivant utilise des objets [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) qui représentent les cultures Anglais (États-Unis) et Anglais (Royaume-Uni), ainsi que les cultures neutres Français et Russe pour mettre en forme une date.</span><span class="sxs-lookup"><span data-stu-id="cb28e-350">The following example uses [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a date.</span></span> 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a><span data-ttu-id="cb28e-351">Interface IFormattable</span><span class="sxs-lookup"><span data-stu-id="cb28e-351">The IFormattable interface</span></span>

<span data-ttu-id="cb28e-352">En règle générale, les types qui surchargent la méthode `ToString` avec une chaîne de format et un paramètre [IFormatProvider](xref:System.IFormatProvider) implémentent également l’interface [IFormattable](xref:System.IFormattable).</span><span class="sxs-lookup"><span data-stu-id="cb28e-352">Typically, types that overload the `ToString` method with a format string and an [IFormatProvider](xref:System.IFormatProvider) parameter also implement the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="cb28e-353">Cette interface comprend un seul membre, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), qui inclut comme paramètres une chaîne de format et un fournisseur de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-353">This interface has a single member, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), that includes both a format string and a format provider as parameters.</span></span>

<span data-ttu-id="cb28e-354">L’implémentation de l’interface [IFormattable](xref:System.IFormattable) pour votre classe définie par l’application présente deux avantages :</span><span class="sxs-lookup"><span data-stu-id="cb28e-354">Implementing the [IFormattable](xref:System.IFormattable) interface for your application-defined class offers two advantages:</span></span> 

* <span data-ttu-id="cb28e-355">Prise en charge de la conversion de chaînes par la classe [Convert](xref:System.Convert).</span><span class="sxs-lookup"><span data-stu-id="cb28e-355">Support for string conversion by the [Convert](xref:System.Convert) class.</span></span> <span data-ttu-id="cb28e-356">Les appels aux méthodes [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) et [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) appellent automatiquement votre implémentation d’[IFormattable](xref:System.IFormattable).</span><span class="sxs-lookup"><span data-stu-id="cb28e-356">Calls to the [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) and [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) methods call your [IFormattable](xref:System.IFormattable) implementation automatically.</span></span>

* <span data-ttu-id="cb28e-357">Prise en charge de la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="cb28e-357">Support for composite formatting.</span></span> <span data-ttu-id="cb28e-358">Si un élément de mise en forme qui inclut une chaîne de format est utilisé pour mettre en forme votre type personnalisé, le Common Language Runtime appelle automatiquement votre implémentation d’[IFormattable](xref:System.IFormattable) et lui passe la chaîne de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-358">If a format item that includes a format string is used to format your custom type, the Common Language Runtime automatically calls your [IFormattable](xref:System.IFormattable) implementation and passes it the format string.</span></span> <span data-ttu-id="cb28e-359">Pour plus d’informations sur la mise en forme composite avec des méthodes telles que `String.Format` ou `Console.WriteLine`, consultez la section [Mise en forme composite](#composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="cb28e-359">For more information about composite formatting with methods such as `String.Format` or `Console.WriteLine`, see the [Composite formatting](#composite-formatting) section.</span></span>

<span data-ttu-id="cb28e-360">L’exemple suivant définit une classe `Temperature` qui implémente l’interface [IFormattable](xref:System.IFormattable).</span><span class="sxs-lookup"><span data-stu-id="cb28e-360">The following example defines a `Temperature` class that implements the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="cb28e-361">Il prend en charge les spécificateurs de format "C" ou "G" pour afficher la température en Celsius, le spécificateur de format "F" pour afficher la température en Fahrenheit et le spécificateur de format "K" pour afficher la température en Kelvin.</span><span class="sxs-lookup"><span data-stu-id="cb28e-361">It supports the "C" or "G" format specifiers to display the temperature in Celsius, the "F" format specifier to display the temperature in Fahrenheit, and the "K" format specifier to display the temperature in Kelvin.</span></span>

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

<span data-ttu-id="cb28e-362">L'exemple suivant instancie un objet `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-362">The following example instantiates a `Temperature` object.</span></span> <span data-ttu-id="cb28e-363">Il appelle ensuite la méthode [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) et utilise plusieurs chaînes de format composites pour obtenir des représentations sous forme de chaîne différentes d’un objet `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-363">It then calls the [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) method and uses several composite format strings to obtain different string representations of a `Temperature` object.</span></span> <span data-ttu-id="cb28e-364">Chacun de ces appels de méthode appelle, à son tour, l’implémentation d’[IFormattable](xref:System.IFormattable) de la classe `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-364">Each of these method calls, in turn, calls the [IFormattable](xref:System.IFormattable) implementation of the `Temperature` class.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a><span data-ttu-id="cb28e-365">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="cb28e-365">Composite formatting</span></span>

<span data-ttu-id="cb28e-366">Certaines méthodes, telles que `String.Format` et `StringBuilder.AppendFormat`, prennent en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="cb28e-366">Some methods, such as `String.Format` and `StringBuilder.AppendFormat`, support composite formatting.</span></span> <span data-ttu-id="cb28e-367">Une chaîne de format composite est un genre de modèle retournant une seule chaîne qui incorpore la représentation sous forme de chaîne de zéro, un ou plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="cb28e-367">A composite format string is a kind of template that returns a single string that incorporates the string representation of zero, one, or more objects.</span></span> <span data-ttu-id="cb28e-368">Chaque objet est représenté dans la chaîne de format composite par un élément de mise en forme indexé.</span><span class="sxs-lookup"><span data-stu-id="cb28e-368">Each object is represented in the composite format string by an indexed format item.</span></span> <span data-ttu-id="cb28e-369">L'index de l'élément de mise en forme correspond à la position de l'objet qu'il représente dans la liste de paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="cb28e-369">The index of the format item corresponds to the position of the object that it represents in the method's parameter list.</span></span> <span data-ttu-id="cb28e-370">Les index sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="cb28e-370">Indexes are zero-based.</span></span> <span data-ttu-id="cb28e-371">Par exemple, dans l'appel suivant à la méthode `String.Format`, le premier élément de mise en forme, `{0:D}`, est remplacé par la représentation sous forme de chaîne de `thatDate` ; le deuxième élément de mise en forme, `{1}`, est remplacé par la représentation sous forme de chaîne `item1` ; le troisième élément de mise en forme, `{2:C2}`, est remplacé par la représentation sous forme de chaîne de `item1.Value`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-371">For example, in the following call to the `String.Format` method, the first format item, `{0:D}`, is replaced by the string representation of `thatDate`; the second format item, `{1}`, is replaced by the string representation of `item1`; and the third format item, `{2:C2}`, is replaced by the string representation of `item1.Value`.</span></span>

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

<span data-ttu-id="cb28e-372">En plus de remplacer un élément de format par la représentation sous forme de chaîne de l'objet correspondant, les éléments de format vous permettent également de contrôler les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cb28e-372">In addition to replacing a format item with the string representation of its corresponding object, format items also let you control the following:</span></span> 

* <span data-ttu-id="cb28e-373">La façon spécifique dont un objet est représenté sous forme de chaîne, si l’objet implémente l’interface [IFormattable](xref:System.IFormattable) et prend en charge les chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="cb28e-373">The specific way in which an object is represented as a string, if the object implements the [IFormattable](xref:System.IFormattable) interface and supports format strings.</span></span> <span data-ttu-id="cb28e-374">Ceci se fait en faisant suivre l’index de l’élément de format d’un caractère « : » (deux-points), suivi d’une chaîne de format valide.</span><span class="sxs-lookup"><span data-stu-id="cb28e-374">You do this by following the format item's index with a : (colon) followed by a valid format string.</span></span> <span data-ttu-id="cb28e-375">L’exemple précédent a fait cela en mettant en forme une valeur de date avec la chaîne de format "d" (modèle de date courte) (par exemple `{0:d}`) et en mettant en forme une valeur numérique avec la chaîne de format "C2" (par exemple `{2:C2}` pour représenter le nombre comme valeur monétaire avec deux décimales).</span><span class="sxs-lookup"><span data-stu-id="cb28e-375">The previous example did this by formatting a date value with the "d" (short date pattern) format string (for example, `{0:d}`) and by formatting a numeric value with the "C2" format string (for example, `{2:C2}` to represent the number as a currency value with two fractional decimal digits).</span></span> 

* <span data-ttu-id="cb28e-376">La largeur du champ qui contient la représentation sous forme de chaîne de l'objet, et l'alignement de la représentation sous forme de chaîne de ce champ.</span><span class="sxs-lookup"><span data-stu-id="cb28e-376">The width of the field that contains the object's string representation, and the alignment of the string representation in that field.</span></span> <span data-ttu-id="cb28e-377">Ceci se fait en faisant suivre l’index de l’élément de format d’un caractère « , » (virgule), suivie de la largeur du champ.</span><span class="sxs-lookup"><span data-stu-id="cb28e-377">You do this by following the format item's index with a , (comma) followed the field width.</span></span> <span data-ttu-id="cb28e-378">La chaîne est alignée à droite dans le champ si la largeur du champ est une valeur positive, et elle est alignée à gauche si la largeur du champ est une valeur négative.</span><span class="sxs-lookup"><span data-stu-id="cb28e-378">The string is right-aligned in the field if the field width is a positive value, and it is left-aligned if the field width is a negative value.</span></span> <span data-ttu-id="cb28e-379">L'exemple suivant aligne à gauche des valeurs de date dans un champ de 20 caractères, et aligne à droite des valeurs décimales avec une décimale dans un champ de 11 caractères.</span><span class="sxs-lookup"><span data-stu-id="cb28e-379">The following example left-aligns date values in a 20-character field, and it right-aligns decimal values with one fractional digit in an 11-character field.</span></span> 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

<span data-ttu-id="cb28e-380">Notez que si le composant de chaîne d'alignement et le composant de chaîne de format sont présents, le premier a priorité sur le deuxième (par exemple `{0,-20:g}`.</span><span class="sxs-lookup"><span data-stu-id="cb28e-380">Note that, if both the alignment string component and the format string component are present, the former precedes the latter (for example, `{0,-20:g}`.</span></span> 

<span data-ttu-id="cb28e-381">Pour plus d’informations sur la mise en forme composite, consultez [Mise en forme composite](composite-format.md).</span><span class="sxs-lookup"><span data-stu-id="cb28e-381">For more information about composite formatting, see [Composite formatting](composite-format.md).</span></span>

## <a name="custom-formatting-with-icustomformatter"></a><span data-ttu-id="cb28e-382">Mise en forme personnalisée avec ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="cb28e-382">Custom formatting with ICustomFormatter</span></span>

<span data-ttu-id="cb28e-383">Deux méthodes de mise en forme composites, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) et [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), incluent un paramètre de fournisseur de format qui prend en charge la mise en forme personnalisée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-383">Two composite formatting methods, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) and [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), include a format provider parameter that supports custom formatting.</span></span> <span data-ttu-id="cb28e-384">Quand l’une de ces méthodes de mise en forme est appelée, elle passe à la méthode `GetFormat` du fournisseur de format un objet [Type](xref:System.Type) qui représente une interface [ICustomFormatter](xref:System.ICustomFormatter).</span><span class="sxs-lookup"><span data-stu-id="cb28e-384">When either of these formatting methods is called, it passes a [Type](xref:System.Type) object that represents an [ICustomFormatter](xref:System.ICustomFormatter) interface to the format provider’s `GetFormat` method.</span></span> <span data-ttu-id="cb28e-385">La méthode `GetFormat` est alors chargée de retourner l’implémentation d’[ICustomFormatter](xref:System.ICustomFormatter) qui fournit la mise en forme personnalisée.</span><span class="sxs-lookup"><span data-stu-id="cb28e-385">The `GetFormat` method is then responsible for returning the [ICustomFormatter](xref:System.ICustomFormatter) implementation that provides custom formatting.</span></span>

<span data-ttu-id="cb28e-386">L’interface [ICustomFormatter](xref:System.ICustomFormatter) a une méthode unique, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), qui est appelée automatiquement par une méthode de mise en forme composite, une fois pour chaque élément de mise en forme dans une chaîne de format composite.</span><span class="sxs-lookup"><span data-stu-id="cb28e-386">The [ICustomFormatter](xref:System.ICustomFormatter) interface has a single method, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), that is called automatically by a composite formatting method, once for each format item in a composite format string.</span></span> <span data-ttu-id="cb28e-387">La méthode [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) a trois paramètres : une chaîne de format, qui représente l’argument *formatString* dans un élément de mise en forme, un objet à mettre en forme et un objet [IFormatProvider](xref:System.IFormatProvider) qui fournit des services de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-387">The [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method has three parameters: a format string, which represents the *formatString* argument in a format item, an object to format, and an [IFormatProvider](xref:System.IFormatProvider) object that provides formatting services.</span></span> <span data-ttu-id="cb28e-388">En général, la classe qui implémente [ICustomFormatter](xref:System.ICustomFormatter) implémente également [IFormatProvider](xref:System.IFormatProvider) ; ce dernier paramètre est donc une référence à la classe de mise en forme personnalisée elle-même.</span><span class="sxs-lookup"><span data-stu-id="cb28e-388">Typically, the class that implements [ICustomFormatter](xref:System.ICustomFormatter) also implements [IFormatProvider](xref:System.IFormatProvider), so this last parameter is a reference to the custom formatting class itself.</span></span> <span data-ttu-id="cb28e-389">La méthode retourne une représentation sous forme de chaîne mise en forme personnalisée de l'objet à mettre en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-389">The method returns a custom formatted string representation of the object to be formatted.</span></span> <span data-ttu-id="cb28e-390">Si la méthode ne peut pas mettre en forme l’objet, elle doit retourner une référence null.</span><span class="sxs-lookup"><span data-stu-id="cb28e-390">If the method cannot format the object, it should return a null reference.</span></span>

<span data-ttu-id="cb28e-391">L’exemple suivant fournit une implémentation d’[ICustomFormatter](xref:System.ICustomFormatter) nommée `ByteByByteFormatter` qui affiche des valeurs entières sous la forme d’une séquence de valeurs hexadécimales à deux chiffres suivie d’un espace.</span><span class="sxs-lookup"><span data-stu-id="cb28e-391">The following example provides an [ICustomFormatter](xref:System.ICustomFormatter) implementation named `ByteByByteFormatter` that displays integer values as a sequence of two-digit hexadecimal values followed by a space.</span></span>

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

<span data-ttu-id="cb28e-392">L'exemple suivant utilise la classe `ByteByByteFormatter` pour mettre en forme des valeurs entières.</span><span class="sxs-lookup"><span data-stu-id="cb28e-392">The following example uses the `ByteByByteFormatter` class to format integer values.</span></span> <span data-ttu-id="cb28e-393">Notez que la méthode [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) est appelée plusieurs fois dans le deuxième appel de méthode [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), et que le fournisseur [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) par défaut est utilisé dans le troisième appel de méthode, car la méthode `.ByteByByteFormatter.Format` ne reconnaît pas la chaîne de format "N0" et retourne une référence null.</span><span class="sxs-lookup"><span data-stu-id="cb28e-393">Note that the [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method is called more than once in the second [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method call, and that the default [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) provider is used in the third method call because the `.ByteByByteFormatter.Format` method does not recognize the "N0" format string and returns a null reference.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a><span data-ttu-id="cb28e-394">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="cb28e-394">Related topics</span></span>

<span data-ttu-id="cb28e-395">Titre</span><span class="sxs-lookup"><span data-stu-id="cb28e-395">Title</span></span> | <span data-ttu-id="cb28e-396">Définition</span><span class="sxs-lookup"><span data-stu-id="cb28e-396">Definition</span></span>
----- | ----------
[<span data-ttu-id="cb28e-397">Chaînes de format numériques standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-397">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="cb28e-398">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-398">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="cb28e-399">Chaînes de format numériques personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-399">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="cb28e-400">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-400">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="cb28e-401">Chaînes de format de date et d’heure standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-401">Standard date and time format strings</span></span>](standard-datetime.md) |  <span data-ttu-id="cb28e-402">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="cb28e-402">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="cb28e-403">Chaînes de format de date et d’heure personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-403">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="cb28e-404">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l’application pour les valeurs [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="cb28e-404">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="cb28e-405">Chaînes de format TimeSpan standard</span><span class="sxs-lookup"><span data-stu-id="cb28e-405">Standard TimeSpan format strings</span></span>](standard-timespan.md) | <span data-ttu-id="cb28e-406">Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.</span><span class="sxs-lookup"><span data-stu-id="cb28e-406">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="cb28e-407">Chaînes de format TimeSpan personnalisées</span><span class="sxs-lookup"><span data-stu-id="cb28e-407">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="cb28e-408">Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.</span><span class="sxs-lookup"><span data-stu-id="cb28e-408">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="cb28e-409">Chaînes de format d’énumération</span><span class="sxs-lookup"><span data-stu-id="cb28e-409">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="cb28e-410">Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.</span><span class="sxs-lookup"><span data-stu-id="cb28e-410">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
[<span data-ttu-id="cb28e-411">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="cb28e-411">Composite formatting</span></span>](composite-format.md) | <span data-ttu-id="cb28e-412">Explique comment incorporer une ou plusieurs valeurs mises en forme dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="cb28e-412">Describes how to embed one or more formatted values in a string.</span></span> <span data-ttu-id="cb28e-413">La chaîne peut ensuite être affichée dans la console ou écrite dans un flux.</span><span class="sxs-lookup"><span data-stu-id="cb28e-413">The string can subsequently be displayed on the console or written to a stream.</span></span>
[<span data-ttu-id="cb28e-414">Exécution d’opérations de mise en forme</span><span class="sxs-lookup"><span data-stu-id="cb28e-414">Performing formatting operations</span></span>](performing-formatting-operations.md) | <span data-ttu-id="cb28e-415">Répertorie les rubriques qui fournissent des instructions pas à pas pour effectuer des opérations de mise en forme spécifiques.</span><span class="sxs-lookup"><span data-stu-id="cb28e-415">Lists topics that provide step-by-step instructions for performing specific formatting operations.</span></span>
[<span data-ttu-id="cb28e-416">Analyse de chaînes</span><span class="sxs-lookup"><span data-stu-id="cb28e-416">Parsing strings</span></span>](parsing-strings.md) | <span data-ttu-id="cb28e-417">Décrit comment initialiser des objets aux valeurs décrites par des représentations sous forme de chaîne de ces objets.</span><span class="sxs-lookup"><span data-stu-id="cb28e-417">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="cb28e-418">L'analyse est l'opération inverse de la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="cb28e-418">Parsing is the inverse operation of formatting.</span></span>

## <a name="reference"></a><span data-ttu-id="cb28e-419">Référence</span><span class="sxs-lookup"><span data-stu-id="cb28e-419">Reference</span></span>

[<span data-ttu-id="cb28e-420">System.IFormattable</span><span class="sxs-lookup"><span data-stu-id="cb28e-420">System.IFormattable</span></span>](xref:System.IFormattable)

[<span data-ttu-id="cb28e-421">System.IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="cb28e-421">System.IFormatProvider</span></span>](xref:System.IFormatProvider)

[<span data-ttu-id="cb28e-422">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="cb28e-422">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

