---
title: "Comment&#160;: utiliser un validateur de nom d&#39;utilisateur et de mot de passe personnalis&#233; | Microsoft Docs"
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
  - "WCF, nom d'utilisateur et mot de passe"
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: utiliser un validateur de nom d&#39;utilisateur et de mot de passe personnalis&#233;
Par défaut, lorsqu'un nom d'utilisateur et un mot de passe sont utilisés pour l'authentification, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise Windows pour valider le nom d'utilisateur et le mot de passe.Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autorise l'utilisation de schémas d'authentification par nom d'utilisateur et mot de passe personnalisés, également connus sous le nom de *validateurs*.Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez\-la.  
  
 Pour obtenir un exemple d'application, consultez [Validateur de nom d'utilisateur et de mot de passe](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1.  Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur\/mot de passe à partir d'une base de données.  
  
     Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1.  Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP\(S\)  
  
     Lors de l'utilisation de la sécurité de message, ajoutez une des liaisons fournies par le système, telles que [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui prend en charge la sécurité de message et le type d'information d'identification `UserName`.  
  
     Lorsque vous utilisez la sécurité au niveau du transport sur HTTP\(S\), ajoutez soit [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), soit [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) et un [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui utilise HTTP\(S\) et le schéma d'authentification `Basic`.  
  
    > [!NOTE]
    >  Lors de l'utilisation du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou une version ultérieure, vous pouvez utiliser un validateur personnalisé de mot de passe et de nom d'utilisateur avec la sécurité de transport et de message.Avec [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], seul un validateur personnalisé de mot de passe et de nom d'utilisateur peut être utilisé avec la sécurité de message.  
  
    > [!TIP]
    >  Pour plus d'informations sur l'utilisation de \<netTcpBinding\> dans ce contexte, consultez [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md).  
  
    1.  Dans le fichier de configuration, sous l'élément [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md), ajoutez un élément [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md).  
  
    2.  Ajoutez un élément [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) à la section des liaisons.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'un élément de liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Affectez à l'attribut `mode` de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) les valeurs `Message`, `Transport`, `or``TransportWithMessageCredential`.  
  
    4.  Définissez l'attribut `clientCredentialType` de [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Lors de l'utilisation de la sécurité de message, attribuez à l'attribut `clientCredentialType` de [\<message\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) la valeur `UserName`.  
  
         Si vous utilisez la sécurité au niveau du transport sur HTTP\(S\), affectez à l'attribut `clientCredentialType` de [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) la valeur `Basic`.  
  
        > [!NOTE]
        >  Lorsqu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé dans IIS \(Internet Information Services\) à l'aide de la sécurité au niveau du transport et que la propriété <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> a la valeur <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>, le schéma d'authentification personnalisé utilise un sous\-ensemble de l'authentification Windows.Cela est dû au fait que dans ce scénario, IIS effectue une authentification Windows avant que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'appelle l'authentificateur personnalisé.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'un élément de liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : spécifier une liaison de service dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     L'exemple suivant présente le code de configuration de la liaison.  
  
    ```  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur\/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.  
  
    1.  Ajoutez un élément [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) en tant qu'enfant de l'élément [\<comportements\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
    2.  Ajoutez un [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à l'élément [\<comportements\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
    3.  Ajoutez un élément [\<comportement\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md), puis affectez à l'attribut `name` une valeur appropriée.  
  
    4.  Ajoutez un [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à l'élément [\<comportement\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md).  
  
    5.  Ajoutez un [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) au [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Affectez la valeur`Custom` à `userNamePasswordValidationMode`.  
  
        > [!IMPORTANT]
        >  Si la valeur `userNamePasswordValidationMode` n'est pas définie, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'authentification Windows au lieu du validateur de nom d'utilisateur et de mot de passe personnalisé.  
  
    7.  Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.  
  
     L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.  
  
    ```  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## Exemple  
 L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé.N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur\/mot de passe à partir d'une base de données.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## Voir aussi  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>   
 [Comment : utiliser le fournisseur d'appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)   
 [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)