---
title: "Balises XML recommandées pour commentaires de Documentation (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4a6c3128a69e8d666d44882ef3eac9f9a31a51a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="99cae-102">Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99cae-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="99cae-103">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur peut traiter les commentaires de documentation dans votre code dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="99cae-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="99cae-104">Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="99cae-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="99cae-105">Les commentaires XML sont autorisés sur les constructions de code telles que les types et membres de type.</span><span class="sxs-lookup"><span data-stu-id="99cae-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="99cae-106">Pour les types partiels, qu’une partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur le commentaire de ses membres.</span><span class="sxs-lookup"><span data-stu-id="99cae-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99cae-107">Commentaires de documentation ne peut pas être appliquées aux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="99cae-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="99cae-108">La raison est qu’un espace de noms peut s’étendre sur plusieurs assemblys, et pas tous les assemblys doivent être chargés en même temps.</span><span class="sxs-lookup"><span data-stu-id="99cae-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="99cae-109">Le compilateur traite n’importe quelle balise XML valid.</span><span class="sxs-lookup"><span data-stu-id="99cae-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="99cae-110">Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="99cae-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="99cae-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="99cae-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="99cae-112">\<code ></span><span class="sxs-lookup"><span data-stu-id="99cae-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="99cae-113">\<exemple ></span><span class="sxs-lookup"><span data-stu-id="99cae-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="99cae-114">[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="99cae-115">[\<inclure >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="99cae-116">\<list></span><span class="sxs-lookup"><span data-stu-id="99cae-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="99cae-117">\<Para ></span><span class="sxs-lookup"><span data-stu-id="99cae-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="99cae-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="99cae-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="99cae-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="99cae-120">[\<autorisation >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="99cae-121">\<Remarques ></span><span class="sxs-lookup"><span data-stu-id="99cae-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="99cae-122">\<Retourne ></span><span class="sxs-lookup"><span data-stu-id="99cae-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="99cae-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="99cae-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="99cae-125">\<Résumé ></span><span class="sxs-lookup"><span data-stu-id="99cae-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="99cae-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="99cae-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="99cae-127">\<valeur ></span><span class="sxs-lookup"><span data-stu-id="99cae-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="99cae-128">(<sup>1</sup> le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="99cae-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99cae-129">Si vous souhaitez des crochets pointus pour apparaître dans le texte d’un commentaire de documentation, utilisez `<` et `>`.</span><span class="sxs-lookup"><span data-stu-id="99cae-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="99cae-130">Par exemple, la chaîne `"<text in angle brackets>"` apparaît sous la forme `<text in angle``brackets>`.</span><span class="sxs-lookup"><span data-stu-id="99cae-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cae-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99cae-131">See Also</span></span>  
 <span data-ttu-id="99cae-132">[Documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="99cae-132">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="99cae-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="99cae-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="99cae-134"> [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="99cae-134"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
