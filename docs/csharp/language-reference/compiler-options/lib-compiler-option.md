---
title: -lib (Options du compilateur C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 476bc43987b5ac8fa222b767b068a9ca14537bc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lib-c-compiler-options"></a><span data-ttu-id="30f73-102">/lib (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="30f73-102">/lib (C# Compiler Options)</span></span>
<span data-ttu-id="30f73-103">L’option **/lib** spécifie l’emplacement des assemblys référencés au moyen de l’option [/reference (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="30f73-103">The **/lib** option specifies the location of assemblies referenced by means of the [/reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30f73-104">Syntax</span></span>  
  
```console  
/lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="30f73-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="30f73-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="30f73-106">Un répertoire dans lequel le compilateur doit effectuer la recherche si un assembly référencé ne se trouve pas dans le répertoire de travail actuel (le répertoire à partir duquel vous appelez le compilateur) ou dans le répertoire système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="30f73-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="30f73-107">Un ou plusieurs répertoires supplémentaires où rechercher des références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30f73-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="30f73-108">Séparez les noms des répertoires supplémentaires par une virgule, sans espace.</span><span class="sxs-lookup"><span data-stu-id="30f73-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30f73-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="30f73-109">Remarks</span></span>  
 <span data-ttu-id="30f73-110">Le compilateur recherche les références d’assembly qui ne sont pas complètes dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="30f73-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="30f73-111">Répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="30f73-111">Current working directory.</span></span> <span data-ttu-id="30f73-112">Il s’agit du répertoire à partir duquel le compilateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="30f73-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="30f73-113">Répertoire système du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="30f73-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="30f73-114">Répertoires spécifiés par **/lib**.</span><span class="sxs-lookup"><span data-stu-id="30f73-114">Directories specified by **/lib**.</span></span>  
  
4.  <span data-ttu-id="30f73-115">Répertoires spécifiés par la variable d’environnement LIB.</span><span class="sxs-lookup"><span data-stu-id="30f73-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="30f73-116">Utilisez **/reference** pour spécifier une référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30f73-116">Use **/reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="30f73-117">**/lib** est additif. Si vous le spécifiez plusieurs fois, il effectue un ajout aux valeurs précédentes.</span><span class="sxs-lookup"><span data-stu-id="30f73-117">**/lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="30f73-118">Au lieu d’utiliser **/lib**, vous pouvez copier dans le répertoire de travail les assemblys nécessaires. De cette façon, vous passez simplement le nom de l’assembly à **/reference**.</span><span class="sxs-lookup"><span data-stu-id="30f73-118">An alternative to using **/lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **/reference**.</span></span> <span data-ttu-id="30f73-119">Vous pouvez ensuite supprimer les assemblys du répertoire de travail.</span><span class="sxs-lookup"><span data-stu-id="30f73-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="30f73-120">Comme le chemin de l’assembly dépendant n’est pas spécifié dans le manifeste de l’assembly, l’application peut être démarrée sur l’ordinateur cible, et recherche et utilise l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="30f73-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="30f73-121">Le fait que le compilateur puisse référencer l’assembly n’implique pas que le common language runtime soit en mesure de rechercher et charger l’assembly au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="30f73-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="30f73-122">Consultez [Méthode de localisation des assemblys par le runtime](../../../framework/deployment/how-the-runtime-locates-assemblies.md) pour plus d’informations sur la façon dont le runtime recherche des assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="30f73-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="30f73-123">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="30f73-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="30f73-124">Ouvrez la boîte de dialogue **Pages de propriété** du projet.</span><span class="sxs-lookup"><span data-stu-id="30f73-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="30f73-125">Cliquez sur la page de propriétés **Chemin aux références**.</span><span class="sxs-lookup"><span data-stu-id="30f73-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="30f73-126">Modifiez le contenu de la zone de liste.</span><span class="sxs-lookup"><span data-stu-id="30f73-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="30f73-127">Pour plus d’informations sur la définition de cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="30f73-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f73-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="30f73-128">Example</span></span>  
 <span data-ttu-id="30f73-129">Compilez t2.cs pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="30f73-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="30f73-130">Le compilateur recherche les références d’assembly dans le répertoire de travail et dans le répertoire racine du lecteur C.</span><span class="sxs-lookup"><span data-stu-id="30f73-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="30f73-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30f73-131">See Also</span></span>  
 [<span data-ttu-id="30f73-132">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="30f73-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="30f73-133">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="30f73-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
