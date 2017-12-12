---
title: "Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: afab503719f67cf7ad1762370ed3062e12ad88e9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="53f82-102">Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="53f82-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="53f82-103">Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="53f82-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="53f82-104">Pour plus d’informations sur VsDevCmd.bat, consultez [l’article Q248802 de la Base de connaissances](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span><span class="sxs-lookup"><span data-stu-id="53f82-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).</span></span>  

> [!NOTE]
> <span data-ttu-id="53f82-105">Le fichier VsDevCmd.bat est un nouveau fichier fourni avec Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="53f82-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="53f82-106">Visual Studio 2015 et versions antérieures utilisaient VSVARS32.bat dans le même but.</span><span class="sxs-lookup"><span data-stu-id="53f82-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="53f82-107">Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span><span class="sxs-lookup"><span data-stu-id="53f82-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="53f82-108">Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="53f82-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="53f82-109">Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="53f82-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="53f82-110">Pour exécuter VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="53f82-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="53f82-111">Dans le menu **Démarrer**, ouvrez **l’invite de commandes développeur pour VS2017**.</span><span class="sxs-lookup"><span data-stu-id="53f82-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="53f82-112">Elle se trouve dans le dossier **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="53f82-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="53f82-113">Accédez au sous-répertoire \Program Files\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools ou \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools de votre installation.</span><span class="sxs-lookup"><span data-stu-id="53f82-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="53f82-114">(*Version* correspond à *2017* pour la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="53f82-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="53f82-115">*Offre* correspond à *Enterprise*, *Professional* ou *Community*.)</span><span class="sxs-lookup"><span data-stu-id="53f82-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="53f82-116">Exécutez VsDevCmd.bat en tapant **VsDevCmd**.</span><span class="sxs-lookup"><span data-stu-id="53f82-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="53f82-117">VsDevCmd.bat peut varier d’un ordinateur à l’autre.</span><span class="sxs-lookup"><span data-stu-id="53f82-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="53f82-118">Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="53f82-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="53f82-119">À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.</span><span class="sxs-lookup"><span data-stu-id="53f82-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f82-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53f82-120">See Also</span></span>  
 [<span data-ttu-id="53f82-121">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="53f82-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
