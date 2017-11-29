---
title: "Comment : spécifier le type d'informations d'identification du client"
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
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35c3b5ee429f7c9337fa3c3e3eb0d0476e3f56d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="8b9a1-102">Comment : spécifier le type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="8b9a1-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="8b9a1-103">Après avoir défini un mode de sécurité (transport ou message), vous avez pouvez définir le type d'informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="8b9a1-104">Cette propriété spécifie le type d'informations d'identification que le client doit fournir au service dans le cadre de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="8b9a1-105">paramètre de mode de sécurité (étape nécessaire avant de définir le type d’informations d’identification du client), consultez [Comment : définir le Mode de sécurité](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="8b9a1-105"> setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="8b9a1-106">Pour définir le type d'informations d'identification du client dans le code</span><span class="sxs-lookup"><span data-stu-id="8b9a1-106">To set the client credential type in code</span></span>  
  
1.  <span data-ttu-id="8b9a1-107">Créez une instance de la liaison que le service utilisera.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="8b9a1-108">Cet exemple utilise la liaison <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2.  <span data-ttu-id="8b9a1-109">Affectez à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="8b9a1-110">Cet exemple utilise le mode de message.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-110">This example uses the Message mode.</span></span>  
  
3.  <span data-ttu-id="8b9a1-111">Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="8b9a1-112">Dans notre exemple, la propriété est définie de sorte à utiliser l'authentification Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="8b9a1-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="8b9a1-113">Pour définir le type d'informations d'identification du client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="8b9a1-113">To set the client credential type in configuration</span></span>  
  
1.  <span data-ttu-id="8b9a1-114">Ajouter un [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-114">Add a [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2.  <span data-ttu-id="8b9a1-115">Comme un élément enfant, ajoutez un [ \<liaisons >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-115">As a child element, add a [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3.  <span data-ttu-id="8b9a1-116">Ajoutez une liaison appropriée.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-116">Add an appropriate binding.</span></span> <span data-ttu-id="8b9a1-117">Cet exemple utilise le [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-117">This example uses the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4.  <span data-ttu-id="8b9a1-118">Ajouter un [ \<liaison >](../../../docs/framework/misc/binding.md) et affectez le `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-118">Add a [\<binding>](../../../docs/framework/misc/binding.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="8b9a1-119">Cet exemple utilise le nom « SecureBinding ».</span><span class="sxs-lookup"><span data-stu-id="8b9a1-119">This example uses the name "SecureBinding".</span></span>  
  
5.  <span data-ttu-id="8b9a1-120">Ajoutez une liaison `<security>`.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-120">Add a `<security>` binding.</span></span> <span data-ttu-id="8b9a1-121">Affectez la valeur appropriée à l'attribut `mode`.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="8b9a1-122">Cet exemple lui affecte la valeur `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-122">This example sets it to `"Message"`.</span></span>  
  
6.  <span data-ttu-id="8b9a1-123">Ajoutez un élément `<message>` ou un élément `<transport>` comme requis par le mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="8b9a1-124">Affectez la valeur appropriée à l'attribut `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="8b9a1-125">Cet exemple utilise `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="8b9a1-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b9a1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b9a1-126">See Also</span></span>  
 [<span data-ttu-id="8b9a1-127">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="8b9a1-127">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="8b9a1-128">Guide pratique pour définir le mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="8b9a1-128">How to: Set the Security Mode</span></span>](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
