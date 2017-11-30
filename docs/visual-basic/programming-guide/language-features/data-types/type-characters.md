---
title: "Caractères de type (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bd017db40fc28c78e960a889947cc7323e3e156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="588b2-102">Tapez les caractères (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="588b2-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="588b2-103">En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation avec un *caractère de type*.</span><span class="sxs-lookup"><span data-stu-id="588b2-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="588b2-104">Le caractère de type doit suivre immédiatement l’élément, sans les caractères de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="588b2-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="588b2-105">Le caractère de type n’est pas partie du nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="588b2-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="588b2-106">Un élément défini avec un caractère de type peut être référencé sans le caractère de type.</span><span class="sxs-lookup"><span data-stu-id="588b2-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="588b2-107">Caractères de type d’identificateur</span><span class="sxs-lookup"><span data-stu-id="588b2-107">Identifier type characters</span></span>

<span data-ttu-id="588b2-108">Visual Basic fournit un jeu de *caractères de type identificateur* que vous pouvez utiliser dans une déclaration pour spécifier le type de données d’une variable ou constante.</span><span class="sxs-lookup"><span data-stu-id="588b2-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="588b2-109">Le tableau suivant présente les caractères de type identificateur disponible avec des exemples d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="588b2-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="588b2-110">Caractère de type identificateur</span><span class="sxs-lookup"><span data-stu-id="588b2-110">Identifier type character</span></span>|<span data-ttu-id="588b2-111">Type de données</span><span class="sxs-lookup"><span data-stu-id="588b2-111">Data type</span></span>|<span data-ttu-id="588b2-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="588b2-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="588b2-113">Il n’existe aucun caractère de type identificateur pour le `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` des types de données, ou pour toute types de données composites tels que les tableaux ou les structures.</span><span class="sxs-lookup"><span data-stu-id="588b2-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="588b2-114">Dans certains cas, vous pouvez ajouter la `$` de caractères à une fonction Visual Basic, par exemple `Left$` au lieu de `Left`, afin d’obtenir une valeur retournée de type `String`.</span><span class="sxs-lookup"><span data-stu-id="588b2-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="588b2-115">Dans tous les cas, le caractère de type identificateur doit suivre immédiatement le nom d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="588b2-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="588b2-116">Caractères de type littéral</span><span class="sxs-lookup"><span data-stu-id="588b2-116">Literal type characters</span></span>

<span data-ttu-id="588b2-117">A *littéral* est une représentation textuelle d’une valeur particulière d’un type de données.</span><span class="sxs-lookup"><span data-stu-id="588b2-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="588b2-118">Types de littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="588b2-118">Default literal types</span></span>

<span data-ttu-id="588b2-119">La forme d’un littéral, tel qu’il apparaît dans votre code normalement détermine son type de données.</span><span class="sxs-lookup"><span data-stu-id="588b2-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="588b2-120">Le tableau suivant présente les types par défaut.</span><span class="sxs-lookup"><span data-stu-id="588b2-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="588b2-121">Sous forme textuelle de littéral</span><span class="sxs-lookup"><span data-stu-id="588b2-121">Textual form of literal</span></span>|<span data-ttu-id="588b2-122">Type de données par défaut</span><span class="sxs-lookup"><span data-stu-id="588b2-122">Default data type</span></span>|<span data-ttu-id="588b2-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="588b2-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="588b2-124">Numérique, aucune partie fractionnaire</span><span class="sxs-lookup"><span data-stu-id="588b2-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="588b2-125">Numérique, aucune partie fractionnaire, trop grand pour`Integer`</span><span class="sxs-lookup"><span data-stu-id="588b2-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="588b2-126">Numérique, partie fractionnaire</span><span class="sxs-lookup"><span data-stu-id="588b2-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="588b2-127">Placé entre guillemets doubles</span><span class="sxs-lookup"><span data-stu-id="588b2-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="588b2-128">Encadrées par des signes dièse</span><span class="sxs-lookup"><span data-stu-id="588b2-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="588b2-129">Types de littéral forcés</span><span class="sxs-lookup"><span data-stu-id="588b2-129">Forced literal types</span></span>

<span data-ttu-id="588b2-130">Visual Basic fournit un jeu de *caractères de type littéral*, que vous pouvez utiliser pour forcer un littéral à prendre un type de données autre que celui de sa forme indique.</span><span class="sxs-lookup"><span data-stu-id="588b2-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="588b2-131">Pour cela, vous devez l’ajout du caractère à la fin du littéral.</span><span class="sxs-lookup"><span data-stu-id="588b2-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="588b2-132">Le tableau suivant présente les caractères de type de littéral disponibles avec des exemples d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="588b2-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="588b2-133">Caractère de type littéral</span><span class="sxs-lookup"><span data-stu-id="588b2-133">Literal type character</span></span>|<span data-ttu-id="588b2-134">Type de données</span><span class="sxs-lookup"><span data-stu-id="588b2-134">Data type</span></span>|<span data-ttu-id="588b2-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="588b2-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="588b2-136">Il n’existe aucun caractère de type de littéral pour les `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` des types de données, ni pour les types de données composites tels que les tableaux ou les structures.</span><span class="sxs-lookup"><span data-stu-id="588b2-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="588b2-137">Les littéraux peuvent également utiliser les caractères de type identificateur (`%`, `&`, `@`, `!`, `#`, `$`), comme des variables, des constantes et des expressions.</span><span class="sxs-lookup"><span data-stu-id="588b2-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="588b2-138">Toutefois, les caractères de type de littéral (`S`, `I`, `L`, `D`, `F`, `R`, `C`) peut être utilisé uniquement avec des littéraux.</span><span class="sxs-lookup"><span data-stu-id="588b2-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="588b2-139">Dans tous les cas, le caractère de type de littéral doit immédiatement suivre la valeur littérale.</span><span class="sxs-lookup"><span data-stu-id="588b2-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="588b2-140">Littéraux hexadécimaux, binaire et octales</span><span class="sxs-lookup"><span data-stu-id="588b2-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="588b2-141">Le compilateur interprète normalement un littéral d’entier dans le système de nombre décimal (base 10).</span><span class="sxs-lookup"><span data-stu-id="588b2-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="588b2-142">Vous pouvez également définir un littéral d’entier comme un nombre hexadécimal (base 16) avec le `&H` préfixe, sous la forme d’un nombre binaire (base 2) avec le `&B` préfixe et comme octal (base 8) chez le `&O` préfixe.</span><span class="sxs-lookup"><span data-stu-id="588b2-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="588b2-143">Les chiffres qui suivent le préfixe doivent être adaptés dans le système.</span><span class="sxs-lookup"><span data-stu-id="588b2-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="588b2-144">Le tableau suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="588b2-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="588b2-145">Nombre de base</span><span class="sxs-lookup"><span data-stu-id="588b2-145">Number base</span></span>|<span data-ttu-id="588b2-146">Préfixe</span><span class="sxs-lookup"><span data-stu-id="588b2-146">Prefix</span></span>|<span data-ttu-id="588b2-147">Valeurs de chiffre valide</span><span class="sxs-lookup"><span data-stu-id="588b2-147">Valid digit values</span></span>|<span data-ttu-id="588b2-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="588b2-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="588b2-149">Hexadécimale (base 16)</span><span class="sxs-lookup"><span data-stu-id="588b2-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="588b2-150">0-9 et A-F</span><span class="sxs-lookup"><span data-stu-id="588b2-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="588b2-151">Binaire (base 2)</span><span class="sxs-lookup"><span data-stu-id="588b2-151">Binary (base 2)</span></span>|`0B`|<span data-ttu-id="588b2-152">0-1</span><span class="sxs-lookup"><span data-stu-id="588b2-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="588b2-153">Octale (base 8)</span><span class="sxs-lookup"><span data-stu-id="588b2-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="588b2-154">0-7</span><span class="sxs-lookup"><span data-stu-id="588b2-154">0-7</span></span>|`&O77`|

<span data-ttu-id="588b2-155">À partir de Visual Basic 2017, vous pouvez utiliser le caractère de soulignement (`_`) comme séparateur de groupes pour améliorer la lisibilité d’un littéral intégral.</span><span class="sxs-lookup"><span data-stu-id="588b2-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="588b2-156">L’exemple suivant utilise le `_` caractère pour regrouper un littéral binaire en groupes de 8 bits :</span><span class="sxs-lookup"><span data-stu-id="588b2-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="588b2-157">Vous pouvez suivre un littéral préfixé par un caractère de type de littéral.</span><span class="sxs-lookup"><span data-stu-id="588b2-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="588b2-158">L’exemple suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="588b2-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="588b2-159">Dans l’exemple précédent, `counter` a la valeur décimale-32 768 et `flags` a la valeur décimale + 32 768.</span><span class="sxs-lookup"><span data-stu-id="588b2-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

## <a name="see-also"></a><span data-ttu-id="588b2-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="588b2-160">See Also</span></span>

 [<span data-ttu-id="588b2-161">Types de données</span><span class="sxs-lookup"><span data-stu-id="588b2-161">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="588b2-162">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="588b2-162">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="588b2-163">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="588b2-163">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="588b2-164">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="588b2-164">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="588b2-165">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="588b2-165">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="588b2-166">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="588b2-166">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="588b2-167">Types de données</span><span class="sxs-lookup"><span data-stu-id="588b2-167">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
