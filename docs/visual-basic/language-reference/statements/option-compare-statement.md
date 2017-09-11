---
title: Option Compare (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 00618cd914c06b896d68b4074464af866f747895
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="option-compare-statement"></a><span data-ttu-id="e8976-102">Option Compare, instruction</span><span class="sxs-lookup"><span data-stu-id="e8976-102">Option Compare Statement</span></span>
<span data-ttu-id="e8976-103">Déclare la méthode de comparaison par défaut à utiliser lors de la comparaison de données de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="e8976-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8976-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="e8976-105">Composants</span><span class="sxs-lookup"><span data-stu-id="e8976-105">Parts</span></span>  
  
|<span data-ttu-id="e8976-106">Terme</span><span class="sxs-lookup"><span data-stu-id="e8976-106">Term</span></span>|<span data-ttu-id="e8976-107">Définition</span><span class="sxs-lookup"><span data-stu-id="e8976-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="e8976-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8976-108">Optional.</span></span> <span data-ttu-id="e8976-109">Se traduit par des comparaisons de chaînes basées sur un ordre de tri dérivé des représentations binaires internes des caractères.</span><span class="sxs-lookup"><span data-stu-id="e8976-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="e8976-110">Ce type de comparaison est utile surtout si les chaînes peuvent contenir des caractères qui ne doivent ne pas être interprétées comme du texte.</span><span class="sxs-lookup"><span data-stu-id="e8976-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="e8976-111">Dans ce cas, il convient de ne pas fausser les comparaisons avec des équivalences alphabétiques comme, par exemple, quand la casse n'est pas respectée.</span><span class="sxs-lookup"><span data-stu-id="e8976-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="e8976-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e8976-112">Optional.</span></span> <span data-ttu-id="e8976-113">Se traduit par des comparaisons de chaînes basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.</span><span class="sxs-lookup"><span data-stu-id="e8976-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="e8976-114">Ce type de comparaison est utile si vos chaînes contiennent toutes des caractères de texte et si vous voulez les comparer en prenant en compte les équivalences alphabétiques, c'est-à-dire des lettres très proches ou de casse différente.</span><span class="sxs-lookup"><span data-stu-id="e8976-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="e8976-115">Par exemple, vous pouvez faire en sorte que les caractères `A` et `a` soient considérés comme identiques et que les caractères `Ä` et `ä` précèdent `B` et `b`.</span><span class="sxs-lookup"><span data-stu-id="e8976-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8976-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="e8976-116">Remarks</span></span>  
 <span data-ttu-id="e8976-117">Si elle est utilisée, l'instruction `Option Compare` doit apparaître dans un fichier avant toute autre instruction de code source.</span><span class="sxs-lookup"><span data-stu-id="e8976-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="e8976-118">L'instruction `Option Compare` permet de spécifier la méthode de comparaison de chaînes (`Binary` ou `Text`).</span><span class="sxs-lookup"><span data-stu-id="e8976-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="e8976-119">La méthode de comparaison de texte par défaut est `Binary`.</span><span class="sxs-lookup"><span data-stu-id="e8976-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="e8976-120">Une comparaison de type `Binary` permet de comparer la valeur Unicode numérique de chaque caractère dans chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="e8976-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="e8976-121">Une comparaison de type `Text` permet de comparer chaque caractère Unicode selon sa signification lexicale dans la culture actuelle.</span><span class="sxs-lookup"><span data-stu-id="e8976-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="e8976-122">Dans Microsoft Windows, l'ordre de tri est déterminé par la page de code.</span><span class="sxs-lookup"><span data-stu-id="e8976-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="e8976-123">Pour plus d’informations, consultez [Pages de codes](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="e8976-123">For more information, see [Code Pages](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="e8976-124">Dans l'exemple suivant, les caractères de la page de codes Anglais/Européen (ANSI 1252) sont triés à l'aide de `Option Compare Binary`, qui génère un ordre de tri binaire standard.</span><span class="sxs-lookup"><span data-stu-id="e8976-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="e8976-125">Quand les mêmes caractères d'une même page de codes sont triés à l'aide de `Option Compare Text`, l'ordre de tri de texte suivant est généré.</span><span class="sxs-lookup"><span data-stu-id="e8976-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="e8976-126">En l'absence d'instruction Option Compare</span><span class="sxs-lookup"><span data-stu-id="e8976-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="e8976-127">Si le code source ne contient pas une `Option Compare` instruction, le **Option Compare** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e8976-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="e8976-128">Si vous utilisez le compilateur de ligne de commande, le paramètre spécifié par le [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) option du compilateur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e8976-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="e8976-129">Pour définir Option Compare dans l'IDE</span><span class="sxs-lookup"><span data-stu-id="e8976-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="e8976-130">Dans **l’Explorateur de solutions**, sélectionnez un projet.</span><span class="sxs-lookup"><span data-stu-id="e8976-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="e8976-131">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e8976-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e8976-132">Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="e8976-132">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="e8976-133">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="e8976-133">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e8976-134">Définissez la valeur de la **Option Compare** boîte.</span><span class="sxs-lookup"><span data-stu-id="e8976-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="e8976-135">Lorsque vous créez un projet, le **Option Compare** définition sur le **compiler** onglet est définie sur le **Option Compare** dans les **Options** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e8976-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="e8976-136">Pour modifier ce paramètre, dans le **outils** menu, cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="e8976-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="e8976-137">Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**.</span><span class="sxs-lookup"><span data-stu-id="e8976-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="e8976-138">Le paramètre par défaut initial dans **valeurs par défaut VB** est **binaire**.</span><span class="sxs-lookup"><span data-stu-id="e8976-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="e8976-139">Pour définir Option Compare sur la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e8976-139">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="e8976-140">Inclure les [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) option du compilateur dans le **vbc** commande.</span><span class="sxs-lookup"><span data-stu-id="e8976-140">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8976-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8976-141">Example</span></span>  
 <span data-ttu-id="e8976-142">L'exemple suivant utilise l'instruction `Option Compare` pour définir la comparaison binaire comme méthode de comparaison de chaînes par défaut.</span><span class="sxs-lookup"><span data-stu-id="e8976-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="e8976-143">Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Binary` et placez-la en haut du fichier source.</span><span class="sxs-lookup"><span data-stu-id="e8976-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="e8976-144">[!code-vb[VbVbalrStatements n °&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8976-144">[!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8976-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8976-145">Example</span></span>  
 <span data-ttu-id="e8976-146">L'exemple suivant utilise l'instruction `Option Compare` pour définir l'ordre de tri de texte sans respect de la casse comme méthode de comparaison de chaînes par défaut.</span><span class="sxs-lookup"><span data-stu-id="e8976-146">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="e8976-147">Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Text` et placez-la en haut du fichier source.</span><span class="sxs-lookup"><span data-stu-id="e8976-147">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="e8976-148">[!code-vb[VbVbalrStatements&#46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e8976-148">[!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8976-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8976-149">See Also</span></span>  
 <span data-ttu-id="e8976-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A></span><span class="sxs-lookup"><span data-stu-id="e8976-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></span></span>   
 <span data-ttu-id="e8976-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span><span class="sxs-lookup"><span data-stu-id="e8976-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span></span>   
 <span data-ttu-id="e8976-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A></span><span class="sxs-lookup"><span data-stu-id="e8976-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></span></span>   
 <span data-ttu-id="e8976-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="e8976-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="e8976-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A></span><span class="sxs-lookup"><span data-stu-id="e8976-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></span></span>   
<span data-ttu-id="e8976-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="e8976-156"> [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-156"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="e8976-157"> [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-157"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="e8976-158"> [LIKE (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-158"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="e8976-159"> [Fonctions de chaîne](../../../visual-basic/language-reference/functions/string-functions.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-159"> [String Functions](../../../visual-basic/language-reference/functions/string-functions.md) </span></span>  
<span data-ttu-id="e8976-160"> [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e8976-160"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="e8976-161"> [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e8976-161"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
