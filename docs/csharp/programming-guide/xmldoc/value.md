---
title: "&lt;value&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
dev_langs:
- CSharp
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
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
ms.openlocfilehash: 71c8d5ab2e99291f05ef362960b0eeac969e9de1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="3cd07-102">&lt;value&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3cd07-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="3cd07-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cd07-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cd07-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3cd07-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="3cd07-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3cd07-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cd07-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="3cd07-106">Remarks</span></span>  
 <span data-ttu-id="3cd07-107">La balise \<value> vous permet de décrire la valeur représentée par une propriété.</span><span class="sxs-lookup"><span data-stu-id="3cd07-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="3cd07-108">Notez que lorsque vous ajoutez une propriété via l’Assistant Code de l’environnement de développement Visual Studio .NET, il ajoute une balise [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="3cd07-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="3cd07-109">Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="3cd07-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3cd07-110">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3cd07-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd07-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cd07-111">Example</span></span>  
 <span data-ttu-id="3cd07-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3cd07-112">[!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd07-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cd07-113">See Also</span></span>  
 <span data-ttu-id="3cd07-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3cd07-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3cd07-115">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="3cd07-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

