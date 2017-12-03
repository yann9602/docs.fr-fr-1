---
title: "Comment : utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1ec4dc2d7f066d79b2cf54c3d474b47e769b626c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Comment : utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé
Par défaut, lorsqu'un nom d'utilisateur et un mot de passe sont utilisés pour l'authentification, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise Windows pour valider le nom d'utilisateur et le mot de passe. Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autorise pour les schémas de l’authentification des nom et mot de passe d’utilisateur personnalisée, également appelé *validateurs*. Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez-la.  
  
 Pour un exemple d’application, consultez [validateur de mot de passe de nom d’utilisateur](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1.  Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production. Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.  
  
     Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé  
  
1.  Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP(S)  
  
     Lorsque vous utilisez la sécurité de message, ajoutez une des liaisons fournies par le système, tel qu’un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) prend en charge la sécurité de message et le `UserName` type des informations d’identification.  
  
     Lors de l’utilisation de sécurité au niveau du transport sur HTTP (S), ajoutez le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), un [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui utilise HTTP (S) et le `Basic` schéma d’authentification.  
  
    > [!NOTE]
    >  Lors de l'utilisation du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou une version ultérieure, vous pouvez utiliser un validateur personnalisé de mot de passe et de nom d'utilisateur avec la sécurité de transport et de message. Avec [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], seul un validateur personnalisé de mot de passe et de nom d'utilisateur peut être utilisé avec la sécurité de message.  
  
    > [!TIP]
    >  Pour plus d’informations sur l’utilisation de \<netTcpBinding > dans ce contexte, consultez [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  Dans le fichier de configuration, sous la [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajouter un [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.  
  
    2.  Ajouter un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) élément à la section des liaisons. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liaison d’élément, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Définir le `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) à `Message`, `Transport`, `or``TransportWithMessageCredential`.  
  
    4.  Définir le `clientCredentialType` attribut de la [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Lorsque vous utilisez la sécurité des messages, définir le `clientCredentialType` attribut de la [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) à `UserName`.  
  
         Sécurité au niveau du transport sur HTTP (S), définissez la `clientCredentialType` attribut de la [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) à `Basic`.  
  
        > [!NOTE]
        >  Lorsqu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé dans IIS (Internet Information Services) à l'aide de la sécurité au niveau du transport et que la propriété <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> a la valeur <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, le schéma d'authentification personnalisé utilise un sous-ensemble de l'authentification Windows. Cela est dû au fait que dans ce scénario, IIS effectue une authentification Windows avant que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'appelle l'authentificateur personnalisé.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liaison d’élément, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     L’exemple suivant présente le code de configuration de la liaison.  
  
    ```xml  
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
  
2.  Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.  
  
    1.  En tant qu’enfant à la [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajouter un [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément.  
  
    2.  Ajouter un [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à la [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément.  
  
    3.  Ajouter un [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) et affectez le `name` attribut une valeur appropriée.  
  
    4.  Ajouter un [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à la [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément.  
  
    5.  Ajouter un [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à la [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Affectez `userNamePasswordValidationMode` à `Custom`.  
  
        > [!IMPORTANT]
        >  Si la valeur `userNamePasswordValidationMode` n'est pas définie, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'authentification Windows au lieu du validateur de nom d'utilisateur et de mot de passe personnalisé.  
  
    7.  Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.  
  
     L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé. N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production. Remplacez le code par votre schéma de validation de nom d’utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d’utilisateur/mot de passe à partir d’une base de données.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [Comment : utiliser le fournisseur d’appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
