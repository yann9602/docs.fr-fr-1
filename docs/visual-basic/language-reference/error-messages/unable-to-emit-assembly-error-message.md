---
title: "Impossible de créer l’assembly : &lt;message d’erreur&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="9e3c7-102">Impossible de créer l’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="9e3c7-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="9e3c7-103">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur appelle l’utilitaire Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste, et l’éditeur de liens signale une erreur lors de l’étape d’émission de création de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="9e3c7-104">**ID d’erreur :** BC30145</span><span class="sxs-lookup"><span data-stu-id="9e3c7-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e3c7-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9e3c7-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="9e3c7-106">Examinez le message d’erreur cité et consultez la rubrique [Erreurs et avertissements de l’outil Al.exe](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pour obtenir davantage d’explications et de conseils.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="9e3c7-107">Essayez de signer l’assembly manuellement, soit à l’aide de la [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) ou le [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="9e3c7-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="9e3c7-108">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="9e3c7-109">Pour signer manuellement l'assembly</span><span class="sxs-lookup"><span data-stu-id="9e3c7-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="9e3c7-110">Utilisez le [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) pour créer un fichier de paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="9e3c7-111">Ce fichier porte l’extension .snk.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="9e3c7-112">Supprimez la référence COM qui génère l'erreur de votre projet.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="9e3c7-113">À partir des fenêtres **Démarrer** menu, pointez sur **programmes**, pointez sur **Microsoft Visual Studio 2008**, pointez sur **Visual Studio Tools**, et puis cliquez sur **invite de commandes de Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="9e3c7-114">Accédez au répertoire dans lequel vous voulez placer le wrapper d'assembly.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="9e3c7-115">Tapez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="9e3c7-116">Voici un exemple du code que vous pouvez entrer.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="9e3c7-117">Utilisez des guillemets doubles (") si un chemin ou un fichier contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="9e3c7-118">Dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], ajoutez une référence à un assembly .NET dans le fichier que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="9e3c7-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3c7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e3c7-119">See Also</span></span>  
 [<span data-ttu-id="9e3c7-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="9e3c7-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="9e3c7-121">Avertissements et erreurs de l’outil Al.exe</span><span class="sxs-lookup"><span data-stu-id="9e3c7-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="9e3c7-122">Sn.exe (outil Strong Name)</span><span class="sxs-lookup"><span data-stu-id="9e3c7-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="9e3c7-123">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="9e3c7-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="9e3c7-124">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="9e3c7-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
