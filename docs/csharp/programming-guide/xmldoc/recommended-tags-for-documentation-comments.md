---
title: "Balises recommandées pour les commentaires de documentation (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4d558bbe58d1f4a1c290b4f36718293d5ba1c734
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="97f84-102">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="97f84-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="97f84-103">Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**.</span><span class="sxs-lookup"><span data-stu-id="97f84-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="97f84-104">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="97f84-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="97f84-105">Les balises sont traitées sur les constructions de code telles que les types et les membres de types.</span><span class="sxs-lookup"><span data-stu-id="97f84-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97f84-106">Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="97f84-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="97f84-107">Le compilateur traite toute balise représentant du code XML correct.</span><span class="sxs-lookup"><span data-stu-id="97f84-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="97f84-108">Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.</span><span class="sxs-lookup"><span data-stu-id="97f84-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="97f84-109">Balises</span><span class="sxs-lookup"><span data-stu-id="97f84-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="97f84-110">\<c></span><span class="sxs-lookup"><span data-stu-id="97f84-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="97f84-111">\<para></span><span class="sxs-lookup"><span data-stu-id="97f84-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="97f84-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)*</span></span>|  
|[<span data-ttu-id="97f84-113">\<code></span><span class="sxs-lookup"><span data-stu-id="97f84-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="97f84-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)*</span></span>|<span data-ttu-id="97f84-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)*</span></span>|  
|[<span data-ttu-id="97f84-116">\<example></span><span class="sxs-lookup"><span data-stu-id="97f84-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="97f84-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="97f84-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="97f84-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="97f84-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="97f84-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)*</span></span>|<span data-ttu-id="97f84-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)*</span></span>|<span data-ttu-id="97f84-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)*</span></span>|  
|<span data-ttu-id="97f84-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*</span><span class="sxs-lookup"><span data-stu-id="97f84-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)*</span></span>|[<span data-ttu-id="97f84-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="97f84-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="97f84-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="97f84-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="97f84-125">\<list></span><span class="sxs-lookup"><span data-stu-id="97f84-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="97f84-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="97f84-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="97f84-127">\<value></span><span class="sxs-lookup"><span data-stu-id="97f84-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="97f84-128">(* indique que le compilateur vérifie la syntaxe.)</span><span class="sxs-lookup"><span data-stu-id="97f84-128">(* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="97f84-129">Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez `<` et `>`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="97f84-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97f84-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97f84-130">See Also</span></span>  
 [<span data-ttu-id="97f84-131">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="97f84-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="97f84-132">/doc (Options du compilateur c#)</span><span class="sxs-lookup"><span data-stu-id="97f84-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="97f84-133">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="97f84-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
