---
title: "Comment&#160;: activer la d&#233;tection de relecture du jeton | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Comment&#160;: activer la d&#233;tection de relecture du jeton
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® Web Forms  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour activer la détection du jeton par reconstitution dans une application ASP.NET qui utilise WIF.  Il fournit également des instructions sur la façon de teste l'application pour vérifier que la détection du jeton par reconstitution est activée.  Cet " Comment " n'a pas le obtenir des instructions détaillées pour créer un service d'émission de jeton de sécurité \(STS\), et utilise à la place le développement STS fourni avec l'outil d'identité et Access.  Le développement STS n'exécute pas la véritable authentification et est prévu pour tester uniquement.  Vous devez installer l'outil d'identité et Access pour remplir cet " Comment ".  Il peut être téléchargé à partir de l'emplacement suivant : [Identité et outil Access](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET et activez la détection par reconstitution  
  
-   Étape 2 \(testez votre solution  
  
## Objectifs  
  
-   Créez une application ASP.NET simple qui utilise WIF et le développement STS de l'identité et accédez à l'outil  
  
-   Activez la détection du jeton par reconstitution et vérifiez que cela fonctionne  
  
## Vue d'ensemble  
 Une attaque par reconstitution se produit lorsque tente d'un client d'authentifier à une partie de confiance avec un jeton de STS que le client a déjà utilisée.  Pour empêcher cette attaque, WIF contient un cache de détection par reconstitution de balisage précédemment utilisées de STS.  Une fois activé, la détection par reconstitution contrôle le jeton de la requête entrante et la vérifie si le jeton a été précédemment utilisée.  Si le jeton a déjà été utilisée, la demande est refusée et une exception d' <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> est levée.  
  
 Les étapes suivantes expliquent les modifications de configuration requises pour activer la détection par reconstitution.  
  
## Résumé des étapes  
  
-   Étape 1 \- créez une simple application Web Forms ASP.NET et activez la détection par reconstitution  
  
-   Étape 2 \(testez votre solution  
  
## Étape 1 \- créez une simple application Web Forms ASP.NET et activez la détection par reconstitution  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifierez *le fichier Web.config* pour activer la détection par reconstitution.  
  
#### Pour créer une simple application ASP.NET  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
4.  Cliquez avec le bouton droit sur le projet de **TestApp** sous **Explorateur de solutions**, puis sélectionnez **identité et Access**.  
  
5.  La fenêtre d' **identité et Access** s'affiche.  Sous **Fournisseurs**, **testez votre application avec le développement local STS**sélectionnez, puis cliquez sur **Appliquer**.  
  
6.  Ajoutez l'élément suivant de **\<tokenReplayDetection\>** *au fichier de configuration Web.config* qui suit immédiatement les éléments de **\<system.identityModel\>** et de **\<identityConfiguration\>** , comme suit :  
  
    ```  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled=”true”/>  
    ```  
  
## Étape 2 \(testez votre solution  
 Dans cette étape, vous allez tester votre application WIF\- activée ASP.NET pour vérifier que la détection par reconstitution a été activée.  
  
#### Pour tester votre application WIF\- activée ASP.NET de détection par reconstitution  
  
1.  Exécutez la solution en appuyant sur la touche de **F5** .  Vous devez être présenté avec la page d'accueil ASP.NET par défaut et être automatiquement authentifié avec le nom d'utilisateur *Terry*, qui est l'utilisateur par défaut retourné par le développement STS.  
  
2.  Appuyez sur le bouton d' **Arrière** du navigateur.  Vous devez être présenté avec une page d' **erreur de serveur dans « \/ » application** avec la description qui suit : *ID1062 : La reconstitution a été détecté pour : Jeton : « System.IdentityModel.Tokens.SamlSecurityToken »*, suivi d'un *AssertionId* et d'un *expéditeur* .  
  
     Vous voyez cette page d'erreurs parce qu'une exception de type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> a été levée lorsque la reconstitution de jeton a été détecté.  Cette erreur se produit parce que vous tentez de retourner la requête initiale POST lorsque le jeton a été présentée la première fois.  Le bouton d' **Arrière** n'entraîne pas ce comportement pour les demandes suivantes au serveur.