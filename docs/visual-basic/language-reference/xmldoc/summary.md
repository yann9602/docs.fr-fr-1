---
title: "&lt;Résumé&gt; (Visual Basic) | Documents Microsoft"
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
ms.openlocfilehash: 42321daf092c4b637d2f75fb7f6d7e95201791ba
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017

---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="a0f26-102">&lt;Résumé&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0f26-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="a0f26-103">Spécifie le résumé du membre.</span><span class="sxs-lookup"><span data-stu-id="a0f26-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0f26-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0f26-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0f26-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a0f26-106">Un résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="a0f26-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0f26-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0f26-107">Remarks</span></span>  
 <span data-ttu-id="a0f26-108">Utilisez le `<summary>` balises pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="a0f26-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="a0f26-109">Utilisez [ \<notes >](../../../visual-basic/language-reference/xmldoc/remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="a0f26-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="a0f26-110">Le texte de la `<summary>` balise est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="a0f26-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="a0f26-111">Pour plus d’informations sur l’Explorateur d’objets, consultez [affichage de la Structure de Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="a0f26-111">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="a0f26-112">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a0f26-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0f26-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0f26-113">Example</span></span>  
 <span data-ttu-id="a0f26-114">Cet exemple utilise le `<summary>` balises pour décrire la `ResetCounter` méthode et `Counter` propriété.</span><span class="sxs-lookup"><span data-stu-id="a0f26-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 <span data-ttu-id="a0f26-115">[!code-vb[VbVbcnXmlDocComments n °&1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0f26-115">[!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f26-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0f26-116">See Also</span></span>  
 [<span data-ttu-id="a0f26-117">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="a0f26-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
