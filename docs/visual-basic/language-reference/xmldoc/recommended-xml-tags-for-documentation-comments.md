---
title: "Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="feca8-102">Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feca8-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="feca8-103">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur peut traiter les commentaires de documentation dans votre code dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="feca8-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="feca8-104">Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="feca8-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="feca8-105">Commentaires XML sont autorisés sur les constructions de code tels que les types et membres de type.</span><span class="sxs-lookup"><span data-stu-id="feca8-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="feca8-106">Pour les types partiels, qu’une partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur le commentaire de ses membres.</span><span class="sxs-lookup"><span data-stu-id="feca8-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feca8-107">Commentaires de documentation ne peut pas être appliqués aux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="feca8-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="feca8-108">La raison est qu’un espace de noms peut s’étendre sur plusieurs assemblys, et non tous les assemblys doit être chargé en même temps.</span><span class="sxs-lookup"><span data-stu-id="feca8-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="feca8-109">Le compilateur traite toute balise XML valid.</span><span class="sxs-lookup"><span data-stu-id="feca8-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="feca8-110">Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="feca8-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="feca8-111">\<c></span><span class="sxs-lookup"><span data-stu-id="feca8-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="feca8-112">\<code></span><span class="sxs-lookup"><span data-stu-id="feca8-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="feca8-113">\<example></span><span class="sxs-lookup"><span data-stu-id="feca8-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="feca8-114">[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="feca8-115">[\<Inclure >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="feca8-116">\<list></span><span class="sxs-lookup"><span data-stu-id="feca8-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="feca8-117">\<para></span><span class="sxs-lookup"><span data-stu-id="feca8-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="feca8-118">[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="feca8-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="feca8-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="feca8-120">[\<autorisation >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="feca8-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="feca8-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="feca8-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="feca8-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="feca8-123">[\<consultez >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="feca8-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="feca8-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="feca8-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="feca8-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="feca8-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="feca8-127">\<value></span><span class="sxs-lookup"><span data-stu-id="feca8-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="feca8-128">(<sup>1</sup> le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="feca8-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feca8-129">Si vous souhaitez des crochets pointus pour apparaître dans le texte d’un commentaire de documentation, utilisez `<` et `>`.</span><span class="sxs-lookup"><span data-stu-id="feca8-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="feca8-130">Par exemple, la chaîne `"<text in angle brackets>"` apparaît sous la forme `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="feca8-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feca8-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feca8-131">See Also</span></span>  
 [<span data-ttu-id="feca8-132">Documentation de votre code avec le langage XML</span><span class="sxs-lookup"><span data-stu-id="feca8-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="feca8-133">/doc</span><span class="sxs-lookup"><span data-stu-id="feca8-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="feca8-134">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="feca8-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
