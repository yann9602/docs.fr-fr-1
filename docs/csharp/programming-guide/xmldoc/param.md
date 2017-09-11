---
title: "&lt;param&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
dev_langs:
- CSharp
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
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
ms.openlocfilehash: 1076405d60c85540eeaeba39821bd20bc628030d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="73ddb-102">&lt;param&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="73ddb-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="73ddb-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73ddb-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73ddb-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="73ddb-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="73ddb-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="73ddb-105">The name of a method parameter.</span></span> <span data-ttu-id="73ddb-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="73ddb-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="73ddb-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="73ddb-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73ddb-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="73ddb-108">Remarks</span></span>  
 <span data-ttu-id="73ddb-109">La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="73ddb-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="73ddb-110">Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param>.</span><span class="sxs-lookup"><span data-stu-id="73ddb-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="73ddb-111">Le texte de la balise \<param> s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="73ddb-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="73ddb-112">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="73ddb-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73ddb-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="73ddb-113">Example</span></span>  
 <span data-ttu-id="73ddb-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="73ddb-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ddb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73ddb-115">See Also</span></span>  
 <span data-ttu-id="73ddb-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="73ddb-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="73ddb-117">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="73ddb-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

