---
title: '&lt;Remarques&gt; (Visual Basic) | Documents Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: c1b2c48dc3247935f703ff4107f29829c494a305
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017

---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="baabd-102">&lt;Remarques&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baabd-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="baabd-103">Spécifie une section Notes pour le membre.</span><span class="sxs-lookup"><span data-stu-id="baabd-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baabd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baabd-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="baabd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="baabd-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="baabd-106">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="baabd-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baabd-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="baabd-107">Remarks</span></span>  
 <span data-ttu-id="baabd-108">Utilisez le `<remarks>` balise pour ajouter des informations sur un type et de compléter les informations spécifiées par [ \<Résumé >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="baabd-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="baabd-109">Cette information s’affiche dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="baabd-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="baabd-110">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la Structure de Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="baabd-110">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="baabd-111">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="baabd-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baabd-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="baabd-112">Example</span></span>  
 <span data-ttu-id="baabd-113">Cet exemple utilise le `<remarks>` balise pour expliquer la `UpdateRecord` méthode.</span><span class="sxs-lookup"><span data-stu-id="baabd-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 <span data-ttu-id="baabd-114">[!code-vb[VbVbcnXmlDocComments n °&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="baabd-114">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baabd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baabd-115">See Also</span></span>  
 [<span data-ttu-id="baabd-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="baabd-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
