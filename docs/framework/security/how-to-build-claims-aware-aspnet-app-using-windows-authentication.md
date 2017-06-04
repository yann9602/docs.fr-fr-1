---
title: "Comment&#160;: g&#233;n&#233;rer une application ASP.NET prenant en charge les revendications &#224; l’aide de l’authentification Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# Comment&#160;: g&#233;n&#233;rer une application ASP.NET prenant en charge les revendications &#224; l’aide de l’authentification Windows
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour créer une application prenant en charge les revendications simple Web Forms ASP.NET qui utilise l'authentification Windows.  Il fournit également des instructions sur la façon de teste l'application pour vérifier que les revendications sont présentées lorsqu'un utilisateur archive dans à l'aide de l'authentification Windows.  
  
## Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification Windows  
  
-   Étape 3 \(testez votre solution  
  
## Objectifs  
  
-   Configurez une application Web Forms ASP.NET de revendications à l'aide de l'authentification Windows  
  
-   Testez l'application Web Forms ASP.NET de vérifier si elle fonctionne correctement  
  
## Vue d'ensemble  
 Dans le .NET 4,5, WIF et son autorisation basée revendication\- ont été inclus en tant que partie intégrante de l'infrastructure.  Précédemment, si vous voulez des revendications d'un utilisateur ASP.NET, vous a été requis pour installer WIF, puis avez un cast des interfaces aux objets principaux tels qu' `Thread.CurrentPrincipal` ou `HttpContext.Current.User`.  Maintenant, les revendications sont servies automatiquement par ces objets principaux.  
  
 L'authentification Windows est dessiné parti de l'inclusion de WIF dans le .NET 4,5 parce que tous les utilisateurs authentifiés par les informations d'identification Windows ont automatiquement des revendications associées.  Vous pouvez commencer à utiliser les revendications immédiatement dans une application ASP.NET qui utilise l'authentification Windows, car cet article explique Comment faire.  
  
## Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET  
  
-   Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification Windows  
  
-   Étape 3 \(testez votre solution  
  
## Étape 1 \- créez une simple application Web Forms ASP.NET  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET.  
  
#### Pour créer une simple application ASP.NET  
  
1.  Démarrez Visual Studio, puis cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
4.  Une fois le projet de **TestApp** créé, cliquez dessus sur le dans **Explorateur de solutions**.  Les propriétés du projet s'affichent dans le volet de **Propriétés** au\-dessous de **Explorateur de solutions**.  Affectez à la propriété de **Authentification Windows** à **Activé**.  
  
    > [!WARNING]
    >  L'authentification Windows est désactivée par défaut dans de nouvelles applications ASP.NET, vous devez manuellement l'activer.  
  
## Étape 2 \- configurer l'application Web Forms ASP.NET de revendications à l'aide de l'authentification Windows  
 Dans cette étape vous ajouterez une entrée de configuration *dans le fichier de configuration Web.config* et modifierez le Default.aspxfile pour afficher les informations de revendications pour un compte.  
  
#### Pour configurer l'application ASP.NET de revendications à l'aide de l'authentification Windows  
  
1.  Dans *le fichier Default.aspx du* projet de **TestApp** , remplacez le balisage existant par celui\-ci :  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
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
  
     Cette étape ajoute un contrôle gridview à votre *page Default.aspx* qui sera remplie avec les revendications récupérées de l'authentification Windows.  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     Le code ci\-dessus affiche des revendications sur un utilisateur authentifié.  
  
3.  Pour modifier le type d'authentification de l'application, modifiez le bloc de **\<authentication\>** dans la section de **\<system.web\>** du fichier Web.config racine du projet de sorte qu'il inclut uniquement l'entrée de configuration suivante :  
  
    ```  
    <authentication mode="Windows" />  
    ```  
  
4.  Enfin, modifiez le bloc de **\<authorization\>** dans la section de **\<system.web\>** du même *fichier Web.config* pour forcer l'authentification :  
  
    ```  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## Étape 3 \(testez votre solution  
 Dans cette étape vous allez tester votre application Web Forms ASP.NET, et vérifiez que les revendications sont présentées lorsqu'un utilisateur archive dans avec l'authentification Windows.  
  
#### Pour tester votre application Web Forms ASP.NET de revendications à l'aide de l'authentification Windows  
  
1.  Appuyez sur **F5** pour générer et exécuter l'application.  Vous devez être présenté avec *Default.aspx, et*le nom de compte Windows \(nom de domaine\) doit déjà apparaître en tant qu'utilisateur authentifié dans l'en haut à droite de la page.  Le contenu de la page doit inclure une table rempli avec les revendications extraites de votre compte Windows.