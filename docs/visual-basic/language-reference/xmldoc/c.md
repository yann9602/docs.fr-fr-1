---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="4397d-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4397d-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="4397d-103">Indique que le texte d’une description est code.</span><span class="sxs-lookup"><span data-stu-id="4397d-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4397d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4397d-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4397d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4397d-105">Parameters</span></span>  
  
|<span data-ttu-id="4397d-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="4397d-106">Parameter</span></span>|<span data-ttu-id="4397d-107">Description</span><span class="sxs-lookup"><span data-stu-id="4397d-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="4397d-108">Texte que vous souhaitez indiquer comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="4397d-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4397d-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4397d-109">Remarks</span></span>  
 <span data-ttu-id="4397d-110">Le `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué en tant que code.</span><span class="sxs-lookup"><span data-stu-id="4397d-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="4397d-111">Utilisez [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) pour indiquer plusieurs lignes comme étant du code.</span><span class="sxs-lookup"><span data-stu-id="4397d-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="4397d-112">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="4397d-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4397d-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="4397d-113">Example</span></span>  
 <span data-ttu-id="4397d-114">Cet exemple utilise le `<c>` balise dans la section Résumé pour indiquer que `Counter` est le code.</span><span class="sxs-lookup"><span data-stu-id="4397d-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4397d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4397d-115">See Also</span></span>  
 [<span data-ttu-id="4397d-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="4397d-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
