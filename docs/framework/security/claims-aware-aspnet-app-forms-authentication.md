---
title: "Comment : générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 987157bc3663330d9c610c1016787890e9dc6137
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="ef32b-102">Comment : générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires</span><span class="sxs-lookup"><span data-stu-id="ef32b-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="ef32b-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="ef32b-103">Applies To</span></span>  
  
-   <span data-ttu-id="ef32b-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ef32b-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ef32b-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="ef32b-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="ef32b-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="ef32b-106">Summary</span></span>  
 <span data-ttu-id="ef32b-107">Cette procédure fournit des procédures pas à pas détaillées pour la création d’une simple application Web Forms ASP.NET prenant en charge les revendications et utilisant l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="ef32b-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="ef32b-108">Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications s’affichent quand un utilisateur se connecte à l’aide de l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="ef32b-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="ef32b-109">Sommaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-109">Contents</span></span>  
  
-   <span data-ttu-id="ef32b-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ef32b-110">Objectives</span></span>  
  
-   <span data-ttu-id="ef32b-111">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ef32b-111">Overview</span></span>  
  
-   <span data-ttu-id="ef32b-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="ef32b-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ef32b-113">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="ef32b-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ef32b-114">Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="ef32b-115">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="ef32b-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="ef32b-116">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ef32b-116">Objectives</span></span>  
  
-   <span data-ttu-id="ef32b-117">Configurer une application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="ef32b-118">Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement</span><span class="sxs-lookup"><span data-stu-id="ef32b-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ef32b-119">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="ef32b-119">Overview</span></span>  
 <span data-ttu-id="ef32b-120">Dans .NET 4.5, WIF et son autorisation basée sur les revendications ont été ajoutés en tant que partie intégrante du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef32b-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="ef32b-121">Auparavant, si vous vouliez obtenir des revendications d’un utilisateur ASP.NET, vous deviez installer WIF et convertir les interfaces en objets Entité de sécurité tels que `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="ef32b-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="ef32b-122">À présent, les revendications sont prises en charge automatiquement par ces objets Entité de sécurité.</span><span class="sxs-lookup"><span data-stu-id="ef32b-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="ef32b-123">L’authentification par formulaire a bénéficié de l’ajout de WIF dans .NET 4.5, car tous les utilisateurs authentifiés par des formulaires sont automatiquement associés à des revendications.</span><span class="sxs-lookup"><span data-stu-id="ef32b-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="ef32b-124">Vous pouvez commencer à utiliser ces revendications immédiatement dans une application ASP.NET qui utilise l’authentification par formulaire, comme l’illustre cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ef32b-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="ef32b-125">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="ef32b-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="ef32b-126">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="ef32b-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="ef32b-127">Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="ef32b-128">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="ef32b-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="ef32b-129">Étape 1 : Créer une application Web Forms ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="ef32b-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="ef32b-130">Lors de cette étape, vous allez créer une application Web Forms ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef32b-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="ef32b-131">Pour créer une simple application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ef32b-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="ef32b-132">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="ef32b-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="ef32b-133">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="ef32b-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="ef32b-134">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ef32b-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ef32b-135">Étape 2 : Configurer l’application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="ef32b-136">Lors de cette étape, vous allez ajouter une entrée de configuration au fichier de configuration *Web.config* et modifier le fichier *Default.aspx* pour afficher les informations sur les revendications d’un compte.</span><span class="sxs-lookup"><span data-stu-id="ef32b-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ef32b-137">Pour configurer une application ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="ef32b-138">Dans le fichier *Default.aspx*, remplacez le balisage existant par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ef32b-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="ef32b-139">Cette étape ajoute un contrôle GridView à votre page *Default.aspx* qui sera remplie avec les revendications récupérées à partir de l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="ef32b-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="ef32b-140">Enregistrez le fichier *Default.aspx*, puis ouvrez son fichier code-behind nommé *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="ef32b-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="ef32b-141">Remplacez le code existant par le code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="ef32b-141">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="ef32b-142">Le code ci-dessus affiche les revendications relatives à un utilisateur authentifié, y compris les utilisateurs identifiés par l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="ef32b-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="ef32b-143">Étape 3 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="ef32b-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="ef32b-144">Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications sont présentées à l’utilisateur qui se connecte à l’aide de l’authentification par formulaire.</span><span class="sxs-lookup"><span data-stu-id="ef32b-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="ef32b-145">Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire</span><span class="sxs-lookup"><span data-stu-id="ef32b-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="ef32b-146">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="ef32b-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="ef32b-147">La page *Default.aspx* doit s’afficher, avec des liens **Register** et **Log in** en haut à droite.</span><span class="sxs-lookup"><span data-stu-id="ef32b-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="ef32b-148">Cliquez sur **Register**.</span><span class="sxs-lookup"><span data-stu-id="ef32b-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="ef32b-149">Dans la page **Register**, créez un compte d’utilisateur, puis cliquez sur **Register**.</span><span class="sxs-lookup"><span data-stu-id="ef32b-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="ef32b-150">Votre compte sera créé à l’aide de l’authentification par formulaire, et vous serez connecté automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ef32b-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="ef32b-151">Après avoir été redirigé vers la page d’accueil, vous devriez voir sous l’en-tête **Your Claims** une table qui inclut les informations de revendications **Issuer**, **OriginalIssuer**, **Type**, **Value** et **ValueType** relatives à votre compte.</span><span class="sxs-lookup"><span data-stu-id="ef32b-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
