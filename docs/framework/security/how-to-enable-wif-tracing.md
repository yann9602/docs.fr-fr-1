---
title: "Comment&#160;: activer le suivi WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# Comment&#160;: activer le suivi WIF
## S'applique à  
  
-   Base \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet article " Comment " fournit les procédures détaillées à suivre détaillées pour activer le traçage de WIF dans une application ASP.NET.  Il fournit également l'instruction tester l'application pour vérifier que l'écouteur de la trace et le journal fonctionnent correctement.  Cet article " Comment " n'a pas obtenir des instructions détaillées pour créer un service d'émission de jeton de sécurité \(STS\), et utilise à la place le développement STS fournis avec l'outil d'identité et Access.  Le développement STS n'exécute pas la vraie authentification et est conçu pour tester uniquement.  Vous devez installer l'outil d'identité et Access pour remplir cet article " Comment ".  Il peut être téléchargé de l'emplacement suivant : [Identité outils et Access](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  L'activation du traçage de WIF pour les applications passives, autrement. Autrement dit., les applications qui utilisent le protocole de WS\-Federation, peut potentiellement exposer l'application aux attaques de \(DoS\) de déni de service ou à la divulgation d'informations à une partie malveillantes.  Ceci inclut le nombre de requêtes par seconde passive et le STSes passif.  Pour cette raison, nous vous recommandons de ne pas activer le traçage de WIF pour la nombre de requêtes par seconde passive ou le STSes dans un environnement de production.  
  
## Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- Créez une simple application Web Forms ASP.NET et activez le traçage  
  
-   Étape 2 – Testez votre solution  
  
## Objectifs  
  
-   Créez une application ASP.NET simple qui utilise WIF et le développement STS de l'identité et accédez à l'outil  
  
-   Activer le traçage et vérifiez qu'il fonctionne  
  
## Vue d'ensemble  
 Le traçage vous permet de déboguer et résoudre de nombreux types de problèmes avec WIF, notamment les jetons, des cookies, des revendications, des messages de gestion de protocole, etc.  Le traçage de WIF est semblable au suivi WCF ; par exemple, vous pouvez choisir les commentaires des traces pour afficher les messages critiques à tous les messages.  Les traces de WIF peuvent être générées dans des fichiers **.xml** ou dans les fichiers **.svclog** qui sont affichables à l'aide de l'outil de Visionneuse de trace des services.  Cet outil se trouve dans le répertoire **bin** du Kit de développement logiciel Chemin d'installation sur votre ordinateur, par exemple : **C:\\Program Files\\Microsoft SDKs\\Windows\\v7.1\\bin\\SvcTraceViewer.exe**.  
  
## Résumé des étapes  
  
-   Étape 1 \- Créez une simple application Web Forms ASP.NET et activez le traçage  
  
-   Étape 2 – Testez votre solution  
  
## Étape 1 \- Créez une simple application Web Forms ASP.NET et activez le traçage  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifiez *le fichier web.config* pour activer le traçage.  
  
#### Pour créer une application ASP.NET simple  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, tapez `TestApp` et appuyez sur **OK**.  
  
4.  Cliquez avec le bouton droit sur le projet **TestApp** sous **Explorateur de solutions**, puis sélectionnez **Identité et accès**.  
  
5.  La fenêtre **Identité et accès** apparaît.  Sous **Fournisseurs**, sélectionnez **Testez votre application avec le développement local STS**, puis cliquez sur **Appliquer**.  
  
6.  Créer un dossier dans nommé **journaux** à la racine du lecteur **C :**, comme indiqué : **C:\\logs**  
  
7.  Ajoutez l'élément suivant **\<system.diagnostics\>** *au fichier de configuration Web.config* immédiatement après l'élément fermant **\<\/configSections\>**, comme indiqué :  
  
    ```  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  L'emplacement du répertoire spécifié dans l'attribut **initializeData** doit exister pour que l'enregistrement puisse démarrer.  Si l'emplacement n'existe pas, aucun journal ne sera créé.  
  
     Les paramètres de configuration ci\-dessus activeront **Commentaires** le traçage pour WIF et sauvegarderont le journal obtenue au fichier **C:\\logs\\WIF.xml**.  
  
## Étape 2 – Testez votre solution  
 Dans cette étape, vous allez tester votre application WIF\- activée ASP.NET de vérifier que les journaux sont stockés.  
  
#### Pour tester votre application WIF\- activée ASP.NET de traçage réussi  
  
1.  Exécutez la solution en appuyant sur la touche **F5**.  Vous devez être présenté avec la page d'accueil ASP.NET par défaut et être automatiquement authentifié avec le nom d'utilisateur *Terry*, qui est l'utilisateur par défaut retourné par le développement STS.  
  
2.  Fermez la fenêtre du navigateur puis accédez au dossier **C:\\logs**.  Ouvrez le **C:\\logs\\WIF.xml** avec un éditeur de texte.  
  
3.  Inspectez le fichier **WIF.xml** et vérifiez qu'il contient des entrées commençant par **\<E2ETraceEvent\>**.  Ces traces contiendront des éléments **\<TraceRecord\>** avec les descriptions de l'activité tracée, telle que **Validation de SecurityToken**.