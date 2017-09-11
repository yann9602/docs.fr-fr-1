---
title: "&lt;typeparam&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparam
dev_langs:
- CSharp
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
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
ms.openlocfilehash: 8bb1d13976cf2cc9df4f573702168c6abdfff3d5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="272a8-102">&lt;typeparam&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="272a8-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="272a8-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="272a8-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="272a8-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="272a8-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="272a8-105">Nom du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="272a8-105">The name of the type parameter.</span></span> <span data-ttu-id="272a8-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="272a8-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="272a8-107">Description du paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="272a8-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="272a8-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="272a8-108">Remarks</span></span>  
 <span data-ttu-id="272a8-109">La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="272a8-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="272a8-110">Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.</span><span class="sxs-lookup"><span data-stu-id="272a8-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="272a8-111">Pour plus d’informations, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="272a8-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="272a8-112">Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) et dans le rapport web de commentaire de code.</span><span class="sxs-lookup"><span data-stu-id="272a8-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="272a8-113">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="272a8-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272a8-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="272a8-114">Example</span></span>  
 <span data-ttu-id="272a8-115">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="272a8-115">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272a8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="272a8-116">See Also</span></span>  
 <span data-ttu-id="272a8-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="272a8-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="272a8-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="272a8-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="272a8-119">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="272a8-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

