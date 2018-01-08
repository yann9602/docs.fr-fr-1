---
title: Guide pratique pour installer un assembly dans le Global Assembly Cache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47867a82432ec6abe2245a0421d800c242d92b2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="54829-102">Guide pratique pour installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="54829-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="54829-103">Il existe deux façons d'installer un assembly avec nom fort dans le Global Assembly Cache (GAC) :</span><span class="sxs-lookup"><span data-stu-id="54829-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54829-104">Seuls les assemblys avec noms forts peuvent être installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="54829-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="54829-105">Pour plus d’informations sur la façon de créer un assembly avec un nom fort, consultez [Guide pratique pour signer un assembly avec un nom fort](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="54829-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="54829-106">Utilisation de [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="54829-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="54829-107">Cela se fait dans Visual Studio 2012 et Visual Studio 2013 lorsque vous créez un projet InstallShield Limited Edition.</span><span class="sxs-lookup"><span data-stu-id="54829-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="54829-108">Il s'agit de la manière recommandée la plus commune pour ajouter des assemblys au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="54829-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="54829-109">Le programme d'installation fournit un décompte de références des assemblys dans le Global Assembly Cache, ainsi que d'autres avantages.</span><span class="sxs-lookup"><span data-stu-id="54829-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="54829-110">Utilisation de l’[outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="54829-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="54829-111">Vous pouvez utiliser Gacutil.exe pour ajouter des assemblys avec nom fort au Global Assembly Cache et visualiser le contenu de ce cache.</span><span class="sxs-lookup"><span data-stu-id="54829-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54829-112">Gacutil.exe ne sert qu'au développement. Il ne doit pas être utilisé pour installer des assemblys de production dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="54829-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54829-113">Dans les versions précédentes du .NET Framework, l'extension d'environnement Windows Shfusion.dll vous permettait de faire glisser des assemblys dans l'Explorateur Windows pour les installer.</span><span class="sxs-lookup"><span data-stu-id="54829-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="54829-114">À partir de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll est obsolète.</span><span class="sxs-lookup"><span data-stu-id="54829-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="54829-115">Pour utiliser l'outil Global Assembly Cache Tool (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="54829-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="54829-116">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="54829-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="54829-117">**gacutil -i** \<*nom_assembly*></span><span class="sxs-lookup"><span data-stu-id="54829-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="54829-118">Dans cette commande, *nom_assembly* est le nom de l’assembly à installer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="54829-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="54829-119">L'exemple suivant installe un assembly avec le nom de fichier `hello.dll` dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="54829-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="54829-120">Pour plus d’informations, consultez [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="54829-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="54829-121">Pour utiliser un projet InstallShield Limited Edition</span><span class="sxs-lookup"><span data-stu-id="54829-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="54829-122">Ajoutez un package de configuration et de déploiement à votre solution en ouvrant le menu contextuel de votre solution, puis en choisissant **Ajouter**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="54829-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="54829-123">Dans la boîte de dialogue **Ajouter un nouveau projet**, dans le dossier **Installé**, choisissez **Autres types de projets**,  **Configuration et déploiement**, **InstallShield Limited Edition**, puis donnez un nom au projet.</span><span class="sxs-lookup"><span data-stu-id="54829-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="54829-124">(Si le système vous y invite, téléchargez, installez et activez InstallShield.)</span><span class="sxs-lookup"><span data-stu-id="54829-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="54829-125">Effectuez la configuration générale de votre projet de configuration et de déploiement à l’aide de l’Assistant Projet de l’**Explorateur de solutions**, ou en choisissant les sous-étapes des étapes numérotées dans l’**Explorateur de solutions**. Paramétrez votre configuration comme si vous n’ajoutiez pas d’assemblys au GAC.</span><span class="sxs-lookup"><span data-stu-id="54829-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="54829-126">Pour démarrer le processus d’ajout d’un assembly au GAC, choisissez **Fichiers**, qui se trouve à l’étape **Spécifiez les données d’application** dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="54829-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="54829-127">Dans le volet **Dossiers de l’ordinateur de destination**, ouvrez le menu contextuel **Ordinateur de destination**, puis choisissez **Afficher le dossier prédéfini**, **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="54829-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="54829-128">Pour chaque projet de la solution qui contient un assembly à installer dans le Global Assembly Cache :</span><span class="sxs-lookup"><span data-stu-id="54829-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="54829-129">Dans le volet **Dossiers de l’ordinateur de destination**, choisissez le projet.</span><span class="sxs-lookup"><span data-stu-id="54829-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="54829-130">Dans le volet **Dossiers de l’ordinateur de destination**, choisissez **[GlobalAssemblyCache]**.</span><span class="sxs-lookup"><span data-stu-id="54829-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="54829-131">Dans le volet **Fichiers de l’ordinateur source**, choisissez **Sortie principale de** *<nom_projet>*.</span><span class="sxs-lookup"><span data-stu-id="54829-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="54829-132">Faites glisser le fichier à l’étape c vers le volet **Fichiers de l’ordinateur de destination** (ou utilisez les commandes **Copier** et **Coller** du menu contextuel du fichier).</span><span class="sxs-lookup"><span data-stu-id="54829-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54829-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54829-133">See Also</span></span>  
 [<span data-ttu-id="54829-134">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="54829-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="54829-135">Guide pratique pour supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="54829-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="54829-136">Gacutil.exe (outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="54829-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="54829-137">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="54829-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="54829-138">Déploiement de Windows Installer</span><span class="sxs-lookup"><span data-stu-id="54829-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
