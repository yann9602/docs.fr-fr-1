---
title: "Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
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
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 569683169c6d7ae50c33ed06d3b365a663f16715
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="62be6-102">Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio</span><span class="sxs-lookup"><span data-stu-id="62be6-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>
<span data-ttu-id="62be6-103">Le fichier vsvars32.bat définit les variables d'environnement appropriées pour permettre des générations à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="62be6-103">The vsvars32.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="62be6-104">Pour plus d’informations sur vsvars32.bat, consultez l’[article Q248802 de la Base de connaissances](http://go.microsoft.com/fwlink/?LinkId=225042).</span><span class="sxs-lookup"><span data-stu-id="62be6-104">For more information about vsvars32.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  
  
 <span data-ttu-id="62be6-105">Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, vous ne devez pas exécuter vcvarsall.bat ni vcvars32.bat à partir de différentes versions dans la même fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="62be6-105">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run vsvars32.bat or vcvars32.bat from different versions in the same Command Prompt window.</span></span>  
  
### <a name="to-run-vsvars32bat"></a><span data-ttu-id="62be6-106">Pour exécuter VSVARS32.BAT</span><span class="sxs-lookup"><span data-stu-id="62be6-106">To run VSVARS32.BAT</span></span>  
  
1.  <span data-ttu-id="62be6-107">Dans le menu **Démarrer**, ouvrez l’**Invite de commandes développeur pour VS2012**.</span><span class="sxs-lookup"><span data-stu-id="62be6-107">From the **Start** menu, open the **Developer Command Prompt for VS2012**.</span></span>  
  
2.  <span data-ttu-id="62be6-108">Accédez au sous-répertoire Program Files\Microsoft Visual Studio *version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio *version*\Common7\Tools de votre installation.</span><span class="sxs-lookup"><span data-stu-id="62be6-108">Change to the Program Files\Microsoft Visual Studio *Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio *Version*\Common7\Tools subdirectory of your installation.</span></span>  
  
3.  <span data-ttu-id="62be6-109">Exécutez VSVARS32.bat en tapant **VSVARS32**.</span><span class="sxs-lookup"><span data-stu-id="62be6-109">Run VSVARS32.bat by typing **VSVARS32**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="62be6-110">VSVARS32.bat peut varier d'un ordinateur à l'autre.</span><span class="sxs-lookup"><span data-stu-id="62be6-110">VSVARS32.bat can vary from computer to computer.</span></span> <span data-ttu-id="62be6-111">Ne remplacez pas un fichier VSVARS32.bat manquant ou endommagé par un fichier VSVARS32.bat d'un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62be6-111">Do not replace a missing or damaged VSVARS32.bat file with a VSVARS32.bat from another computer.</span></span> <span data-ttu-id="62be6-112">À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.</span><span class="sxs-lookup"><span data-stu-id="62be6-112">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62be6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62be6-113">See Also</span></span>  
 [<span data-ttu-id="62be6-114">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="62be6-114">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)

