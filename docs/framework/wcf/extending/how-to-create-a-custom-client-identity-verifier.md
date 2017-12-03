---
title: "Comment : créer un vérificateur d'identité du client personnalisé"
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
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70c94d38a50425c702e382edcd7290cba3d61e91
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="25983-102">Comment : créer un vérificateur d'identité du client personnalisé</span><span class="sxs-lookup"><span data-stu-id="25983-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="25983-103">Le *identité* fonctionnalité de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permet à un client de spécifier à l’avance l’identité attendue du service.</span><span class="sxs-lookup"><span data-stu-id="25983-103">The *identity* feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="25983-104">Lorsqu'un serveur s'authentifie auprès du client, l'identité est vérifiée par rapport à l'identité attendue.</span><span class="sxs-lookup"><span data-stu-id="25983-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="25983-105">(Pour obtenir une explication de l’identité et son fonctionnement, consultez [l’identité du Service et l’authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="25983-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="25983-106">Si nécessaire, la vérification peut être personnalisée à l'aide d'un vérificateur d'identité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="25983-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="25983-107">Par exemple, vous pouvez effectuer des contrôles supplémentaires de vérification de l'identité du service.</span><span class="sxs-lookup"><span data-stu-id="25983-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="25983-108">Dans cet exemple, le vérificateur d'identité personnalisé vérifie des revendications supplémentaires dans le certificat X.509 retourné par le serveur.</span><span class="sxs-lookup"><span data-stu-id="25983-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="25983-109">Pour un exemple d’application, consultez [exemple](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="25983-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="25983-110">Pour étendre la classe EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="25983-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="25983-111">Définissez une nouvelle classe dérivée de la classe <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="25983-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="25983-112">Cet exemple nomme l'extension `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="25983-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="25983-113">Ajoutez les membres privés avec les propriétés qui seront utilisées par la classe <xref:System.ServiceModel.Security.IdentityVerifier> étendue pour exécuter le contrôle d'identité par rapport aux revendications dans le jeton de sécurité retourné par le service.</span><span class="sxs-lookup"><span data-stu-id="25983-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="25983-114">Cet exemple définit une propriété : la propriété `OrganizationClaim`.</span><span class="sxs-lookup"><span data-stu-id="25983-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="25983-115">Pour étendre la classe IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="25983-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="25983-116">Définissez une nouvelle classe dérivée de <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="25983-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="25983-117">Cet exemple nomme l'extension `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="25983-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="25983-118">Remplacez la méthode <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A>.</span><span class="sxs-lookup"><span data-stu-id="25983-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="25983-119">La méthode détermine si le contrôle d'identité a réussi ou a échoué.</span><span class="sxs-lookup"><span data-stu-id="25983-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="25983-120">La méthode `CheckAccess` possède deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="25983-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="25983-121">Le premier est une instance de la classe <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="25983-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="25983-122">Le second est une instance de la classe <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="25983-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="25983-123">Dans l'implémentation de méthode, examinez la collection de revendications retournée par la propriété <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> de la classe <xref:System.IdentityModel.Policy.AuthorizationContext> et exécutez des contrôles d'authentification selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="25983-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="25983-124">Cet exemple commence par rechercher les revendications de type « Distinguished Name » puis compare le nom à l'extension du <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="25983-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="25983-125">Pour implémenter la méthode TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="25983-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="25983-126">Implémentez la méthode <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> qui détermine si une instance de la classe <xref:System.ServiceModel.EndpointIdentity> peut être retournée par le client.</span><span class="sxs-lookup"><span data-stu-id="25983-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="25983-127">L'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] appelle d'abord l'implémentation de la méthode `TryGetIdentity` pour récupérer l'identité du service à partir du message.</span><span class="sxs-lookup"><span data-stu-id="25983-127">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="25983-128">Ensuite, l'infrastructure appelle l'implémentation `CheckAccess` avec les `EndpointIdentity` et <xref:System.IdentityModel.Policy.AuthorizationContext> retournés.</span><span class="sxs-lookup"><span data-stu-id="25983-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="25983-129">Dans la méthode `TryGetIdentity`, insérez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="25983-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="25983-130">Pour implémenter une liaison personnalisée et définir l'IdentityVerifier personnalisé</span><span class="sxs-lookup"><span data-stu-id="25983-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="25983-131">Créez une méthode qui retourne un objet <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="25983-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="25983-132">Cet exemple commence par créer une instance de la classe <xref:System.ServiceModel.WSHttpBinding> et affecte à son mode de sécurité la valeur <xref:System.ServiceModel.SecurityMode.Message>, et à son <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> la valeur <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="25983-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="25983-133">Créez un <xref:System.ServiceModel.Channels.BindingElementCollection> à l'aide de la méthode <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="25983-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="25983-134">Retournez le <xref:System.ServiceModel.Channels.SecurityBindingElement> de la collection et effectuez un cast en une variable <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="25983-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="25983-135">Affectez à la propriété <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> de la classe <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> une nouvelle instance de la classe `CustomIdentityVerifier` créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="25983-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="25983-136">La liaison personnalisée retournée est utilisée pour créer une instance du client et de la classe.</span><span class="sxs-lookup"><span data-stu-id="25983-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="25983-137">Le client peut effectuer ensuite une vérification personnalisée de l'identité du service comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="25983-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="25983-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="25983-138">Example</span></span>  
 <span data-ttu-id="25983-139">L'exemple suivant illustre une implémentation complète de la classe <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="25983-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="25983-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="25983-140">Example</span></span>  
 <span data-ttu-id="25983-141">L'exemple suivant illustre une implémentation complète de la classe <xref:System.ServiceModel.EndpointIdentity>.</span><span class="sxs-lookup"><span data-stu-id="25983-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="25983-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25983-142">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [<span data-ttu-id="25983-143">Exemple d’identité de service</span><span class="sxs-lookup"><span data-stu-id="25983-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [<span data-ttu-id="25983-144">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="25983-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="25983-145">Stratégie d’autorisation</span><span class="sxs-lookup"><span data-stu-id="25983-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
