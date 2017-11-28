---
title: "Invite de commandes développeur pour Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command prompt, Windows SDK
- Visual Studio command prompt
- command prompt, Visual Studio
- SDK command prompt
- tools [.NET Framework], setting environment variables
- environment variables, setting for tools
- developer command prompt
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e93a1d116ac0480c80e259ddbadbc65fd9539389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="developer-command-prompt-for-visual-studio"></a><span data-ttu-id="ef3c6-102">Invite de commandes développeur pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef3c6-102">Developer Command Prompt for Visual Studio</span></span>
<span data-ttu-id="ef3c6-103">L’invite de commandes développeur pour Visual Studio définit automatiquement les variables d’environnement qui vous permettent d’utiliser facilement les outils du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-103">The Developer Command Prompt for Visual Studio automatically sets the environment variables that enable you to easily use .NET Framework tools.</span></span> <span data-ttu-id="ef3c6-104">L’invite de commandes développeur est installée avec la version complète ou la version Community de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-104">The Developer Command Prompt is installed with full or community editions of Visual Studio.</span></span> <span data-ttu-id="ef3c6-105">Elle n’est pas installée avec la version Express de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-105">It is not installed with the Express versions of Visual Studio.</span></span>  
  
<a name="find"></a>   
## <a name="searching-for-the-command-prompt-on-your-machine"></a><span data-ttu-id="ef3c6-106">Recherche de l’invite de commandes sur votre machine</span><span class="sxs-lookup"><span data-stu-id="ef3c6-106">Searching for the Command Prompt on your machine</span></span>  
 <span data-ttu-id="ef3c6-107">Vous pouvez voir plusieurs invites de commandes, selon la version de Visual Studio et tout kit de développement logiciel (SDK) que vous avez installés.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-107">You may see multiple command prompts, depending on the version of Visual Studio and any additional SDKs you've installed.</span></span> <span data-ttu-id="ef3c6-108">Par exemple, les versions 64 bits de Visual Studio fournissent à la fois des invites de commandes 32 bits et 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-108">For example, 64-bit versions of Visual Studio provide both 32-bit and 64-bit command prompts.</span></span> <span data-ttu-id="ef3c6-109">(Les versions 32 bits et 64 bits de la plupart des outils sont identiques ; toutefois, certains outils apportent des modifications spécifiques aux environnements 32 bits et 64 bits.) Si les étapes ci-dessous ne fonctionnent pas, vous pouvez essayer de [rechercher manuellement les fichiers sur votre ordinateur](#alternative) ou de [lancer l’invite de commandes à partir de Visual Studio](#visualstudio).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-109">(The 32-bit and 64-bit versions of most tools are identical; however, a few tools make changes specific to 32-bit and 64-bit environments.) If the steps below don't work, you can try [Manually locating the files on your machine](#alternative) or [Running command prompt from inside Visual Studio](#visualstudio).</span></span>  
  
 <span data-ttu-id="ef3c6-110">**Sous Windows 10**</span><span class="sxs-lookup"><span data-stu-id="ef3c6-110">**In Windows 10**</span></span>  
  
1.  <span data-ttu-id="ef3c6-111">Ouvrez le menu **Démarrer**, par exemple en appuyant sur la touche du logo Windows ![Logo Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") de votre clavier.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-111">Open the **Start** menu, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ef3c6-112">Dans le menu **Démarrer**, entrez `dev`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-112">On the **Start** menu, enter `dev`.</span></span> <span data-ttu-id="ef3c6-113">Cela entraîne l’affichage d’une liste des applications installées qui correspondent à votre modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-113">This will bring a list of installed apps that match your search pattern.</span></span> <span data-ttu-id="ef3c6-114">Si vous recherchez une autre invite de commandes, essayez d’entrer un autre terme de recherche, par exemple `prompt`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-114">If you're looking for a different command prompt, try entering a different search term such as `prompt`.</span></span>  
  
3.  <span data-ttu-id="ef3c6-115">Choisissez **Invite de commandes développeur** (ou l’invite de commandes que vous voulez utiliser).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-115">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ef3c6-116">**Sous Windows 8.1**</span><span class="sxs-lookup"><span data-stu-id="ef3c6-116">**In Windows 8.1**</span></span>  
  
1.  <span data-ttu-id="ef3c6-117">Accédez à l’écran **Démarrer**, par exemple en appuyant sur la touche du logo Windows ![Logo Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") de votre clavier.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-117">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ef3c6-118">Dans l’écran **Démarrer**, appuyez sur `CTRL + TAB` pour ouvrir la liste **Applications**, puis entrez `V`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-118">On the **Start** screen, press `CTRL + TAB` to open the **Apps** list and then enter `V`.</span></span> <span data-ttu-id="ef3c6-119">Cela entraîne l’affichage d’une liste qui inclut toutes les invites de commandes Visual Studio installées.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-119">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
3.  <span data-ttu-id="ef3c6-120">Choisissez **Invite de commandes développeur** (ou l’invite de commandes que vous voulez utiliser).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-120">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ef3c6-121">**Sous Windows 8**</span><span class="sxs-lookup"><span data-stu-id="ef3c6-121">**In Windows 8**</span></span>  
  
1.  <span data-ttu-id="ef3c6-122">Accédez à l’écran **Démarrer**, par exemple en appuyant sur la touche du logo Windows ![Logo Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") de votre clavier.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-122">Go to the **Start** screen, by pressing the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard for example.</span></span>  
  
2.  <span data-ttu-id="ef3c6-123">Sur l’écran **Démarrer**, appuyez sur la touche du logo Windows ![Logo Windows](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-123">On the **Start** screen, press the Windows logo key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") `+ Z`.</span></span>  
  
3.  <span data-ttu-id="ef3c6-124">Choisissez l’icône **Vue Applications** en bas de l’écran, puis entrez `V`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-124">Choose the **Apps view** icon at the bottom of the screen and then enter `V`.</span></span> <span data-ttu-id="ef3c6-125">Cela entraîne l’affichage d’une liste qui inclut toutes les invites de commandes Visual Studio installées.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-125">This will bring a list that includes all installed Visual Studio command prompts.</span></span>  
  
4.  <span data-ttu-id="ef3c6-126">Choisissez **Invite de commandes développeur** (ou l’invite de commandes que vous voulez utiliser).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-126">Choose the **Developer Command Prompt** (or the command prompt you want to use).</span></span>  
  
 <span data-ttu-id="ef3c6-127">**Sous Windows 7**</span><span class="sxs-lookup"><span data-stu-id="ef3c6-127">**In Windows 7**</span></span>  
  
1.  <span data-ttu-id="ef3c6-128">Sélectionnez **Démarrer**, développez **Tous les programmes**, puis développez **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-128">Choose **Start**, expand **All Programs**, and then expand **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="ef3c6-129">Selon la version de Visual Studio que vous avez installée, choisissez **Visual Studio Tools**, **Invite de commandes Visual Studio** ou l’invite de commandes que vous voulez utiliser.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-129">Depending on the version of Visual Studio you have installed, choose  **Visual Studio Tools**, **Visual Studio Command Prompt**, or the command prompt you want to use.</span></span>  
  
 <span data-ttu-id="ef3c6-130">Si vous avez installé le [SDK Windows](http://msdn.microsoft.com/windows/desktop/aa904949) ou le [SDK Windows Phone](https://dev.windowsphone.com/downloadsdk), vous pouvez voir des invites de commandes supplémentaires pour les architectures ARM, x86 ou x64.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-130">If you have the [Windows SDK](http://msdn.microsoft.com/windows/desktop/aa904949) or [Windows Phone SDK](https://dev.windowsphone.com/downloadsdk) installed, you may see additional command prompts for ARM, x86, or x64 architectures.</span></span> <span data-ttu-id="ef3c6-131">Consultez la documentation relatives aux divers outils afin de déterminer la version de l'invite de commandes que vous devez utiliser.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-131">Check the documentation for the individual tools to determine which version of the command prompt you should use.</span></span>  
  
<a name="alternative"></a>   
## <a name="manually-locating-the-files-on-your-machine"></a><span data-ttu-id="ef3c6-132">Recherche manuelle des fichiers sur votre machine</span><span class="sxs-lookup"><span data-stu-id="ef3c6-132">Manually locating the files on your machine</span></span>  
  <span data-ttu-id="ef3c6-133">En règle générale, les raccourcis des invites de commandes que vous avez installées sont placés dans le dossier **Menu Démarrer** de Visual Studio, par exemple dans C:\ProgramData\Microsoft\Windows\Menu Démarrer\Programmes\Visual Studio 2015\Visual Studio Tools.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-133">Usually, the shortcuts for the command prompts you have installed will be placed at the **Start Menu** folder for Visual Studio, such as in C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Visual Studio 2015\Visual Studio Tools.</span></span>    <span data-ttu-id="ef3c6-134">Mais si pour une raison quelconque, la recherche de l’invite de commandes ne donne pas les résultats attendus, vous pouvez tenter de localiser manuellement le raccourci sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-134">But if for some reason, searching for the command prompt doesn't yield the expected results, you can try to manually locate the shortcut on your machine in order to use it.</span></span>   <span data-ttu-id="ef3c6-135">Essayez de rechercher le nom du fichier d’invite de commandes, par exemple VsDevCmd.bat, ou accédez au dossier Tools sur C:\Program Files (x86) \Microsoft Visual Studio 14.0\Common7\Tools (le chemin varie selon l’emplacement d’installation et la version de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-135">Try searching for the name of the command prompt file such as VsDevCmd.bat or go to the Tools folder such as C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools (path will change according to your Visual Studio version and installation location).</span></span>  
  
<a name="visualstudio"></a>   
## <a name="running-command-prompt-from-inside-visual-studio"></a><span data-ttu-id="ef3c6-136">Exécution de l’invite de commandes à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef3c6-136">Running command prompt from inside Visual Studio</span></span>  
 <span data-ttu-id="ef3c6-137">Pour faciliter l’accès, vous pouvez ajouter l’invite de commandes développeur Visual Studio ou toute autre invite de commandes au menu Outils de Visual Studio. Pour cela, il vous suffit de l’ajouter à la liste des outils externes.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-137">For easier access, you can add the Visual Studio Developer Command Prompt  or any other command prompt to the Tools menu on Visual Studio, by adding it to the external tools list.</span></span> <span data-ttu-id="ef3c6-138">Voici comment procéder :</span><span class="sxs-lookup"><span data-stu-id="ef3c6-138">This is how you can accomplish that:</span></span>  
  
1.  <span data-ttu-id="ef3c6-139">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-139">Open Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ef3c6-140">Sélectionnez le menu **Outils**, puis choisissez **Outils externes**.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-140">Select the **Tools** menu and choose **External Tools...**.</span></span>  
  
3.  <span data-ttu-id="ef3c6-141">Dans la boîte de dialogue **Outils externes**, choisissez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-141">On the **External Tools** dialog box, choose the **Add** button.</span></span> <span data-ttu-id="ef3c6-142">Une nouvelle entrée apparaît</span><span class="sxs-lookup"><span data-stu-id="ef3c6-142">A new entry appears</span></span>  
  
4.  <span data-ttu-id="ef3c6-143">Entrez un **titre** pour votre nouvel élément de menu, par exemple `Command Prompt`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-143">Enter a **Title** for your new menu item such as `Command Prompt`.</span></span>  
  
5.  <span data-ttu-id="ef3c6-144">Dans le champ **Commande**, spécifiez le fichier à lancer, par exemple `%comspec%` ou `C:\Windows\System32\cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-144">In the **Command** field, specify the file you want to launch such as `%comspec%` or `C:\Windows\System32\cmd.exe` .</span></span>  
  
6.  <span data-ttu-id="ef3c6-145">Dans le champ **Arguments**, indiquez où trouver l’invite de commandes à utiliser en particulier, par exemple `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (cela permet de lancer l’invite de commandes développeur installée avec [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ef3c6-145">In the **Arguments** field, specify where to find the specific command prompt you want to use such as `/k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\Tools\VsDevCmd.bat"` (this will launch the Developer Command Prompt installed with [!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]).</span></span> <span data-ttu-id="ef3c6-146">Vous devez changer cette valeur en fonction de l’emplacement d’installation et de la version de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-146">This value needs to be changed according to your Visual Studio version and installation location.</span></span>  
  
7.  <span data-ttu-id="ef3c6-147">Choisissez une valeur pour le champ **Répertoire Initial**, par exemple **Répertoire du projet**.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-147">Choose a value for the **Initial directory** field such as **Project Directory** .</span></span>  
  
8.  <span data-ttu-id="ef3c6-148">Sélectionnez le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="ef3c6-148">Choose the **OK** button.</span></span>  
  
 <span data-ttu-id="ef3c6-149">Le nouvel élément de menu est ensuite ajouté et vous pouvez accéder à l’invite de commandes à partir du menu **Outils**.</span><span class="sxs-lookup"><span data-stu-id="ef3c6-149">After that, the new menu item is added and you can access the command prompt from the **Tools** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3c6-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef3c6-150">See Also</span></span>  
 [<span data-ttu-id="ef3c6-151">Outils</span><span class="sxs-lookup"><span data-stu-id="ef3c6-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="ef3c6-152">Gestion des outils externes</span><span class="sxs-lookup"><span data-stu-id="ef3c6-152">Managing External Tools</span></span>](/visualstudio/ide/managing-external-tools)
