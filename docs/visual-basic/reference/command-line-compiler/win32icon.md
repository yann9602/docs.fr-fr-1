---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65149c617220966bc3bb6897d757a71cd60167d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon"></a><span data-ttu-id="e1e4f-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="e1e4f-102">/win32icon</span></span>
<span data-ttu-id="e1e4f-103">Insère un fichier .ico dans le fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="e1e4f-104">Ce fichier .ico représente le fichier de sortie dans **l’Explorateur de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e4f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1e4f-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1e4f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e1e4f-106">Arguments</span></span>  
  
|<span data-ttu-id="e1e4f-107">Terme</span><span class="sxs-lookup"><span data-stu-id="e1e4f-107">Term</span></span>|<span data-ttu-id="e1e4f-108">Définition</span><span class="sxs-lookup"><span data-stu-id="e1e4f-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="e1e4f-109">Le fichier .ico à ajouter à votre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="e1e4f-110">Placez le nom de fichier entre guillemets ( » «) si elle contient un espace.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e4f-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e1e4f-111">Remarks</span></span>  
 <span data-ttu-id="e1e4f-112">Vous pouvez créer un fichier .ico avec le compilateur de ressources (RC) Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="e1e4f-113">Le compilateur de ressources est appelé lorsque vous compilez un programme Visual C++ ; un fichier .ico est créé à partir du fichier .rc.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="e1e4f-114">Le `/win32icon` et `/win32resource` options s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="e1e4f-115">Consultez [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) référence un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fichier de ressources, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="e1e4f-116">Consultez [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) pour importer un fichier .res.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="e1e4f-117">Pour définir les /win32icon dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1e4f-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="e1e4f-118">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e1e4f-119">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e1e4f-120">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="e1e4f-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="e1e4f-121">2.  Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="e1e4f-121">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="e1e4f-122">3.  Modifiez la valeur dans la **icône** boîte.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-122">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1e4f-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1e4f-123">Example</span></span>  
 <span data-ttu-id="e1e4f-124">Le code suivant compile `In.vb` et attache un fichier .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="e1e4f-124">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1e4f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1e4f-125">See Also</span></span>  
 [<span data-ttu-id="e1e4f-126">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1e4f-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e1e4f-127">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e1e4f-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
