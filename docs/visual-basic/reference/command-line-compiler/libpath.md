---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a><span data-ttu-id="3601c-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="3601c-102">/libpath</span></span>
<span data-ttu-id="3601c-103">Spécifie l’emplacement des assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="3601c-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3601c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3601c-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="3601c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3601c-105">Arguments</span></span>  
  
|<span data-ttu-id="3601c-106">Terme</span><span class="sxs-lookup"><span data-stu-id="3601c-106">Term</span></span>|<span data-ttu-id="3601c-107">Définition</span><span class="sxs-lookup"><span data-stu-id="3601c-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="3601c-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3601c-108">Required.</span></span> <span data-ttu-id="3601c-109">Délimitée par des points-virgules de liste de répertoires pour le compilateur doit vérifier si un assembly référencé est introuvable dans le répertoire de travail actif (le répertoire à partir duquel vous appelez le compilateur) ou le répertoire du système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3601c-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="3601c-110">Si le nom de répertoire contient un espace, placez-le entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="3601c-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3601c-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="3601c-111">Remarks</span></span>  
 <span data-ttu-id="3601c-112">Le `/libpath` option spécifie l’emplacement des assemblys référencés par le [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span><span class="sxs-lookup"><span data-stu-id="3601c-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="3601c-113">Le compilateur recherche les références d’assembly qui ne sont pas complètes dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="3601c-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="3601c-114">Répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="3601c-114">Current working directory.</span></span> <span data-ttu-id="3601c-115">Il s’agit du répertoire à partir duquel le compilateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="3601c-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="3601c-116">Répertoire système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3601c-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="3601c-117">Répertoires spécifiés par `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="3601c-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="3601c-118">Répertoires spécifiés par la variable d’environnement LIB.</span><span class="sxs-lookup"><span data-stu-id="3601c-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="3601c-119">Le `/libpath` option est additif ; en spécifiant plus qu’une seule fois ajoute aux valeurs précédentes.</span><span class="sxs-lookup"><span data-stu-id="3601c-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="3601c-120">Utilisez `/reference` pour spécifier une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="3601c-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="3601c-121">Pour définir /libpath dans Visual Studio environnement de développement intégré</span><span class="sxs-lookup"><span data-stu-id="3601c-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3601c-122">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="3601c-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3601c-123">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3601c-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="3601c-124">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="3601c-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="3601c-125">2.  Cliquez sur l’onglet **Références**.</span><span class="sxs-lookup"><span data-stu-id="3601c-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="3601c-126">3.  Cliquez sur le **référencer les chemins d’accès...**  bouton.</span><span class="sxs-lookup"><span data-stu-id="3601c-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="3601c-127">4.  Dans le **chemins d’accès de référence** boîte de dialogue, entrez le nom du répertoire dans le **dossier :** boîte.</span><span class="sxs-lookup"><span data-stu-id="3601c-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="3601c-128">5.  Cliquez sur **ajouter un dossier**.</span><span class="sxs-lookup"><span data-stu-id="3601c-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3601c-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="3601c-129">Example</span></span>  
 <span data-ttu-id="3601c-130">Le code suivant compile `T2.vb` pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="3601c-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="3601c-131">Le compilateur recherche dans le répertoire de travail, dans le répertoire racine du lecteur C: et dans le répertoire de nouveaux assemblys du lecteur C:, références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="3601c-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3601c-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3601c-132">See Also</span></span>  
 [<span data-ttu-id="3601c-133">Assemblys et le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="3601c-133">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="3601c-134">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3601c-134">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3601c-135">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3601c-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
