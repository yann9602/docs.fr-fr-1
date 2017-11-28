---
title: "&lt;value&gt; (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="31edd-102">&lt;value&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="31edd-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="31edd-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31edd-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31edd-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31edd-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="31edd-105">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="31edd-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31edd-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="31edd-106">Remarks</span></span>  
 <span data-ttu-id="31edd-107">La balise \<value> vous permet de décrire la valeur représentée par une propriété.</span><span class="sxs-lookup"><span data-stu-id="31edd-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="31edd-108">Notez que lorsque vous ajoutez une propriété via l’Assistant Code de l’environnement de développement Visual Studio .NET, il ajoute une balise [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="31edd-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="31edd-109">Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="31edd-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="31edd-110">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="31edd-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31edd-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="31edd-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="31edd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31edd-112">See Also</span></span>  
 [<span data-ttu-id="31edd-113">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="31edd-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="31edd-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="31edd-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
