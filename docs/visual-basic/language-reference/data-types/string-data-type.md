---
title: "String, type de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90f126a5cca36969617446e81a8d13434e39df75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="6bd53-102">String, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bd53-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="6bd53-103">Contient des séquences de points de code de non signé 16 bits (2 octets) cette plage dans une valeur comprise entre 0 et 65 535.</span><span class="sxs-lookup"><span data-stu-id="6bd53-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="6bd53-104">Chaque *point de code*, ou le code de caractère, représente un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bd53-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="6bd53-105">Une chaîne peut contenir de 0 à environ deux milliards (2 ^ 31) caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bd53-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bd53-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="6bd53-106">Remarks</span></span>  
 <span data-ttu-id="6bd53-107">Utilisez le `String` type de données pour contenir plusieurs caractères sans les charges de gestion tableau de `Char()`, un tableau de `Char` éléments.</span><span class="sxs-lookup"><span data-stu-id="6bd53-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="6bd53-108">La valeur par défaut `String` est `Nothing` (une référence null).</span><span class="sxs-lookup"><span data-stu-id="6bd53-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="6bd53-109">Notez que cela n’est pas identique à la chaîne vide (valeur `""`).</span><span class="sxs-lookup"><span data-stu-id="6bd53-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="6bd53-110">Caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="6bd53-110">Unicode Characters</span></span>  
 <span data-ttu-id="6bd53-111">Les premiers points de 128 code (0 à 127) Unicode correspondent aux lettres et des symboles sur un clavier américain standard.</span><span class="sxs-lookup"><span data-stu-id="6bd53-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="6bd53-112">Ces premiers points de 128 code sont les mêmes que ceux du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="6bd53-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="6bd53-113">Les deuxième 128 points de code (128 à 255) représentent des caractères spéciaux, tels que des lettres de l’alphabet de latines, les accents, les symboles monétaires et les fractions.</span><span class="sxs-lookup"><span data-stu-id="6bd53-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="6bd53-114">Unicode utilise les points de code restants (256-65 535) pour une large gamme de symboles.</span><span class="sxs-lookup"><span data-stu-id="6bd53-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="6bd53-115">Cela inclut les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="6bd53-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="6bd53-116">Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur un caractère dans un `String` variable pour déterminer sa classification Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bd53-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="6bd53-117">Exigences relatives au format</span><span class="sxs-lookup"><span data-stu-id="6bd53-117">Format Requirements</span></span>  
 <span data-ttu-id="6bd53-118">Vous devez placer un `String` littérale entre guillemets (`" "`).</span><span class="sxs-lookup"><span data-stu-id="6bd53-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="6bd53-119">Si vous devez inclure un guillemet comme l’un des caractères dans la chaîne, vous utilisez deux guillemets contigus (`""`).</span><span class="sxs-lookup"><span data-stu-id="6bd53-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="6bd53-120">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="6bd53-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="6bd53-121">Notez que les guillemets contigus qui représentent un guillemet dans la chaîne sont indépendants des guillemets qui commencent et terminent le `String` littéral.</span><span class="sxs-lookup"><span data-stu-id="6bd53-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="6bd53-122">Manipulations de chaînes</span><span class="sxs-lookup"><span data-stu-id="6bd53-122">String Manipulations</span></span>  
 <span data-ttu-id="6bd53-123">Une fois que vous assignez une chaîne à un `String` variable, cette chaîne est *immuable*, ce qui signifie que vous ne pouvez pas modifier sa longueur ou son contenu.</span><span class="sxs-lookup"><span data-stu-id="6bd53-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="6bd53-124">Lorsque vous modifiez une chaîne en aucune façon, Visual Basic crée une nouvelle chaîne et abandonne la précédente.</span><span class="sxs-lookup"><span data-stu-id="6bd53-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="6bd53-125">Le `String` variable puis pointe vers la nouvelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="6bd53-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="6bd53-126">Vous pouvez manipuler le contenu d’un `String` variable à l’aide de diverses fonctions de chaîne.</span><span class="sxs-lookup"><span data-stu-id="6bd53-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="6bd53-127">L’exemple suivant illustre la <xref:Microsoft.VisualBasic.Strings.Left%2A> (fonction)</span><span class="sxs-lookup"><span data-stu-id="6bd53-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="6bd53-128">Une chaîne créée par un autre composant peut être remplie avec les espaces à gauche ou.</span><span class="sxs-lookup"><span data-stu-id="6bd53-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="6bd53-129">Si vous recevez une telle chaîne, vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, et <xref:Microsoft.VisualBasic.Strings.RTrim%2A> fonctions pour supprimer ces espaces.</span><span class="sxs-lookup"><span data-stu-id="6bd53-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="6bd53-130">Pour plus d’informations sur les manipulations de chaînes, consultez [chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bd53-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="6bd53-131">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="6bd53-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="6bd53-132">**Nombres négatifs.**</span><span class="sxs-lookup"><span data-stu-id="6bd53-132">**Negative Numbers.**</span></span> <span data-ttu-id="6bd53-133">Souvenez-vous que les caractères stockés par `String` ne sont pas signés et ne peut pas représenter des valeurs négatives.</span><span class="sxs-lookup"><span data-stu-id="6bd53-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="6bd53-134">Dans tous les cas, vous ne devez pas utiliser `String` pour contenir des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="6bd53-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="6bd53-135">**Considérations sur l’interopérabilité.**</span><span class="sxs-lookup"><span data-stu-id="6bd53-135">**Interop Considerations.**</span></span> <span data-ttu-id="6bd53-136">Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les chaînes de caractères possèdent une largeur de données différente (8 bits) dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="6bd53-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="6bd53-137">Si vous passez un argument de chaîne de caractères 8 bits à un tel composant, déclarez-le en tant que `Byte()`, un tableau de `Byte` éléments, au lieu de `String` dans votre nouveau code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6bd53-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="6bd53-138">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="6bd53-138">**Type Characters.**</span></span> <span data-ttu-id="6bd53-139">L’ajout du caractère de type identificateur `$` à n’importe quel identificateur force ce dernier à la `String` type de données.</span><span class="sxs-lookup"><span data-stu-id="6bd53-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="6bd53-140">`String`n’a aucun caractère de type de littéral.</span><span class="sxs-lookup"><span data-stu-id="6bd53-140">`String` has no literal type character.</span></span> <span data-ttu-id="6bd53-141">Toutefois, le compilateur traite les littéraux compris entre guillemets (`" "`) en tant que `String`.</span><span class="sxs-lookup"><span data-stu-id="6bd53-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="6bd53-142">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="6bd53-142">**Framework Type.**</span></span> <span data-ttu-id="6bd53-143">Le type correspondant dans le .NET Framework est la <xref:System.String?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="6bd53-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd53-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bd53-144">See Also</span></span>  
 <xref:System.String?displayProperty=nameWithType>  
 [<span data-ttu-id="6bd53-145">Types de données</span><span class="sxs-lookup"><span data-stu-id="6bd53-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6bd53-146">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="6bd53-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="6bd53-147">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="6bd53-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="6bd53-148">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="6bd53-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="6bd53-149">Guide pratique : appeler une fonction Windows qui possède des types non signés</span><span class="sxs-lookup"><span data-stu-id="6bd53-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="6bd53-150">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="6bd53-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
