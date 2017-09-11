---
title: '&lt;paramref&gt; (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
dev_langs:
- CSharp
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: 12
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
ms.openlocfilehash: 452701c4f70bf6cbc619064d62de552fa54bba65
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="d3e84-102">&lt;paramref&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d3e84-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d3e84-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e84-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e84-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3e84-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d3e84-105">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="d3e84-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="d3e84-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="d3e84-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3e84-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d3e84-107">Remarks</span></span>  
 <span data-ttu-id="d3e84-108">La balise \<paramref> vous offre un moyen d’indiquer qu’un mot dans les commentaires du code, par exemple dans un bloc \<summary> ou \<remarks>, fait référence à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="d3e84-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="d3e84-109">Le fichier XML peut être traité de manière à mettre en forme ce mot d’une façon particulière, par exemple en gras ou en italique.</span><span class="sxs-lookup"><span data-stu-id="d3e84-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="d3e84-110">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="d3e84-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e84-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3e84-111">Example</span></span>  
 <span data-ttu-id="d3e84-112">[!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d3e84-112">[!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e84-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e84-113">See Also</span></span>  
 <span data-ttu-id="d3e84-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d3e84-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d3e84-115">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="d3e84-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

