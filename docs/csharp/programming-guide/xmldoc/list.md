---
title: "&lt;list&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs:
- CSharp
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b9d3dfa60530734a142295c8a8f2c32c4ecd9a47
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="f0d5d-102">&lt;list&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f0d5d-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f0d5d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0d5d-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
#### <a name="parameters"></a><span data-ttu-id="f0d5d-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0d5d-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="f0d5d-105">Terme à définir, qui est défini dans `description`.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="f0d5d-106">Élément contenu dans une puce ou une liste numérotée ou définition d’un `term`.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0d5d-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0d5d-107">Remarks</span></span>  
 <span data-ttu-id="f0d5d-108">Le bloc \<listheader> permet de définir la ligne d’en-tête d’une table ou d’une liste de définitions.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="f0d5d-109">Au moment de définir une table, il vous suffit de fournir une entrée pour le terme figurant dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="f0d5d-110">Chaque élément de la liste est spécifié avec un bloc \<item>.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="f0d5d-111">Au moment de créer une liste de définitions, vous devez spécifier à la fois `term` et `description`.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="f0d5d-112">Cependant, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="f0d5d-113">Une liste ou une table peut comporter autant de blocs \<item> que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="f0d5d-114">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="f0d5d-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d5d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0d5d-115">Example</span></span>  
 <span data-ttu-id="f0d5d-116">[!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f0d5d-116">[!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d5d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0d5d-117">See Also</span></span>  
 <span data-ttu-id="f0d5d-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f0d5d-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f0d5d-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="f0d5d-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

