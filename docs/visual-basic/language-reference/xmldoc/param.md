---
title: '&lt;Param&gt; (Visual Basic) | Documents Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: ddf5baf83816d757edf67cdf1c66dc24e4313b83
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017

---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="c9bf5-102">&lt;Param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9bf5-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="c9bf5-103">Définit un nom de paramètre et une description.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9bf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9bf5-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9bf5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9bf5-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c9bf5-106">Le nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-106">The name of a method parameter.</span></span> <span data-ttu-id="c9bf5-107">Placez le nom entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="c9bf5-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c9bf5-108">Une description pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9bf5-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9bf5-109">Remarks</span></span>  
 <span data-ttu-id="c9bf5-110">Le `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="c9bf5-111">Le texte de la `<param>` balise apparaît dans les emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="c9bf5-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="c9bf5-112">Informations sur les paramètres d’IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="c9bf5-113">Pour plus d’informations, consultez [Utilisation d’IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="c9bf5-113">For more information, see [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="c9bf5-114">Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-114">Object Browser.</span></span> <span data-ttu-id="c9bf5-115">Pour plus d’informations, consultez [Affichage de la structure du code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="c9bf5-115">For more information, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="c9bf5-116">Compilez avec [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour traiter les commentaires de documentation dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9bf5-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="c9bf5-117">Example</span></span>  
 <span data-ttu-id="c9bf5-118">Cet exemple utilise le `<param>` balises pour décrire le `id` paramètre.</span><span class="sxs-lookup"><span data-stu-id="c9bf5-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 <span data-ttu-id="c9bf5-119">[!code-vb[VbVbcnXmlDocComments n °&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c9bf5-119">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bf5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9bf5-120">See Also</span></span>  
 [<span data-ttu-id="c9bf5-121">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="c9bf5-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
