---
title: '&lt;Para&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2a034974ed94b18da374fbd372063ea4d575440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="25d2e-102">&lt;Para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25d2e-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="25d2e-103">Spécifie que le contenu est mis en forme comme un paragraphe.</span><span class="sxs-lookup"><span data-stu-id="25d2e-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25d2e-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25d2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25d2e-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="25d2e-106">Texte du paragraphe.</span><span class="sxs-lookup"><span data-stu-id="25d2e-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25d2e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="25d2e-107">Remarks</span></span>  
 <span data-ttu-id="25d2e-108">Le `<para>` balise est destinée à l’intérieur d’une balise, tel que [ \<Résumé >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Notes >](../../../visual-basic/language-reference/xmldoc/remarks.md), ou [ \<retourne >](../../../visual-basic/language-reference/xmldoc/returns.md), et vous permet de structurer le texte.</span><span class="sxs-lookup"><span data-stu-id="25d2e-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="25d2e-109">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="25d2e-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d2e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="25d2e-110">Example</span></span>  
 <span data-ttu-id="25d2e-111">Cet exemple utilise le `<para>` balise pour fractionner la section Notes pour le `UpdateRecord` méthode en deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="25d2e-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="25d2e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25d2e-112">See Also</span></span>  
 [<span data-ttu-id="25d2e-113">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="25d2e-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
