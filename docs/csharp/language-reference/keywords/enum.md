---
title: "enum (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 36
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
ms.openlocfilehash: cf12724ec9e450a2bc237db614f235d7f03a4a7e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="enum-c-reference"></a><span data-ttu-id="bb482-102">enum (référence C#)</span><span class="sxs-lookup"><span data-stu-id="bb482-102">enum (C# Reference)</span></span>
<span data-ttu-id="bb482-103">Le mot clé `enum` est utilisé pour déclarer une énumération. Il s’agit d’un type distinct qui se compose d’un ensemble de constantes nommées, appelé liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="bb482-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="bb482-104">Il est généralement préférable de définir une énumération directement dans un espace de noms pour que toutes les classes de l’espace de noms puissent y accéder avec la même facilité.</span><span class="sxs-lookup"><span data-stu-id="bb482-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="bb482-105">Toutefois, une énumération peut également être imbriquée dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="bb482-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="bb482-106">Par défaut, le premier énumérateur a la valeur 0 et chaque énumérateur successif est augmenté de 1.</span><span class="sxs-lookup"><span data-stu-id="bb482-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="bb482-107">Par exemple, dans l’énumération suivante, `Sat` est `0`, `Sun` est `1`, `Mon` est `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="bb482-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="bb482-108">Les énumérateurs peuvent utiliser des initialiseurs pour remplacer les valeurs par défaut, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bb482-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="bb482-109">Dans cette énumération, le début de la séquence des éléments est forcé à `1` au lieu de `0`.</span><span class="sxs-lookup"><span data-stu-id="bb482-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="bb482-110">Il est cependant recommandé d’inclure une constante qui a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="bb482-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="bb482-111">Pour plus d’informations, consultez [Types énumération](../../../csharp/programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="bb482-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="bb482-112">Chaque type énumération a un type sous-jacent qui peut être tout type intégral sauf [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="bb482-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="bb482-113">Le type sous-jacent par défaut des éléments de l’énumération est [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="bb482-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="bb482-114">Pour déclarer une énumération d’un autre type intégral, comme [byte](../../../csharp/language-reference/keywords/byte.md), utilisez un signe deux-points après l’identificateur, suivi du type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bb482-114">To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="bb482-115">Les types approuvés pour une énumération sont `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [court](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md)ou [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="bb482-115">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="bb482-116">Une variable de type `Days` peut être affectée de n’importe quelle valeur dans la plage du type sous-jacent ; les valeurs ne sont pas limitées aux constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="bb482-116">A variable of type `Days` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="bb482-117">La valeur par défaut de `enum E` est la valeur produite par l’expression `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="bb482-117">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb482-118">Le nom d’un énumérateur ne peut pas contenir d’espaces.</span><span class="sxs-lookup"><span data-stu-id="bb482-118">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="bb482-119">Le type sous-jacent spécifie la quantité de stockage allouée pour chaque énumérateur.</span><span class="sxs-lookup"><span data-stu-id="bb482-119">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="bb482-120">Cependant, un cast explicite est nécessaire pour convertir du type `enum` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="bb482-120">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="bb482-121">Par exemple, l’instruction suivante affecte l’énumérateur `Sun` à une variable du type [int](../../../csharp/language-reference/keywords/int.md) en utilisant un cast pour convertir de `enum` en `int`.</span><span class="sxs-lookup"><span data-stu-id="bb482-121">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Days.Sun;  
```  
  
 <span data-ttu-id="bb482-122">Quand vous appliquez <xref:System.FlagsAttribute?displayProperty=fullName> à une énumération qui contient des éléments qui peuvent être combinés avec une opération `OR` au niveau du bit, l’attribut affecte le comportement d’ `enum` quand elle est utilisée avec certains outils.</span><span class="sxs-lookup"><span data-stu-id="bb482-122">When you apply <xref:System.FlagsAttribute?displayProperty=fullName> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="bb482-123">Vous pouvez remarquer ces modifications quand vous utilisez des outils comme les méthodes de la classe <xref:System.Console> et l’évaluateur d’expression.</span><span class="sxs-lookup"><span data-stu-id="bb482-123">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="bb482-124">(Voir le troisième exemple.)</span><span class="sxs-lookup"><span data-stu-id="bb482-124">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bb482-125">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="bb482-125">Robust Programming</span></span>  
 <span data-ttu-id="bb482-126">Tout comme avec n’importe quelle constante, toutes les références aux valeurs individuelles d’une énumération sont converties en littéraux numériques au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="bb482-126">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="bb482-127">Cette opération peut créer des problèmes potentiels de gestion de version, comme décrit dans [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="bb482-127">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="bb482-128">L’affectation de valeurs supplémentaires à de nouvelles versions d’énumérations ou la modification des valeurs des membres d’une énumération dans une nouvelle version peut entraîner des problèmes pour le code source dépendant.</span><span class="sxs-lookup"><span data-stu-id="bb482-128">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="bb482-129">Les valeurs des énumérations sont souvent utilisées dans des instructions [switch](../../../csharp/language-reference/keywords/switch.md) .</span><span class="sxs-lookup"><span data-stu-id="bb482-129">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="bb482-130">Si des éléments supplémentaires ont été ajoutées au type `enum` , la section par défaut de l’instruction switch peut être sélectionnée de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="bb482-130">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="bb482-131">Si d’autres développeurs utilisent votre code, vous devez fournir des instructions sur la manière dont leur code doit réagir si de nouveaux éléments sont ajoutés à des types `enum` .</span><span class="sxs-lookup"><span data-stu-id="bb482-131">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb482-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb482-132">Example</span></span>  
 <span data-ttu-id="bb482-133">Dans l’exemple suivant, une énumération, `Days`, est déclarée.</span><span class="sxs-lookup"><span data-stu-id="bb482-133">In the following example, an enumeration, `Days`, is declared.</span></span> <span data-ttu-id="bb482-134">Deux énumérateurs sont explicitement convertis en entiers et affectés à des variables entières.</span><span class="sxs-lookup"><span data-stu-id="bb482-134">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 <span data-ttu-id="bb482-135">[!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bb482-135">[!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb482-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb482-136">Example</span></span>  
 <span data-ttu-id="bb482-137">Dans l’exemple suivant, l’option de type de base est utilisée pour déclarer une `enum` dont les membres sont de type `long`.</span><span class="sxs-lookup"><span data-stu-id="bb482-137">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="bb482-138">Notez que même si le type sous-jacent de l’énumération est `long`, les membres de l’énumération doivent toujours être explicitement convertis en type `long` en utilisant un cast.</span><span class="sxs-lookup"><span data-stu-id="bb482-138">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 <span data-ttu-id="bb482-139">[!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bb482-139">[!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb482-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb482-140">Example</span></span>  
 <span data-ttu-id="bb482-141">L’exemple de code suivant montre l’utilisation et l’effet de l’attribut <xref:System.FlagsAttribute?displayProperty=fullName> sur une déclaration `enum` .</span><span class="sxs-lookup"><span data-stu-id="bb482-141">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=fullName> attribute on an `enum` declaration.</span></span>  
  
 <span data-ttu-id="bb482-142">[!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bb482-142">[!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="bb482-143">Commentaires</span><span class="sxs-lookup"><span data-stu-id="bb482-143">Comments</span></span>  
 <span data-ttu-id="bb482-144">Si vous supprimez `Flags`, l’exemple affiche les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="bb482-144">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb482-145">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bb482-145">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb482-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb482-146">See Also</span></span>  
 <span data-ttu-id="bb482-147">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-147">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bb482-148">[Types énumération](../../../csharp/programming-guide/enumeration-types.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-148">[Enumeration Types](../../../csharp/programming-guide/enumeration-types.md) </span></span>  
 <span data-ttu-id="bb482-149">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-149">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="bb482-150">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-150">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="bb482-151">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-151">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="bb482-152">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="bb482-152">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="bb482-153">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="bb482-153">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

