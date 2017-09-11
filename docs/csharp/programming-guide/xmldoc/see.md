---
title: "&lt;see&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs:
- CSharp
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
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
ms.openlocfilehash: 831caae9574c25f16e8b2ede734746f48019198e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="dd555-102">&lt;see&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="dd555-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="dd555-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd555-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd555-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd555-104">Parameters</span></span>  
 <span data-ttu-id="dd555-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="dd555-105">cref = " `member`"</span></span>  
 <span data-ttu-id="dd555-106">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="dd555-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="dd555-107">Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. Placez *member* entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="dd555-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd555-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd555-108">Remarks</span></span>  
 <span data-ttu-id="dd555-109">La balise \<see> vous permet de spécifier un lien à partir de l’intérieur du texte.</span><span class="sxs-lookup"><span data-stu-id="dd555-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="dd555-110">Utilisez [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) pour indiquer que le texte doit être placé dans une section Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="dd555-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="dd555-111">Utilisez l’[attribut cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) pour créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="dd555-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="dd555-112">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="dd555-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="dd555-113">L’exemple suivant présente une balise \<see> dans une section de résumé (summary).</span><span class="sxs-lookup"><span data-stu-id="dd555-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 <span data-ttu-id="dd555-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd555-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd555-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd555-115">See Also</span></span>  
 <span data-ttu-id="dd555-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd555-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="dd555-117">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="dd555-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

