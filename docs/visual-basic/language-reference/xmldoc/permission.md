---
title: '&lt;autorisation&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 67e11998e43a43f92c26eb5f7daa488d288823c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltpermissiongt-visual-basic"></a><span data-ttu-id="4b78b-102">&lt;autorisation&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b78b-102">&lt;permission&gt; (Visual Basic)</span></span>
<span data-ttu-id="4b78b-103">Spécifie une autorisation requise pour le membre.</span><span class="sxs-lookup"><span data-stu-id="4b78b-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b78b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b78b-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b78b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b78b-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="4b78b-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="4b78b-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4b78b-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="4b78b-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="4b78b-108">Placez `member` entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="4b78b-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4b78b-109">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="4b78b-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b78b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="4b78b-110">Remarks</span></span>  
 <span data-ttu-id="4b78b-111">Utilisez le `<permission>` balise pour documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="4b78b-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="4b78b-112">Utilisez le <xref:System.Security.PermissionSet> pour spécifier l’accès à un membre de classe.</span><span class="sxs-lookup"><span data-stu-id="4b78b-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="4b78b-113">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="4b78b-113">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b78b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b78b-114">Example</span></span>  
 <span data-ttu-id="4b78b-115">Cet exemple utilise le `<permission>` balises pour décrire que les <xref:System.Security.Permissions.FileIOPermission> est requis par le `ReadFile` (méthode).</span><span class="sxs-lookup"><span data-stu-id="4b78b-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/permission_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4b78b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b78b-116">See Also</span></span>  
 [<span data-ttu-id="4b78b-117">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="4b78b-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
