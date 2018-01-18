---
title: "Jeu de caractères en entrée (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13d291d3-e6bc-4719-b953-758b61a590b6
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d75d8c96d1cc028bed8beea16e2728e5654a12c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="input-character-set-entity-sql"></a><span data-ttu-id="b9694-102">Jeu de caractères en entrée (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b9694-102">Input Character Set (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b9694-103"> accepte les caractères UNICODE encodés en UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b9694-103"> accepts UNICODE characters encoded in UTF-16.</span></span>  
  
 <span data-ttu-id="b9694-104">Les littéraux de chaîne peuvent contenir tout caractère UTF-16 placé entre guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="b9694-104">String literals can contain any UTF-16 character enclosed in single quotes.</span></span> <span data-ttu-id="b9694-105">Par exemple, N'文字列リテラル'.</span><span class="sxs-lookup"><span data-stu-id="b9694-105">For example, N'文字列リテラル'.</span></span> <span data-ttu-id="b9694-106">Lorsque les littéraux de chaîne sont comparés, les valeurs UTF-16 d'origine sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="b9694-106">When string literals are compared, the original UTF-16 values are used.</span></span> <span data-ttu-id="b9694-107">Par exemple, N'ABC est différent dans les pages de code du japonais et du latin.</span><span class="sxs-lookup"><span data-stu-id="b9694-107">For example, N'ABC' is different in Japanese and Latin codepages.</span></span>  
  
 <span data-ttu-id="b9694-108">Les commentaires peuvent contenir tout caractère UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b9694-108">Comments can contain any UTF-16 character.</span></span>  
  
 <span data-ttu-id="b9694-109">Les identificateurs placés dans une séquence d'échappement peuvent contenir tout caractère UTF-16 placé entre crochets.</span><span class="sxs-lookup"><span data-stu-id="b9694-109">Escaped identifiers can contain any UTF-16 character enclosed in square brackets.</span></span> <span data-ttu-id="b9694-110">Par exemple, [エスケープされた識別子].</span><span class="sxs-lookup"><span data-stu-id="b9694-110">For example, [エスケープされた識別子].</span></span> <span data-ttu-id="b9694-111">La comparaison d'identificateurs UTF-16 placés dans une séquence d'échappement ne respecte pas la casse.</span><span class="sxs-lookup"><span data-stu-id="b9694-111">The comparison of UTF-16 escaped identifiers is case insensitive.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b9694-112"> traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents.</span><span class="sxs-lookup"><span data-stu-id="b9694-112"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="b9694-113">Par exemple, [ABC] est équivalent à [abc] si les caractères correspondants proviennent de la même page de codes.</span><span class="sxs-lookup"><span data-stu-id="b9694-113">For example, [ABC] is equivalent to [abc] if the corresponding characters are from the same code page.</span></span> <span data-ttu-id="b9694-114">Toutefois, si ces deux mêmes identificateurs utilisent des pages de codes différentes, ils ne sont pas équivalents.</span><span class="sxs-lookup"><span data-stu-id="b9694-114">However, if the same two identifiers are from different code pages, they are not equivalent.</span></span>  
  
 <span data-ttu-id="b9694-115">L'espace blanc correspond à tout caractère d'espace blanc UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b9694-115">White space is any UTF-16 white space character.</span></span>  
  
 <span data-ttu-id="b9694-116">Un saut de ligne est tout caractère normalisé de saut de ligne UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b9694-116">A newline is any normalized UTF-16 newline character.</span></span> <span data-ttu-id="b9694-117">Par exemple, '\n' et'\r\n' sont considérés comme des caractères de saut de ligne, mais '\r' n'est pas un caractère de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="b9694-117">For example, '\n' and '\r\n' are considered newline characters, but '\r' is not a newline character.</span></span>  
  
 <span data-ttu-id="b9694-118">Les mots clés, les expressions et la ponctuation peuvent être tout caractère UTF-16 qui est normalisé en latin.</span><span class="sxs-lookup"><span data-stu-id="b9694-118">Keywords, expressions, and punctuation can be any UTF-16 character that normalizes to Latin.</span></span> <span data-ttu-id="b9694-119">Par exemple, SELECT dans une page de codes pour le japonais est un mot clé valide.</span><span class="sxs-lookup"><span data-stu-id="b9694-119">For example, SELECT in a Japanese codepage is a valid keyword.</span></span>  
  
 <span data-ttu-id="b9694-120">Les mots clés, les expressions et la ponctuation peuvent être uniquement des caractères latins.</span><span class="sxs-lookup"><span data-stu-id="b9694-120">Keywords, expressions, and punctuation can only be Latin characters.</span></span> <span data-ttu-id="b9694-121">`SELECT` dans une page de codes japonaise n'est pas un mot clé.</span><span class="sxs-lookup"><span data-stu-id="b9694-121">`SELECT` in a Japanese codepage is not a keyword.</span></span> <span data-ttu-id="b9694-122">+, -, \*, /, =, (, ), ‘, [, ] et toute autre construction de langage non citée ici ne peuvent être que des caractères latins.</span><span class="sxs-lookup"><span data-stu-id="b9694-122">+, -, \*, /, =, (, ), ‘, [, ] and any other language construct not quoted here can only be Latin characters.</span></span>  
  
 <span data-ttu-id="b9694-123">Les identificateurs simples ne peuvent être que des caractères latins.</span><span class="sxs-lookup"><span data-stu-id="b9694-123">Simple identifiers can only be Latin characters.</span></span> <span data-ttu-id="b9694-124">Cela évite l'ambiguïté pendant la comparaison, car les valeurs d'origine sont comparées.</span><span class="sxs-lookup"><span data-stu-id="b9694-124">This avoids ambiguity during comparison, because original values are compared.</span></span> <span data-ttu-id="b9694-125">Par exemple, ABC est différent dans la page de code du japonais et celle du latin.</span><span class="sxs-lookup"><span data-stu-id="b9694-125">For example, ABC would be different in in Japanese and Latin codepages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9694-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9694-126">See Also</span></span>  
 [<span data-ttu-id="b9694-127">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b9694-127">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
