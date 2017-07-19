---
title: "Comment&#160;: utiliser le fournisseur d&#39;appartenances ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF et ASP.NET"
  - "WCF, autorisation"
  - "WCF, sécurité"
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Comment&#160;: utiliser le fournisseur d&#39;appartenances ASP.NET
Le fournisseur d'appartenances [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est une fonctionnalité qui permet aux développeurs [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de créer des sites Web permettant aux utilisateurs de créer des combinaisons uniques de nom d'utilisateur et de mot de passe.Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui\-ci et à ses services.Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.Au lieu de cela, l'utilisateur qui fournit ses informations d'identification \(combinaison nom d'utilisateur\/mot de passe\) peut utiliser le site et ses services.  
  
 Pour obtenir un exemple d'application, consultez [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).Pour plus d'informations sur l'utilisation de la fonctionnalité de fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 La fonctionnalité d'appartenance requiert l'utilisation d'une base de données SQL Server pour stocker les informations utilisateur.Elle inclut également des méthodes qui consistent à poser une question aux utilisateurs qui ont oublié leur mot de passe.  
  
 Les développeurs [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent tirer parti de ces fonctionnalités à des fins de sécurité.En cas d'intégration dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les utilisateurs doivent fournir une combinaison nom d'utilisateur\/mot de passe à l'application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Pour transférer les données au service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], utilisez une liaison qui prend en charge les informations d'identification nom d'utilisateur\/mot de passe, telle que <xref:System.ServiceModel.WSHttpBinding> \(dans la configuration, [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)\) et affectez `UserName` au type d'informations d'identification du client.Sur le service, la sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] authentifie l'utilisateur en fonction du nom et du mot de passe, et assigne également le rôle spécifié par le rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne fournit pas de méthode visant à remplir la base de données avec les combinaisons nom d'utilisateur\/mot de passe ou autres informations utilisateur.  
  
### Pour configurer le fournisseur d'appartenances  
  
1.  Dans le fichier Web.config, sous l'élément \<`system.web`\>, créez un élément \<`membership`\>.  
  
2.  Sous l'élément `<membership>`, créez un élément `<providers>`.  
  
3.  Ajoutez un élément `<clear />` en tant qu'enfant de l'élément \<`providers`\> afin de vider la collection de fournisseurs.  
  
4.  Sous l'élément `<clear />`, créez un élément \<`add`\> avec les attributs suivants définis aux valeurs appropriées : `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail` et `passwordFormat`.L'attribut `name` est utilisé ultérieurement comme valeur dans le fichier de configuration.L'exemple suivant lui affecte la valeur `SqlMembershipProvider`.  
  
     L'exemple suivant présente la section de configuration.  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### Pour configurer la sécurité de service afin d'accepter la combinaison nom d'utilisateur\/mot de passe  
  
1.  Dans le fichier de configuration, sous l'élément [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md), ajoutez un élément [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md).  
  
2.  Ajoutez un élément [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) à la section des liaisons.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'un élément de liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Affectez à l'attribut `mode` de l'élément `<security>` la valeur `Message`.  
  
4.  Affectez `UserName` à l'attribut `clientCredentialType` de l'élément \<`message`\>.Cela spécifie qu'une paire nom d'utilisateur\/mot de passe sera utilisée comme information d'identification du client.  
  
     L'exemple suivant présente le code de configuration de la liaison.  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### Pour configurer un service permettant d'utiliser le fournisseur d'appartenances  
  
1.  Ajoutez un [\<comportements\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) en tant qu'enfant de l'élément `<system.serviceModel>`.  
  
2.  Ajoutez une section [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l'élément \<`behaviors`\>.  
  
3.  Ajoutez un [\<comportement\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et affectez une valeur appropriée à l'attribut `name`.  
  
4.  Ajoutez un élément [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à l'élément \<`behavior`\>.  
  
5.  Ajoutez un [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à l'élément `<serviceCredentials>`.  
  
6.  Affectez `MembershipProvider` à l'attribut `userNamePasswordValidationMode`.  
  
    > [!IMPORTANT]
    >  Si la valeur `userNamePasswordValidationMode` n'est pas définie, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'authentification Windows au lieu du fournisseur d'appartenances [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
7.  Affectez à l'attribut `membershipProviderName` le nom du fournisseur \(spécifié lors de l'ajout du fournisseur dans la première procédure de cette rubrique\).L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
  
    ```  
  
## Exemple  
 Le code suivant montre la configuration d'un service qui utilise la fonctionnalité d'appartenance ASP.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## Voir aussi  
 [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)