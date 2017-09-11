---
title: /linkresource (Visual Basic) | Documents Microsoft
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8d4d2d2fdacef0c830414790efa544a96c35fd3c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="06578-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06578-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="06578-103">Crée un lien à une ressource managée.</span><span class="sxs-lookup"><span data-stu-id="06578-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06578-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06578-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="06578-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="06578-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="06578-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06578-106">Required.</span></span> <span data-ttu-id="06578-107">Le fichier de ressources à lier à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="06578-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="06578-108">Si le nom de fichier contient un espace, placez le nom entre guillemets (« »).</span><span class="sxs-lookup"><span data-stu-id="06578-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="06578-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="06578-109">Optional.</span></span> <span data-ttu-id="06578-110">Nom logique de la ressource.</span><span class="sxs-lookup"><span data-stu-id="06578-110">The logical name for the resource.</span></span> <span data-ttu-id="06578-111">Le nom qui est utilisé pour charger la ressource.</span><span class="sxs-lookup"><span data-stu-id="06578-111">The name that is used to load the resource.</span></span> <span data-ttu-id="06578-112">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="06578-112">The default is the name of the file.</span></span> <span data-ttu-id="06578-113">Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d’assembly, par exemple : `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="06578-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="06578-114">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="06578-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06578-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="06578-115">Remarks</span></span>  
 <span data-ttu-id="06578-116">Le `/linkresource` option n’incorpore pas le fichier de ressources dans le fichier de sortie ; Utilisez la `/resource` option pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="06578-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="06578-117">Le `/linkresource` option requiert l’une de le `/target` options autres que `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="06578-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="06578-118">Si `filename` est un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] le fichier de ressources créé, par exemple, par le [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources>espace de noms.</xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="06578-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="06578-119">(Pour plus d’informations, consultez <xref:System.Resources.ResourceManager>.)</xref:System.Resources.ResourceManager> Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la <xref:System.Reflection.Assembly>classe.</xref:System.Reflection.Assembly></span><span class="sxs-lookup"><span data-stu-id="06578-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="06578-120">Le nom de fichier peut être n’importe quel format de fichier.</span><span class="sxs-lookup"><span data-stu-id="06578-120">The file name can be any file format.</span></span> <span data-ttu-id="06578-121">Par exemple, vous souhaiterez une DLL native de l’assembly, de sorte que peut être installé dans le global assembly cache et accessible à partir du code managé dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="06578-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="06578-122">La forme abrégée de `/linkresource` est `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="06578-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06578-123">La `/linkresource` option n’est pas disponible à partir de l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="06578-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06578-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="06578-124">Example</span></span>  
 <span data-ttu-id="06578-125">Le code suivant compile `In.vb` et des liens vers le fichier de ressources `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="06578-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="06578-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06578-126">See Also</span></span>  
 <span data-ttu-id="06578-127">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="06578-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="06578-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="06578-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="06578-129"> [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span><span class="sxs-lookup"><span data-stu-id="06578-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span></span>  
<span data-ttu-id="06578-130"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="06578-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
