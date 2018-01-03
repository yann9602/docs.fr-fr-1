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
ms.workload: dotnet
ms.openlocfilehash: a7c72d77b4894376fb6cb8aed2d1c6641a3977da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-token-replay-detection"></a>Guide pratique pour activer la détection de relecture de jetons
## <a name="applies-to"></a>S'applique à  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms ASP.NET®  
  
## <a name="summary"></a>Récapitulatif  
 Cette procédure fournit des procédures pas à pas détaillées pour l’activation de la détection de relecture de jetons dans une application ASP.NET qui utilise WIF. Elle fournit également des instructions pour tester l’application afin de vérifier que la détection de relecture de jetons est activée. Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès. Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement. Vous devez installer l'outil Identité et accès pour exécuter cette procédure. Il peut être téléchargé à partir de l’emplacement suivant : [Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>Sommaire  
  
-   Objectifs  
  
-   Vue d'ensemble  
  
-   Résumé des étapes  
  
-   Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture  
  
-   Étape 2 : tester votre solution  
  
## <a name="objectives"></a>Objectifs  
  
-   Créer une simple application ASP.NET qui utilise WIF et le service STS de développement à partir de l’outil Identity and Access Tool  
  
-   Activer la détection de relecture de jetons et vérifier son fonctionnement  
  
## <a name="overview"></a>Vue d'ensemble  
 Une attaque par relecture se produit quand un client essaie de s’authentifier auprès d’une partie de confiance avec un jeton STS que le client a déjà utilisé. Pour éviter ce genre d’attaque, WIF contient un cache de détection de relecture de jetons STS précédemment utilisés. Quand elle est activée, la détection de relecture vérifie le jeton de la demande entrante et si le jeton a été utilisé précédemment ou non. Si le jeton a déjà été utilisé, la demande est refusée et une exception <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> est levée.  
  
 Les étapes suivantes illustrent les modifications de configuration requises pour activer la détection de relecture.  
  
## <a name="summary-of-steps"></a>Résumé des étapes  
  
-   Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture  
  
-   Étape 2 : tester votre solution  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>Étape 1 : créer une simple application Web Forms ASP.NET et activer la détection de relecture  
 Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifier le fichier *Web.config* pour activer la détection de relecture.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Pour créer une application ASP.NET simple  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.  
  
4.  Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).  
  
5.  La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche. Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.  
  
6.  Ajoutez l’élément **\<tokenReplayDetection>** suivant au fichier de configuration *Web.config* immédiatement après les éléments **\<system.identityModel>** et **\<identityConfiguration>**, comme illustré ci-dessous :  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>Étape 2 : tester votre solution  
 Dans cette étape, vous allez tester votre application ASP.NET WIF pour vérifier que la détection de relecture a été activée.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Pour tester votre application ASP.NET WIF pour la détection de relecture  
  
1.  Exécutez la solution en appuyant sur la touche **F5**. La page d’accueil ASP.NET par défaut doit s’afficher et vous devez être automatiquement authentifié avec le nom d’utilisateur *Terry*, qui est l’utilisateur par défaut retourné par le service STS de développement.  
  
2.  Appuyez sur le bouton **Précédent** du navigateur. Une page **Erreur du serveur dans l’application ‘/’** doit s’afficher avec la description suivante : *ID1062 : relecture détectée pour : Jeton : 'System.IdentityModel.Tokens.SamlSecurityToken'*, suivie des éléments *AssertionId* et *Émetteur*.  
  
     Vous voyez cette page d’erreur, car une exception de type <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> a été levée lors de la détection de la relecture de jetons. Cette erreur se produit parce que vous essayez d’envoyer à nouveau la requête POST initiale où le jeton est apparu la première fois. Le bouton **Précédent** n’entraîne pas ce comportement pour les demandes suivantes au serveur.
