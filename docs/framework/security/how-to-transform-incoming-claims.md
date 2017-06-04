---
title: "Comment&#160;: transformer les revendications entrantes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Comment&#160;: transformer les revendications entrantes
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour créer une application prenant en charge les revendications simple Web Forms ASP.NET et transformer des revendications entrantes.  Il fournit également des instructions sur la façon de teste l'application pour vérifier que les revendications transformées sont présentées lorsque l'application est exécutée.  
  
## Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- l'implémentation réclame la transformation à l'aide d'un ClaimsAuthenticationManager personnalisé  
  
-   Étape 3 \(testez votre solution  
  
## Objectifs  
  
-   Configurez une application Web Forms ASP.NET d'authentification basée revendication\-  
  
-   Transformez les revendications entrantes en ajoutant un rôle Administrateur de revendication  
  
-   Testez l'application Web Forms ASP.NET de vérifier si elle fonctionne correctement  
  
## Vue d'ensemble  
 WIF expose une classe nommée <xref:System.Security.Claims.ClaimsAuthenticationManager> qui permet aux utilisateurs de modifier des revendications avant d'être présentées à une application de définition de données \(RP\) partie de confiance.  <xref:System.Security.Claims.ClaimsAuthenticationManager> est utile pour la séparation des aspects d'un problème entre l'authentification et le code d'application sous\-jacent.  L'exemple suivant montre comment ajouter un rôle des revendications dans <xref:System.Security.Claims.ClaimsPrincipal> entrant qui peut être requis par le RP.  
  
## Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- l'implémentation réclame la transformation à l'aide d'un ClaimsAuthenticationManager personnalisé  
  
-   Étape 3 \(testez votre solution  
  
## Étape 1 \- créez une simple application Web Forms ASP.NET  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### Pour créer une simple application ASP.NET  
  
1.  Démarrez Visual Studio en mode élevé en tant qu'administrateur.  
  
2.  Dans Visual Studio, cliquez sur **Fichier**, cliquez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web Forms ASP.NET**.  
  
4.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
5.  Cliquez avec le bouton droit sur le projet de **TestApp** sous **Explorateur de solutions**, puis sélectionnez **identité et Access**.  
  
6.  La fenêtre d' **identité et Access** s'affiche.  Sous **Fournisseurs**, **testez votre application avec le développement local STS**sélectionnez, puis cliquez sur **Appliquer**.  
  
7.  Dans *le fichier Default.aspx* , remplacez le balisage existant par le suivant, puis enregistrez le fichier :  
  
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
  
8.  Ouvrez le fichier code\-behind nommé *Default.aspx.cs.* Remplacez le code existant par le code suivant, puis enregistrez le fichier :  
  
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
  
## Étape 2 \- l'implémentation réclame la transformation à l'aide d'un ClaimsAuthenticationManager personnalisé  
 Dans cette étape vous substituerez la fonctionnalité par défaut dans la classe d' <xref:System.Security.Claims.ClaimsAuthenticationManager> pour ajouter un rôle Administrateur à l'entité entrante.  
  
#### Pour implémenter la transformation de revendications à l'aide d'un ClaimsAuthenticationManager personnalisé  
  
1.  Dans Visual Studio, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis cliquez sur **Nouveau projet**.  
  
2.  Dans la fenêtre de **Ajouter un nouveau projet** , **Bibliothèque de classes** sélectionnez les modèles de **Visual C\#** la liste, entrez `ClaimsTransformation`, puis appuyez **OK**.  Le projet est créé dans votre dossier de solution.  
  
3.  Cliquez avec le bouton droit sur **Références** sous le projet de **ClaimsTransformation** , puis cliquez sur **Ajouter une référence**.  
  
4.  Dans la fenêtre de **référencez le gestionnaire** , **System.IdentityModel**sélectionnez, puis cliquez sur **OK**.  
  
5.  **Class1.cs**ouvert, ou s'il n'existe pas, cliquez avec le bouton droit sur **ClaimsTransformation**, cliquez sur **Ajouter**, puis cliquez sur **classez…**  
  
6.  Ajoutez les directives using suivantes au fichier de code :  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  Ajoutez la classe et la méthode suivantes dans le fichier de code.  
  
    > [!WARNING]
    >  Le code suivant est à des fins de démonstration uniquement ; assurez \-vous que vous vérifiez vos autorisations prévues dans le code de production.  
  
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
  
8.  Enregistrez le fichier et régénérez le projet de **ClaimsTransformation** .  
  
9. Dans votre projet de **TestApp** ASP.NET, cliquez avec le bouton droit sur les références, puis cliquez sur **Ajouter une référence**.  
  
10. Dans la fenêtre de **référencez le gestionnaire** , **Solution** sélectionnez dans le menu gauche, **ClaimsTransformation** sélectionnez les options remplies, puis cliquez sur **OK**.  
  
11. Dans le fichier de **Web.config** racine, accédez à l'entrée de **\<system.identityModel\>** .  Dans les éléments de **\<identityConfiguration\>** , ajoutez la ligne suivante et enregistrez le fichier :  
  
    ```  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## Étape 3 \(testez votre solution  
 Dans cette étape vous allez tester votre application Web Forms ASP.NET, et vérifiez que les revendications sont présentées lorsqu'un utilisateur archive dans avec l'authentification par formulaire.  
  
#### Pour tester votre application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
1.  Appuyez sur **F5** pour générer et exécuter l'application.  Vous devez être présenté avec *Default.aspx.*  
  
2.  Sur *la page Default.aspx* , vous devez constater un tableau sous titre de **Les revendications** qui inclut des informations **Émetteur**, **OriginalIssuer**, **Type**, **Valeur**, et de **ValueType** revendications sur votre compte.  La dernière ligne doit être présentée de la manière suivante :  
  
    ||||||  
    |-|-|-|-|-|  
    |AUTORITE LOCALE|AUTORITE LOCALE|http:\/\/schemas.microsoft.com\/ws\/2008\/06\/identity\/claims\/role|Admin|http:\/\/www.w3.org\/2001\/XMLSchema\#string|