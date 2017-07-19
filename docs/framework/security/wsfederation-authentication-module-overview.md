---
title: "Vue d’ensemble du module d’authentification WSFederation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02c4d5e8-f0a7-49ee-9cf5-3647578510ad
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# Vue d’ensemble du module d’authentification WSFederation
Windows Identity Foundation \(WIF\) offre une prise en charge de l'authentification fédérée dans les applications ASP.NET via le module WS\- fédéré d'authentification \(WS\-FAM\).  Cette rubrique vous aidera à comprendre comment l'authentification fédérée fonctionne et son utilisation.  
  
### Vue d'ensemble de l'authentification fédérée  
 L'authentification fédérée permet à un service d'émission de jeton de sécurité \(STS\) dans un domaine d'approbation pour fournir des informations d'authentification à STS dans un autre domaine d'approbation lorsqu'une relation d'approbation entre les deux domaines.  Un exemple de ceci est indiqué dans l'illustration suivante.  
  
 ![Scénario d'authentification par fédération](../../../docs/framework/security/media/federatedauthentication.png "FederatedAuthentication")  
  
1.  Un client dans le domaine d'approbation de Fabrikam envoie une demande à une application de \(RP\) de partie de confiance du domaine d'approbation Contoso.  
  
2.  Le RP redirige le client vers STS dans le domaine d'approbation Contoso.  Ce STS n'a pas connaissance du client.  
  
3.  Le STS Contoso redirige le client vers STS dans le domaine d'approbation de Fabrikam, auquel le domaine d'approbation Contoso a une relation d'approbation.  
  
4.  Le Fabrikam STS vérifie l'identité du client et fournit un jeton de sécurité au STS Contoso.  
  
5.  Le STS Contoso utilise ce jeton de Fabrikam pour créer son propre jeton qui peut être utilisé par le RP et l'envoie au RP.  
  
6.  Le RP récupère les revendications du client du jeton de sécurité et prend une décision d'autorisation.  
  
### Utilisation du module fédéré d'authentification avec ASP.NET  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WS\-FAM\) est un module HTTP qui vous permet d'ajouter l'authentification fédérée à une application d'[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  L'authentification fédérée laisse la logique d'authentification être gérée par STS et vous permet de vous concentrer sur la logique métier d'écriture.  
  
 Vous configurez le WS\-FAM pour spécifier STS auquel les requêtes non authentifiées doivent être redirigée.  WIF vous permet d'authentifier un utilisateur de deux façons :  
  
1.  Le passif redirection : Lorsque les données d'un utilisateur non authentifié pour accéder à une ressource protégée, et vous voulez rediriger simplement à STS sans nécessiter une page de connexion, alors c'est une bonne approche.  STS vérifie l'identité de l'utilisateur, et émet un jeton de sécurité qui contient les revendications appropriées pour cet utilisateur.  Cette option requiert le WS\-FAM à ajouter dans le pipeline de modules HTTP.  Vous pouvez utiliser l'identité et l'outil Access pour Visual Studio 2012 pour modifier le fichier de configuration de votre application pour utiliser le WS\-FAM et vous fédérer avec STS.  Pour plus d'informations, consultez [Outil Identité et accès pour Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
2.  Vous pouvez appeler la méthode <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignIn%2A?displayProperty=fullName> ou la méthode <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectToIdentityProvider%2A> du code\-behind d'une page de connexion dans votre application de RP.  
  
 Dans le mode passif redirection, toutes les communications est effectué via la réponse\/redirige client \(généralement un navigateur\).  Vous pouvez ajouter le WS\-FAM au pipeline HTTP de votre application, où il regarde pour les requêtes utilisateur non authentifiées et redirige les utilisateurs à STS que vous spécifiez.  
  
 Le WS\-FAM déclenche également plusieurs événements qui vous permettent de personnaliser ses fonctionnalités dans une application d'[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
### Fonctionnement du WS\-FAM fonctionne  
 Le WS\-FAM est implémenté dans la classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.  En général, vous ajoutez le WS\-FAM au pipeline HTTP de votre application d'[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] RP.  Lorsque les données d'un utilisateur non authentifié pour accéder à une ressource protégée, le RP retourne une réponse HTTP refusée « 401 par autorisations ».  Le WS\-FAM désactive cette réponse au lieu de permettre au client pour recevoir, il redirige l'utilisateur vers STS spécifié.  STS émet un jeton de sécurité, que le WS\-FAM arrête à nouveau.  Le WS\-FAM utilise ce jeton pour créer une instance d'<xref:System.Security.Claims.ClaimsPrincipal> pour l'utilisateur authentifié, qui permet aux mécanismes d'autorisation d'[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] classique pour fonctionner.  
  
 Comme HTTP est sans état, nous avons besoin d'un moyen d'éviter de répéter ce processus entier chaque fois que l'utilisateur essaie d'accéder à une autre ressource protégée.  C'est là entrée <xref:System.IdentityModel.Services.SessionAuthenticationModule>.  Lorsque STS émet un jeton de sécurité de l'utilisateur, <xref:System.IdentityModel.Services.SessionAuthenticationModule> crée également un jeton de sécurité de session de l'utilisateur et le place dans un cookie.  Pour les demandes suivantes, <xref:System.IdentityModel.Services.SessionAuthenticationModule> intercepte ce cookie et l'utilise pour régénérer <xref:System.Security.Claims.ClaimsPrincipal>de l'utilisateur.  
  
 Le diagramme suivant présente le flux de données global du passif redirigent le cas.  La demande est automatiquement redirigée via STS de définir les informations d'identification sans page de connexion :  
  
 ![Diagramme de minutage pour la connexion avec redirection passive](../../../docs/framework/security/media/signinusingpassiveredirect.png "SignInUsingPassiveRedirect")  
  
 Le diagramme suivant affiche plus de détails sur ce qui se produit lorsque l'utilisateur a authentifié à STS et les jetons de sécurité sont traités par <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>:  
  
 ![Minutage pour le traitement du jeton avec redirection passive](../../../docs/framework/security/media/signinusingpassiveredirect-tokenprocessing.png "SignInUsingPassiveRedirect\_TokenProcessing")  
  
 Le diagramme suivant affiche plus de détails sur ce qui se produit lorsque les jetons de sécurité de l'utilisateur ont été sérialisés dans des cookies et sont désactivés par <xref:System.IdentityModel.Services.SessionAuthenticationModule>:  
  
 ![Diagramme de minutage SAM indiquant les contrôles d'utilisation de connexion](../../../docs/framework/security/media/signinusingconrols-sam.png "SignInUsingConrols\_SAM")  
  
### Événements  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>, <xref:System.IdentityModel.Services.SessionAuthenticationModule>, et leur classe parente, <xref:System.IdentityModel.Services.HttpModuleBase>, événements d'augmenter à différentes étapes de traitement des requêtes HTTP.  Vous pouvez gérer ces événements dans le fichier `global.asax` de votre application d'[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
-   L'infrastructure ASP.NET appelle la méthode <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> du module pour initialiser le module.  
  
-   L'événement <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated?displayProperty=fullName> est déclenché lorsque l'infrastructure ASP.NET appelle la méthode <xref:System.IdentityModel.Services.HttpModuleBase.Init%2A> pour la première fois sur un des modules de l'utilisation qui dérivent d'<xref:System.IdentityModel.Services.HttpModuleBase>.  Cette méthode accède à la propriété <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName> statique, qui provoque la configuration à charger du fichier Web.config.  Cet événement n'est déclenché pour la première fois cette propriété est accessible.  L'objet <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> qui est initialisé de la configuration est accessible via la propriété <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=fullName> dans un gestionnaire d'événements.  Vous pouvez utiliser cet événement pour modifier la configuration avant d'être appliquée à tous les modules.  Vous pouvez ajouter un gestionnaire de cet événement dans la méthode d'Application\_Start :  
  
    ```  
    void Application_Start(object sender, EventArgs e)  
    {  
        FederatedAuthentication.FederationConfigurationCreated += new EventHandler<FederationConfigurationCreatedEventArgs>(FederatedAuthentication_FederationConfigurationCreated);  
    }  
    ```  
  
     Chaque module substitue <xref:System.IdentityModel.Services.HttpModuleBase.InitializeModule%2A?displayProperty=fullName> et <xref:System.IdentityModel.Services.HttpModuleBase.InitializePropertiesFromConfiguration%2A?displayProperty=fullName> résument les méthodes.  Le premier de ces méthodes ajoute des gestionnaires pour les événements de pipeline ASP.NET présentent un intérêt au module.  Dans la plupart des cas l'implémentation par défaut du module action.  Le second de ces méthodes initialise les propriétés du module de sa propriété <xref:System.IdentityModel.Services.HttpModuleBase.FederationConfiguration%2A?displayProperty=fullName>. \(C'est une copie de la configuration qui a été chargé précédemment.\) Vous devrez peut\-être substituer cette seconde méthode si vous souhaitez prendre en charge l'initialisation de nouvelles propriétés de configuration des classes que vous dérivez de <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou de <xref:System.IdentityModel.Services.SessionAuthenticationModule>.  Dans ce cas vous devez également dériver des objets appropriés de configuration pour prendre en charge les propriétés ajoutées de configuration ; par exemple, d'<xref:System.IdentityModel.Configuration.IdentityConfiguration>, en <xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>, ou d'<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>.  
  
-   Le WS\-FAM déclenche l'événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenReceived> lorsqu'il libère un jeton de sécurité qui a été publié par STS.  
  
-   Le WS\-FAM déclenche l'événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SecurityTokenValidated> après qu'il a validé le jeton.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> déclenche l'événement <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenCreated> lorsqu'il crée un jeton de sécurité de session de l'utilisateur.  
  
-   <xref:System.IdentityModel.Services.SessionAuthenticationModule> déclenche l'événement <xref:System.IdentityModel.Services.SessionAuthenticationModule.SessionSecurityTokenReceived> lorsqu'il intercepte les demandes suivantes avec le cookie qui contient le jeton de sécurité de session.  
  
-   Avant que le WS\-FAM redirige l'utilisateur vers l'émetteur, il déclenche l'événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.  Connectez\-vous de WS\-Federation est disponible via la propriété <xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs.SignInRequestMessage%2A> d'<xref:System.IdentityModel.Services.RedirectingToIdentityProviderEventArgs> passé en cas.  Vous pouvez choisir de modifier la requête avant d'envoyer cela à l'émetteur.  
  
-   Le WS\-FAM déclenche l'événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SignedIn> lorsque le cookie est correctement écrit et l'utilisateur est archivé dans.  
  
-   Le WS\-FAM déclenche l'événement <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SigningOut> une fois par session lorsque la session est fermée vers le bas pour chaque utilisateur.  Il n'est pas déclenché si la session est fermée vers le bas côté client \(par exemple, en supprimant le cookie de session\).  Dans un environnement de SSO, l'IP\-STS peut inviter chaque RP pour signer, aussi.  Cela déclenchera également cet événement, avec <xref:System.IdentityModel.Services.SigningOutEventArgs.IsIPInitiated%2A> la valeur `true`.  
  
> [!NOTE]
>  Vous ne devez pas utiliser la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> pendant un événement déclenché par <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> ou <xref:System.IdentityModel.Services.SessionAuthenticationModule>.  Ceci car <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> est défini après la procédure d'authentification, tandis que les événements sont déclenchés pendant le processus d'authentification.  
  
### Configuration de l'authentification fédérée  
 Les WS\-FAM et SAM sont configurés dans l'élément [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md).  L'élément enfant [\<wsFederation\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md) configure les valeurs par défaut pour les propriétés de WS\-FAM ; telle que la propriété <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Issuer%2A> et la propriété <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.Realm%2A>. \(Ces valeurs peuvent être modifiées sur une base par demande en fournissant des gestionnaires pour certains événements de WS\-FAM ; par exemple, <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>.\) Le gestionnaire de cookie utilisé par SAM est configuré via l'élément enfant [\<cookieHandler\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md).  WIF fournit un gestionnaire par défaut de cookie implémenté dans la classe <xref:System.IdentityModel.Services.ChunkedCookieHandler> qui peut avoir sa taille du segment définie dans l'élément [\<chunkedCookieHandler\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md).  L'élément `<federationConfiguration>` référence <xref:System.IdentityModel.Configuration.IdentityConfiguration>, qui fournit la configuration d'autres composants de WIF utilisés dans l'application, par exemple <xref:System.Security.Claims.ClaimsAuthenticationManager> et <xref:System.Security.Claims.ClaimsAuthorizationManager>.  La configuration d'identité peut être marquée explicitement en spécifiant un élément nommé [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) dans l'attribut `identityConfigurationName` de l'élément `<federationConfiguration>`.  Si la configuration d'identité n'est pas référencée explicitement, la configuration par défaut d'identité sera utilisée.  
  
 XML suivant montre une configuration d'une application de \(RP\) de partie de confiance ASP.NET.  Les sections de configuration d'<xref:System.IdentityModel.Configuration.SystemIdentityModelSection> et <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> sont ajoutées sous l'élément `<configSections>`.  SAM et les WS\-FAM ajoutés aux modules HTTP sous `<system.webServer>`\/élément`<modules>`.  Enfin les composants de WIF sont configurés sous `<system.identityModel>`\/`<identityConfiguration>` et `<system.identityModel.services>`\/éléments`<federationConfiguration>`.  Cette configuration spécifie le gestionnaire chunked de cookie comme c'est le gestionnaire par défaut de cookie et il n'existe pas de type du gestionnaire de cookie spécifié dans l'élément `<cookieHandler>`.  
  
> [!WARNING]
>  Dans l'exemple suivant, l'attribut `requireHttps` de l'élément `<wsFederation>` et l'attribut `requireSsl` de l'élément `<cookieHandler>` sont `false`.  Cela présente une menace éventuelle pour la sécurité.  Dans la production, ces deux valeurs doivent être `true`défini.  
  
```  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  ...  
  
  <system.webServer>  
    <modules>  
      <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
    </modules>  
  </system.webServer>  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost:50969/" />  
      </audienceUris>  
      <certificateValidation certificateValidationMode="None" />  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
        <trustedIssuers>  
          <add thumbprint="9B74CB2F320F7AAFC156E1252270B1DC01EF40D0" name="LocalSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
    </identityConfiguration>  
  </system.identityModel>  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:15839/wsFederationSTS/Issue" realm="http://localhost:50969/" reply="http://localhost:50969/" requireHttps="false" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>   
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)