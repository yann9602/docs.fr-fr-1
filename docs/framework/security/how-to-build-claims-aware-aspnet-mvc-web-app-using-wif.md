---
title: "Comment&#160;: g&#233;n&#233;rer une application web ASP.NET MVC prenant en charge les revendications &#224; l’aide de WIF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# Comment&#160;: g&#233;n&#233;rer une application web ASP.NET MVC prenant en charge les revendications &#224; l’aide de WIF
## S'applique à  
  
-   Foundation \(WIF\) d'identité Microsoft® Windows®  
  
-   ASP.NET® MVC  
  
## Résumé  
 Cet " Comment " fournit des procédures pas \- à \- pas détaillées pour créer l'application Web prenant en charge les revendications simple ASP.NET MVC.  Il fournit également des instructions comment tester l'application Web prenant en charge les revendications simple ASP.NET MVC pour l'implémentation réussie de l'authentification basée revendication\-.  Cet " Comment " n'a pas le obtenir des instructions détaillées pour créer un service d'émission de jeton de sécurité \(STS\), et le suppose que vous avez déjà configuré STS.  
  
## Sommaire  
  
-   Objectifs  
  
-   Résumé des étapes  
  
-   Étape 1 \- créez l'application ASP.NET MVC simple  
  
-   Étape 2 \(configurez l'application ASP.NET MVC pour l'authentification Basée Revendication\-  
  
-   Étape 3 \(testez votre solution  
  
-   Élément connexe  
  
## Objectifs  
  
-   Configurez l'application Web ASP.NET MVC pour l'authentification basée revendication\-  
  
-   Testez l'application Web prenant en charge les revendications réussie ASP.NET MVC  
  
## Résumé des étapes  
  
-   Étape 1 \- créez l'application ASP.NET MVC simple  
  
-   Étape 2 \(configurez l'application ASP.NET MVC pour l'authentification Basée Revendication\-  
  
-   Étape 3 \(testez votre solution  
  
## Étape 1 \- créez l'application ASP.NET MVC simple  
 Dans cette étape, vous allez créer une application ASP.NET MVC.  
  
#### Pour créer l'application ASP.NET MVC simple  
  
1.  Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.  
  
2.  Dans la fenêtre de **Nouveau projet** , cliquez sur **Application Web ASP.NET MVC 3**.  
  
3.  Dans **Nom**, entrez `TestApp` et appuyez **OK**.  
  
4.  Dans la boîte de dialogue **Nouveau projet ASP.NET MVC 3** , sélectionnez **application Web** des modèles disponibles, vérifiez **moteur d'affichage** a la valeur **Razor**, puis cliquez sur **OK**.  
  
5.  Lorsque le nouveau projet s'ouvre, cliquez avec le bouton droit sur le projet **TestApp** dans **Explorateur de solutions** et sélectionnez l'option **Propriétés** .  
  
6.  Dans la page de propriétés du projet, cliquez sur l'onglet **Web** sur la gauche et assurez \-vous que l'option **Serveur Web IIS local d'utilisation** est sélectionnée.  
  
## Étape 2 \(configurez l'application ASP.NET MVC pour l'authentification Basée Revendication\-  
 Dans cette étape vous ajouterez des entrées de configuration *dans le fichier de configuration Web.config* de votre application Web ASP.NET MVC de le informer.  
  
#### Pour configurer l'application ASP.NET MVC pour l'authentification basée revendication\-  
  
1.  Ajoutez les définitions de section de configuration suivantes *au fichier de configuration Web.config* .  Elles définissent des sections de configuration requises par IDENTITY Windows Foundation.  Ajoutez les définitions immédiatement **\<configuration\>** après l'élément d'ouverture :  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  Ajoutez un élément de **\<location\>** qui permet d'accéder aux métadonnées de fédération de l'application :  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  Ajoutez les entrées de configuration suivantes dans les éléments de **\<system.web\>** pour refuser des utilisateurs, désactivez l'authentification native, et permettent à WIF de gérer l'authentification.  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  Ajoutez les entrées de configuration connexes par Windows Foundation IDENTITY suivantes et vérifiez l'URL de cette votre application ASP.NET et la correspondance de numéro de port les valeurs dans l'entrée de **\<audienceUris\>** , l'attribut de **domaine** de l'élément de **\<wsFederation\>** , et l'attribut de **réponse** de l'élément de **\<wsFederation\>** .  Assurez\-vous également que la valeur **expéditeur** ajuste votre URL de \(STS\) de service d'émission de jeton de sécurité.  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5.  Ajoutez la référence à l'assembly d' [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) .  
  
6.  Compilez la solution pour vous assurer qu'il existe des erreurs.  
  
## Étape 3 \(testez votre solution  
 Dans cette étape vous allez tester votre application Web ASP.NET MVC configurée pour l'authentification basée revendication\-.  Pour exécuter le test de base vous ajouterez du code simple qui affiche des revendications dans le jeton émise par le service d'émission de jeton de sécurité \(STS\).  
  
#### Pour tester votre application ASP.NET MVC pour l'authentification basée revendication\-  
  
1.  Dans **Explorateur de solutions**, développez le dossier de **Contrôleurs** et ouvrez *le fichier de HomeController.cs* dans l'éditeur.  Ajoutez le code suivant à la méthode **Index** :  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
  
    ```  
  
2.  Dans **Explorateur de solutions** développez **Affichages** puis les dossiers **Accueil** et ouvrez *le fichier d'Index.cshtml* dans l'éditeur.  Supprimez son contenu et ajoutez le balisage suivant :  
  
    ```html  
  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
  
    ```  
  
3.  Exécutez la solution en appuyant sur la touche de **F5** .  
  
4.  Vous devez être présenté avec la page qui affiche les revendications dans le jeton qui a été fournie à vous de service d'émission de jeton de sécurité.  
  
## Élément connexe  
  
-   [Comment : générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)