---
title: /LIBPATH | Documents Microsoft
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
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
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
ms.openlocfilehash: 7f24dd7707645f45677dcf7009e1adc64afaaa7c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="libpath"></a><span data-ttu-id="53949-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="53949-102">/libpath</span></span>
<span data-ttu-id="53949-103">Spécifie l’emplacement des assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="53949-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53949-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53949-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="53949-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="53949-105">Arguments</span></span>  
  
|<span data-ttu-id="53949-106">Terme</span><span class="sxs-lookup"><span data-stu-id="53949-106">Term</span></span>|<span data-ttu-id="53949-107">Définition</span><span class="sxs-lookup"><span data-stu-id="53949-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="53949-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="53949-108">Required.</span></span> <span data-ttu-id="53949-109">Liste de délimitée par des points-virgules des répertoires où le compilateur doit vérifier si un assembly référencé est introuvable dans le répertoire de travail actuel (le répertoire à partir duquel vous appelez le compilateur) ou le répertoire du système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="53949-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="53949-110">Si le nom de répertoire contient un espace, placez le nom entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="53949-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53949-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="53949-111">Remarks</span></span>  
 <span data-ttu-id="53949-112">Le `/libpath` option spécifie l’emplacement des assemblys référencés par le [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span><span class="sxs-lookup"><span data-stu-id="53949-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="53949-113">Le compilateur recherche les références d’assembly qui ne sont pas qualifiés complets dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="53949-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="53949-114">Répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="53949-114">Current working directory.</span></span> <span data-ttu-id="53949-115">C’est le répertoire à partir duquel le compilateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="53949-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="53949-116">Le répertoire système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="53949-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="53949-117">Répertoires spécifiés par `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="53949-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="53949-118">Répertoires spécifiés par la variable d’environnement LIB.</span><span class="sxs-lookup"><span data-stu-id="53949-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="53949-119">La `/libpath` option est additif ; spécification plus qu’une seule fois ajoute aux valeurs précédentes.</span><span class="sxs-lookup"><span data-stu-id="53949-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="53949-120">Utilisez `/reference` pour spécifier une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="53949-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="53949-121">Pour définir /libpath dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="53949-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="53949-122">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="53949-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="53949-123">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="53949-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="53949-124">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="53949-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="53949-125">2.  Cliquez sur le **références** onglet.</span><span class="sxs-lookup"><span data-stu-id="53949-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="53949-126">3.  Cliquez sur le **référencer les chemins d’accès... ** bouton.</span><span class="sxs-lookup"><span data-stu-id="53949-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="53949-127">4.  Dans le **chemins d’accès de référence** boîte de dialogue, entrez le nom du répertoire dans le **dossier :** boîte.</span><span class="sxs-lookup"><span data-stu-id="53949-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="53949-128">5.  Cliquez sur **ajouter un dossier**.</span><span class="sxs-lookup"><span data-stu-id="53949-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53949-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="53949-129">Example</span></span>  
 <span data-ttu-id="53949-130">Le code suivant compile `T2.vb` pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="53949-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="53949-131">Le compilateur recherche dans le répertoire de travail, dans le répertoire racine du lecteur C: et dans le répertoire New Assemblies du lecteur C: de références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="53949-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="53949-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53949-132">See Also</span></span>  
 <span data-ttu-id="53949-133">[Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="53949-133">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="53949-134"> [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="53949-134"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="53949-135"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="53949-135"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
