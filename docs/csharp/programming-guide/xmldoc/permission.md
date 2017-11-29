---
title: '&lt;permission&gt; (Guide de programmation C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37bb37ea14edc1f91225f9b04b18b354d99579b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="c58af-102">&lt;permission&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c58af-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c58af-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c58af-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c58af-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c58af-104">Parameters</span></span>  
 <span data-ttu-id="c58af-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="c58af-105">cref = " `member`"</span></span>  
 <span data-ttu-id="c58af-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="c58af-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="c58af-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="c58af-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="c58af-108">Le *membre* doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="c58af-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="c58af-109">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="c58af-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="c58af-110">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="c58af-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c58af-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c58af-111">Remarks</span></span>  
 <span data-ttu-id="c58af-112">La balise \<permission> vous permet de documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="c58af-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="c58af-113">La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="c58af-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="c58af-114">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c58af-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c58af-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="c58af-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c58af-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c58af-116">See Also</span></span>  
 [<span data-ttu-id="c58af-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="c58af-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c58af-118">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c58af-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
