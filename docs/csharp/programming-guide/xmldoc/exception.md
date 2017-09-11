---
title: '&lt;exception&gt; (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs:
- CSharp
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
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
ms.openlocfilehash: bdcbe116db4ed0f63ea73c524c482266b4ac1a38
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="a1dbd-102">&lt;exception&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a1dbd-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a1dbd-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1dbd-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1dbd-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1dbd-104">Parameters</span></span>  
 <span data-ttu-id="a1dbd-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="a1dbd-105">cref = " `member`"</span></span>  
 <span data-ttu-id="a1dbd-106">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="a1dbd-107">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="a1dbd-108">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="a1dbd-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="a1dbd-109">Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="a1dbd-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="a1dbd-110">Description de l'exception.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1dbd-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="a1dbd-111">Remarks</span></span>  
 <span data-ttu-id="a1dbd-112">La balise \<exception> vous permet de spécifier quelles exceptions peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="a1dbd-113">Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="a1dbd-114">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a1dbd-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="a1dbd-115">Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1dbd-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1dbd-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="a1dbd-116">Example</span></span>  
 <span data-ttu-id="a1dbd-117">[!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a1dbd-117">[!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dbd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1dbd-118">See Also</span></span>  
 <span data-ttu-id="a1dbd-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1dbd-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="a1dbd-120">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="a1dbd-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

