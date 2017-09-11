---
title: Mid, instruction | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e94500c8bd7f2c6351c91ba028c1ad6d8d3dd4c3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="mid-statement"></a><span data-ttu-id="623da-102">Mid, instruction</span><span class="sxs-lookup"><span data-stu-id="623da-102">Mid Statement</span></span>
<span data-ttu-id="623da-103">Remplace un nombre spécifié de caractères dans un `String` variable avec des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="623da-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="623da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="623da-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="623da-105">Composants</span><span class="sxs-lookup"><span data-stu-id="623da-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="623da-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="623da-106">Required.</span></span> <span data-ttu-id="623da-107">Nom de la `String` variable à modifier.</span><span class="sxs-lookup"><span data-stu-id="623da-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="623da-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="623da-108">Required.</span></span> <span data-ttu-id="623da-109">`Integer`expression.</span><span class="sxs-lookup"><span data-stu-id="623da-109">`Integer` expression.</span></span> <span data-ttu-id="623da-110">Position du caractère dans `Target` où commence le remplacement de texte.</span><span class="sxs-lookup"><span data-stu-id="623da-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="623da-111">`Start`utilise un index de base&1;.</span><span class="sxs-lookup"><span data-stu-id="623da-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="623da-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="623da-112">Optional.</span></span> <span data-ttu-id="623da-113">`Integer`expression.</span><span class="sxs-lookup"><span data-stu-id="623da-113">`Integer` expression.</span></span> <span data-ttu-id="623da-114">Nombre de caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="623da-114">Number of characters to replace.</span></span> <span data-ttu-id="623da-115">Si omis, tous les `String` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="623da-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="623da-116">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="623da-116">Required.</span></span> <span data-ttu-id="623da-117">`String`Expression qui remplace une partie de `Target`.</span><span class="sxs-lookup"><span data-stu-id="623da-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="623da-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="623da-118">Exceptions</span></span>  
  
|<span data-ttu-id="623da-119">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="623da-119">Exception type</span></span>|<span data-ttu-id="623da-120">Condition</span><span class="sxs-lookup"><span data-stu-id="623da-120">Condition</span></span>|  
|--------------------|---------------|  
|<span data-ttu-id="623da-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="623da-121"><xref:System.ArgumentException></span></span>|<span data-ttu-id="623da-122">`Start`<= 0="" or=""></=>`Length`< 0.></ 0.></span><span class="sxs-lookup"><span data-stu-id="623da-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="623da-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="623da-123">Remarks</span></span>  
 <span data-ttu-id="623da-124">Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.</span><span class="sxs-lookup"><span data-stu-id="623da-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="623da-125">Visual Basic a un <xref:Microsoft.VisualBasic.Strings.Mid%2A>fonction et un `Mid` relevé.</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="623da-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="623da-126">Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères pendant que la `Mid` instruction remplace les caractères.</span><span class="sxs-lookup"><span data-stu-id="623da-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="623da-127">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="623da-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="623da-128">La `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets, plutôt que des caractères.</span><span class="sxs-lookup"><span data-stu-id="623da-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="623da-129">Il est utilisé principalement pour la conversion de chaînes dans les applications codés sur deux octets (DBCS) de jeu.</span><span class="sxs-lookup"><span data-stu-id="623da-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="623da-130">Toutes les chaînes Visual Basic sont en Unicode, et `MidB` n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="623da-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="623da-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="623da-131">Example</span></span>  
 <span data-ttu-id="623da-132">Cet exemple utilise la `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable de chaîne de caractères à partir d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="623da-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 <span data-ttu-id="623da-133">[!code-vb[VbVbalrStrings n °&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="623da-133">[!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="623da-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="623da-134">Requirements</span></span>  
 <span data-ttu-id="623da-135">**Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="623da-135">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="623da-136">**Module :**`Strings`</span><span class="sxs-lookup"><span data-stu-id="623da-136">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="623da-137">**Assembly :**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span><span class="sxs-lookup"><span data-stu-id="623da-137">**Assembly:** [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="623da-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="623da-138">See Also</span></span>  
 <span data-ttu-id="623da-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="623da-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
<span data-ttu-id="623da-140"> [Chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="623da-140"> [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md) </span></span>  
<span data-ttu-id="623da-141"> [Introduction aux chaînes en Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="623da-141"> [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
