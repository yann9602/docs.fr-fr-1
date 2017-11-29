---
title: '&lt;valeur&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a72c6330596e59d26fbae9d13f6b9c8b1987e519
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="3a0e0-102">&lt;valeur&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a0e0-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="3a0e0-103">Spécifie la description d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a0e0-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a0e0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a0e0-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="3a0e0-106">Description de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a0e0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3a0e0-107">Remarks</span></span>  
 <span data-ttu-id="3a0e0-108">Utilisez le `<value>` balises pour décrire une propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="3a0e0-109">Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant de code dans l’environnement de développement Visual Studio, il ajoute un [ \<Résumé >](../../../visual-basic/language-reference/xmldoc/summary.md) balise pour la nouvelle propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="3a0e0-110">Vous devez ensuite ajouter manuellement une `<value>` balises pour décrire la valeur représentée par la propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3a0e0-111">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0e0-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="3a0e0-112">Example</span></span>  
 <span data-ttu-id="3a0e0-113">Cet exemple utilise le `<value>` balises pour décrire la valeur que le `Counter` blocages de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3a0e0-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a0e0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a0e0-114">See Also</span></span>  
 [<span data-ttu-id="3a0e0-115">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="3a0e0-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
