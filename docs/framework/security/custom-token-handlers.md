---
title: "Gestionnaires de jetons personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Gestionnaires de jetons personnalis&#233;
Cette rubrique traite des gestionnaires de jetons dans WIF et comment ils sont utilisés pour traiter les jetons.  La rubrique couvre également ce qui est nécessaire pour créer les gestionnaires de jetons personnalisés pour les types de jetons qui ne sont pas pris en charge par défaut dans WIF.  
  
## Introduction aux gestionnaires de jetons dans WIF  
 WIF s'appuie sur des gestionnaires de jetons de sécurité pour créer, lire, écrire, et valide les marqueurs pour une application ou un service d'émission de jeton de sécurité \(STS\) de définition de données \(RP\) partie de confiance.  Les gestionnaires de jetons sont des points d'extensibilité d'ajouter un gestionnaire de jetons personnalisé dans le pipeline de WIF, ou pour personnaliser la façon dont un gestionnaire de jetons existant gère les jetons.  WIF fournit neuf gestionnaires de jetons de sécurité intégrés qui peuvent être modifiés ou entièrement remplacés pour modifier la fonctionnalité selon vos besoins.  
  
## Gestionnaires de jetons de sécurité intégrés dans WIF  
 WIF 4,5 inclut nouveau classes de gestionnaire de jetons de sécurité qui dérivent de la classe de base abstraite <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## Ajouter un gestionnaire de jetons personnalisé  
 Certains types de jetons, tels que le simples \(JWT\) de jetons \(SWT\) de site Web et de site Web JSON n'ont pas les gestionnaires de jetons prédéfinis fournis par WIF.  Pour ces types de jetons et d'autres qui n'ont pas de gestionnaire intégré, vous devez exécuter les étapes suivantes pour créer un gestionnaire de jetons personnalisé.  
  
#### Ajouter un gestionnaire de jetons personnalisé  
  
1.  Créez une classe qui dérive d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.  
  
2.  Substituez les méthodes suivantes et fournissez votre propre implémentation :  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  Ajoutez une référence au nouveau gestionnaire de jetons personnalisé dans *le fichier Web.config ou* l'App.configfile *,* dans la section de **\<system.identityModel\>** qui s'applique à WIF.  Par exemple, le balisage de configuration spécifient un nouveau gestionnaire de jetons nommé **MyCustomTokenHandler** qui se trouve dans l'espace de noms de **CustomToken** .  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     Notez que si vous fournissez votre propre gestionnaire de jetons pour gérer un type de jeton qui a déjà un gestionnaire de jetons prédéfinis, vous devez ajouter un élément de **\<remove\>** pour supprimer le gestionnaire par défaut et utiliser votre gestionnaire personnalisé à la place.  Par exemple, le paramètre suivant remplace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> par défaut par le gestionnaire de jetons personnalisé :  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type=”System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789”>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```