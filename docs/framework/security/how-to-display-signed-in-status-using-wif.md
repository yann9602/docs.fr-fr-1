---
title: "Comment&#160;: afficher l’&#233;tat Connect&#233; &#224; l’aide de WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# Comment&#160;: afficher l’&#233;tat Connect&#233; &#224; l’aide de WIF
## S'applique à  
  
-   Base \(WIF\) 4,5 d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cette rubrique décrit comment afficher le signe dans l'état dans une application WIF\- activée ASP.NET.  WIF fournit un mécanisme pour rendre votre application prenant en charge les revendications, et gérer l'authentification et l'autorisation de ressources d'application.  
  
## Sommaire  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- Installez l'identité et accédez à l'extension  
  
-   Étape 2 \- Créez une application ASP.NET de partie de confiance  
  
-   Étape 3 \- Permettre au développement local STS pour authentifier des utilisateurs  
  
-   Étape 4 \- Modifiez votre application ASP.NET d'afficher archivent dans l'état  
  
-   Étape 5 \- Testez l'intégration entre WIF et votre application ASP.NET  
  
## Vue d'ensemble  
 Cette rubrique montre comment créer une application prenant en charge les revendications simple à WIF et comment afficher facilement, qu'un utilisateur a archivé dans ou pas.  Les étapes suivantes utilisent le développement local STS inclus avec l'identité et l'extension Access Visual Studio.  Le développement local STS est conçu pour un test et un environnement de développement fournit une méthode intégrer des revendications dans votre application.  Il ne doit jamais être utilisé dans un environnement de production, car il n'exécute pas la vraie authentification et les informations d'identification ne sont pas nécessaires.  Toutefois, le code impératif dans les étapes suivantes est le même pour une application prête à produire à la vraie authentification.  
  
## Résumé des étapes  
  
-   Étape 1 \- Installez l'identité et accédez à l'extension  
  
-   Étape 2 \- Créez une application ASP.NET de partie de confiance  
  
-   Étape 3 \- Permettre au développement local STS pour authentifier des utilisateurs  
  
-   Étape 4 \- Modifiez votre application ASP.NET d'afficher archivent dans l'état  
  
-   Étape 5 \- Testez l'intégration entre WIF et votre application ASP.NET  
  
## Étape 1 \- Installez l'identité et accédez à l'extension  
 Cette étape décrit comment configurer l'identité et accéder à l'extension de Visual Studio 2012.  Cette extension automatise le processus de configurer votre application pour communiquer avec des extrémités de STS.  
  
#### Pour installer l'identité et accéder à l'extension  
  
1.  Démarrez Visual Studio en mode élevé en tant qu'administrateur.  
  
2.  Dans Visual Studio, cliquez sur **Outils** et cliquez sur **Gestionnaire d'extensions**.  La fenêtre **Gestionnaire d'extensions** apparaît.  
  
3.  Dans **Gestionnaire d'extensions**, cliquez sur **Extensions en ligne** du menu de gauche, puis sélectionnez **Galerie Visual Studio**.  
  
4.  Dans le coin supérieur droit de la **Gestionnaire d'extensions**, recherchez *l'identité et y accédez*.  
  
5.  L'élément **Identité et accès** s'affiche dans les résultats de la recherche.  Cliquez dessus, puis cliquez sur **Télécharger**.  
  
6.  La boîte de dialogue **Télécharger et installer** apparaît.  Si vous êtes d'accord avec les termes du contrat de licence, cliquez sur **Installer**.  
  
7.  Lorsque l'extension **Identité et accès** a terminé l'installation, redémarrez Visual Studio en mode Administrateur.  
  
## Étape 2 \- Créez une application ASP.NET de partie de confiance  
 Cette étape décrit comment créer une application Web Forms ASP.NET de partie de confiance qui est intégrée avec WIF.  
  
#### Pour créer une application ASP.NET simple  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, tapez `TestApp` et appuyez sur **OK**.  
  
## Étape 3 \- Permettre au développement local STS pour authentifier des utilisateurs  
 Cette étape décrit comment activer le développement local STS dans votre application.  Le développement local STS est activé via l'extension d'identité et Access pour Visual Studio.  
  
#### Pour activer le développement local STS dans votre application ASP.NET  
  
1.  Dans Visual Studio, cliquez avec le bouton droit sur le projet **TestApp** sous **Explorateur de solutions**, puis sélectionnez **Identité et accès**.  
  
2.  La fenêtre **Identité et accès** apparaît.  Sous **Fournisseurs**, sélectionnez **Testez votre application avec le développement local STS**, puis cliquez sur **Appliquer**.  
  
## Étape 4 \- Modifiez votre application ASP.NET d'afficher archivent dans l'état  
 Cette étape décrit comment modifier votre application ASP.NET d'afficher dynamiquement si l'utilisateur actuel est archivé dans.  Une fois votre fournisseur de STS a été configuré, WIF traite les revendications entrantes.  Maintenant vous devez configurer votre code d'application pour afficher le résultat de l'authentification.  
  
#### Pour afficher archivez dans l'état  
  
1.  Dans Visual Studio, ouvrez le fichier **Default.aspx** sous le projet **TestApp**.  
  
2.  Remplacez la balise existante dans le fichier **Default.aspx** par le balisage suivant :  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  Enregistrez **Default.aspx**, puis ouvrez son code\-behind nommé **Default.aspx.cs**fichier.  
  
    > [!NOTE]
    >  **Default.aspx.cs** peut être masqué sous l'explorateur **Default.aspx** en solution.  Si **Default.aspx.cs** n'est pas visible, développez **Default.aspx** en cliquant sur le triangle en regard de celle\-ci.  
  
4.  Remplacez le code existant dans **Default.aspx.cs** par le code suivant :  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  Enregistrez **Default.aspx.cs**, puis générez l'application.  
  
## Étape 5 \- Testez l'intégration entre WIF et votre application ASP.NET  
 Cette étape décrit comment vous pouvez tester l'intégration entre WIF et votre application ASP.NET.  
  
#### Pour tester l'intégration entre WIF et ASP.NET  
  
1.  Dans Visual Studio, appuyez sur **F5** pour démarrer le débogage de votre application.  Si aucune erreur n'est trouvée, une nouvelle fenêtre de navigateur s'ouvre.  
  
2.  Vous pouvez remarquer que le navigateur redirige automatiquement votre application à STS, puis ouvrez la page Default.aspx.  Si WIF est correctement configuré, vous devez voir le site afficher le texte suivant : **« Vous avez archivé dans »**.