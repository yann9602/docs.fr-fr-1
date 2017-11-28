---
title: '&lt;paramref&gt; (Guide de programmation C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="c4bae-102">&lt;paramref&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c4bae-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c4bae-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4bae-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4bae-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4bae-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c4bae-105">Nom du paramètre auquel faire référence.</span><span class="sxs-lookup"><span data-stu-id="c4bae-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="c4bae-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="c4bae-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4bae-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4bae-107">Remarks</span></span>  
 <span data-ttu-id="c4bae-108">La balise \<paramref> vous offre un moyen d’indiquer qu’un mot dans les commentaires du code, par exemple dans un bloc \<summary> ou \<remarks>, fait référence à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="c4bae-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="c4bae-109">Le fichier XML peut être traité de manière à mettre en forme ce mot d’une façon particulière, par exemple en gras ou en italique.</span><span class="sxs-lookup"><span data-stu-id="c4bae-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="c4bae-110">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c4bae-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4bae-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4bae-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c4bae-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4bae-112">See Also</span></span>  
 [<span data-ttu-id="c4bae-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c4bae-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c4bae-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c4bae-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
