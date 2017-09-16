---
title: Guide pratique pour transformer les revendications entrantes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-transform-incoming-claims"></a>Guide pratique pour transformer les revendications entrantes
## <a name="applies-to"></a>S'applique à  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms ASP.NET®  
  
## <a name="summary"></a>Résumé  
 Cette procédure fournit des procédures pas à pas détaillées pour créer une application Web Forms ASP.NET simple prenant en charge les revendications et pour transformer les revendications entrantes. Elle fournit également des instructions pour tester l’application afin de vérifier que les revendications transformées sont présentées au moment de l’exécution de l’application.  
  
## <a name="contents"></a>Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 : Créer une application Web Forms ASP.NET simple  
  
-   Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé  
  
-   Étape 3 : Tester votre solution  
  
## <a name="objectives"></a>Objectifs  
  
-   Configurer une application Web Forms ASP.NET pour l’authentification basée sur les revendications  
  
-   Transformer les revendications entrantes en ajoutant une revendication de rôle d’administrateur (Administrator)  
  
-   Tester l’application Web Forms ASP.NET pour vérifier si elle fonctionne correctement  
  
## <a name="overview"></a>Vue d'ensemble  
 WIF expose une classe nommée <xref:System.Security.Claims.ClaimsAuthenticationManager> qui permet aux utilisateurs de modifier les revendications avant leur présentation à une application par partie de confiance. La classe <xref:System.Security.Claims.ClaimsAuthenticationManager> est utile pour la séparation des responsabilités entre l’authentification et le code d’application sous-jacent. L’exemple ci-dessous montre comment ajouter un rôle aux revendications dans le principal <xref:System.Security.Claims.ClaimsPrincipal> entrant quand il est requis par l’application par partie de confiance.  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
-   Étape 1 : Créer une application Web Forms ASP.NET simple  
  
-   Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé  
  
-   Étape 3 : Tester votre solution  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a>Étape 1 : Créer une application Web Forms ASP.NET simple  
 Lors de cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une application ASP.NET simple  
  
1.  Démarrez Visual Studio en mode élevé en tant qu’administrateur.  
  
2.  Dans Visual Studio, cliquez sur **Fichier**, sur **Nouveau**, puis sur **Projet**.  
  
3.  Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
4.  Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
5.  Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).  
  
6.  La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche. Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.  
  
7.  Dans le fichier *Default.aspx*, remplacez le balisage existant par le code suivant, puis enregistrez le fichier :  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  Ouvrez le fichier code-behind nommé *Default.aspx.cs*. Remplacez le code existant par celui qui suit, puis enregistrez le fichier :  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Étape 2 : Implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé  
 Dans cette étape, vous allez substituer les fonctionnalités par défaut dans la classe <xref:System.Security.Claims.ClaimsAuthenticationManager> pour ajouter un rôle d’administrateur (Administrator) au principal entrant.  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a>Pour implémenter la transformation des revendications à l’aide d’un ClaimsAuthenticationManager personnalisé  
  
1.  Dans Visual Studio, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
2.  Dans la fenêtre **Ajouter un nouveau projet**, sélectionnez **Bibliothèque de classes** dans la liste de modèles **Visual C#**, entrez `ClaimsTransformation`, puis appuyez sur **OK**. Le nouveau projet est créé dans votre dossier de solutions.  
  
3.  Cliquez avec le bouton droit sur **Références** sous le projet **ClaimsTransformation**, puis cliquez sur **Ajouter une référence**.  
  
4.  Dans la fenêtre **Gestionnaire de références**, sélectionnez **System.IdentityModel**, puis cliquez sur **OK**.  
  
5.  Ouvrez **Class1.cs**. Si cette classe n’existe pas, cliquez avec le bouton droit sur **ClaimsTransformation**, cliquez sur **Ajouter** et cliquez sur **Classe...**  
  
6.  Ajoutez le code suivant à l’aide de directives dans le fichier de code :  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Ajoutez la classe et la méthode suivantes dans le fichier de code.  
  
    > [!WARNING]
    >  Le code suivant est fourni à titre de démonstration uniquement. Vérifiez les autorisations prévues dans votre code de production.  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  Enregistrez le fichier et générez le projet **ClaimsTransformation**.  
  
9. Dans votre projet **TestApp** ASP.NET, cliquez avec le bouton droit sur Références, puis cliquez sur **Ajouter une référence**.  
  
10. Dans la fenêtre **Gestionnaire de références**, sélectionnez **Solution** dans le menu de gauche, sélectionnez **ClaimsTransformation** dans les options remplies, puis cliquez sur **OK**.  
  
11. Dans le fichier racine **Web.config**, accédez à l’entrée **\<system.identityModel>**. Dans les éléments **\<identityConfiguration>**, ajoutez la ligne suivante, puis enregistrez le fichier :  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a>Étape 3 : Tester votre solution  
 Dans cette étape, vous allez tester votre application Web Forms ASP.NET et vérifier que les revendications sont présentées à l’utilisateur qui se connecte à l’aide de l’authentification par formulaire.  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a>Pour tester votre application Web Forms ASP.NET pour les revendications à l’aide de l’authentification par formulaire  
  
1.  Appuyez sur **F5** pour générer et exécuter l’application. La page *Default.aspx* doit s’afficher.  
  
2.  Dans la page *Default.aspx*, sous l’en-tête **Your Claims** (Vos revendications), vous voyez normalement un tableau qui affiche ces informations sur les revendications associées à votre compte : **Issuer**, **OriginalIssuer**, **Type**, **Value** et **ValueType**. La dernière ligne doit se présenter de cette façon :  
  
    ||||||  
    |-|-|-|-|-|  
    |LOCAL AUTHORITY|LOCAL AUTHORITY|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|Administrateur|http://www.w3.org/2001/XMLSchema#string|

