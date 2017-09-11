---
title: "Tapez les caractères (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 335306eca12070de456a72e918bcbba1e22ab55b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="6f444-102">Caractères de type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f444-102">Type Characters (Visual Basic)</span></span>
<span data-ttu-id="6f444-103">En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation avec un *caractère de type*.</span><span class="sxs-lookup"><span data-stu-id="6f444-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="6f444-104">Le caractère de type doit suivre immédiatement l’élément, sans caractères concernés de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="6f444-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>  
  
 <span data-ttu-id="6f444-105">Le caractère de type ne fait pas partie du nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6f444-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="6f444-106">Un élément défini avec un caractère de type peut être référencé sans caractère de type.</span><span class="sxs-lookup"><span data-stu-id="6f444-106">An element defined with a type character can be referenced without the type character.</span></span>  
  
## <a name="identifier-type-characters"></a><span data-ttu-id="6f444-107">Caractères de Type d’identificateur</span><span class="sxs-lookup"><span data-stu-id="6f444-107">Identifier Type Characters</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="6f444-108">fournit un jeu de *caractères de type d’identificateur*, que vous pouvez utiliser dans une déclaration pour spécifier le type de données d’une variable ou constante.</span><span class="sxs-lookup"><span data-stu-id="6f444-108"> supplies a set of *identifier type characters*, which you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="6f444-109">Le tableau suivant présente les caractères de type identificateur disponible avec des exemples d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6f444-109">The following table shows the available identifier type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="6f444-110">Caractère de type d’identificateur</span><span class="sxs-lookup"><span data-stu-id="6f444-110">Identifier type character</span></span>|<span data-ttu-id="6f444-111">Type de données</span><span class="sxs-lookup"><span data-stu-id="6f444-111">Data type</span></span>|<span data-ttu-id="6f444-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f444-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="6f444-113">Il n’existe aucun caractère de type identificateur pour le `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` des types de données, ni pour les types de données composites tels que les tableaux ou les structures.</span><span class="sxs-lookup"><span data-stu-id="6f444-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="6f444-114">Dans certains cas, vous pouvez ajouter la `$` à un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de fonction, par exemple `Left$` au lieu de `Left`, afin d’obtenir une valeur retournée de type `String`.</span><span class="sxs-lookup"><span data-stu-id="6f444-114">In some cases, you can append the `$` character to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>  
  
 <span data-ttu-id="6f444-115">Dans tous les cas, le caractère de type identificateur doit suivre immédiatement le nom d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="6f444-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>  
  
## <a name="literal-type-characters"></a><span data-ttu-id="6f444-116">Caractères de Type littéral</span><span class="sxs-lookup"><span data-stu-id="6f444-116">Literal Type Characters</span></span>  
 <span data-ttu-id="6f444-117">A *littéral* est une représentation textuelle d’une valeur particulière d’un type de données.</span><span class="sxs-lookup"><span data-stu-id="6f444-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  
  
### <a name="default-literal-types"></a><span data-ttu-id="6f444-118">Types de littéral par défaut</span><span class="sxs-lookup"><span data-stu-id="6f444-118">Default Literal Types</span></span>  
 <span data-ttu-id="6f444-119">La forme d’un littéral, tel qu’il apparaît dans votre code normalement détermine son type de données.</span><span class="sxs-lookup"><span data-stu-id="6f444-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="6f444-120">Le tableau suivant présente les types par défaut.</span><span class="sxs-lookup"><span data-stu-id="6f444-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="6f444-121">Forme textuelle de littéral</span><span class="sxs-lookup"><span data-stu-id="6f444-121">Textual form of literal</span></span>|<span data-ttu-id="6f444-122">Type de données par défaut</span><span class="sxs-lookup"><span data-stu-id="6f444-122">Default data type</span></span>|<span data-ttu-id="6f444-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f444-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="6f444-124">Numérique, aucune partie fractionnaire</span><span class="sxs-lookup"><span data-stu-id="6f444-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="6f444-125">Numérique, aucune partie fractionnaire, trop grand pour`Integer`</span><span class="sxs-lookup"><span data-stu-id="6f444-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="6f444-126">Numérique, partie fractionnaire</span><span class="sxs-lookup"><span data-stu-id="6f444-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="6f444-127">Placé entre guillemets doubles</span><span class="sxs-lookup"><span data-stu-id="6f444-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="6f444-128">Compris entre signes dièse</span><span class="sxs-lookup"><span data-stu-id="6f444-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a><span data-ttu-id="6f444-129">Types de littéral forcés</span><span class="sxs-lookup"><span data-stu-id="6f444-129">Forced Literal Types</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="6f444-130">fournit un jeu de *caractères de type littéral*, que vous pouvez utiliser pour forcer un littéral à prendre un type de données différent de celui de son formulaire indique.</span><span class="sxs-lookup"><span data-stu-id="6f444-130"> supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="6f444-131">Pour cela, en ajoutant le caractère à la fin du littéral.</span><span class="sxs-lookup"><span data-stu-id="6f444-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="6f444-132">Le tableau suivant présente les caractères de type de littéral disponibles avec des exemples d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6f444-132">The following table shows the available literal type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="6f444-133">Caractère de type littéral</span><span class="sxs-lookup"><span data-stu-id="6f444-133">Literal type character</span></span>|<span data-ttu-id="6f444-134">Type de données</span><span class="sxs-lookup"><span data-stu-id="6f444-134">Data type</span></span>|<span data-ttu-id="6f444-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f444-135">Example</span></span>|  
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
  
 <span data-ttu-id="6f444-136">Il n’existe aucun caractère de type de littéral pour les `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` des types de données, ni pour les types de données composites tels que les tableaux ou les structures.</span><span class="sxs-lookup"><span data-stu-id="6f444-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="6f444-137">Les littéraux peuvent également utiliser les caractères de type d’identificateur (`%`, `&`, `@`, `!`, `#`, `$`), comme des variables, des constantes et des expressions.</span><span class="sxs-lookup"><span data-stu-id="6f444-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="6f444-138">Toutefois, les caractères de type de littéral (`S`, `I`, `L`, `D`, `F`, `R`, `C`) peut être utilisé uniquement avec des littéraux.</span><span class="sxs-lookup"><span data-stu-id="6f444-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>  
  
 <span data-ttu-id="6f444-139">Dans tous les cas, le caractère de type de littéral doit suivre immédiatement la valeur littérale.</span><span class="sxs-lookup"><span data-stu-id="6f444-139">In all cases, the literal type character must immediately follow the literal value.</span></span>  
  
## <a name="hexadecimal-and-octal-literals"></a><span data-ttu-id="6f444-140">Littéraux hexadécimaux et octaux</span><span class="sxs-lookup"><span data-stu-id="6f444-140">Hexadecimal and Octal Literals</span></span>  
 <span data-ttu-id="6f444-141">Le compilateur construes normalement un littéral d’entier dans le système décimal (base 10).</span><span class="sxs-lookup"><span data-stu-id="6f444-141">The compiler normally construes an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="6f444-142">Vous pouvez forcer un littéral entier à être hexadécimal (base 16) avec le `&H` préfixe et vous pouvez le forcer à être octal (base 8) avec le `&O` préfixe.</span><span class="sxs-lookup"><span data-stu-id="6f444-142">You can force an integer literal to be hexadecimal (base 16) with the `&H` prefix, and you can force it to be octal (base 8) with the `&O` prefix.</span></span> <span data-ttu-id="6f444-143">Les chiffres qui suivent le préfixe doivent être appropriées pour le système.</span><span class="sxs-lookup"><span data-stu-id="6f444-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="6f444-144">Le tableau suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="6f444-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="6f444-145">Nombre de base</span><span class="sxs-lookup"><span data-stu-id="6f444-145">Number base</span></span>|<span data-ttu-id="6f444-146">Préfixe</span><span class="sxs-lookup"><span data-stu-id="6f444-146">Prefix</span></span>|<span data-ttu-id="6f444-147">Valeurs de chiffre valide</span><span class="sxs-lookup"><span data-stu-id="6f444-147">Valid digit values</span></span>|<span data-ttu-id="6f444-148">Exemple</span><span class="sxs-lookup"><span data-stu-id="6f444-148">Example</span></span>|  
|-----------------|------------|------------------------|-------------|  
|<span data-ttu-id="6f444-149">Hexadécimale (base 16)</span><span class="sxs-lookup"><span data-stu-id="6f444-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="6f444-150">0-9 et A-F</span><span class="sxs-lookup"><span data-stu-id="6f444-150">0-9 and A-F</span></span>|`&HFFFF`|  
|<span data-ttu-id="6f444-151">Octale (base 8)</span><span class="sxs-lookup"><span data-stu-id="6f444-151">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="6f444-152">0-7</span><span class="sxs-lookup"><span data-stu-id="6f444-152">0-7</span></span>|`&O77`|  
  
 <span data-ttu-id="6f444-153">Vous pouvez suivre un littéral préfixé avec un caractère de type littéral.</span><span class="sxs-lookup"><span data-stu-id="6f444-153">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="6f444-154">L’exemple suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="6f444-154">The following example shows this.</span></span>  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 <span data-ttu-id="6f444-155">Dans l’exemple précédent, `counter` a la valeur décimale-32&768; et `flags` a la valeur décimale +&32;&768;.</span><span class="sxs-lookup"><span data-stu-id="6f444-155">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f444-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f444-156">See Also</span></span>  
 <span data-ttu-id="6f444-157">[Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-157">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="6f444-158"> [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-158"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="6f444-159"> [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-159"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="6f444-160"> [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-160"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="6f444-161"> [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-161"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="6f444-162"> [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="6f444-162"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="6f444-163"> [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="6f444-163"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
