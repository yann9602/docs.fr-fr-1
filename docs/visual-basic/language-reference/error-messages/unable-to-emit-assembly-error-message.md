---
title: "Impossible de créer l’assembly : &lt;message d’erreur&gt; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
dev_langs:
- VB
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
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
ms.openlocfilehash: d15981a1a2fb31ba377066fa421f5a9979d47a12
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="87cc9-102">Impossible de créer l’assembly : &lt;message d’erreur&gt;</span><span class="sxs-lookup"><span data-stu-id="87cc9-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="87cc9-103">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur appelle l’utilitaire Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste, et l’éditeur de liens signale une erreur lors de l’étape d’émission de création de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="87cc9-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="87cc9-104">**ID d’erreur :** BC30145</span><span class="sxs-lookup"><span data-stu-id="87cc9-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87cc9-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="87cc9-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="87cc9-106">Examinez le message d’erreur cité et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pour davantage d’explications et de conseils.</span><span class="sxs-lookup"><span data-stu-id="87cc9-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="87cc9-107">Essayez de signer l’assembly manuellement, soit à l’aide de la [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) ou [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="87cc9-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="87cc9-108">Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="87cc9-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="87cc9-109">Pour signer manuellement l'assembly</span><span class="sxs-lookup"><span data-stu-id="87cc9-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="87cc9-110">Utilisez le [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) pour créer un fichier de paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="87cc9-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="87cc9-111">Ce fichier porte l’extension .snk.</span><span class="sxs-lookup"><span data-stu-id="87cc9-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="87cc9-112">Supprimez la référence COM qui génère l'erreur de votre projet.</span><span class="sxs-lookup"><span data-stu-id="87cc9-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="87cc9-113">À partir des fenêtres **Démarrer** menu, pointez sur **programmes**, pointez sur **Microsoft Visual Studio 2008**, pointez sur **Visual Studio Tools**, puis cliquez sur **invite de commandes de Visual Studio 2008**.</span><span class="sxs-lookup"><span data-stu-id="87cc9-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="87cc9-114">Accédez au répertoire dans lequel vous voulez placer le wrapper d'assembly.</span><span class="sxs-lookup"><span data-stu-id="87cc9-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="87cc9-115">Tapez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="87cc9-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="87cc9-116">Voici un exemple du code que vous pouvez entrer.</span><span class="sxs-lookup"><span data-stu-id="87cc9-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="87cc9-117">Utilisez des guillemets doubles (") si un chemin ou un fichier contient des espaces.</span><span class="sxs-lookup"><span data-stu-id="87cc9-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="87cc9-118">Dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], ajoutez une référence à un assembly .NET dans le fichier que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="87cc9-118">In [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cc9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87cc9-119">See Also</span></span>  
 <span data-ttu-id="87cc9-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="87cc9-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="87cc9-121"> [Avertissements et erreurs de l’outil Al.exe](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="87cc9-121"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="87cc9-122"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="87cc9-122"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="87cc9-123"> [Comment : créer une paire de clés publique/privée](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span><span class="sxs-lookup"><span data-stu-id="87cc9-123"> [How to: Create a Public-Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span></span>  
<span data-ttu-id="87cc9-124"> [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="87cc9-124"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
