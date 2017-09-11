---
title: '&lt;permission&gt; (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- permission
- <permission>
dev_langs:
- CSharp
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
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
ms.openlocfilehash: 4b8f109d7e01f6e630f09939161b6a20c3a13f73
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltpermissiongt-c-programming-guide"></a><span data-ttu-id="e05fa-102">&lt;permission&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e05fa-102">&lt;permission&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e05fa-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e05fa-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e05fa-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e05fa-104">Parameters</span></span>  
 <span data-ttu-id="e05fa-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="e05fa-105">cref = " `member`"</span></span>  
 <span data-ttu-id="e05fa-106">Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="e05fa-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="e05fa-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="e05fa-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="e05fa-108">Le *membre* doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="e05fa-108">*member* must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="e05fa-109">Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="e05fa-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="e05fa-110">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="e05fa-110">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e05fa-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e05fa-111">Remarks</span></span>  
 <span data-ttu-id="e05fa-112">La balise \<permission> vous permet de documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="e05fa-112">The \<permission> tag lets you document the access of a member.</span></span> <span data-ttu-id="e05fa-113">La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="e05fa-113">The <xref:System.Security.PermissionSet> class lets you specify access to a member.</span></span>  
  
 <span data-ttu-id="e05fa-114">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="e05fa-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e05fa-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="e05fa-115">Example</span></span>  
 <span data-ttu-id="e05fa-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e05fa-116">[!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05fa-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e05fa-117">See Also</span></span>  
 <span data-ttu-id="e05fa-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e05fa-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="e05fa-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e05fa-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

