---
title: "Littéraux (F#)"
description: "En savoir plus sur les types de littéral dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="e4ff8-104">Littéraux</span><span class="sxs-lookup"><span data-stu-id="e4ff8-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="e4ff8-105">Les liens de référence des API dans cet article vous permettront MSDN (pour l’instant).</span><span class="sxs-lookup"><span data-stu-id="e4ff8-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="e4ff8-106">Cette rubrique fournit une table qui montre comment spécifier le type d’un littéral en F #.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="e4ff8-107">Types de littéral</span><span class="sxs-lookup"><span data-stu-id="e4ff8-107">Literal Types</span></span>
<span data-ttu-id="e4ff8-108">Le tableau suivant indique les types de littéraux en F #.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="e4ff8-109">Les caractères qui représentent des chiffres en notation hexadécimale ne sont pas la casse ; les caractères qui identifient le type respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="e4ff8-110">Type</span><span class="sxs-lookup"><span data-stu-id="e4ff8-110">Type</span></span>|<span data-ttu-id="e4ff8-111">Description</span><span class="sxs-lookup"><span data-stu-id="e4ff8-111">Description</span></span>|<span data-ttu-id="e4ff8-112">Préfixe ou suffixe</span><span class="sxs-lookup"><span data-stu-id="e4ff8-112">Suffix or prefix</span></span>|<span data-ttu-id="e4ff8-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="e4ff8-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="e4ff8-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="e4ff8-114">sbyte</span></span>|<span data-ttu-id="e4ff8-115">Entier signé 8 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-115">signed 8-bit integer</span></span>|<span data-ttu-id="e4ff8-116">o</span><span class="sxs-lookup"><span data-stu-id="e4ff8-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="e4ff8-117">byte</span><span class="sxs-lookup"><span data-stu-id="e4ff8-117">byte</span></span>|<span data-ttu-id="e4ff8-118">nombre non signé 8 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="e4ff8-119">UY</span><span class="sxs-lookup"><span data-stu-id="e4ff8-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="e4ff8-120">int16</span><span class="sxs-lookup"><span data-stu-id="e4ff8-120">int16</span></span>|<span data-ttu-id="e4ff8-121">Entier signé 16 bits.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-121">signed 16-bit integer</span></span>|<span data-ttu-id="e4ff8-122">s</span><span class="sxs-lookup"><span data-stu-id="e4ff8-122">s</span></span>|`86s`|
|<span data-ttu-id="e4ff8-123">uint16</span><span class="sxs-lookup"><span data-stu-id="e4ff8-123">uint16</span></span>|<span data-ttu-id="e4ff8-124">nombre non signé 16 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="e4ff8-125">us</span><span class="sxs-lookup"><span data-stu-id="e4ff8-125">us</span></span>|`86us`|
|<span data-ttu-id="e4ff8-126">int</span><span class="sxs-lookup"><span data-stu-id="e4ff8-126">int</span></span><br /><br /><span data-ttu-id="e4ff8-127">int32</span><span class="sxs-lookup"><span data-stu-id="e4ff8-127">int32</span></span>|<span data-ttu-id="e4ff8-128">Entier signé 32 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-128">signed 32-bit integer</span></span>|<span data-ttu-id="e4ff8-129">l ou none</span><span class="sxs-lookup"><span data-stu-id="e4ff8-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="e4ff8-130">uint</span><span class="sxs-lookup"><span data-stu-id="e4ff8-130">uint</span></span><br /><br /><span data-ttu-id="e4ff8-131">uint32</span><span class="sxs-lookup"><span data-stu-id="e4ff8-131">uint32</span></span>|<span data-ttu-id="e4ff8-132">nombre de naturel 32 bits non signé</span><span class="sxs-lookup"><span data-stu-id="e4ff8-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="e4ff8-133">u ou ul</span><span class="sxs-lookup"><span data-stu-id="e4ff8-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="e4ff8-134">unativeint</span><span class="sxs-lookup"><span data-stu-id="e4ff8-134">unativeint</span></span>|<span data-ttu-id="e4ff8-135">pointeur natif sous forme de nombre naturel non signé</span><span class="sxs-lookup"><span data-stu-id="e4ff8-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="e4ff8-136">Annuler</span><span class="sxs-lookup"><span data-stu-id="e4ff8-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="e4ff8-137">int64</span><span class="sxs-lookup"><span data-stu-id="e4ff8-137">int64</span></span>|<span data-ttu-id="e4ff8-138">Entier signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-138">signed 64-bit integer</span></span>|<span data-ttu-id="e4ff8-139">L</span><span class="sxs-lookup"><span data-stu-id="e4ff8-139">L</span></span>|`86L`|
|<span data-ttu-id="e4ff8-140">uint64</span><span class="sxs-lookup"><span data-stu-id="e4ff8-140">uint64</span></span>|<span data-ttu-id="e4ff8-141">nombre non signé 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="e4ff8-142">UL</span><span class="sxs-lookup"><span data-stu-id="e4ff8-142">UL</span></span>|`86UL`|
|<span data-ttu-id="e4ff8-143">float32 unique,</span><span class="sxs-lookup"><span data-stu-id="e4ff8-143">single, float32</span></span>|<span data-ttu-id="e4ff8-144">nombre à virgule flottante 32 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-144">32-bit floating point number</span></span>|<span data-ttu-id="e4ff8-145">F ou f</span><span class="sxs-lookup"><span data-stu-id="e4ff8-145">F or f</span></span>|<span data-ttu-id="e4ff8-146">`4.14F` ou `4.14f`</span><span class="sxs-lookup"><span data-stu-id="e4ff8-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="e4ff8-147">saut de ligne</span><span class="sxs-lookup"><span data-stu-id="e4ff8-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="e4ff8-148">type float ; Double</span><span class="sxs-lookup"><span data-stu-id="e4ff8-148">float; double</span></span>|<span data-ttu-id="e4ff8-149">nombre à virgule flottante 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-149">64-bit floating point number</span></span>|<span data-ttu-id="e4ff8-150">aucun</span><span class="sxs-lookup"><span data-stu-id="e4ff8-150">none</span></span>|<span data-ttu-id="e4ff8-151">`4.14`ou `2.3E+32` ou`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="e4ff8-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="e4ff8-152">SAUT DE LIGNE</span><span class="sxs-lookup"><span data-stu-id="e4ff8-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="e4ff8-153">bigint</span><span class="sxs-lookup"><span data-stu-id="e4ff8-153">bigint</span></span>|<span data-ttu-id="e4ff8-154">entier non limité à la représentation sous forme de 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4ff8-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="e4ff8-155">I</span><span class="sxs-lookup"><span data-stu-id="e4ff8-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="e4ff8-156">decimal</span><span class="sxs-lookup"><span data-stu-id="e4ff8-156">decimal</span></span>|<span data-ttu-id="e4ff8-157">nombre de fractions de seconde représentée comme un point fixe ou d’un nombre rationnel</span><span class="sxs-lookup"><span data-stu-id="e4ff8-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="e4ff8-158">M ou m</span><span class="sxs-lookup"><span data-stu-id="e4ff8-158">M or m</span></span>|<span data-ttu-id="e4ff8-159">`0.7833M` ou `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="e4ff8-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="e4ff8-160">Char</span><span class="sxs-lookup"><span data-stu-id="e4ff8-160">Char</span></span>|<span data-ttu-id="e4ff8-161">caractère Unicode</span><span class="sxs-lookup"><span data-stu-id="e4ff8-161">Unicode character</span></span>|<span data-ttu-id="e4ff8-162">aucun</span><span class="sxs-lookup"><span data-stu-id="e4ff8-162">none</span></span>|`'a'`|
|<span data-ttu-id="e4ff8-163">Chaîne</span><span class="sxs-lookup"><span data-stu-id="e4ff8-163">String</span></span>|<span data-ttu-id="e4ff8-164">chaîne Unicode</span><span class="sxs-lookup"><span data-stu-id="e4ff8-164">Unicode string</span></span>|<span data-ttu-id="e4ff8-165">aucun</span><span class="sxs-lookup"><span data-stu-id="e4ff8-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="e4ff8-166">ou</span><span class="sxs-lookup"><span data-stu-id="e4ff8-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="e4ff8-167">ou</span><span class="sxs-lookup"><span data-stu-id="e4ff8-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="e4ff8-168">ou</span><span class="sxs-lookup"><span data-stu-id="e4ff8-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="e4ff8-169">Voir aussi [chaînes](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="e4ff8-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="e4ff8-170">byte</span><span class="sxs-lookup"><span data-stu-id="e4ff8-170">byte</span></span>|<span data-ttu-id="e4ff8-171">Caractère ASCII</span><span class="sxs-lookup"><span data-stu-id="e4ff8-171">ASCII character</span></span>|<span data-ttu-id="e4ff8-172">B</span><span class="sxs-lookup"><span data-stu-id="e4ff8-172">B</span></span>|`'a'B`|
|<span data-ttu-id="e4ff8-173">byte[]</span><span class="sxs-lookup"><span data-stu-id="e4ff8-173">byte[]</span></span>|<span data-ttu-id="e4ff8-174">Chaîne ASCII</span><span class="sxs-lookup"><span data-stu-id="e4ff8-174">ASCII string</span></span>|<span data-ttu-id="e4ff8-175">B</span><span class="sxs-lookup"><span data-stu-id="e4ff8-175">B</span></span>|`"text"B`|
|<span data-ttu-id="e4ff8-176">[] String ou byte</span><span class="sxs-lookup"><span data-stu-id="e4ff8-176">String or byte[]</span></span>|<span data-ttu-id="e4ff8-177">chaîne textuelle</span><span class="sxs-lookup"><span data-stu-id="e4ff8-177">verbatim string</span></span>|<span data-ttu-id="e4ff8-178">préfixe @</span><span class="sxs-lookup"><span data-stu-id="e4ff8-178">@ prefix</span></span>|<span data-ttu-id="e4ff8-179">`@"\\server\share"`(Unicode)</span><span class="sxs-lookup"><span data-stu-id="e4ff8-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="e4ff8-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="e4ff8-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4ff8-181">Remarques</span><span class="sxs-lookup"><span data-stu-id="e4ff8-181">Remarks</span></span>
<span data-ttu-id="e4ff8-182">Chaînes Unicode peuvent contenir des encodages explicites que vous pouvez spécifier à l’aide de `\u` suivi d’un code hexadécimal 16 bits ou les encodages UTF-32 que vous pouvez spécifier à l’aide de `\U` suivi d’un code hexadécimal 32 bits qui représente un Unicode paire de substitution.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="e4ff8-183">À compter de F # 3.1, vous pouvez utiliser le `+` se connecter pour combiner des littéraux de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="e4ff8-184">Vous pouvez également utiliser l’opérateur de bits ou (`|||`) opérateur pour combiner les indicateurs de l’enum.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="e4ff8-185">Par exemple, le code suivant est autorisé dans F # 3.1 :</span><span class="sxs-lookup"><span data-stu-id="e4ff8-185">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="e4ff8-186">L’utilisation d’autres opérateurs de bits n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="e4ff8-187">Littéraux nommés</span><span class="sxs-lookup"><span data-stu-id="e4ff8-187">Named Literals</span></span>
<span data-ttu-id="e4ff8-188">Les valeurs qui sont destinés à être des constantes peuvent être marquées avec le [littéral](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribut.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="e4ff8-189">Cet attribut a pour effet de provoquer une valeur doit être compilé en tant que constante.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="e4ff8-190">Dans les expressions de critères spéciaux, les identificateurs qui commencent par les caractères minuscules sont toujours traités en tant que variables d’être lié, plutôt que comme des littéraux, par conséquent, vous devez généralement utiliser majuscules lorsque vous définissez des littéraux.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="e4ff8-191">Nombres entiers dans d’autres Bases</span><span class="sxs-lookup"><span data-stu-id="e4ff8-191">Integers In Other Bases</span></span>

<span data-ttu-id="e4ff8-192">Entiers signés de 32 bits peuvent également être spécifiés en hexadécimal, octal ou binaire à l’aide un `0x`, `0o` ou `0b` respectivement de préfixe.</span><span class="sxs-lookup"><span data-stu-id="e4ff8-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="e4ff8-193">Traits de soulignement dans les littéraux numériques</span><span class="sxs-lookup"><span data-stu-id="e4ff8-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="e4ff8-194">À compter de F # 4.1, vous pouvez séparer les chiffres par le caractère de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="e4ff8-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="e4ff8-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4ff8-195">See Also</span></span>

[<span data-ttu-id="e4ff8-196">Core.LiteralAttribute, classe</span><span class="sxs-lookup"><span data-stu-id="e4ff8-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
