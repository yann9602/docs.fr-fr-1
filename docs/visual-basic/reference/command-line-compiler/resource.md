---
title: /Resource (Visual Basic) | Documents Microsoft
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
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
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
ms.openlocfilehash: 2278902f96f7b6349e91a9803f58c3caa89f4f33
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="resource-visual-basic"></a><span data-ttu-id="0dde4-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dde4-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="0dde4-103">Incorpore une ressource managée dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="0dde4-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dde4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dde4-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0dde4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0dde4-105">Arguments</span></span>  
  
|<span data-ttu-id="0dde4-106">Terme</span><span class="sxs-lookup"><span data-stu-id="0dde4-106">Term</span></span>|<span data-ttu-id="0dde4-107">Définition</span><span class="sxs-lookup"><span data-stu-id="0dde4-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="0dde4-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0dde4-108">Required.</span></span> <span data-ttu-id="0dde4-109">Le nom du fichier de ressources à incorporer dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="0dde4-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="0dde4-110">Par défaut, `filename` est public dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0dde4-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="0dde4-111">Placez le nom de fichier entre guillemets (« ») s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="0dde4-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="0dde4-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0dde4-112">Optional.</span></span> <span data-ttu-id="0dde4-113">Le nom logique de la ressource. le nom utilisé pour le charger.</span><span class="sxs-lookup"><span data-stu-id="0dde4-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="0dde4-114">La valeur par défaut est le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="0dde4-114">The default is the name of the file.</span></span> <span data-ttu-id="0dde4-115">Si vous le souhaitez, vous pouvez spécifier si la ressource est publique ou privée dans le manifeste d’assembly, comme avec les éléments suivants : `/res:``filename.res`,`myname.res`,`public`</span><span class="sxs-lookup"><span data-stu-id="0dde4-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dde4-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="0dde4-116">Remarks</span></span>  
 <span data-ttu-id="0dde4-117">Utilisez `/linkresource` pour lier une ressource à un assembly sans placer le fichier de ressources dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="0dde4-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="0dde4-118">Si `filename` est un [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] le fichier de ressources créé, par exemple, par le [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources>espace de noms (voir <xref:System.Resources.ResourceManager>Pour plus d’informations).</xref:System.Resources.ResourceManager> </xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="0dde4-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="0dde4-119">Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez une des méthodes suivantes : <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A></span><span class="sxs-lookup"><span data-stu-id="0dde4-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="0dde4-120">La forme abrégée de `/resource` est `/res`.</span><span class="sxs-lookup"><span data-stu-id="0dde4-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="0dde4-121">Pour plus d’informations sur la définition `/resource` dans l’IDE de Visual Studio, consultez [ressources de gestion de l’Application (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="0dde4-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dde4-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="0dde4-122">Example</span></span>  
 <span data-ttu-id="0dde4-123">Le code suivant compile `In.vb` et le fichier de ressources joint `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="0dde4-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dde4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dde4-124">See Also</span></span>  
 <span data-ttu-id="0dde4-125">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="0dde4-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="0dde4-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span><span class="sxs-lookup"><span data-stu-id="0dde4-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span></span>  
<span data-ttu-id="0dde4-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span><span class="sxs-lookup"><span data-stu-id="0dde4-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span></span>  
<span data-ttu-id="0dde4-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="0dde4-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="0dde4-129"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="0dde4-129"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
