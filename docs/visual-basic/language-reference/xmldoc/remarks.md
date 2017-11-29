---
title: '&lt;la section Notes&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f70c2d7df190d2ff8187882a9176dbe98984296
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="a0e8a-102">&lt;la section Notes&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0e8a-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="a0e8a-103">Spécifie une section de la section Notes pour le membre.</span><span class="sxs-lookup"><span data-stu-id="a0e8a-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e8a-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0e8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0e8a-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a0e8a-106">Description du membre.</span><span class="sxs-lookup"><span data-stu-id="a0e8a-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0e8a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0e8a-107">Remarks</span></span>  
 <span data-ttu-id="a0e8a-108">Utilisez le `<remarks>` balise pour ajouter des informations sur un type, de compléter les informations spécifiées avec [ \<Résumé >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="a0e8a-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="a0e8a-109">Ces informations s’affichent dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="a0e8a-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="a0e8a-110">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la Structure du Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="a0e8a-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="a0e8a-111">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="a0e8a-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0e8a-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0e8a-112">Example</span></span>  
 <span data-ttu-id="a0e8a-113">Cet exemple utilise le `<remarks>` balise pour expliquer la `UpdateRecord` méthode.</span><span class="sxs-lookup"><span data-stu-id="a0e8a-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a0e8a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0e8a-114">See Also</span></span>  
 [<span data-ttu-id="a0e8a-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="a0e8a-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
