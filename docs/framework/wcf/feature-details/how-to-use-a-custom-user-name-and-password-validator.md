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
ms.workload: dotnet
ms.openlocfilehash: ee138c52c8cdd63137bf3c468ebbdd064d60d443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="00a8f-102">Comment : utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="00a8f-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="00a8f-103">Par défaut, lorsqu'un nom d'utilisateur et un mot de passe sont utilisés pour l'authentification, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise Windows pour valider le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="00a8f-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="00a8f-104">Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autorise pour les schémas de l’authentification des nom et mot de passe d’utilisateur personnalisée, également appelé *validateurs*.</span><span class="sxs-lookup"><span data-stu-id="00a8f-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="00a8f-105">Pour incorporer un validateur de nom d'utilisateur et de mot de passe personnalisé, créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, puis configurez-la.</span><span class="sxs-lookup"><span data-stu-id="00a8f-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="00a8f-106">Pour un exemple d’application, consultez [validateur de mot de passe de nom d’utilisateur](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="00a8f-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="00a8f-107">Pour créer validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="00a8f-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="00a8f-108">Créez une classe qui dérive de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="00a8f-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="00a8f-109">Implémentez le schéma d'authentification personnalisé en substituant la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="00a8f-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="00a8f-110">N'utilisez pas le code dans l'exemple suivant qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="00a8f-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="00a8f-111">Remplacez le code par votre schéma de validation de nom d'utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d'utilisateur/mot de passe à partir d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="00a8f-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="00a8f-112">Pour renvoyer des erreurs d'authentification au client, levez une exception <xref:System.ServiceModel.FaultException> dans la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="00a8f-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="00a8f-113">Pour configurer un service pour utiliser un validateur de nom d'utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="00a8f-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="00a8f-114">Configurez une liaison qui utilise la sécurité de message sur un transport ou la sécurité au niveau du transport sur HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="00a8f-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="00a8f-115">Lorsque vous utilisez la sécurité de message, ajoutez une des liaisons fournies par le système, tel qu’un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), ou un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) prend en charge la sécurité de message et le `UserName` type des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="00a8f-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="00a8f-116">Lors de l’utilisation de sécurité au niveau du transport sur HTTP (S), ajoutez le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), un [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) ou un [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) qui utilise HTTP (S) et le `Basic` schéma d’authentification.</span><span class="sxs-lookup"><span data-stu-id="00a8f-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="00a8f-117">Lors de l'utilisation du [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou une version ultérieure, vous pouvez utiliser un validateur personnalisé de mot de passe et de nom d'utilisateur avec la sécurité de transport et de message.</span><span class="sxs-lookup"><span data-stu-id="00a8f-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="00a8f-118">Avec [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], seul un validateur personnalisé de mot de passe et de nom d'utilisateur peut être utilisé avec la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="00a8f-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="00a8f-119">Pour plus d’informations sur l’utilisation de \<netTcpBinding > dans ce contexte, consultez [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="00a8f-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="00a8f-120">Dans le fichier de configuration, sous la [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajouter un [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="00a8f-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="00a8f-121">Ajouter un [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ou [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) élément à la section des liaisons.</span><span class="sxs-lookup"><span data-stu-id="00a8f-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a8f-122">Création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liaison d’élément, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="00a8f-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="00a8f-123">Définir le `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ou [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) à `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="00a8f-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="00a8f-124">Définir le `clientCredentialType` attribut de la [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) ou [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="00a8f-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="00a8f-125">Lorsque vous utilisez la sécurité des messages, définir le `clientCredentialType` attribut de la [ \<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) à `UserName`.</span><span class="sxs-lookup"><span data-stu-id="00a8f-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="00a8f-126">Sécurité au niveau du transport sur HTTP (S), définissez la `clientCredentialType` attribut de la [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) ou [ \<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) à `Basic`.</span><span class="sxs-lookup"><span data-stu-id="00a8f-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="00a8f-127">Lorsqu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est hébergé dans IIS (Internet Information Services) à l'aide de la sécurité au niveau du transport et que la propriété <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> a la valeur <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, le schéma d'authentification personnalisé utilise un sous-ensemble de l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="00a8f-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="00a8f-128">Cela est dû au fait que dans ce scénario, IIS effectue une authentification Windows avant que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'appelle l'authentificateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="00a8f-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="00a8f-129">Création d’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] liaison d’élément, consultez [Comment : spécifier une liaison de Service dans la Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="00a8f-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="00a8f-130">L’exemple suivant présente le code de configuration de la liaison.</span><span class="sxs-lookup"><span data-stu-id="00a8f-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2.  <span data-ttu-id="00a8f-131">Configurez un comportement qui spécifie qu'un validateur de nom d'utilisateur et de mot de passe personnalisé est utilisé pour valider des paires nom d'utilisateur/mot de passe pour les jetons de sécurité <xref:System.IdentityModel.Tokens.UserNameSecurityToken> entrants.</span><span class="sxs-lookup"><span data-stu-id="00a8f-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="00a8f-132">En tant qu’enfant à la [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément, ajouter un [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="00a8f-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="00a8f-133">Ajouter un [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à la [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="00a8f-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="00a8f-134">Ajouter un [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) et affectez le `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="00a8f-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="00a8f-135">Ajouter un [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) à la [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="00a8f-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="00a8f-136">Ajouter un [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) à la [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="00a8f-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="00a8f-137">Affectez `userNamePasswordValidationMode` à `Custom`.</span><span class="sxs-lookup"><span data-stu-id="00a8f-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="00a8f-138">Si la valeur `userNamePasswordValidationMode` n'est pas définie, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'authentification Windows au lieu du validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="00a8f-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="00a8f-139">Affectez au `customUserNamePasswordValidatorType` le type qui représente votre validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="00a8f-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="00a8f-140">L'exemple suivant présente le fragment `<serviceCredentials>` à ce point.</span><span class="sxs-lookup"><span data-stu-id="00a8f-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="00a8f-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="00a8f-141">Example</span></span>  
 <span data-ttu-id="00a8f-142">L'exemple de code suivant montre comment créer un validateur de nom d'utilisateur et de mot de passe personnalisé.</span><span class="sxs-lookup"><span data-stu-id="00a8f-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="00a8f-143">N'utilisez pas le code qui substitue la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="00a8f-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="00a8f-144">Remplacez le code par votre schéma de validation de nom d’utilisateur et de mot de passe personnalisé, ce qui peut impliquer la récupération de paires nom d’utilisateur/mot de passe à partir d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="00a8f-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="00a8f-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00a8f-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="00a8f-146">Guide pratique pour utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="00a8f-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="00a8f-147">Authentification</span><span class="sxs-lookup"><span data-stu-id="00a8f-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
