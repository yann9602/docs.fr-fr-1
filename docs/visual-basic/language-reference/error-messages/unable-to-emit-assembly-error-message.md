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
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="5e396-102">Impossible de créer l’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="5e396-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="5e396-103">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur appelle l’utilitaire Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste, et l’éditeur de liens signale une erreur lors de l’étape d’émission de création de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5e396-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="5e396-104">**ID d’erreur :** BC30145</span><span class="sxs-lookup"><span data-stu-id="5e396-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e396-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5e396-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="5e396-106">Examinez le message d’erreur entre guillemets et consultez la rubrique [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="5e396-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="5e396-107">Pour obtenir davantage d’explications et de conseils.</span><span class="sxs-lookup"><span data-stu-id="5e396-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="5e396-108">Essayez de signer l’assembly manuellement, soit à l’aide de la [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou le [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5e396-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="5e396-109">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5e396-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="5e396-110">Pour signer manuellement l'assembly</span><span class="sxs-lookup"><span data-stu-id="5e396-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="5e396-111">Utilisez le [Sn.exe (outil Strong Name)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) pour créer un fichier de paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="5e396-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="5e396-112">Ce fichier porte l’extension .snk.</span><span class="sxs-lookup"><span data-stu-id="5e396-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="5e396-113">Supprimez la référence COM qui génère l'erreur de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5e396-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="5e396-114">À partir des fenêtres **Démarrer** menu, pointez sur **programmes**, pointez sur **Microsoft Visual Studio 2008**, pointez sur **Visual Studio Tools**, et puis cliquez sur **invite de commandes de Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="5e396-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="5e396-115">Accédez au répertoire dans lequel vous voulez placer le wrapper d'assembly.</span><span class="sxs-lookup"><span data-stu-id="5e396-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="5e396-116">Tapez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="5e396-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="5e396-117">Voici un exemple du code que vous pouvez entrer.</span><span class="sxs-lookup"><span data-stu-id="5e396-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="5e396-118">Utilisez des guillemets doubles (") si un chemin ou un fichier contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="5e396-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="5e396-119">Dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], ajoutez une référence à un assembly .NET dans le fichier que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="5e396-119">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e396-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e396-120">See Also</span></span>  
 
 <span data-ttu-id="5e396-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="5e396-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="5e396-122">[Sn.exe (outil Strong Name)] [Sn.exe (outil Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="5e396-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="5e396-123">Guide pratique pour créer une paire de clés publique/privée</span><span class="sxs-lookup"><span data-stu-id="5e396-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="5e396-124">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="5e396-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
