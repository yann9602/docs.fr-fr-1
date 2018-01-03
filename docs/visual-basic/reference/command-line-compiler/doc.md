---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f9d4f584f217e6996a499614b97f184b28664f8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="doc"></a><span data-ttu-id="8d6bf-102">/doc</span><span class="sxs-lookup"><span data-stu-id="8d6bf-102">/doc</span></span>
<span data-ttu-id="8d6bf-103">Traite les commentaires de documentation pour les diriger vers un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d6bf-104">Syntax</span></span>  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8d6bf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8d6bf-105">Arguments</span></span>  
  
|<span data-ttu-id="8d6bf-106">Terme</span><span class="sxs-lookup"><span data-stu-id="8d6bf-106">Term</span></span>|<span data-ttu-id="8d6bf-107">Définition</span><span class="sxs-lookup"><span data-stu-id="8d6bf-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="8d6bf-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8d6bf-108">`+` &#124; `-`</span></span>|<span data-ttu-id="8d6bf-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-109">Optional.</span></span> <span data-ttu-id="8d6bf-110">Spécification +, ou simplement `/doc`, indique au compilateur de générer des informations de documentation et les placer dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-110">Specifying +, or just `/doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="8d6bf-111">Spécification de `-` est l’équivalent de ne pas spécifier `/doc`, à l’origine d’aucune information de documentation doit être créé.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-111">Specifying `-` is the equivalent of not specifying `/doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="8d6bf-112">Obligatoire si l'option `/doc:` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-112">Required if `/doc:` is used.</span></span> <span data-ttu-id="8d6bf-113">Spécifie le fichier XML de sortie, qui est renseigné avec les commentaires à partir des fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="8d6bf-114">Si le nom de fichier contient un espace, mettre le nom entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="8d6bf-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d6bf-115">Notes</span><span class="sxs-lookup"><span data-stu-id="8d6bf-115">Remarks</span></span>  
 <span data-ttu-id="8d6bf-116">Le `/doc` option contrôle si le compilateur génère un fichier XML contenant les commentaires de documentation.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-116">The `/doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="8d6bf-117">Si vous utilisez la `/doc:``file` syntaxe, la `file` paramètre spécifie le nom du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-117">If you use the `/doc:``file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="8d6bf-118">Si vous utilisez `/doc` ou `/doc+`, le compilateur prend le nom du fichier XML à partir du fichier exécutable ou la bibliothèque que le compilateur est en train de créer.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-118">If you use `/doc` or `/doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="8d6bf-119">Si vous utilisez `/doc-` ou ne spécifiez pas la `/doc` option, le compilateur ne crée pas d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-119">If you use `/doc-` or do not specify the `/doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="8d6bf-120">Dans les fichiers de code source, les commentaires de documentation peuvent précéder les définitions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d6bf-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="8d6bf-121">Défini par l’utilisateur tape, comme un [classe](../../../visual-basic/language-reference/statements/class-statement.md) ou [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8d6bf-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="8d6bf-122">Membres, par exemple un champ, [événement](../../../visual-basic/language-reference/statements/event-statement.md), [propriété](../../../visual-basic/language-reference/statements/property-statement.md), [fonction](../../../visual-basic/language-reference/statements/function-statement.md), ou [sous-routine](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d6bf-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="8d6bf-123">Pour utiliser le fichier XML généré avec la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) la fonctionnalité, soit le nom de fichier du fichier XML de la même que l’assembly que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-123">To use the generated XML file with the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="8d6bf-124">Assurez-vous que le fichier XML est dans le même répertoire que l’assembly afin que lorsque l’assembly est référencé dans le [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projet, le fichier .xml soit également recherché.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="8d6bf-125">Fichiers de documentation XML ne sont pas requis pour qu’IntelliSense fonctionne pour le code dans un projet ou dans des projets référencés par un projet.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="8d6bf-126">Sauf si vous compilez avec `/target:module`, le fichier XML contient les balises `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="8d6bf-127">Ces balises spécifient le nom du fichier contenant le manifeste d’assembly pour le fichier de sortie de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="8d6bf-128">Consultez [balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) pour savoir comment générer la documentation à partir de commentaires dans votre code.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="8d6bf-129">Pour définir /doc dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="8d6bf-129">To set /doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8d6bf-130">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8d6bf-131">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8d6bf-132">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8d6bf-133">3.  Définissez la valeur de la **fichier de documentation XML de générer** boîte.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d6bf-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d6bf-134">Example</span></span>  
 <span data-ttu-id="8d6bf-135">Consultez [documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) pour obtenir un exemple.</span><span class="sxs-lookup"><span data-stu-id="8d6bf-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6bf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d6bf-136">See Also</span></span>  
 [<span data-ttu-id="8d6bf-137">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d6bf-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8d6bf-138">Documentation de votre code avec le langage XML</span><span class="sxs-lookup"><span data-stu-id="8d6bf-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
