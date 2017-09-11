---
title: /win32manifest (Visual Basic) | Documents Microsoft
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
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
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
ms.openlocfilehash: 4a9693bd7eb03dee5a2a9f2d43360b963e9fd876
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="win32manifest-visual-basic"></a><span data-ttu-id="b6565-102">/win32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6565-102">/win32manifest (Visual Basic)</span></span>
<span data-ttu-id="b6565-103">Identifie un fichier manifeste d'application Win32 défini par l'utilisateur à incorporer dans le fichier exécutable portable (PE) d'un projet.</span><span class="sxs-lookup"><span data-stu-id="b6565-103">Identifies a user-defined Win32 application manifest file to be embedded into a project's portable executable (PE) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6565-104">Syntax</span></span>  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6565-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6565-105">Arguments</span></span>  
  
|<span data-ttu-id="b6565-106">Terme</span><span class="sxs-lookup"><span data-stu-id="b6565-106">Term</span></span>|<span data-ttu-id="b6565-107">Définition</span><span class="sxs-lookup"><span data-stu-id="b6565-107">Definition</span></span>|  
|---|---|  
|`fileName`|<span data-ttu-id="b6565-108">Le chemin d’accès du fichier manifeste personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b6565-108">The path of the custom manifest file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6565-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="b6565-109">Remarks</span></span>  
 <span data-ttu-id="b6565-110">Par défaut, le compilateur Visual Basic incorpore un manifeste d’application qui spécifie le niveau d’exécution demandé asInvoker.</span><span class="sxs-lookup"><span data-stu-id="b6565-110">By default, the Visual Basic compiler embeds an application manifest that specifies a requested execution level of asInvoker.</span></span> <span data-ttu-id="b6565-111">Il crée le manifeste dans le même dossier que celui dans lequel le fichier exécutable est généré, en général le dossier bin\Debug ou bin\Release lorsque vous utilisez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b6565-111">It creates the manifest in the same folder in which the executable file is built, typically the bin\Debug or bin\Release folder when you use Visual Studio.</span></span> <span data-ttu-id="b6565-112">Si vous souhaitez fournir un manifeste personnalisé, par exemple, pour spécifier le niveau d’exécution demandé de « highestAvailable » ou requireAdministrator, utilisez cette option pour spécifier le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="b6565-112">If you want to supply a custom manifest, for example to specify a requested execution level of highestAvailable or requireAdministrator, use this option to specify the name of the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6565-113">Cette option et la [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="b6565-113">This option and the [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) option are mutually exclusive.</span></span> <span data-ttu-id="b6565-114">Si vous essayez d’utiliser les deux options dans la même ligne de commande, vous obtiendrez une erreur de build.</span><span class="sxs-lookup"><span data-stu-id="b6565-114">If you try to use both options in the same command line, you will get a build error.</span></span>  
  
 <span data-ttu-id="b6565-115">Une application qui n’a aucune application manifeste qui spécifie qu'un niveau d’exécution demandé sera soumis à la virtualisation de fichiers et du Registre sous la fonctionnalité contrôle de compte d’utilisateur dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="b6565-115">An application that has no application manifest that specifies a requested execution level will be subject to file/registry virtualization under the User Account Control feature in Windows Vista.</span></span> <span data-ttu-id="b6565-116">Pour plus d’informations sur la virtualisation, consultez [déploiement ClickOnce sur Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="b6565-116">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="b6565-117">Votre application sera soumis à la virtualisation si une des conditions suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="b6565-117">Your application will be subject to virtualization if either of the following conditions is true:</span></span>  
  
1.  <span data-ttu-id="b6565-118">Vous utilisez la `/nowin32manifest` option et si vous ne fournissez pas de manifeste dans une étape de génération ultérieure ou en tant que partie d’un fichier de ressources Windows (.res) à l’aide de la `/win32resource` option.</span><span class="sxs-lookup"><span data-stu-id="b6565-118">You use the `/nowin32manifest` option and you do not provide a manifest in a later build step or as part of a Windows Resource (.res) file by using the `/win32resource` option.</span></span>  
  
2.  <span data-ttu-id="b6565-119">Vous fournissez un manifeste personnalisé qui ne spécifie pas un niveau d’exécution demandé.</span><span class="sxs-lookup"><span data-stu-id="b6565-119">You provide a custom manifest that does not specify a requested execution level.</span></span>  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="b6565-120">Crée un fichier .manifest de valeur par défaut et le stocke dans les répertoires debug et release avec le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="b6565-120"> creates a default .manifest file and stores it in the debug and release directories alongside the executable file.</span></span> <span data-ttu-id="b6565-121">Vous pouvez afficher ou modifier le fichier App.manifest par défaut en cliquant sur **afficher les paramètres UAC** sur la **Application** onglet du Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="b6565-121">You can view or edit the default app.manifest file by clicking **View UAC Settings** on the **Application** tab in the Project Designer.</span></span> <span data-ttu-id="b6565-122">Pour plus d’informations, consultez [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b6565-122">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="b6565-123">Vous pouvez fournir le manifeste d’application comme une étape après génération personnalisée ou en tant que partie d’un fichier de ressources Win32 à l’aide de la `/nowin32manifest` option.</span><span class="sxs-lookup"><span data-stu-id="b6565-123">You can provide the application manifest as a custom post-build step or as part of a Win32 resource file by using the `/nowin32manifest` option.</span></span> <span data-ttu-id="b6565-124">Utilisez cette même option si vous souhaitez que votre application soit soumis à la virtualisation de fichiers ou du Registre dans Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="b6565-124">Use that same option if you want your application to be subject to file or registry virtualization on Windows Vista.</span></span> <span data-ttu-id="b6565-125">Cela empêchera le compilateur de créer et d’incorporer un manifeste par défaut dans le fichier PE.</span><span class="sxs-lookup"><span data-stu-id="b6565-125">This will prevent the compiler from creating and embedding a default manifest in the PE file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6565-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6565-126">Example</span></span>  
 <span data-ttu-id="b6565-127">L’exemple suivant présente le manifeste par défaut que le compilateur Visual Basic insère dans un PE.</span><span class="sxs-lookup"><span data-stu-id="b6565-127">The following example shows the default manifest that the Visual Basic compiler inserts into a PE.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6565-128">Le compilateur insère un nom d’application standard, MyApplication.app, au manifeste XML.</span><span class="sxs-lookup"><span data-stu-id="b6565-128">The compiler inserts a standard application name MyApplication.app into the manifest XML.</span></span> <span data-ttu-id="b6565-129">Il s’agit d’une solution de contournement pour permettre aux applications de s’exécuter sur Windows Server 2003 Service Pack 3.</span><span class="sxs-lookup"><span data-stu-id="b6565-129">This is a workaround to enable applications to run on Windows Server 2003 Service Pack 3.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6565-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6565-130">See Also</span></span>  
 <span data-ttu-id="b6565-131">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6565-131">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b6565-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span><span class="sxs-lookup"><span data-stu-id="b6565-132"> [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)</span></span>
