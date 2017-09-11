---
title: Documenter votre Code avec XML (Visual Basic) | Documents Microsoft
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
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0ce3f216f9e851feb0b3506b6ed1279b7d9479e7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="50f03-102">Documentation de votre code avec le langage XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50f03-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="50f03-103">Dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez documenter votre code à l’aide de XML</span><span class="sxs-lookup"><span data-stu-id="50f03-103">In [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="50f03-104">Commentaires de documentation XML</span><span class="sxs-lookup"><span data-stu-id="50f03-104">XML Documentation Comments</span></span>  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="50f03-105">fournit un moyen simple de créer automatiquement de documentation XML pour les projets.</span><span class="sxs-lookup"><span data-stu-id="50f03-105"> provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="50f03-106">Vous pouvez générer automatiquement une structure XML pour vos types et membres et puis fournir des résumés, une documentation descriptive pour chaque paramètre et d’autres notes.</span><span class="sxs-lookup"><span data-stu-id="50f03-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="50f03-107">La configuration est appropriée, la documentation XML est émise automatiquement dans un fichier XML portant le même nom que votre projet et l’extension .xml.</span><span class="sxs-lookup"><span data-stu-id="50f03-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="50f03-108">Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="50f03-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="50f03-109">Le fichier XML peut être consommé ou manipulé en tant que XML.</span><span class="sxs-lookup"><span data-stu-id="50f03-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="50f03-110">Ce fichier se trouve dans le même répertoire que le fichier de sortie .exe ou .dll de votre projet.</span><span class="sxs-lookup"><span data-stu-id="50f03-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="50f03-111">Documentation XML commence par `'''`.</span><span class="sxs-lookup"><span data-stu-id="50f03-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="50f03-112">Le traitement de ces commentaires présente certaines restrictions :</span><span class="sxs-lookup"><span data-stu-id="50f03-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="50f03-113">La documentation doit être correcte XML.</span><span class="sxs-lookup"><span data-stu-id="50f03-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="50f03-114">Si le XML n’est pas correct, un avertissement est généré et le fichier de documentation contient un commentaire indiquant qu’une erreur est survenue.</span><span class="sxs-lookup"><span data-stu-id="50f03-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="50f03-115">Les développeurs sont libres de créer leur propre jeu de balises.</span><span class="sxs-lookup"><span data-stu-id="50f03-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="50f03-116">Il existe un jeu de balises (voir « Rubriques connexes » dans cette rubrique) recommandé.</span><span class="sxs-lookup"><span data-stu-id="50f03-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="50f03-117">Certaines des balises recommandées ont des significations spéciales :</span><span class="sxs-lookup"><span data-stu-id="50f03-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="50f03-118">Le \<param > balise est utilisée pour décrire les paramètres.</span><span class="sxs-lookup"><span data-stu-id="50f03-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="50f03-119">Si utilisé, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="50f03-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="50f03-120">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="50f03-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="50f03-121">Le `cref` attribut pouvant être joints à n’importe quelle balise pour fournir une référence à un élément de code.</span><span class="sxs-lookup"><span data-stu-id="50f03-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="50f03-122">Le compilateur vérifie l’existence de cet élément de code.</span><span class="sxs-lookup"><span data-stu-id="50f03-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="50f03-123">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="50f03-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="50f03-124">Le compilateur respecte également les `Imports` instructions lorsqu’il recherche un type décrit dans le `cref` attribut.</span><span class="sxs-lookup"><span data-stu-id="50f03-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="50f03-125">Le \<résumé > balise est employée par IntelliSense dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] pour afficher des informations supplémentaires sur un type ou membre.</span><span class="sxs-lookup"><span data-stu-id="50f03-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50f03-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="50f03-126">Related Sections</span></span>  
 <span data-ttu-id="50f03-127">Pour plus d’informations sur la création d’un fichier XML avec des commentaires de documentation, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="50f03-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="50f03-128">/doc</span><span class="sxs-lookup"><span data-stu-id="50f03-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="50f03-129">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="50f03-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="50f03-130">Traitement du fichier XML</span><span class="sxs-lookup"><span data-stu-id="50f03-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="50f03-131">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="50f03-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="50f03-132">Outils XML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="50f03-132">XML Tools in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="50f03-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f03-133">See Also</span></span>  
 <span data-ttu-id="50f03-134">[Développement d’Applications avec Visual Basic](../../../visual-basic/developing-apps/index.md) </span><span class="sxs-lookup"><span data-stu-id="50f03-134">[Developing Applications with Visual Basic](../../../visual-basic/developing-apps/index.md) </span></span>  
<span data-ttu-id="50f03-135"> [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="50f03-135"> [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)</span></span>
