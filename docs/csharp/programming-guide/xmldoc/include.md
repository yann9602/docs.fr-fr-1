---
title: '&lt;include&gt; (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- CSharp
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
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
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0cabcc25c4e35027c600e4af2bccfad7f9db1514
ms.contentlocale: fr-fr
ms.lasthandoff: 08/29/2017

---
# <a name="ltincludegt-c-programming-guide"></a><span data-ttu-id="019aa-102">&lt;include&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="019aa-102">&lt;include&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="019aa-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="019aa-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="019aa-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="019aa-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="019aa-105">Nom du fichier XML contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="019aa-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="019aa-106">Le nom de fichier peut être qualifié avec un chemin.</span><span class="sxs-lookup"><span data-stu-id="019aa-106">The file name can be qualified with a path.</span></span> <span data-ttu-id="019aa-107">Mettez `filename` entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="019aa-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="019aa-108">Chemin des balises contenues dans `filename` qui mène à la balise `name`.</span><span class="sxs-lookup"><span data-stu-id="019aa-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="019aa-109">Mettez le chemin entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="019aa-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="019aa-110">Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.</span><span class="sxs-lookup"><span data-stu-id="019aa-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="019aa-111">ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="019aa-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="019aa-112">Mettez l’ID entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="019aa-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="019aa-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="019aa-113">Remarks</span></span>  
 <span data-ttu-id="019aa-114">La balise \<include> vous permet de faire référence à des commentaires dans un autre fichier qui décrivent les types et les membres dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="019aa-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="019aa-115">Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="019aa-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="019aa-116">En plaçant la documentation dans un fichier distinct, vous pouvez appliquer un contrôle de code source à la documentation indépendamment du code source.</span><span class="sxs-lookup"><span data-stu-id="019aa-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="019aa-117">Ainsi, une personne peut extraire le fichier de code source et une autre personne peut extraire le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="019aa-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="019aa-118">La balise \<include> utilise la syntaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="019aa-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="019aa-119">Reportez-vous à la documentation de XPath pour savoir comment personnaliser votre utilisation de \<include>.</span><span class="sxs-lookup"><span data-stu-id="019aa-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="019aa-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="019aa-120">Example</span></span>  
 <span data-ttu-id="019aa-121">Cet exemple comprend plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="019aa-121">This is a multifile example.</span></span> <span data-ttu-id="019aa-122">Le premier, qui utilise \<include>, est présenté ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="019aa-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 <span data-ttu-id="019aa-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="019aa-123">[!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]</span></span>  
  
 <span data-ttu-id="019aa-124">Le deuxième, xml_include_tag.doc, contient les commentaires de la documentation suivants :</span><span class="sxs-lookup"><span data-stu-id="019aa-124">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="019aa-125">Sortie du programme</span><span class="sxs-lookup"><span data-stu-id="019aa-125">Program Output</span></span>  
 <span data-ttu-id="019aa-126">La sortie suivante est générée quand vous compilez les classes Test et Test2 avec la ligne de commande suivante : `/doc:DocFileName.xml.` Dans Visual Studio, l’option de commentaires de document XML est spécifiée dans le volet de génération du Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="019aa-126">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="019aa-127">Dès que le compilateur C# trouve la balise \<include>, il recherche des commentaires de la documentation dans xml_include_tag.doc et non dans le fichier source actuel.</span><span class="sxs-lookup"><span data-stu-id="019aa-127">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="019aa-128">Le compilateur génère ensuite DocFileName.xml, c’est-à-dire le fichier dont se servent les outils de documentation tels que [Sandcastle](https://github.com/EWSoftware/SHFB) pour produire la documentation finale.</span><span class="sxs-lookup"><span data-stu-id="019aa-128">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="019aa-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="019aa-129">See Also</span></span>  
 <span data-ttu-id="019aa-130">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="019aa-130">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="019aa-131">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="019aa-131">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

