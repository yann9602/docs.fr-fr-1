---
title: "enum (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords: enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 00ae9b555ae73db445fe4a4facf00753bf8c759a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-c-reference"></a><span data-ttu-id="8a2cb-102">enum (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8a2cb-102">enum (C# Reference)</span></span>
<span data-ttu-id="8a2cb-103">Le mot clé `enum` est utilisé pour déclarer une énumération. Il s’agit d’un type distinct qui se compose d’un ensemble de constantes nommées, appelé liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="8a2cb-104">Il est généralement préférable de définir une énumération directement dans un espace de noms pour que toutes les classes de l’espace de noms puissent y accéder avec la même facilité.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="8a2cb-105">Toutefois, une énumération peut également être imbriquée dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="8a2cb-106">Par défaut, le premier énumérateur a la valeur 0 et chaque énumérateur successif est augmenté de 1.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="8a2cb-107">Par exemple, dans l’énumération suivante, `Sat` est `0`, `Sun` est `1`, `Mon` est `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="8a2cb-108">Les énumérateurs peuvent utiliser des initialiseurs pour remplacer les valeurs par défaut, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="8a2cb-109">Dans cette énumération, le début de la séquence des éléments est forcé à `1` au lieu de `0`.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="8a2cb-110">Il est cependant recommandé d’inclure une constante qui a la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="8a2cb-111">Pour plus d’informations, consultez [Types énumération](../../../csharp/programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="8a2cb-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="8a2cb-112">Chaque type énumération a un type sous-jacent qui peut être tout type intégral sauf [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="8a2cb-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="8a2cb-113">Le type sous-jacent par défaut des éléments de l’énumération est [int](../../../csharp/language-reference/keywords/int.md). Pour déclarer une énumération d’un autre type intégral, comme [byte](../../../csharp/language-reference/keywords/byte.md), utilisez un signe deux-points après l’identificateur, suivi du type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="8a2cb-114">Les types approuvés pour une énumération sont `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [court](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md)ou [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="8a2cb-114">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="8a2cb-115">Une variable de type `Days` peut être affectée de n’importe quelle valeur dans la plage du type sous-jacent ; les valeurs ne sont pas limitées aux constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-115">A variable of type `Days` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="8a2cb-116">La valeur par défaut de `enum E` est la valeur produite par l’expression `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a2cb-117">Le nom d’un énumérateur ne peut pas contenir d’espaces.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="8a2cb-118">Le type sous-jacent spécifie la quantité de stockage allouée pour chaque énumérateur.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="8a2cb-119">Cependant, un cast explicite est nécessaire pour convertir du type `enum` en un type intégral.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="8a2cb-120">Par exemple, l’instruction suivante affecte l’énumérateur `Sun` à une variable du type [int](../../../csharp/language-reference/keywords/int.md) en utilisant un cast pour convertir de `enum` en `int`.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Days.Sun;  
```  
  
 <span data-ttu-id="8a2cb-121">Quand vous appliquez <xref:System.FlagsAttribute?displayProperty=nameWithType> à une énumération qui contient des éléments qui peuvent être combinés avec une opération `OR` au niveau du bit, l’attribut affecte le comportement d’ `enum` quand elle est utilisée avec certains outils.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="8a2cb-122">Vous pouvez remarquer ces modifications quand vous utilisez des outils comme les méthodes de la classe <xref:System.Console> et l’évaluateur d’expression.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="8a2cb-123">(Voir le troisième exemple.)</span><span class="sxs-lookup"><span data-stu-id="8a2cb-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8a2cb-124">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="8a2cb-124">Robust Programming</span></span>  
 <span data-ttu-id="8a2cb-125">Tout comme avec n’importe quelle constante, toutes les références aux valeurs individuelles d’une énumération sont converties en littéraux numériques au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="8a2cb-126">Cette opération peut créer des problèmes potentiels de gestion de version, comme décrit dans [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="8a2cb-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="8a2cb-127">L’affectation de valeurs supplémentaires à de nouvelles versions d’énumérations ou la modification des valeurs des membres d’une énumération dans une nouvelle version peut entraîner des problèmes pour le code source dépendant.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="8a2cb-128">Les valeurs des énumérations sont souvent utilisées dans des instructions [switch](../../../csharp/language-reference/keywords/switch.md) .</span><span class="sxs-lookup"><span data-stu-id="8a2cb-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="8a2cb-129">Si des éléments supplémentaires ont été ajoutées au type `enum` , la section par défaut de l’instruction switch peut être sélectionnée de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="8a2cb-130">Si d’autres développeurs utilisent votre code, vous devez fournir des instructions sur la manière dont leur code doit réagir si de nouveaux éléments sont ajoutés à des types `enum` .</span><span class="sxs-lookup"><span data-stu-id="8a2cb-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a2cb-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a2cb-131">Example</span></span>  
 <span data-ttu-id="8a2cb-132">Dans l’exemple suivant, une énumération, `Days`, est déclarée.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-132">In the following example, an enumeration, `Days`, is declared.</span></span> <span data-ttu-id="8a2cb-133">Deux énumérateurs sont explicitement convertis en entiers et affectés à des variables entières.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8a2cb-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a2cb-134">Example</span></span>  
 <span data-ttu-id="8a2cb-135">Dans l’exemple suivant, l’option de type de base est utilisée pour déclarer une `enum` dont les membres sont de type `long`.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="8a2cb-136">Notez que même si le type sous-jacent de l’énumération est `long`, les membres de l’énumération doivent toujours être explicitement convertis en type `long` en utilisant un cast.</span><span class="sxs-lookup"><span data-stu-id="8a2cb-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8a2cb-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="8a2cb-137">Example</span></span>  
 <span data-ttu-id="8a2cb-138">L’exemple de code suivant montre l’utilisation et l’effet de l’attribut <xref:System.FlagsAttribute?displayProperty=nameWithType> sur une déclaration `enum` .</span><span class="sxs-lookup"><span data-stu-id="8a2cb-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="8a2cb-139">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8a2cb-139">Comments</span></span>  
 <span data-ttu-id="8a2cb-140">Si vous supprimez `Flags`, l’exemple affiche les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a2cb-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a2cb-141">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8a2cb-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a2cb-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a2cb-142">See Also</span></span>  
 [<span data-ttu-id="8a2cb-143">Référence C#</span><span class="sxs-lookup"><span data-stu-id="8a2cb-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a2cb-144">Types d’énumération</span><span class="sxs-lookup"><span data-stu-id="8a2cb-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="8a2cb-145">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="8a2cb-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8a2cb-146">Tableau des types intégraux</span><span class="sxs-lookup"><span data-stu-id="8a2cb-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="8a2cb-147">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="8a2cb-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="8a2cb-148">Tableau des conversions numériques implicites</span><span class="sxs-lookup"><span data-stu-id="8a2cb-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="8a2cb-149">Tableau des conversions numériques explicites</span><span class="sxs-lookup"><span data-stu-id="8a2cb-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
