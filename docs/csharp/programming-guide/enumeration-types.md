---
title: "Types énumération (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 677de7c6e0c0f72b600ce8ee5a8bad265725f6d3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="16e56-102">Types énumération (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="16e56-102">Enumeration Types (C# Programming Guide)</span></span>
<span data-ttu-id="16e56-103">Un type énumération (également appelé énumération ou enum) offre un moyen efficace de définir un ensemble de constantes intégrales nommées qui peuvent être assignées à une variable.</span><span class="sxs-lookup"><span data-stu-id="16e56-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="16e56-104">Par exemple, supposez que vous devez définir une variable dont la valeur représente un jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="16e56-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="16e56-105">Il n’y a que sept valeurs significatives qui pourront être stockées par cette variable.</span><span class="sxs-lookup"><span data-stu-id="16e56-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="16e56-106">Pour définir ces valeurs, vous pouvez utiliser un type énumération, qui est déclaré à l’aide du mot clé [enum](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="16e56-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>  
  
 <span data-ttu-id="16e56-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span></span>  
  
 <span data-ttu-id="16e56-108">Par défaut, le type sous-jacent de chaque élément dans l’énumération est [int](../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="16e56-108">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="16e56-109">Vous pouvez spécifier un autre type numérique intégral à l’aide d’un signe deux-points, comme illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="16e56-109">You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="16e56-110">Pour obtenir une liste complète des types possibles, consultez [enum (référence C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="16e56-110">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="16e56-111">Vous pouvez vérifier les valeurs numériques sous-jacentes en effectuant un cast sur le type sous-jacent, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="16e56-111">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>  
  
```csharp  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 <span data-ttu-id="16e56-112">Voici les avantages qu’offre l’utilisation d’un enum par rapport à un type numérique :</span><span class="sxs-lookup"><span data-stu-id="16e56-112">The following are advantages of using an enum instead of a numeric type:</span></span>  
  
-   <span data-ttu-id="16e56-113">Vous spécifiez clairement pour le code client les valeurs qui sont valides pour la variable.</span><span class="sxs-lookup"><span data-stu-id="16e56-113">You clearly specify for client code which values are valid for the variable.</span></span>  
  
-   <span data-ttu-id="16e56-114">Dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense répertorie les valeurs définies.</span><span class="sxs-lookup"><span data-stu-id="16e56-114">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>  
  
 <span data-ttu-id="16e56-115">Quand vous ne spécifiez pas de valeurs pour les éléments dans la liste d’énumérateurs, les valeurs sont automatiquement incrémentées de 1.</span><span class="sxs-lookup"><span data-stu-id="16e56-115">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="16e56-116">Dans l’exemple précédent, `Days.Sunday` a la valeur 0, `Days.Monday` a la valeur 1 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="16e56-116">In the previous example, `Days.Sunday` has a value of 0, `Days.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="16e56-117">Quand vous créez un objet `Days`, il a la valeur par défaut `Days.Sunday` (0) si vous ne lui assignez pas une valeur explicitement.</span><span class="sxs-lookup"><span data-stu-id="16e56-117">When you create a new `Days` object, it will have a default value of `Days.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="16e56-118">Quand vous créez un enum, sélectionnez la valeur par défaut la plus logique et affectez-lui une valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="16e56-118">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="16e56-119">Ainsi, tous les enums auront cette valeur par défaut si aucune valeur ne leur est assignée explicitement lors de leur création.</span><span class="sxs-lookup"><span data-stu-id="16e56-119">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>  
  
 <span data-ttu-id="16e56-120">Si la variable `meetingDay` est de type `Days`, alors (sans un cast explicite) vous pouvez uniquement lui affecter l’une des valeurs définies par `Days`.</span><span class="sxs-lookup"><span data-stu-id="16e56-120">If the variable `meetingDay` is of type `Days`, then (without an explicit cast) you can only assign it one of the values defined by `Days`.</span></span> <span data-ttu-id="16e56-121">Si le jour de la réunion change, vous pouvez affecter une nouvelle valeur de `Days` à `meetingDay` :</span><span class="sxs-lookup"><span data-stu-id="16e56-121">And if the meeting day changes, you can assign a new value from `Days` to `meetingDay`:</span></span>  
  
 <span data-ttu-id="16e56-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16e56-123">Il est possible d’assigner une valeur entière arbitraire à `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="16e56-123">It is possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="16e56-124">Par exemple, cette ligne de code ne produit pas d’erreur : `meetingDay = (Days) 42`.</span><span class="sxs-lookup"><span data-stu-id="16e56-124">For example, this line of code does not produce an error: `meetingDay = (Days) 42`.</span></span> <span data-ttu-id="16e56-125">Toutefois, vous ne devez pas le faire car l’attente implicite est qu’une variable enum ne contiendra que l’une des valeurs définies par l’enum.</span><span class="sxs-lookup"><span data-stu-id="16e56-125">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="16e56-126">Affecter une valeur arbitraire à une variable de type énumération présente un risque élevé d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="16e56-126">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>  
  
 <span data-ttu-id="16e56-127">Vous pouvez affecter n’importe quelle valeur aux éléments dans la liste d’énumérateurs d’un type énumération, et vous pouvez également utiliser des valeurs calculées :</span><span class="sxs-lookup"><span data-stu-id="16e56-127">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>  
  
 <span data-ttu-id="16e56-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span></span>  
  
## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="16e56-129">Types énumération comme indicateurs binaires</span><span class="sxs-lookup"><span data-stu-id="16e56-129">Enumeration Types as Bit Flags</span></span>  
 <span data-ttu-id="16e56-130">Vous pouvez utiliser un type énumération pour définir des indicateurs binaires, ce qui permet à une instance du type énumération de stocker n’importe quelle combinaison des valeurs définies dans la liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="16e56-130">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="16e56-131">(Bien entendu, certaines combinaisons peuvent ne pas être significatives ou autorisées dans votre code de programme.)</span><span class="sxs-lookup"><span data-stu-id="16e56-131">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>  
  
 <span data-ttu-id="16e56-132">Pour créer un enum d’indicateurs binaires, vous devez appliquer l’attribut <xref:System.FlagsAttribute?displayProperty=fullName> et définir les valeurs de manière appropriée afin que les opérations au niveau du bit `AND`, `OR`, `NOT` et `XOR` puissent être effectuées sur elles.</span><span class="sxs-lookup"><span data-stu-id="16e56-132">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=fullName> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="16e56-133">Dans l’enum d’indicateurs binaires, incluez une constante nommée avec une valeur zéro qui signifie « aucun indicateur n’est défini. »</span><span class="sxs-lookup"><span data-stu-id="16e56-133">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="16e56-134">N’attribuez pas la valeur zéro à un indicateur si cela ne signifie pas « aucun indicateur n’est défini ».</span><span class="sxs-lookup"><span data-stu-id="16e56-134">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>  
  
 <span data-ttu-id="16e56-135">Dans l’exemple suivant, une autre version de l’enum `Days`, nommée `Days2`, est définie.</span><span class="sxs-lookup"><span data-stu-id="16e56-135">In the following example, another version of the `Days` enum, which is named `Days2`, is defined.</span></span> <span data-ttu-id="16e56-136">`Days2` a l’attribut `Flags`, et à chaque valeur est affectée la puissance de deux supérieure suivante.</span><span class="sxs-lookup"><span data-stu-id="16e56-136">`Days2` has the `Flags` attribute and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="16e56-137">Cela vous permet de créer une variable `Days2` dont la valeur est `Days2.Tuesday` et `Days2.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="16e56-137">This enables you to create a `Days2` variable whose value is `Days2.Tuesday` and `Days2.Thursday`.</span></span>  
  
 <span data-ttu-id="16e56-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span></span>  
  
 <span data-ttu-id="16e56-139">Pour définir un indicateur sur un enum, utilisez l’opérateur binaire `OR` comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="16e56-139">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>  
  
 <span data-ttu-id="16e56-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span></span>  
  
 <span data-ttu-id="16e56-141">Pour déterminer si un indicateur spécifique est défini, utilisez une opération `AND` au niveau du bit, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="16e56-141">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>  
  
 <span data-ttu-id="16e56-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span></span>  
  
 <span data-ttu-id="16e56-143">Pour plus d’informations sur les éléments à prendre en compte quand vous définissez des types énumération avec l’attribut <xref:System.FlagsAttribute?displayProperty=fullName>, consultez <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="16e56-143">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=fullName> attribute, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="16e56-144">Utilisation des méthodes System.Enum pour découvrir et manipuler des valeurs enum</span><span class="sxs-lookup"><span data-stu-id="16e56-144">Using the System.Enum Methods to Discover and Manipulate Enum Values</span></span>  
 <span data-ttu-id="16e56-145">Tous les enums sont des instances du type <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="16e56-145">All enums are instances of the <xref:System.Enum?displayProperty=fullName> type.</span></span> <span data-ttu-id="16e56-146">Vous ne pouvez pas dériver de nouvelles classes à partir de <xref:System.Enum?displayProperty=fullName>, mais vous pouvez utiliser ses méthodes pour découvrir des informations et manipuler les valeurs d’une instance enum.</span><span class="sxs-lookup"><span data-stu-id="16e56-146">You cannot derive new classes from <xref:System.Enum?displayProperty=fullName>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>  
  
 <span data-ttu-id="16e56-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="16e56-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span></span>  
  
 <span data-ttu-id="16e56-148">Pour plus d'informations, consultez <xref:System.Enum?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="16e56-148">For more information, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="16e56-149">Vous pouvez également créer une méthode pour un enum à l’aide d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="16e56-149">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="16e56-150">Pour plus d’informations, consultez [Guide pratique pour créer une méthode pour une énumération](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="16e56-150">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="16e56-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16e56-151">See Also</span></span>  
 <span data-ttu-id="16e56-152"><xref:System.Enum?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="16e56-152"><xref:System.Enum?displayProperty=fullName></span></span>   
 <span data-ttu-id="16e56-153">[Guide de programmation C#](../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="16e56-153">[C# Programming Guide](../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="16e56-154">enum</span><span class="sxs-lookup"><span data-stu-id="16e56-154">enum</span></span>](../../csharp/language-reference/keywords/enum.md)

