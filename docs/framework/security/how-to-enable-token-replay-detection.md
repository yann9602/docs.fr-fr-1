---
title: "Guide pratique pour activer la détection de relecture de jetons"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: cde32407f072f3d29af4a8d1aae559e46057ae3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-token-replay-detection"></a><span data-ttu-id="26118-102">Guide pratique pour activer la détection de relecture de jetons</span><span class="sxs-lookup"><span data-stu-id="26118-102">How To: Enable Token Replay Detection</span></span>
## <a name="applies-to"></a><span data-ttu-id="26118-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="26118-103">Applies To</span></span>  
  
-   <span data-ttu-id="26118-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="26118-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="26118-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="26118-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="26118-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="26118-106">Summary</span></span>  
 <span data-ttu-id="26118-107">Cette procédure fournit des procédures pas à pas détaillées pour l’activation de la détection de relecture de jetons dans une application ASP.NET qui utilise WIF.</span><span class="sxs-lookup"><span data-stu-id="26118-107">This How-To provides detailed step-by-step procedures for enabling token replay detection in an ASP.NET application that uses WIF.</span></span> <span data-ttu-id="26118-108">Elle fournit également des instructions pour tester l’application afin de vérifier que la détection de relecture de jetons est activée.</span><span class="sxs-lookup"><span data-stu-id="26118-108">It also provides instructions for how to test the application to verify that token replay detection is enabled.</span></span> <span data-ttu-id="26118-109">Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès.</span><span class="sxs-lookup"><span data-stu-id="26118-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="26118-110">Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="26118-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="26118-111">Vous devez installer l'outil Identité et accès pour exécuter cette procédure.</span><span class="sxs-lookup"><span data-stu-id="26118-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="26118-112">Il peut être téléchargé à partir de l’emplacement suivant : [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="26118-112">It can be downloaded from the following location: [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)</span></span>  
  
## <a name="contents"></a><span data-ttu-id="26118-113">Sommaire</span><span class="sxs-lookup"><span data-stu-id="26118-113">Contents</span></span>  
  
-   <span data-ttu-id="26118-114">Objectifs</span><span class="sxs-lookup"><span data-stu-id="26118-114">Objectives</span></span>  
  
-   <span data-ttu-id="26118-115">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="26118-115">Overview</span></span>  
  
-   <span data-ttu-id="26118-116">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="26118-116">Summary of Steps</span></span>  
  
-   <span data-ttu-id="26118-117">Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture</span><span class="sxs-lookup"><span data-stu-id="26118-117">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="26118-118">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="26118-118">Step 2 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="26118-119">Objectifs</span><span class="sxs-lookup"><span data-stu-id="26118-119">Objectives</span></span>  
  
-   <span data-ttu-id="26118-120">Créer une simple application ASP.NET qui utilise WIF et le service STS de développement à partir de l’outil Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="26118-120">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>  
  
-   <span data-ttu-id="26118-121">Activer la détection de relecture de jetons et vérifier son fonctionnement</span><span class="sxs-lookup"><span data-stu-id="26118-121">Enable token replay detection and verify that it is working</span></span>  
  
## <a name="overview"></a><span data-ttu-id="26118-122">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="26118-122">Overview</span></span>  
 <span data-ttu-id="26118-123">Une attaque par relecture se produit quand un client essaie de s’authentifier auprès d’une partie de confiance avec un jeton STS que le client a déjà utilisé.</span><span class="sxs-lookup"><span data-stu-id="26118-123">A replay attack occurs when a client attempts to authenticate to a relying party with an STS token that the client has already used.</span></span> <span data-ttu-id="26118-124">Pour éviter ce genre d’attaque, WIF contient un cache de détection de relecture de jetons STS précédemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="26118-124">To help prevent this attack, WIF contains a replay detection cache of previously used STS tokens.</span></span> <span data-ttu-id="26118-125">Quand elle est activée, la détection de relecture vérifie le jeton de la demande entrante et si le jeton a été utilisé précédemment ou non.</span><span class="sxs-lookup"><span data-stu-id="26118-125">When enabled, replay detection checks the token of the incoming request and verifies whether or not the token has been previously used.</span></span> <span data-ttu-id="26118-126">Si le jeton a déjà été utilisé, la demande est refusée et une exception <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> est levée.</span><span class="sxs-lookup"><span data-stu-id="26118-126">If the token has been used already, the request is refused and a <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> exception is thrown.</span></span>  
  
 <span data-ttu-id="26118-127">Les étapes suivantes illustrent les modifications de configuration requises pour activer la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="26118-127">The following steps demonstrate the configuration changes required to enable replay detection.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="26118-128">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="26118-128">Summary of Steps</span></span>  
  
-   <span data-ttu-id="26118-129">Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture</span><span class="sxs-lookup"><span data-stu-id="26118-129">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
  
-   <span data-ttu-id="26118-130">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="26118-130">Step 2 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a><span data-ttu-id="26118-131">Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture</span><span class="sxs-lookup"><span data-stu-id="26118-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Replay Detection</span></span>  
 <span data-ttu-id="26118-132">Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifier le fichier *Web.config* pour activer la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="26118-132">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable replay detection.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="26118-133">Pour créer une simple application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="26118-133">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="26118-134">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="26118-134">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="26118-135">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="26118-135">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="26118-136">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="26118-136">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="26118-137">Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="26118-137">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
5.  <span data-ttu-id="26118-138">La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche.</span><span class="sxs-lookup"><span data-stu-id="26118-138">The **Identity and Access** window appears.</span></span> <span data-ttu-id="26118-139">Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="26118-139">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
6.  <span data-ttu-id="26118-140">Ajoutez l’élément **\<tokenReplayDetection>** suivant au fichier de configuration *Web.config* immédiatement après les éléments **\<system.identityModel>** et **\<identityConfiguration>**, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="26118-140">Add the following **\<tokenReplayDetection>** element to the *Web.config* configuration file immediately following the **\<system.identityModel>** and **\<identityConfiguration>** elements, like shown:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a><span data-ttu-id="26118-141">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="26118-141">Step 2 – Test Your Solution</span></span>  
 <span data-ttu-id="26118-142">Dans cette étape, vous allez tester votre application ASP.NET WIF pour vérifier que la détection de relecture a été activée.</span><span class="sxs-lookup"><span data-stu-id="26118-142">In this step, you will test your WIF-enabled ASP.NET application to verify that replay detection has been enabled.</span></span>  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a><span data-ttu-id="26118-143">Pour tester votre application ASP.NET WIF pour la détection de relecture</span><span class="sxs-lookup"><span data-stu-id="26118-143">To test your WIF-enabled ASP.NET application for replay detection</span></span>  
  
1.  <span data-ttu-id="26118-144">Exécutez la solution en appuyant sur la touche **F5**.</span><span class="sxs-lookup"><span data-stu-id="26118-144">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="26118-145">La page d’accueil ASP.NET par défaut doit s’afficher et vous devez être automatiquement authentifié avec le nom d’utilisateur *Terry*, qui est l’utilisateur par défaut retourné par le service STS de développement.</span><span class="sxs-lookup"><span data-stu-id="26118-145">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>  
  
2.  <span data-ttu-id="26118-146">Appuyez sur le bouton **Précédent** du navigateur.</span><span class="sxs-lookup"><span data-stu-id="26118-146">Press the browser’s **Back** button.</span></span> <span data-ttu-id="26118-147">Une page **Erreur du serveur dans l’application ‘/’** doit s’afficher avec la description suivante : *ID1062 : relecture détectée pour : Jeton : 'System.IdentityModel.Tokens.SamlSecurityToken'*, suivie des éléments *AssertionId* et *Émetteur*.</span><span class="sxs-lookup"><span data-stu-id="26118-147">You should be presented with a **Server Error in ‘/’ Application** page with the following description: *ID1062: Replay has been detected for: Token: 'System.IdentityModel.Tokens.SamlSecurityToken'*, followed by an *AssertionId* and an *Issuer*.</span></span>  
  
     <span data-ttu-id="26118-148">Vous voyez cette page d’erreur, car une exception de type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> a été levée lors de la détection de la relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="26118-148">You are seeing this error page because an exception of type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> was thrown when the token replay was detected.</span></span> <span data-ttu-id="26118-149">Cette erreur se produit parce que vous essayez d’envoyer à nouveau la requête POST initiale où le jeton est apparu la première fois.</span><span class="sxs-lookup"><span data-stu-id="26118-149">This error occurs because you are attempting to re-send the initial POST request when the token was first presented.</span></span> <span data-ttu-id="26118-150">Le bouton **Précédent** n’entraîne pas ce comportement pour les demandes suivantes au serveur.</span><span class="sxs-lookup"><span data-stu-id="26118-150">The **Back** button will not cause this behavior on subsequent requests to the server.</span></span>
