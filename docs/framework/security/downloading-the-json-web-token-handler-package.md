---
title: "Téléchargement du package du Gestionnaire de jetons Web JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d3821ff1da945df7c6e07e5baf69730173eacc87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a><span data-ttu-id="1876c-102">Téléchargement du package du Gestionnaire de jetons Web JSON</span><span class="sxs-lookup"><span data-stu-id="1876c-102">Downloading the JSON Web Token Handler Package</span></span>
<span data-ttu-id="1876c-103">Cette rubrique explique comment télécharger et utiliser le Gestionnaire de jetons Web JSON dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="1876c-103">This topic discusses how to download and use the JSON Web Token Handler in your project.</span></span>  
  
## <a name="downloading-the-json-web-token-handler"></a><span data-ttu-id="1876c-104">Téléchargement du Gestionnaire de jetons Web JSON</span><span class="sxs-lookup"><span data-stu-id="1876c-104">Downloading the JSON Web Token Handler</span></span>  
 <span data-ttu-id="1876c-105">L’extension du Gestionnaire de jetons Web JSON est disponible sous forme de package NuGet, qui ajoute les assemblys et les références nécessaires à votre projet.</span><span class="sxs-lookup"><span data-stu-id="1876c-105">The JSON Web Token Handler extension is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="1876c-106">Si vous n’avez pas encore installé NuGet, accédez à [nuget.org](http://nuget.org) pour l’installer.</span><span class="sxs-lookup"><span data-stu-id="1876c-106">If you do not already have NuGet installed, go to [nuget.org](http://nuget.org) to install it.</span></span> <span data-ttu-id="1876c-107">Vous pouvez voir l’historique de gestion de version de l’extension en accédant à sa page sur NuGet : [Gestionnaire de jetons Web JSON sur NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span><span class="sxs-lookup"><span data-stu-id="1876c-107">You can see the versioning history for the extension by visiting its page on NuGet: [JSON Web Token Handler on NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a><span data-ttu-id="1876c-108">Téléchargement du Gestionnaire de jetons Web JSON à l’aide de l’interface graphique utilisateur du Gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="1876c-108">Downloading the JSON Web Token Handler by using the Package Manager GUI</span></span>  
  
1.  <span data-ttu-id="1876c-109">Dans Visual Studio, cliquez sur votre projet dans l’**Explorateur de solutions**, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1876c-109">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>  
  
2.  <span data-ttu-id="1876c-110">Dans la fenêtre **Gérer les packages NuGet**, cliquez sur la zone de recherche et tapez `JWT Token Handler`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="1876c-110">In the **Manage NuGet Packages** window, click the search box and enter `JWT Token Handler` and press **Enter**.</span></span>  
  
3.  <span data-ttu-id="1876c-111">Dans le volet de résultats, cliquez sur le bouton **Installer** pour le premier résultat.</span><span class="sxs-lookup"><span data-stu-id="1876c-111">From the results pane, click the **Install** button for the first result.</span></span>  
  
4.  <span data-ttu-id="1876c-112">Le téléchargement du package commence.</span><span class="sxs-lookup"><span data-stu-id="1876c-112">The package will begin downloading.</span></span> <span data-ttu-id="1876c-113">Avant l’ajout du package à votre projet, la boîte de dialogue d’acceptation de licence s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1876c-113">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="1876c-114">Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Accepter**.</span><span class="sxs-lookup"><span data-stu-id="1876c-114">If you agree to the license terms, click **I Accept**.</span></span>  
  
5.  <span data-ttu-id="1876c-115">Les assemblys du Gestionnaire de jetons Web JSON les plus récents seront téléchargés et ajoutés à votre projet.</span><span class="sxs-lookup"><span data-stu-id="1876c-115">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a><span data-ttu-id="1876c-116">Téléchargement du Gestionnaire de jetons Web JSON à l’aide de la console du Gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="1876c-116">Downloading the JSON Web Token Handler by using the Package Manager Console</span></span>  
  
1.  <span data-ttu-id="1876c-117">Dans Visual Studio, cliquez sur **Outils**, **Gestionnaire de package de bibliothèque**, puis **Console du Gestionnaire de package**.</span><span class="sxs-lookup"><span data-stu-id="1876c-117">In Visual Studio, click **Tools**, **Library Package Manager**, and then **Package Manager Console**.</span></span>  
  
2.  <span data-ttu-id="1876c-118">La **Console du Gestionnaire de package** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1876c-118">The **Package Manager Console** appears.</span></span> <span data-ttu-id="1876c-119">Tapez le texte suivant et appuyez sur **Entrée** :</span><span class="sxs-lookup"><span data-stu-id="1876c-119">Enter the following text and press **Enter**:</span></span>  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  <span data-ttu-id="1876c-120">Les assemblys du Gestionnaire de jetons Web JSON les plus récents seront téléchargés et ajoutés à votre projet.</span><span class="sxs-lookup"><span data-stu-id="1876c-120">The latest JSON Web Token Handler assemblies will be downloaded and added to your project.</span></span>
