---
title: "Comment : examiner le contexte de sécurité"
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
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 72bc3dfcc91cb0fe5b393c9735c83b6331d5e0dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="9df90-102">Comment : examiner le contexte de sécurité</span><span class="sxs-lookup"><span data-stu-id="9df90-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="9df90-103">Lorsque vous programmez des services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], le contexte de sécurité vous permet de déterminer les détails relatifs aux informations d'identification du client et les revendications utilisées pour authentifier avec le service.</span><span class="sxs-lookup"><span data-stu-id="9df90-103">When programming [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="9df90-104">Pour ce faire, utilisez les propriétés de la classe <xref:System.ServiceModel.ServiceSecurityContext>.</span><span class="sxs-lookup"><span data-stu-id="9df90-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="9df90-105">Par exemple, vous pouvez récupérer l'identité du client actuel en utilisant la propriété <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9df90-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="9df90-106">Pour déterminer si le client est ou non anonyme, utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.</span><span class="sxs-lookup"><span data-stu-id="9df90-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="9df90-107">Vous pouvez également déterminer les revendications effectuées pour le compte du client en effectuant une itération dans la collection de revendications de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="9df90-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="9df90-108">Pour obtenir le contexte de sécurité actuel</span><span class="sxs-lookup"><span data-stu-id="9df90-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="9df90-109">Accédez à la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> statique pour obtenir le contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="9df90-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="9df90-110">Examinez chacune des propriétés du contexte actuel à partir de la référence.</span><span class="sxs-lookup"><span data-stu-id="9df90-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="9df90-111">Pour déterminer l'identité de l'appelant</span><span class="sxs-lookup"><span data-stu-id="9df90-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="9df90-112">Imprimez la valeur des propriétés <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="9df90-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="9df90-113">Pour analyser les revendications d'un appelant</span><span class="sxs-lookup"><span data-stu-id="9df90-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="9df90-114">Retournez la classe actuelle <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="9df90-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="9df90-115">Utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pour retourner le contexte de sécurité des services actuel, puis retournez `AuthorizationContext` à l'aide de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.</span><span class="sxs-lookup"><span data-stu-id="9df90-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="9df90-116">Analysez la collection d'objets <xref:System.IdentityModel.Claims.ClaimSet> retournés par la propriété <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> de la classe <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="9df90-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df90-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="9df90-117">Example</span></span>  
 <span data-ttu-id="9df90-118">L'exemple suivant imprime les valeurs des propriétés <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> du contexte de sécurité actuel ainsi que la propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, la valeur de ressource de la revendication et la propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> de chaque revendication du contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="9df90-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9df90-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9df90-119">Compiling the Code</span></span>  
 <span data-ttu-id="9df90-120">Le code utilise les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="9df90-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="9df90-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9df90-121">See Also</span></span>  
 [<span data-ttu-id="9df90-122">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="9df90-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="9df90-123">L’authentification et identité de Service</span><span class="sxs-lookup"><span data-stu-id="9df90-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
