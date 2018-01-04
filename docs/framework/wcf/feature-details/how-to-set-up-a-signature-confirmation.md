---
title: "Comment : configurer une confirmation de signature"
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
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53e38658671f3a36da67619c796667ecad61f286
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="108de-102">Comment : configurer une confirmation de signature</span><span class="sxs-lookup"><span data-stu-id="108de-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="108de-103">*Confirmation de signature* est un mécanisme pour un initiateur de message pour vous assurer qu’un message reçu a été généré en réponse au message d’origine de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="108de-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="108de-104">La confirmation de signature est définie dans la spécification WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="108de-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="108de-105">Si un point de terminaison prend en charge WS-Security 1.0, vous ne pouvez pas utiliser la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="108de-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="108de-106">Les procédures suivantes spécifient comment activer la confirmation de signature à l'aide de <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="108de-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="108de-107">Vous pouvez utiliser la même procédure avec <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="108de-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="108de-108">La procédure s’appuie sur les étapes de base trouvés dans [Comment : créer un personnalisé de liaison à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="108de-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="108de-109">Pour activer la confirmation de signature dans le code</span><span class="sxs-lookup"><span data-stu-id="108de-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="108de-110">Créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection>.</span><span class="sxs-lookup"><span data-stu-id="108de-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="108de-111">Créez une instance de la <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="108de-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="108de-112">Affectez <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à `true`.</span><span class="sxs-lookup"><span data-stu-id="108de-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="108de-113">Ajoutez l’élément de sécurité à la collection de liaisons.</span><span class="sxs-lookup"><span data-stu-id="108de-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="108de-114">Créer une liaison personnalisée, comme spécifié dans [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="108de-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="108de-115">Pour activer la confirmation de signature dans la configuration</span><span class="sxs-lookup"><span data-stu-id="108de-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="108de-116">Ajoutez un élément `<customBinding>` à la section `<bindings>` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="108de-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="108de-117">Ajoutez un élément `<binding>` et affectez une valeur appropriée à l'attribut de nom.</span><span class="sxs-lookup"><span data-stu-id="108de-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="108de-118">Ajoutez un élément d'encodage approprié.</span><span class="sxs-lookup"><span data-stu-id="108de-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="108de-119">L'exemple suivant ajoute un élément `<TextMessageEncoding>`.</span><span class="sxs-lookup"><span data-stu-id="108de-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="108de-120">Ajoutez un élément enfant `<security>` et affectez `requireSignatureConfirmation` à l'attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="108de-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="108de-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="108de-121">Optional.</span></span> <span data-ttu-id="108de-122">Pour activer la confirmation de signature pendant le programme d’amorçage, ajoutez un [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément enfant et définissez la `equireSignatureConfirmation` attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="108de-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="108de-123">Ajoutez un élément de transport approprié.</span><span class="sxs-lookup"><span data-stu-id="108de-123">Add an appropriate transport element.</span></span> <span data-ttu-id="108de-124">L’exemple suivant ajoute une [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="108de-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a><span data-ttu-id="108de-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="108de-125">Example</span></span>  
 <span data-ttu-id="108de-126">Le code suivant crée une instance de <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> et affecte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="108de-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="108de-127">Notez que cet exemple n'utilise pas l'élément `<secureConversationBootstrap>` indiqué dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="108de-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="108de-128">Cet exemple présente la confirmation de signature lors de l'utilisation d'un jeton Windows (protocole Kerberos).</span><span class="sxs-lookup"><span data-stu-id="108de-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="108de-129">Dans ce cas, la signature du client est retournée dans toutes les réponses du service et est confirmée par le client.</span><span class="sxs-lookup"><span data-stu-id="108de-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="108de-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="108de-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="108de-131">Guide pratique pour créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="108de-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="108de-132">Guide pratique pour créer un SecurityBindingElement pour un mode d’authentification spécifié</span><span class="sxs-lookup"><span data-stu-id="108de-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
