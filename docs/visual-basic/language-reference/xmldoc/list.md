---
title: '&lt;liste&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="b365f-102">&lt;liste&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b365f-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="b365f-103">Définit une liste ou une table.</span><span class="sxs-lookup"><span data-stu-id="b365f-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b365f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b365f-104">Syntax</span></span>  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b365f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b365f-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="b365f-106">Le type de la liste.</span><span class="sxs-lookup"><span data-stu-id="b365f-106">The type of the list.</span></span> <span data-ttu-id="b365f-107">Doivent être des « puce » pour une liste à puces, le « nombre » pour une liste numérotée, ou « table » pour une table à deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="b365f-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="b365f-108">Utilisé uniquement lorsque `type` est « table ».</span><span class="sxs-lookup"><span data-stu-id="b365f-108">Only used when `type` is "table."</span></span> <span data-ttu-id="b365f-109">Un terme à définir, qui est défini dans la balise de description.</span><span class="sxs-lookup"><span data-stu-id="b365f-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="b365f-110">Lorsque `type` est « puce » ou « number », `description` est un élément dans la liste lorsque `type` est « table », `description` est la définition de `term`.</span><span class="sxs-lookup"><span data-stu-id="b365f-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b365f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="b365f-111">Remarks</span></span>  
 <span data-ttu-id="b365f-112">Le `<listheader>` bloc définit le titre d’une table ou une définition de liste.</span><span class="sxs-lookup"><span data-stu-id="b365f-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="b365f-113">Lorsque vous définissez une table, il vous suffit de fournir une entrée pour `term` dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="b365f-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="b365f-114">Chaque élément dans la liste est spécifié avec un `<item>` bloc.</span><span class="sxs-lookup"><span data-stu-id="b365f-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="b365f-115">Lorsque vous créez une liste de définitions, vous devez spécifier les deux `term` et `description`.</span><span class="sxs-lookup"><span data-stu-id="b365f-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="b365f-116">Toutefois, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.</span><span class="sxs-lookup"><span data-stu-id="b365f-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="b365f-117">Une liste ou une table peut comporter autant `<item>` bloque en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="b365f-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="b365f-118">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="b365f-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b365f-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="b365f-119">Example</span></span>  
 <span data-ttu-id="b365f-120">Cet exemple utilise le `<list>` balise pour définir une liste à puces dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="b365f-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b365f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b365f-121">See Also</span></span>  
 [<span data-ttu-id="b365f-122">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="b365f-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
