---
title: "Exemple d'expression régulière : recherche de valeurs HREF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: fae2c15b-7adf-4b15-b118-58eb3906994f
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bc9db7317c7a73f70a2cb83322b8b3a4c3771b9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-example-scanning-for-hrefs"></a><span data-ttu-id="52993-102">Exemple d'expression régulière : recherche de valeurs HREF</span><span class="sxs-lookup"><span data-stu-id="52993-102">Regular Expression Example: Scanning for HREFs</span></span>
<span data-ttu-id="52993-103">L’exemple suivant recherche une chaîne d’entrée et affiche toutes les valeurs href="…" et leurs emplacements dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="52993-103">The following example searches an input string and displays all the href="…" values and their locations in the string.</span></span>  
  
## <a name="the-regex-object"></a><span data-ttu-id="52993-104">Objet Regex</span><span class="sxs-lookup"><span data-stu-id="52993-104">The Regex Object</span></span>  
 <span data-ttu-id="52993-105">Étant donné que la `DumpHRefs` méthode peut être appelée plusieurs fois à partir du code utilisateur, il utilise le `static` (`Shared` en Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="52993-105">Because the `DumpHRefs` method can be called multiple times from user code, it uses the `static` (`Shared` in Visual Basic) <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="52993-106">Cela permet au moteur d’expression régulière pour mettre en cache de l’expression régulière et évite d’instanciation d’un nouvel <xref:System.Text.RegularExpressions.Regex> objet chaque fois que la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="52993-106">This enables the regular expression engine to cache the regular expression and avoids the overhead of instantiating a new <xref:System.Text.RegularExpressions.Regex> object each time the method is called.</span></span> <span data-ttu-id="52993-107">A <xref:System.Text.RegularExpressions.Match> objet est ensuite utilisé pour itérer sur toutes les correspondances dans la chaîne.</span><span class="sxs-lookup"><span data-stu-id="52993-107">A <xref:System.Text.RegularExpressions.Match> object is then used to iterate through all matches in the string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#1)]
 [!code-vb[RegularExpressions.Examples.HREF#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#1)]  
  
 <span data-ttu-id="52993-108">L’exemple suivant illustre un appel à la méthode `DumpHRefs`.</span><span class="sxs-lookup"><span data-stu-id="52993-108">The following example then illustrates a call to the `DumpHRefs` method.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.HREF#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.HREF/cs/example.cs#2)]
 [!code-vb[RegularExpressions.Examples.HREF#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.HREF/vb/example.vb#2)]  
  
 <span data-ttu-id="52993-109">Le modèle d'expression régulière `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` est interprété comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="52993-109">The regular expression pattern `href\s*=\s*(?:["'](?<1>[^"']*)["']|(?<1>\S+))` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="52993-110">Modèle</span><span class="sxs-lookup"><span data-stu-id="52993-110">Pattern</span></span>|<span data-ttu-id="52993-111">Description</span><span class="sxs-lookup"><span data-stu-id="52993-111">Description</span></span>|  
|-------------|-----------------|  
|`href`|<span data-ttu-id="52993-112">Correspond à la chaîne littérale « href ».</span><span class="sxs-lookup"><span data-stu-id="52993-112">Match the literal string "href".</span></span> <span data-ttu-id="52993-113">La recherche de correspondance ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="52993-113">The match is case-insensitive.</span></span>|  
|`\s*`|<span data-ttu-id="52993-114">Correspond à zéro, un ou plusieurs espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="52993-114">Match zero or more white-space characters.</span></span>|  
|`=`|<span data-ttu-id="52993-115">Mettre en correspondance le signe égal.</span><span class="sxs-lookup"><span data-stu-id="52993-115">Match the equals sign.</span></span>|  
|`\s*`|<span data-ttu-id="52993-116">Correspond à zéro, un ou plusieurs espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="52993-116">Match zero or more white-space characters.</span></span>|  
|`(?:["'](?<1>[^"']*)"&#124;(?<1>\S+))`|<span data-ttu-id="52993-117">Correspond à une des valeurs suivantes sans affecter le résultat à un groupe capturé :</span><span class="sxs-lookup"><span data-stu-id="52993-117">Match one of the following without assigning the result to a captured group:</span></span><br /><br /> <span data-ttu-id="52993-118">-Un guillemet ou l’apostrophe, suivie de zéro ou plusieurs occurrences de n’importe quel caractère autre qu’un guillemet ou l’apostrophe, suivi par une apostrophe ou un guillemet.</span><span class="sxs-lookup"><span data-stu-id="52993-118">-   A quotation mark or apostrophe, followed by zero or more occurrences of any character other than a quotation mark or apostrophe, followed by a quotation mark or apostrophe.</span></span> <span data-ttu-id="52993-119">Le groupe nommé `1` est inclus dans ce modèle.</span><span class="sxs-lookup"><span data-stu-id="52993-119">The group named `1` is included in this pattern.</span></span><br /><span data-ttu-id="52993-120">-Un ou plusieurs caractères autre qu’un espace blanc.</span><span class="sxs-lookup"><span data-stu-id="52993-120">-   One or more non-white-space characters.</span></span> <span data-ttu-id="52993-121">Le groupe nommé `1` est inclus dans ce modèle.</span><span class="sxs-lookup"><span data-stu-id="52993-121">The group named `1` is included in this pattern.</span></span>|  
|`(?<1>[^"']*)`|<span data-ttu-id="52993-122">Affecte zéro, une ou plusieurs occurrences de tout caractère autre qu’un guillemet ou une apostrophe au groupe de capture nommé `1`.</span><span class="sxs-lookup"><span data-stu-id="52993-122">Assign zero or more occurrences of any character other than a quotation mark or apostrophe to the capturing group named `1`.</span></span>|  
|`"(?<1>\S+)`|<span data-ttu-id="52993-123">Affecte un ou plusieurs caractères non espace blanc au groupe de capture nommé `1`.</span><span class="sxs-lookup"><span data-stu-id="52993-123">Assign one or more non-white-space characters to the capturing group named `1`.</span></span>|  
  
## <a name="match-result-class"></a><span data-ttu-id="52993-124">Classe de résultats Match</span><span class="sxs-lookup"><span data-stu-id="52993-124">Match Result Class</span></span>  
 <span data-ttu-id="52993-125">Les résultats d’une recherche sont stockés dans le <xref:System.Text.RegularExpressions.Match> (classe), qui permet d’accéder à toutes les sous-chaînes extraites par la recherche.</span><span class="sxs-lookup"><span data-stu-id="52993-125">The results of a search are stored in the <xref:System.Text.RegularExpressions.Match> class, which provides access to all the substrings extracted by the search.</span></span> <span data-ttu-id="52993-126">Il conserve également la chaîne recherchée et l’expression régulière utilisée, afin qu’il peut appeler le <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> méthode pour effectuer une nouvelle recherche commençant où la dernière s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="52993-126">It also remembers the string being searched and the regular expression being used, so it can call the <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> method to perform another search starting where the last one ended.</span></span>  
  
## <a name="explicitly-named-captures"></a><span data-ttu-id="52993-127">Captures explicitement nommées</span><span class="sxs-lookup"><span data-stu-id="52993-127">Explicitly Named Captures</span></span>  
 <span data-ttu-id="52993-128">Dans les expressions régulières classiques, les parenthèses de capture sont automatiquement numérotées dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="52993-128">In traditional regular expressions, capturing parentheses are automatically numbered sequentially.</span></span> <span data-ttu-id="52993-129">Cela génère deux problèmes.</span><span class="sxs-lookup"><span data-stu-id="52993-129">This leads to two problems.</span></span> <span data-ttu-id="52993-130">Tout d’abord, si une expression régulière est modifiée par l’insertion ou la suppression d’un jeu de parenthèses, tout code qui fait référence aux captures numérotées doit être réécrit pour refléter la nouvelle numérotation.</span><span class="sxs-lookup"><span data-stu-id="52993-130">First, if a regular expression is modified by inserting or removing a set of parentheses, all code that refers to the numbered captures must be rewritten to reflect the new numbering.</span></span> <span data-ttu-id="52993-131">Ensuite, étant donné que différents jeux de parenthèses sont souvent utilisés pour fournir deux expressions différentes pour une correspondance acceptable, il peut s’avérer difficile de déterminer laquelle des deux expressions en fait retourné un résultat.</span><span class="sxs-lookup"><span data-stu-id="52993-131">Second, because different sets of parentheses often are used to provide two alternative expressions for an acceptable match, it might be difficult to determine which of the two expressions actually returned a result.</span></span>  
  
 <span data-ttu-id="52993-132">Pour résoudre ces problèmes, le <xref:System.Text.RegularExpressions.Regex> classe prend en charge la syntaxe `(?<name>…)` permettant de capturer une correspondance dans un emplacement spécifié (l’emplacement peut être nommé à l’aide d’une chaîne ou un entier ; entiers peuvent être rappelées plus rapidement).</span><span class="sxs-lookup"><span data-stu-id="52993-132">To address these problems, the <xref:System.Text.RegularExpressions.Regex> class supports the syntax `(?<name>…)` for capturing a match into a specified slot (the slot can be named using a string or an integer; integers can be recalled more quickly).</span></span> <span data-ttu-id="52993-133">Ainsi, les autres correspondances de la même chaîne peuvent toutes être dirigées vers le même emplacement.</span><span class="sxs-lookup"><span data-stu-id="52993-133">Thus, alternative matches for the same string all can be directed to the same place.</span></span> <span data-ttu-id="52993-134">En cas de conflit, la dernière correspondance placée dans un emplacement est la correspondance correcte.</span><span class="sxs-lookup"><span data-stu-id="52993-134">In case of a conflict, the last match dropped into a slot is the successful match.</span></span> <span data-ttu-id="52993-135">(Toutefois, la liste complète des différentes correspondances pour un seul emplacement est disponible.</span><span class="sxs-lookup"><span data-stu-id="52993-135">(However, a complete list of multiple matches for a single slot is available.</span></span> <span data-ttu-id="52993-136">Consultez le <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection pour plus d’informations.)</span><span class="sxs-lookup"><span data-stu-id="52993-136">See the <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> collection for details.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52993-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52993-137">See Also</span></span>  
 [<span data-ttu-id="52993-138">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="52993-138">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
