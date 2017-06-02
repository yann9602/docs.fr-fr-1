---
title: "Recommandations sur la migration d’une application g&#233;n&#233;r&#233;e &#224; l’aide de WIF&#160;3.5 &#224; WIF&#160;4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# Recommandations sur la migration d’une application g&#233;n&#233;r&#233;e &#224; l’aide de WIF&#160;3.5 &#224; WIF&#160;4.5
## S'applique à  
  
-   Base \(WIF\) 3,5 et 4,5 d'identité Microsoft® Windows®.  
  
## Vue d'ensemble  
 Windows Identity Foundation \(WIF\) a été initialement publié dans le calendrier SP1 .NET 3,5.  Cette version de WIF désignés par WIF 3,5.  Elle a été libérée comme runtime et SDK distincts, qui signifiait que chaque ordinateur sur lequel une application WIF\- activée a fonctionné devait disposer des produits d'exécution de WIF et les développeurs ont dû télécharger et installer le WIF Kit de développement logiciel pour obtenir les modèles et l'outillage Visual Studio qui a activé le développement d'applications WIF\- activées.  Depuis .NET 4,5, WIF a été entièrement intégré dans le .NET Framework.  Un runtime distinct n'est plus nécessaire et l'outillage de WIF peut être installé dans Visual Studio 2012 à l'aide du Gestionnaire d'extensions Visual Studio.  Cette version de WIF désignés par WIF 4,5.  
  
 L'intégration de WIF dans le .NET a nécessité plusieurs modifications de la surface d'API de WIF.  WIF 4,5 inclut de nouveaux espaces de noms, des modifications aux éléments de configuration, puis nouvel outils pour Visual Studio.  Cette rubrique fournit des instructions que vous pouvez utiliser pour vous aider à migrer les applications construites à WIF 3,5 à WIF 4,5. Il peut exister des scénarios dans lesquels vous devez exécuter les applications héritées générées à l'aide de WIF 3,5 sur les ordinateurs exécutant des fenêtres en cours de exécution 8 ou Windows Server 2012.  Cette rubrique fournit également l'aide concernant l'activation WIF 3,5 pour ces systèmes d'exploitation.  
  
## Modifications requises pour WIF 4,5  
 Cette section décrit les modifications nécessaires pour migrer une application de WIF 3,5 à WIF 4,5.  
  
### Modifications d'assembly et l'espace de noms  
 Dans WIF 3,5, toutes les classes de WIF étaient contenues dans l'assembly d'`Microsoft.IdentityModel` \(microsoft.identitymicrosoft.identitymodel.dll\).  Dans WIF 4,5, les classes de WIF ont été fractionnées entre les assemblys suivants : `mscorlib` \(mscorlib.dll\), `System.IdentityModel` \(System.IdentityModel.dll\), `System.IdentityModel.Services` \(System.IdentityModel.Services.dll\), et `System.ServiceModel` \(System.ServiceModel.dll\).  
  
 Toutes de WIF 3,5 les classes étaient contenues dans l'un des espaces de noms `Microsoft.IdentityModel` ; par exemple, `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`, etc.  Dans WIF 4,5, les classes de WIF sont maintenant étalées [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) entre les espaces de noms, l'espace de noms <xref:System.Security.Claims?displayProperty=fullName>, et l'espace de noms <xref:System.ServiceModel.Security?displayProperty=fullName>.  En plus de cette réorganisation, d'un certain WIF 3,5 ont été supprimées dans WIF 4,5.  
  
 Le tableau suivant affiche certaines des espaces de noms plus importants de WIF 4,5 et du genre de classes qu'ils contiennent.  Pour plus d'informations sur la façon dont le mappage d'espaces de noms entre WIF 3,5 et WIF 4,5 et sur les espaces de noms et des classes supprimés dans WIF 4,5, consultez [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|L'espace de noms WIF 4,5|Description|  
|------------------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=fullName>|Contient des classes qui représentent des transformations de cookie, les services d'émission de jeton de sécurité, et lecteurs spécialisés de dictionnaire XML.  Contient des classes des espaces de noms suivants de WIF 3,5 : `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, et `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=fullName>|Contient des classes qui représentent des revendications, des identités basées sur les revendications, des entités basées sur des revendications, et d'autres artefacts du modèle d'identité basés sur des revendications.  Contient des classes de l'espace de noms `Microsoft.IdentityModel.Claims`.|  
|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|Contient des classes qui représentent des jetons de sécurité, les gestionnaires de jetons de sécurité, et d'autres artefacts de jeton de sécurité.  Contient des classes des espaces de noms suivants de WIF 3,5 : `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, et `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=fullName>|Contient des classes utilisées dans les scénarios passifs \(WS\-Federation\).  Contient des classes de l'espace de noms `Microsoft.IdentityModel.Web`.|  
|<xref:System.ServiceModel.Security?displayProperty=fullName>|Les classes qui représentent les contrats WCF, les canaux, les hôtes de service et d'autres artefacts utilisés dans les scénarios actifs \(WS\-Trust\) sont maintenant dans cet espace de noms.  Dans WIF 3,5, ces classes étaient dans l'espace de noms `Microsoft.IdentityModel.Protocols.WSTrust`.|  
  
> [!IMPORTANT]
>  Espaces de noms `System.IdentityModel` suivants contiennent des classes qui implémentent le modèle d'identité basé sur revendications WCF : <xref:System.IdentityModel.Claims?displayProperty=fullName>, <xref:System.IdentityModel.Policy?displayProperty=fullName>, et <xref:System.IdentityModel.Selectors?displayProperty=fullName>.  Le modèle d'identité basé sur revendications WCF est remplacé par WIF.  Vous ne devez pas utiliser des classes dans ces trois espaces de noms en générant des solutions sur WIF.  
  
### Modifications en raison de l'intégration .NET  
 WIF est maintenant intégré dans le .NET Framework.  La plupart des classes Identity et d'entité .NET dérivent désormais d'<xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>.  Les résultats dans les modifications suivantes dans WIF 4,5 :  
  
-   Les classes de WIF qui représentent des revendications, les identités, et les entités existe maintenant dans l'espace de noms <xref:System.Security.Claims?displayProperty=fullName>.  
  
    > [!IMPORTANT]
    >  L'espace de noms <xref:System.IdentityModel.Claims?displayProperty=fullName> contient des classes qui représentent des artefacts du modèle d'identité basé sur revendications WCF.  Ces classes ont des noms identiques à des classes de WIF ; par exemple, `Claims`.  N'utilisez pas ces classes en générant des solutions sur WIF.  
  
-   les classes Identity et d'entité .NET dérivent désormais directement de <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> et <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>, qui représentent des identités basées sur les revendications et des entités.  Pour cette raison, les interfaces `IClaimsIdentity` WIF 3,5 et `IClaimsPrincipal` sont plus nécessaires et ne sont pas disponibles dans WIF 4,5.  
  
-   Les classes Identity et d'entité de Because.NET telles que <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> et l'<xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> dérivent désormais d'<xref:System.Security.Claims.ClaimsIdentity> et <xref:System.Security.Claims.ClaimsPrincipal>, elles ont l'élément de fonctionnalité des revendications.  Pour cette raison, d'identité de revendication\- détaillée et d'entité telles que `WindowsClaimsIdentity` et `WindowsClaimsPrincipal` qui étaient présentes dans WIF 3,5 sont plus nécessaires et n'existent dans WIF 4,5.  
  
### Autres modifications des fonctionnalités de WIF  
 Outre les modifications de l'espace de noms et les modifications en raison de l'intégration au .NET, les modifications générales suivantes à la fonctionnalité de WIF se produisent dans WIF 4,5.  
  
-   La classe `Microsoft.IdentityModel.ExceptionMapper`, qui a fourni une fonctionnalité qui vous permettait de mapper des exceptions en erreurs spécifiques SOAP, est supprimée.  
  
-   La surface d'exception a été largement réduite.  
  
-   Plusieurs des classes que le protocole défini ou les constantes spécifiques de WS\-\* ont été supprimées ; par exemple, la classe `Microsoft.IdentityModel.WSAddressing10Constants`, ayant défini des constantes liées à WS\-Addressing 1,0.  
  
-   Les revendications au service d'émission de jeton Windows \(c2wts\) et à ses classes associées dans l'espace de noms `Microsoft.IdentityModel.WindowsTokenService` sont supprimées.  
  
### Modifications de configuration de WIF  
 Plusieurs des modifications du fichier de configuration ont été provoqués par des mises à jour de l'espace de noms dans WIF 4,5. Par exemple, considérez l'entrée suivante de WIF 3,5 dans la section d'`<httpModules>` pour ajouter le gestionnaire d'authentification de WS\-Federation à une application :  
  
```  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Cette entrée a été mise à jour dans WIF 4,5 pour inclure les nouveaux espaces de noms et version d'assembly :  
  
```  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 La liste suivante énumère les principales modifications au fichier de configuration pour WIF 4,5.  
  
-   La section relative aux `<microsoft.identityModel>` est maintenant la section [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md).  
  
-   L'élément `<service>` est désormais l'élément [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md).  
  
-   Une nouvelle section, [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), a été ajoutée pour spécifier des paramètres ce comportement de contrôle dans les scénarios passifs \(WS\-Federation\).  
  
-   L'élément [\<federationConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) et ses éléments enfants ont été déplacés de l'élément `<service>` dans WIF 3,5 au nouvel élément `<system.identityModel.services>`.  
  
-   Plusieurs éléments qui peuvent être spécifiés au niveau service directement sous l'élément `<service>` dans WIF 3,5 ont été autorisée à la spécification sous l'élément [\<securityTokenHandlerConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md). \(Ils peuvent être spécifiés sous l'élément [\<identityConfiguration\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) dans WIF 4,5 pour la compatibilité descendante.\)  
  
 Pour une liste complète des éléments de configuration WIF 4,5, consultez [Schéma de configuration de WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### Modifications d'outils de Visual Studio  
 Le WIF 3,5 SDK a envoyé un utilitaire autonome de fédération, FedUtil.exe \(FedUtil\), que vous pouvez utiliser pour externaliser la gestion des identités dans les applications WIF\- activées pour un service d'émission de jeton de sécurité \(STS\).  Cet outil dispose des paramètres de WIF au fichier de configuration de l'application pour permettre à l'application d'accéder aux jetons de sécurité de l'un ou plusieurs STSs, il a été apprêté dans Visual Studio via le bouton **Ajoutez la référence de service de STS**.  FedUtil n'est fourni pas avec WIF 4,5. À la place, WIF 4,5 prend en charge une nouvelle extension Visual Studio nommée l'identité et l'outil Access pour Visual Studio 2012 que vous pouvez utiliser pour modifier le fichier de configuration de votre application avec les paramètres de WIF requis pour externaliser la gestion des identités à STS.  L'identité et l'outil Access implémente également STS appelé Local STS que vous pouvez utiliser pour tester vos applications WIF\- activées.  Dans de nombreux cas, cette fonctionnalité obvie à la nécessité de générer STSs personnalisé qui étaient souvent nécessaire dans WIF 3,5 pour tester les solutions en cours de développement.  Pour cette raison, les modèles de STS ne sont plus pris en charge dans Visual Studio 2012 ; Toutefois, les classes qui prennent en charge le développement de STSs sont toujours disponibles dans WIF 4,5.  
  
 Vous pouvez configurer l'identité et l'outil Access des extensions et mettez à jour le gestionnaire dans Visual Studio ou vous pouvez télécharger à la page suivante sur la Galerie de code : [Identité outils et Access pour Visual Studio 2012 sur la Galerie de code](http://go.microsoft.com/fwlink/?LinkID=245849).  Les modifications d'outils de Visual Studio sont décrits dans la liste suivante :  
  
-   La fonctionnalité de référence de service de STS d'addition est supprimée.  Le remplacement est l'outil d'identité et Access.  
  
-   Les modèles Visual Studio STS sont supprimés.  Vous pouvez utiliser STS local disponibles via l'identité et l'outil Access pour tester les solutions Compteur que vous développez avec WIF.  La configuration locale de STS peut être modifiée pour personnaliser les revendications qu'il sert.  
  
-   L'utilitaire autonome de fédération \(FedUtil\) est pas disponible dans WIF 4,5. Vous pouvez utiliser l'identité et l'outil Access pour modifier les fichiers de configuration pour externaliser la gestion des identités à STS.  
  
 Pour plus d'informations sur l'identité et l'outil Access, consultez [Outil Identité et accès pour Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### Scénarios passifs \(WS\-Federation\) :  
  
-   Les classes qui prennent en charge les scénarios passifs ont été déplacées vers l'espace de noms <xref:System.IdentityModel.Services?displayProperty=fullName>.  Dans WIF 3,5 ces classes étaient dans l'espace de noms `Microsoft.IdentityModel.Web`.  
  
-   Les classes de l'espace de noms `Microsoft.IdentityModel.Web.Configuration` ont été déplacées vers <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>.  Ces classes représentent des objets spécifiques à la configuration dans les scénarios passifs.  
  
-   `FederatedPasssiveSignInControl` n'est plus pris en charge ; toutes les classes dans l'espace de noms `Microsoft.IdentityModel.Web.Controls` ont été supprimées de WIF 4,5.  
  
-   La fonctionnalité de signe \- de module d'authentification de WS\-Federation \(<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>\) est différente WIF 3,5.  Pour plus d'informations sur la manière dont le signe \- fonctionne dans WIF 4,5, consultez la rubrique de classe <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>.  
  
### Scénarios \(WCF\/WS\-Trust\) actifs :  
  
-   L'espace de noms `Microsoft.IdentityModel.Protocols.WSTrust` a été fractionné principalement en deux espaces de noms dans WIF 4,5. Les classes qui représentent les artefacts qui sont spécifiques au protocole de WS\-Trust sont maintenant dans <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>.  Cela inclut les classes comme <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>.  Les classes qui représentent les contrats de service, les canaux, les hôtes de service et d'autres artefacts impliquées en utilisant WS\-Trust dans les applications WCF ont été déplacées vers <xref:System.ServiceModel.Security?displayProperty=fullName>; par exemple, l'interface <xref:System.ServiceModel.Security.IWSTrust13AsyncContract>.  
  
-   La configuration d'une application WCF d'utiliser WIF a été considérablement simplifiées.  Auparavant `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` devait être ajouté en tant qu'extension de comportement et cette fonction a été utilisée pour coincer WIF dans le comportement du service en spécifiant un élément `<federatedServiceHostConfiguration>`.  WIF 4,5 plus étroitement a été intégré à WCF.  Maintenant vous activez WIF sur un service WCF en spécifiant l'attribut `useIdentityConfiguration` sur `<system.serviceModel>`\/`<behaviors>`\/`<serviceBehaviors>`\/élément`<serviceCredentials>` comme dans le code XML suivant :  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   Dans WIF 4,5 le certificat de service utilisé par un service actif \(WCF\) doit être spécifié sur l'hôte de service.  Dans la configuration, vous pouvez le faire via `<system.serviceModel>`\/`<behaviors>`\/`<serviceBehaviors>`\/`<serviceCredentials>`\/élément`<serviceCertificate>` comme indiqué dans l'exemple précédent.  Dans WIF 3,5 le certificat de service peut être spécifié via l'élément enfant d'`<serviceCertificate>` de l'élément `<service>` de WIF.  Cette fonctionnalité n'existe pas dans WIF 4,5 ; spécifiez l'élément `<serviceCertificate>` sous l'élément `<serviceCredentials>` à la place.  
  
-   Les classes utilisées pour coincer WIF 3,5 dans WCF n'existent plus.  Cela inclut les classes suivantes dans l'espace de noms `Microsoft.IdentityModel.Tokens` : `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, `IdentityModelServiceAuthorizationManager`, ainsi que la classe `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement`.  
  
## Activation de WIF 3,5 dans Windows 8  
 Comme WIF 4,5 fait partie du .NET 4,5, il est automatiquement activé sur des ordinateurs exécutant Windows 8 et Windows Server 2012 et les applications qui sont générés à l'WIF 4,5 s'exécuteront sous Windows 8 ou Windows Server 2012 par défaut.  Toutefois, vous devrez peut\-être exécuter les applications générées à WIF 3,5 sur un ordinateur qui exécute Windows 8 ou Windows Server 2012.  Dans ce cas, vous devez activer WIF 3,5 sur l'ordinateur cible.  Dans Windows en cours de exécution 8 d'un ordinateur, vous pouvez utiliser l'outil de la Gestion et maintenance des images de déploiement \(DISM\).  Sur un ordinateur qui exécute Windows Server 2012, vous pouvez utiliser l'outil de DISM ou l'applet de commande Windows PowerShell `Add-WindowsFeature`.  Dans les deux cas, les commandes appropriées peuvent être appelées sur la ligne de commande ou depuis l'environnement Windows PowerShell.  
  
 Les commandes suivantes montrent comment utiliser l'outil de DISM de la ligne de commande ou depuis l'environnement Windows PowerShell.  Par défaut, le module de DISM PowerShell est inclus dans Windows 8 et Windows Server 2012 et ne doit pas être importé.  Pour plus d'informations sur l'utilisation DISM avec Windows PowerShell, voir [Utilisation DISM dans Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=254419).  
  
 Pour activer WIF 3,5 à DISM :  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 Pour désactiver WIF 3,5 à DISM :  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Pour vérifier si des fonctionnalités est activé ou désactivé à DISM :  
  
```  
dism /online /get-features  
```  
  
 Sinon, sur les ordinateurs Windows Server 2012, vous pouvez activer WIF 3,5 en utilisant l'applet de commande Windows PowerShell `Add-WindowsFeature`.  Pour faire de la ligne de commande, vous pouvez sélectionner la commande suivante :  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 De l'intérieur de l'environnement Windows PowerShell, vous pouvez sélectionner la commande directement :  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Comme nombreuses classes dans WIF 3,5 et WIF 4,5 partages les mêmes noms, lorsque vous utilisez WIF 3,5 et WIF 4,5 ensemble, soient thread\-safe aux noms de classe qualifiés complets de utilisation ou aux alias d'espace de noms d'utilisation distinguer les classes dans WIF 3,5 et WIF 4,5.  
  
## Voir aussi  
 [Schéma de configuration de WIF](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)   
 [Mappage des espaces de noms entre WIF 3.5 et WIF 4.5](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)   
 [Nouveautés de Windows Identity Foundation 4.5](../../../docs/framework/security/whats-new-in-wif.md)   
 [Outil Identité et accès pour Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md)