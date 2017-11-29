---
title: '&lt;exception&gt; (Guide de programmation C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="1f6ba-102">&lt;exception&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="1f6ba-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1f6ba-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f6ba-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f6ba-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f6ba-104">Parameters</span></span>  
 <span data-ttu-id="1f6ba-105">cref = " `member`"</span><span class="sxs-lookup"><span data-stu-id="1f6ba-105">cref = " `member`"</span></span>  
 <span data-ttu-id="1f6ba-106">Référence à une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="1f6ba-107">Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="1f6ba-108">`member` doit apparaître entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="1f6ba-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="1f6ba-109">Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span><span class="sxs-lookup"><span data-stu-id="1f6ba-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="1f6ba-110">Description de l'exception.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6ba-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="1f6ba-111">Remarks</span></span>  
 <span data-ttu-id="1f6ba-112">La balise \<exception> vous permet de spécifier quelles exceptions peuvent être levées.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="1f6ba-113">Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="1f6ba-114">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="1f6ba-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="1f6ba-115">Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f6ba-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6ba-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f6ba-116">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1f6ba-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f6ba-117">See Also</span></span>  
 [<span data-ttu-id="1f6ba-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1f6ba-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1f6ba-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="1f6ba-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
