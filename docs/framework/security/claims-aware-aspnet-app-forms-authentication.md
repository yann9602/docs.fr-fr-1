---
title: "Comment&#160;: g&#233;n&#233;rer une application ASP.NET prenant en charge les revendications &#224; l’aide de l’authentification bas&#233;e sur les formulaires | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# Comment&#160;: g&#233;n&#233;rer une application ASP.NET prenant en charge les revendications &#224; l’aide de l’authentification bas&#233;e sur les formulaires
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour créer une application prenant en charge les revendications simple Web Forms ASP.NET qui utilise l'authentification par formulaire.  Il fournit également des instructions sur la façon de teste l'application pour vérifier que les revendications sont présentées lorsqu'un utilisateur archive dans avec l'authentification par formulaire.  
  
## Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
-   Étape 3 \(testez votre solution  
  
## Objectifs  
  
-   Configurez une application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
-   Testez l'application Web Forms ASP.NET de vérifier si elle fonctionne correctement  
  
## Vue d'ensemble  
 Dans le .NET 4,5, WIF et son autorisation basée revendication\- ont été inclus en tant que partie intégrante de l'infrastructure.  Précédemment, si vous voulez des revendications d'un utilisateur ASP.NET, vous a été requis pour installer WIF, puis avez un cast des interfaces aux objets principaux tels qu' `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.  Maintenant, les revendications sont servies automatiquement par ces objets principaux.  
  
 L'authentification par formulaire est dessiné parti de l'inclusion de WIF dans le .NET 4,5 parce que tous les utilisateurs authentifiés par les formulaires ont automatiquement des revendications associées.  Vous pouvez commencer à utiliser les revendications immédiatement dans une application ASP.NET qui utilise l'authentification par formulaire, car cet article explique Comment faire.  
  
## Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
-   Étape 3 \(testez votre solution  
  
## Étape 1 \- créez une simple application Web Forms ASP.NET  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### Pour créer une simple application ASP.NET  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
## Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
 Dans cette étape vous ajouterez une entrée de configuration *dans le fichier de configuration Web.config* et éditerez le Default.aspxfile pour afficher les informations de revendications pour un compte.  
  
#### Pour configurer l'application ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
1.  Dans *le fichier Default.aspx* , remplacez le balisage existant par celui\-ci :  
  
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
  
     Cette étape ajoute un contrôle gridview à votre *page Default.aspx* qui sera remplie avec les revendications récupérées de l'authentification par formulaire.  
  
2.  Enregistrez *le fichier Default.aspx* , puis ouvrez le fichier code\-behind nommé Default.aspx.cs.  Remplacez le code existant par celui\-ci :  
  
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
  
     Le code ci\-dessus affiche des revendications sur un utilisateur authentifié, y compris les utilisateurs identifiés par l'authentification par formulaire.  
  
## Étape 3 \(testez votre solution  
 Dans cette étape vous allez tester votre application Web Forms ASP.NET, et vérifiez que les revendications sont présentées lorsqu'un utilisateur archive dans avec l'authentification par formulaire.  
  
#### Pour tester votre application Web Forms ASP.NET de revendications à l'aide de l'authentification par formulaire  
  
1.  Appuyez sur **F5** pour générer et exécuter l'application.  Vous devez être présenté avec *Default.aspx, qui*a **Inscrire** et des liens de **Se connecter** dans l'en haut à droite de la page.  Cliquez sur **S'inscrire**.  
  
2.  Dans la page de **Inscrire** , créez un compte d'utilisateur, puis cliquez sur **Inscrire**.  Votre compte est créé à l'aide de l'authentification par formulaire, et vous êtes automatiquement signé dans.  
  
3.  Après avoir été redirigé vers la page d'accueil, vous devez constater un tableau sous titre de **Les revendications** qui inclut des informations **Émetteur**, **OriginalIssuer**, **Type**, **Valeur**, et de **ValueType** revendications sur votre compte.