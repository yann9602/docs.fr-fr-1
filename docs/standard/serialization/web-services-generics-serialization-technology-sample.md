---
title: "Sérialisation de génériques de services Web, exemple de technologie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9d5ed7a1bb55803cd1df8c6c6c740e8facb306e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="18002-102">Sérialisation de génériques de services Web, exemple de technologie</span><span class="sxs-lookup"><span data-stu-id="18002-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="18002-103">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="18002-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="18002-104">Cet exemple montre comment utiliser et contrôler la sérialisation de génériques dans les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="18002-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="18002-105">Pour générer l'exemple à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18002-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="18002-106">Ouvrez Visual Studio et sélectionnez **Nouveau site web** dans le menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="18002-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="18002-107">Dans le volet gauche de la boîte de dialogue **Nouveau site web**, sélectionnez le langage de programmation de votre choix, puis dans le volet droit, sélectionnez **Service web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="18002-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="18002-108">Cliquez sur **Parcourir** et accédez au sous-répertoire \CS\GenericsService.</span><span class="sxs-lookup"><span data-stu-id="18002-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="18002-109">Sélectionnez Service.asmx pour ouvrir le fichier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="18002-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="18002-110">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="18002-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18002-111">Les cinq premières étapes de cette liste sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="18002-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="18002-112">L'exécution .NET Framework générera automatiquement le service Web lors de la première demande du service.</span><span class="sxs-lookup"><span data-stu-id="18002-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18002-113">Les étapes suivantes sont obligatoires pour générer l'exemple.</span><span class="sxs-lookup"><span data-stu-id="18002-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="18002-114">Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez au sous-répertoire \CS.</span><span class="sxs-lookup"><span data-stu-id="18002-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="18002-115">Cliquez avec le bouton droit sur l’icône du sous-répertoire GenericsService et sélectionnez **Partage et sécurité**.</span><span class="sxs-lookup"><span data-stu-id="18002-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="18002-116">Sous l’onglet **Partage web**, sélectionnez **Partager ce dossier**.</span><span class="sxs-lookup"><span data-stu-id="18002-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18002-117">Notez le nom du répertoire virtuel affiché dans le volet **Alias**, car vous en aurez besoin pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="18002-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="18002-118">Pour générer l'exemple à l'aide des services IIS (Internet Information Services)</span><span class="sxs-lookup"><span data-stu-id="18002-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="18002-119">Ouvrez le composant logiciel enfichable de gestion **Internet Information Services** et développez **Sites web**.</span><span class="sxs-lookup"><span data-stu-id="18002-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="18002-120">Cliquez sur **Site web par défaut**, sélectionnez **Nouveau**, puis sélectionnez **Répertoire virtuel** pour créer l’**Assistant Création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="18002-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="18002-121">Cliquez sur **Suivant**, entrez l’alias public de votre répertoire virtuel, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="18002-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="18002-122">Entrez le chemin d’accès au répertoire où vous avez enregistré l’exemple (en général, il s’agit du sous-répertoire \CS\GenericsService) et cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="18002-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="18002-123">Cliquez sur **Suivant** pour quitter l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="18002-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18002-124">Notez le nom du répertoire virtuel affiché dans le volet **Alias**, car vous en aurez besoin pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="18002-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="18002-125">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="18002-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="18002-126">Ouvrez une fenêtre de navigateur et sélectionnez sa barre d'adresses.</span><span class="sxs-lookup"><span data-stu-id="18002-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="18002-127">Tapez **http://localhost/[répertoire virtuel]/Service.asmx**, où [répertoire virtuel] représente le répertoire virtuel que vous avez créé au moment de la génération de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="18002-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18002-128">Notes</span><span class="sxs-lookup"><span data-stu-id="18002-128">Remarks</span></span>  
 <span data-ttu-id="18002-129">L'exemple affiche une page ASP.NET par défaut qui contient des liens vers la définition du service Web.</span><span class="sxs-lookup"><span data-stu-id="18002-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="18002-130">Vous pouvez modifier le code source pour le service Web, mais également personnaliser l'affichage.</span><span class="sxs-lookup"><span data-stu-id="18002-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="18002-131">Pour plus d’informations, consultez [Création de clients de service web XML](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span><span class="sxs-lookup"><span data-stu-id="18002-131">For more information, see [Building XML Web Service Clients](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18002-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18002-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="18002-133">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="18002-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="18002-134">Création de services Web XML à l’aide de clients de service Web XML et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="18002-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)
