---
title: "Notions de base dans Visual Basic de chaîne | Documents Microsoft"
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
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
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
ms.openlocfilehash: 98c2707ef8aabc77951b21cfe9f4edcd3a88c863
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="e7bd4-102">Concepts de base des chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7bd4-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="e7bd4-103">Le type de données `String` représente une série de caractères (chacun représentant à son tour une instance du type de données `Char`).</span><span class="sxs-lookup"><span data-stu-id="e7bd4-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="e7bd4-104">Cette rubrique présente les concepts de base des chaînes en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="e7bd4-104">This topic introduces the basic concepts of strings in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="e7bd4-105">Variables de chaîne</span><span class="sxs-lookup"><span data-stu-id="e7bd4-105">String Variables</span></span>  
 <span data-ttu-id="e7bd4-106">Il est possible d'assigner à une instance de chaîne une valeur littérale représentant une série de caractères.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="e7bd4-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-107">For example:</span></span>  
  
 <span data-ttu-id="e7bd4-108">[!code-vb[VbVbalrStrings&#63;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-108">[!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-109">Une variable `String` peut également accepter une expression quelconque qui prend la valeur d'une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="e7bd4-110">En voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-110">Examples are shown below:</span></span>  
  
 <span data-ttu-id="e7bd4-111">[!code-vb[VbVbalrStrings&#64;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-111">[!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-112">Tout littéral assigné à une variable `String` doit être placé entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="e7bd4-112">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="e7bd4-113">Cela signifie que des guillemets dans une chaîne ne peuvent pas être représentés par des guillemets.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-113">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="e7bd4-114">Par exemple, le code suivant génère une erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-114">For example, the following code causes a compiler error:</span></span>  
  
 <span data-ttu-id="e7bd4-115">[!code-vb[VbVbalrStrings&#65;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-115">[!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-116">Ce code entraîne une erreur car le compilateur arrête la chaîne après les deuxièmes guillemets, et le reste de la chaîne est interprété comme du code.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-116">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="e7bd4-117">Pour résoudre ce problème, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interprète deux guillemets dans un littéral de chaîne comme des guillemets simples dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-117">To solve this problem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="e7bd4-118">L'exemple suivant illustre comment inclure correctement des guillemets dans une chaîne :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-118">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 <span data-ttu-id="e7bd4-119">[!code-vb[VbVbalrStrings&#66;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-119">[!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-120">Dans l'exemple précédent, les deux guillemets qui précèdent le mot `Look` deviennent des guillemets simples dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-120">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="e7bd4-121">Les trois guillemets à la fin de la ligne correspondent aux guillemets simples dans la chaîne et au caractère de fin de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-121">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="e7bd4-122">Les littéraux de chaîne peuvent contenir plusieurs lignes :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-122">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
  
```  
  
 <span data-ttu-id="e7bd4-123">La chaîne obtenue contient les séquences de saut de ligne que vous utilisiez dans votre littéral de chaîne (vbcr, vbcrlf, etc.).</span><span class="sxs-lookup"><span data-stu-id="e7bd4-123">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="e7bd4-124">Vous n'avez plus besoin d'utiliser l'ancienne solution de contournement :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-124">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="e7bd4-125">Caractères dans des chaînes</span><span class="sxs-lookup"><span data-stu-id="e7bd4-125">Characters in Strings</span></span>  
 <span data-ttu-id="e7bd4-126">Une chaîne peut être considérée comme une série de valeurs `Char` et le type `String` possède des fonctions intégrées qui vous permettent d'exécuter de nombreuses manipulations sur une chaîne qui ressemblent aux manipulations autorisées par les tableaux.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-126">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="e7bd4-127">Comme tous les tableaux dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], ce sont des tableaux de base zéro.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-127">Like all array in [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="e7bd4-128">Vous pouvez vous référer à un caractère spécifique dans une chaîne via la propriété `Chars`, ce qui permet d'accéder à un caractère à la position où il apparaît dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-128">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="e7bd4-129">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-129">For example:</span></span>  
  
 <span data-ttu-id="e7bd4-130">[!code-vb[VbVbalrStrings&#67;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-130">[!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-131">Dans l'exemple ci-dessus, la propriété `Chars` de la chaîne retourne le quatrième caractère de la chaîne, qui est `D`, et l'assigne à `myChar`.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-131">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="e7bd4-132">Vous pouvez également obtenir la longueur d'une chaîne particulière via la propriété `Length`.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-132">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="e7bd4-133">Si vous devez exécuter plusieurs manipulations de type tableau sur une chaîne, vous pouvez la convertir en tableau d'instances `Char` à l'aide de la fonction `ToCharArray` de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-133">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="e7bd4-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-134">For example:</span></span>  
  
 <span data-ttu-id="e7bd4-135">[!code-vb[VbVbalrStrings&#68;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-135">[!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-136">La variable `myArray` contient à présent un tableau de valeurs `Char`, dont chacune représente un caractère issu de `myString`.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-136">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="e7bd4-137">Immuabilité des chaînes</span><span class="sxs-lookup"><span data-stu-id="e7bd4-137">The Immutability of Strings</span></span>  
 <span data-ttu-id="e7bd4-138">Une chaîne est *immuable*, ce qui signifie que sa valeur ne peut pas être modifiée une fois qu’il a été créé.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-138">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="e7bd4-139">Toutefois, cela ne vous empêche pas d'assigner plusieurs valeurs à une variable de chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-139">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="e7bd4-140">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e7bd4-140">Consider the following example:</span></span>  
  
 <span data-ttu-id="e7bd4-141">[!code-vb[VbVbalrStrings&#69;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7bd4-141">[!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]</span></span>  
  
 <span data-ttu-id="e7bd4-142">Ici, une variable de chaîne est créée, une valeur lui est attribuée, puis sa valeur est modifiée.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-142">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="e7bd4-143">Plus spécifiquement, dans la première ligne, une instance de type `String` est créée et la valeur `This string is immutable` lui est attribuée.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-143">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="e7bd4-144">Dans la seconde ligne de l'exemple, une nouvelle instance est créée et la valeur `Or is it?` lui est attribuée. La variable de chaîne ignore sa référence à la première instance et stocke une référence à la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-144">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="e7bd4-145">Contrairement à d'autres types de données intrinsèques, `String` est un type référence.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-145">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="e7bd4-146">Quand une variable de type référence est passée en tant qu'argument à une fonction ou à une sous-routine, une référence à l'adresse mémoire où sont stockées les données est passée à la place de la valeur réelle de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-146">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="e7bd4-147">Ainsi, dans l'exemple précédent, le nom de la variable reste le même, mais il pointe vers une instance nouvelle et différente de la classe `String`, qui contient la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="e7bd4-147">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7bd4-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7bd4-148">See Also</span></span>  
 <span data-ttu-id="e7bd4-149">[Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span><span class="sxs-lookup"><span data-stu-id="e7bd4-149">[Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md) </span></span>  
<span data-ttu-id="e7bd4-150"> [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="e7bd4-150"> [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) </span></span>  
<span data-ttu-id="e7bd4-151"> [Type de données char](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="e7bd4-151"> [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="e7bd4-152"> [Opérations de chaînes de base](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span><span class="sxs-lookup"><span data-stu-id="e7bd4-152"> [Basic String Operations](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)</span></span>
