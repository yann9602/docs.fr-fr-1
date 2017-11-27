---
title: Mid, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61d812ef91acc65728b04efc9aa99e3975e71d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mid-statement"></a><span data-ttu-id="3c1af-102">Mid, instruction</span><span class="sxs-lookup"><span data-stu-id="3c1af-102">Mid Statement</span></span>
<span data-ttu-id="3c1af-103">Remplace un nombre spécifié de caractères dans un `String` variable avec des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="3c1af-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c1af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c1af-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="3c1af-105">Composants</span><span class="sxs-lookup"><span data-stu-id="3c1af-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="3c1af-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c1af-106">Required.</span></span> <span data-ttu-id="3c1af-107">Nom de la `String` variable à modifier.</span><span class="sxs-lookup"><span data-stu-id="3c1af-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="3c1af-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c1af-108">Required.</span></span> <span data-ttu-id="3c1af-109">`Integer`expression.</span><span class="sxs-lookup"><span data-stu-id="3c1af-109">`Integer` expression.</span></span> <span data-ttu-id="3c1af-110">Position du caractère dans `Target` où commence le remplacement de texte.</span><span class="sxs-lookup"><span data-stu-id="3c1af-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="3c1af-111">`Start`utilise un index de base un.</span><span class="sxs-lookup"><span data-stu-id="3c1af-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="3c1af-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="3c1af-112">Optional.</span></span> <span data-ttu-id="3c1af-113">`Integer`expression.</span><span class="sxs-lookup"><span data-stu-id="3c1af-113">`Integer` expression.</span></span> <span data-ttu-id="3c1af-114">Nombre de caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="3c1af-114">Number of characters to replace.</span></span> <span data-ttu-id="3c1af-115">Si omis, toutes les `String` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3c1af-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="3c1af-116">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3c1af-116">Required.</span></span> <span data-ttu-id="3c1af-117">`String`Expression qui remplace une partie de `Target`.</span><span class="sxs-lookup"><span data-stu-id="3c1af-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="3c1af-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3c1af-118">Exceptions</span></span>  
  
|<span data-ttu-id="3c1af-119">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="3c1af-119">Exception type</span></span>|<span data-ttu-id="3c1af-120">Condition</span><span class="sxs-lookup"><span data-stu-id="3c1af-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="3c1af-121">`Start`< = 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="3c1af-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c1af-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="3c1af-122">Remarks</span></span>  
 <span data-ttu-id="3c1af-123">Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.</span><span class="sxs-lookup"><span data-stu-id="3c1af-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="3c1af-124">Visual Basic propose une <xref:Microsoft.VisualBasic.Strings.Mid%2A> (fonction) et un `Mid` instruction.</span><span class="sxs-lookup"><span data-stu-id="3c1af-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="3c1af-125">Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères lors de la `Mid` instruction remplace les caractères.</span><span class="sxs-lookup"><span data-stu-id="3c1af-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="3c1af-126">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="3c1af-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c1af-127">La `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets, plutôt que des caractères.</span><span class="sxs-lookup"><span data-stu-id="3c1af-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="3c1af-128">Il est utilisé principalement pour la conversion de chaînes dans les applications les caractères codés sur deux octets (DBCS) de jeu.</span><span class="sxs-lookup"><span data-stu-id="3c1af-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="3c1af-129">Toutes les chaînes Visual Basic sont au format Unicode, et `MidB` n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3c1af-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c1af-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="3c1af-130">Example</span></span>  
 <span data-ttu-id="3c1af-131">Cet exemple utilise la `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable de chaîne de caractères à partir d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="3c1af-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="3c1af-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3c1af-132">Requirements</span></span>  
 <span data-ttu-id="3c1af-133">**Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="3c1af-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="3c1af-134">**Module :**`Strings`</span><span class="sxs-lookup"><span data-stu-id="3c1af-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="3c1af-135">**Assembly :** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c1af-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1af-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c1af-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="3c1af-137">Chaînes</span><span class="sxs-lookup"><span data-stu-id="3c1af-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="3c1af-138">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c1af-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
