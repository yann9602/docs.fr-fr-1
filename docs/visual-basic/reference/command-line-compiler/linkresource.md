---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="c7ecb-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7ecb-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="c7ecb-103">Crée un lien à une ressource managée.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ecb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7ecb-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7ecb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7ecb-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c7ecb-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-106">Required.</span></span> <span data-ttu-id="c7ecb-107">Le fichier de ressources à lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="c7ecb-108">Si le nom de fichier contient un espace, placez-le entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="c7ecb-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="c7ecb-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-109">Optional.</span></span> <span data-ttu-id="c7ecb-110">Le nom logique pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-110">The logical name for the resource.</span></span> <span data-ttu-id="c7ecb-111">Le nom qui est utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-111">The name that is used to load the resource.</span></span> <span data-ttu-id="c7ecb-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-112">The default is the name of the file.</span></span> <span data-ttu-id="c7ecb-113">Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d’assembly, par exemple : `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="c7ecb-114">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7ecb-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7ecb-115">Remarks</span></span>  
 <span data-ttu-id="c7ecb-116">Le `/linkresource` option ne pas incorpore le fichier de ressources dans le fichier de sortie ; Utilisez la `/resource` option pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="c7ecb-117">Le `/linkresource` option requiert l’une de le `/target` options autres que `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="c7ecb-118">Si `filename` est un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] le fichier de ressources créé, par exemple, par le [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="c7ecb-119">(Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la <xref:System.Reflection.Assembly> classe.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="c7ecb-120">Le nom de fichier peut être n’importe quel format de fichier.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-120">The file name can be any file format.</span></span> <span data-ttu-id="c7ecb-121">C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="c7ecb-122">La forme abrégée de `/linkresource` est `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ecb-123">Le `/linkresource` option n’est pas disponible à partir de l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7ecb-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7ecb-124">Example</span></span>  
 <span data-ttu-id="c7ecb-125">Le code suivant compile `In.vb` et des liens vers le fichier de ressources `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="c7ecb-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7ecb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7ecb-126">See Also</span></span>  
 [<span data-ttu-id="c7ecb-127">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7ecb-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c7ecb-128">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7ecb-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="c7ecb-129">/Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7ecb-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="c7ecb-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="c7ecb-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
