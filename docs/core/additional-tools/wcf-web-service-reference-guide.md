---
title: Outil Microsoft WCF Web Service Reference Provider
description: "Vue d’ensemble de l’outil Microsoft WCF Web Service Reference Provider, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à la fonctionnalité Ajouter une référence de service pour les projets .NET Framework."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: e445361f9f4a858f4b34ca1008670fadc62b8b3c
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="a6e57-103">Outil Microsoft WCF Web Service Reference Provider</span><span class="sxs-lookup"><span data-stu-id="a6e57-103">Microsoft WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="a6e57-104">Au fil des années, de nombreux développeurs Visual Studio ont apprécié le gain de productivité offert par l’outil [**Ajouter une référence de service**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) quand leurs projets .NET Framework avaient besoin d’accéder à des services web.</span><span class="sxs-lookup"><span data-stu-id="a6e57-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="a6e57-105">L’outil **WCF Web Service Reference** est une extension de service connecté de Visual Studio qui fournit une expérience semblable à la fonctionnalité Ajouter une référence de service pour les projets .NET Core et ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6e57-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="a6e57-106">Cet outil récupère les métadonnées d’un service web dans la solution actuelle sur un emplacement réseau ou dans un fichier WSDL, puis génère un fichier source compatible .NET Core contenant du code de proxy client WCF (Windows Communication Foundation) que vous pouvez utiliser pour accéder au service web.</span><span class="sxs-lookup"><span data-stu-id="a6e57-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6e57-107">Vous devez référencer des services uniquement à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="a6e57-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="a6e57-108">L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a6e57-108">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="how-to-use-the-extension"></a><span data-ttu-id="a6e57-109">Comment utiliser l’extension</span><span class="sxs-lookup"><span data-stu-id="a6e57-109">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="a6e57-110">L’option **WCF Web Service Reference** s’applique aux projets créés à l’aide des modèles de projet suivants :</span><span class="sxs-lookup"><span data-stu-id="a6e57-110">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="a6e57-111">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="a6e57-111">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="a6e57-112">**Visual C#** > **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="a6e57-112">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="a6e57-113">**Visual C#** > **Web** > **Application web ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="a6e57-113">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="a6e57-114">Prenant le modèle de projet **Application web ASP.NET Core** en guise d’exemple, cet article explique comment ajouter une référence de service WCF au projet :</span><span class="sxs-lookup"><span data-stu-id="a6e57-114">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="a6e57-115">Dans l’Explorateur de solutions, double-cliquez sur le nœud du projet **Services connectés** (pour un projet .NET Core ou .NET Standard, cette option est disponible quand vous cliquez avec le bouton droit sur le nœud **Dépendances** du projet dans l’Explorateur de solutions).</span><span class="sxs-lookup"><span data-stu-id="a6e57-115">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

<span data-ttu-id="a6e57-116">La page **Services connectés** s’affiche, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a6e57-116">The **Connected Services** page appears as shown in the following image:</span></span>

![Onglet Services connectés](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="a6e57-118">Dans la page **Services connectés**, cliquez sur **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-118">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="a6e57-119">L’Assistant **Configurer la référence de services web WCF** apparaît :</span><span class="sxs-lookup"><span data-stu-id="a6e57-119">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

![Onglet Point de terminaison de service](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="a6e57-121">Sélectionnez un service.</span><span class="sxs-lookup"><span data-stu-id="a6e57-121">Select a service.</span></span>

    <span data-ttu-id="a6e57-122">3a.</span><span class="sxs-lookup"><span data-stu-id="a6e57-122">3a.</span></span> <span data-ttu-id="a6e57-123">Plusieurs options de recherche de services sont disponibles dans l’Assistant **Configurer la référence de services web WCF** :</span><span class="sxs-lookup"><span data-stu-id="a6e57-123">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>
    
     * <span data-ttu-id="a6e57-124">Pour rechercher parmi les services définis dans la solution actuelle, cliquez sur le bouton **Découvrir**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-124">To search for services defined in the current solution, click the **Discover** button.</span></span> 
     * <span data-ttu-id="a6e57-125">Pour rechercher parmi les services hébergés à une adresse spécifiée, entrez une URL de service dans la zone **Adresse**, puis cliquez sur le bouton **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-125">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="a6e57-126">Pour sélectionner un fichier WSDL qui contient les informations de métadonnées de service web, cliquez sur le bouton **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-126">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span> 
     
    <span data-ttu-id="a6e57-127">3b.</span><span class="sxs-lookup"><span data-stu-id="a6e57-127">3b.</span></span> <span data-ttu-id="a6e57-128">Sélectionnez le service dans la liste des résultats de recherche dans la zone **Services**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-128">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="a6e57-129">Si nécessaire, entrez l’espace de noms du code généré dans la zone de texte **Espace de noms** correspondante.</span><span class="sxs-lookup"><span data-stu-id="a6e57-129">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>
    
    <span data-ttu-id="a6e57-130">3c.</span><span class="sxs-lookup"><span data-stu-id="a6e57-130">3c.</span></span> <span data-ttu-id="a6e57-131">Cliquez sur le bouton **Suivant** pour ouvrir les pages **Options du type de données** et **Options du client**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-131">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="a6e57-132">Vous pouvez aussi cliquer sur le bouton **Terminer** pour utiliser les options par défaut.</span><span class="sxs-lookup"><span data-stu-id="a6e57-132">Alternatively, click the **Finish** button to use the default options.</span></span>


4. <span data-ttu-id="a6e57-133">Le formulaire **Options du type de données** vous permet d’affiner les paramètres de configuration de référence de service générés :</span><span class="sxs-lookup"><span data-stu-id="a6e57-133">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

![Onglet Options du type de données](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> <span data-ttu-id="a6e57-135">La case à cocher **Réutiliser les types dans les assemblys référencés** est utile quand les types de données nécessaires pour la génération du code de référence de service sont définis dans l’un des assemblys référencés de votre projet.</span><span class="sxs-lookup"><span data-stu-id="a6e57-135">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="a6e57-136">Il est important de réutiliser ces types de données existants pour éviter les conflits de type au moment de la compilation ou les problèmes au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a6e57-136">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

<span data-ttu-id="a6e57-137">Il peut y avoir un délai pendant le chargement des informations de type, en fonction du nombre de dépendances du projet et d’autres facteurs de performances système.</span><span class="sxs-lookup"><span data-stu-id="a6e57-137">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="a6e57-138">Le bouton **Terminer** est désactivé pendant le chargement, sauf si la case **Réutiliser les types dans les assemblys référencés** est cochée.</span><span class="sxs-lookup"><span data-stu-id="a6e57-138">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="a6e57-139">Cliquez sur **Terminer** quand vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="a6e57-139">Click **Finish** when you are done.</span></span>


<span data-ttu-id="a6e57-140">Lors de l’affichage de la progression, l’outil :</span><span class="sxs-lookup"><span data-stu-id="a6e57-140">While displaying progress, the tool:</span></span>

* <span data-ttu-id="a6e57-141">Télécharge les métadonnées à partir du service WCF.</span><span class="sxs-lookup"><span data-stu-id="a6e57-141">Downloads metadata from the WCF service.</span></span> 
* <span data-ttu-id="a6e57-142">Génère le code de référence de service dans un fichier nommé *reference.cs* et l’ajoute à votre projet sous le nœud **Services connectés**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-142">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span> 
* <span data-ttu-id="a6e57-143">Met à jour le fichier projet (.csproj) avec les références de package NuGet nécessaires pour la compilation et l’exécution sur la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="a6e57-143">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Fenêtre de progression](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="a6e57-145">Une fois ces processus terminés, vous pouvez créer une instance du type de client WCF généré et appeler les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="a6e57-145">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a6e57-146">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a6e57-146">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="a6e57-147">Commentaires et questions</span><span class="sxs-lookup"><span data-stu-id="a6e57-147">Feedback & questions</span></span>
<span data-ttu-id="a6e57-148">Si vous avez des questions ou des commentaires, [ouvrez un problème sur GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="a6e57-148">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="a6e57-149">Vous pouvez également consulter les questions ou problèmes existants dans le [dépôt WCF sur GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="a6e57-149">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="a6e57-150">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="a6e57-150">Release notes</span></span>
* <span data-ttu-id="a6e57-151">Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md).</span><span class="sxs-lookup"><span data-stu-id="a6e57-151">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span> 
