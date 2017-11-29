---
title: "&lt;param&gt; (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a5325b91130623442c9cf5453e52418bb44cc34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="148d6-102">&lt;param&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="148d6-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="148d6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="148d6-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="148d6-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="148d6-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="148d6-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="148d6-105">The name of a method parameter.</span></span> <span data-ttu-id="148d6-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="148d6-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="148d6-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="148d6-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="148d6-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="148d6-108">Remarks</span></span>  
 <span data-ttu-id="148d6-109">La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="148d6-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="148d6-110">Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param>.</span><span class="sxs-lookup"><span data-stu-id="148d6-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="148d6-111">Le texte de la balise \<param> s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="148d6-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="148d6-112">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="148d6-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="148d6-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="148d6-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="148d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="148d6-114">See Also</span></span>  
 [<span data-ttu-id="148d6-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="148d6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="148d6-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="148d6-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
