---
title: "Sérialisation avec tolérance de version, exemple de technologie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bde508f6fd578050501f95f2f9316c6c458017de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="9188f-102">Sérialisation avec tolérance de version, exemple de technologie</span><span class="sxs-lookup"><span data-stu-id="9188f-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="9188f-103">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="9188f-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="9188f-104">Cet exemple illustre les fonctionnalités de tolérance de version de la sérialisation .NET.</span><span class="sxs-lookup"><span data-stu-id="9188f-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="9188f-105">L'exemple génère des applications qui utilisent différentes versions de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour sérialiser et désérialiser des données.</span><span class="sxs-lookup"><span data-stu-id="9188f-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="9188f-106">En dépit de la présence de versions de type différent, les applications communiquent de façon transparente.</span><span class="sxs-lookup"><span data-stu-id="9188f-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="9188f-107">Pour plus d’informations, consultez [Sérialisation avec tolérance de version](../../../docs/standard/serialization/version-tolerant-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="9188f-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="9188f-108">Pour générer l'exemple à partir de l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="9188f-108">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="9188f-109">Ouvrez une fenêtre d'invite de commandes et accédez à l'un des sous-répertoires spécifiques au langage (sous l'application V1 ou l'application V2) pour l'exemple.</span><span class="sxs-lookup"><span data-stu-id="9188f-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2.  <span data-ttu-id="9188f-110">Tapez **msbuild.exe \<ver> application.sln** sur la ligne de commande (où \<ver> est v1 ou v2).</span><span class="sxs-lookup"><span data-stu-id="9188f-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="9188f-111">Pour générer l'exemple à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9188f-111">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="9188f-112">Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez à l'un des sous-répertoires spécifiques aux différents langages de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="9188f-112">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="9188f-113">Accédez au sous-répertoire de l'application V1 du répertoire sélectionné à l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="9188f-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3.  <span data-ttu-id="9188f-114">Double-cliquez sur l'icône de V1 Application.sln pour ouvrir le fichier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9188f-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4.  <span data-ttu-id="9188f-115">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="9188f-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="9188f-116">Accédez au sous-répertoire de l'application V2 et répétez les deux étapes précédentes pour générer l'application V2.</span><span class="sxs-lookup"><span data-stu-id="9188f-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="9188f-117">Les applications seront générées dans le sous-répertoire \bin ou \bin\Debug par défaut de leur projet respectif.</span><span class="sxs-lookup"><span data-stu-id="9188f-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="9188f-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="9188f-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="9188f-119">Dans la fenêtre d'invite de commandes, accédez au sous-répertoire spécifique au langage que vous avez sélectionné lors de la création des exemples d'applications.</span><span class="sxs-lookup"><span data-stu-id="9188f-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2.  <span data-ttu-id="9188f-120">Tapez **runme.cmd** sur la ligne de commande pour exécuter en même temps les deux applications.</span><span class="sxs-lookup"><span data-stu-id="9188f-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="9188f-121">Vous pouvez aussi accéder aux répertoires qui contiennent les nouveaux fichiers exécutables et les exécuter séquentiellement.</span><span class="sxs-lookup"><span data-stu-id="9188f-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9188f-122">L'exemple génère des applications console.</span><span class="sxs-lookup"><span data-stu-id="9188f-122">The sample builds console applications.</span></span> <span data-ttu-id="9188f-123">Vous devez les lancer et les exécuter dans une fenêtre d'invite de commandes pour consulter leur sortie.</span><span class="sxs-lookup"><span data-stu-id="9188f-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9188f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9188f-124">See Also</span></span>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
