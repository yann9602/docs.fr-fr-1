---
title: "Comment : sécuriser un service avec un certificat X.509"
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
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ec2800d2b6a910f75366e323b7580afe08de2acb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="1f477-102">Comment : sécuriser un service avec un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="1f477-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="1f477-103">La sécurisation d'un service avec un certificat X.509 est une technique de base que la plupart des liaisons dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisent.</span><span class="sxs-lookup"><span data-stu-id="1f477-103">Securing a service with an X.509 certificate is a basic technique that most bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] use.</span></span> <span data-ttu-id="1f477-104">Cette rubrique décrit les étapes de la configuration d'un service auto-hébergé avec un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="1f477-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="1f477-105">L'une des conditions préalables est de disposer d'un certificat valide pouvant être utilisé pour authentifier le serveur.</span><span class="sxs-lookup"><span data-stu-id="1f477-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="1f477-106">Le certificat doit être envoyé au serveur par une autorité de certification approuvée.</span><span class="sxs-lookup"><span data-stu-id="1f477-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="1f477-107">Si le certificat n'est pas valide, les clients qui essayeront d'utiliser le service ne lui feront pas confiance, et par conséquent aucune connexion ne sera établie.</span><span class="sxs-lookup"><span data-stu-id="1f477-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1f477-108">l’utilisation de certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1f477-108"> using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="1f477-109">Pour configurer un service avec un certificat à l'aide du code</span><span class="sxs-lookup"><span data-stu-id="1f477-109">To configure a service with a certificate using code</span></span>  
  
1.  <span data-ttu-id="1f477-110">Créez le contrat de service et le service implémenté.</span><span class="sxs-lookup"><span data-stu-id="1f477-110">Create the service contract and the implemented service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1f477-111">[Conception et implémentation de Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f477-111"> [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2.  <span data-ttu-id="1f477-112">Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding> et affectez <xref:System.ServiceModel.SecurityMode.Message> à son mode de sécurité, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1f477-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  <span data-ttu-id="1f477-113">Créez deux variables <xref:System.Type>, une pour le type de contrat et l'autre pour le contrat implémenté, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1f477-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  <span data-ttu-id="1f477-114">Créez une instance de la classe <xref:System.Uri> pour l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="1f477-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="1f477-115">`WSHttpBinding` utilisant le transport HTTP, l'URI (Uniform Resource Identifier) doit commencer par ce schéma, sinon [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] lèvera une exception lors de l'ouverture du service.</span><span class="sxs-lookup"><span data-stu-id="1f477-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  <span data-ttu-id="1f477-116">Créez une nouvelle instance de la classe <xref:System.ServiceModel.ServiceHost> avec la variable de type de contrat implémentée et l'URI.</span><span class="sxs-lookup"><span data-stu-id="1f477-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  <span data-ttu-id="1f477-117">Ajoutez <xref:System.ServiceModel.Description.ServiceEndpoint> au service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f477-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="1f477-118">Transmettez le contrat, la liaison et une adresse de point de terminaison au constructeur, tel qu’indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1f477-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  <span data-ttu-id="1f477-119">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1f477-119">Optional.</span></span> <span data-ttu-id="1f477-120">Pour récupérer les métadonnées du service, créez un objet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> et affectez <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="1f477-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  <span data-ttu-id="1f477-121">Utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> pour ajouter le certificat valide au service.</span><span class="sxs-lookup"><span data-stu-id="1f477-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="1f477-122">La méthode peut utiliser l'une des nombreuses options disponibles pour rechercher un certificat.</span><span class="sxs-lookup"><span data-stu-id="1f477-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="1f477-123">Cet exemple utilise l'énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName>.</span><span class="sxs-lookup"><span data-stu-id="1f477-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="1f477-124">L'énumération spécifie que la valeur fournie est le nom de l'entité à laquelle le certificat a été envoyé.</span><span class="sxs-lookup"><span data-stu-id="1f477-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="1f477-125">Appelez la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> pour commencer l'écoute du service.</span><span class="sxs-lookup"><span data-stu-id="1f477-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="1f477-126">Si vous créez une application console, appelez la méthode <xref:System.Console.ReadLine%2A> pour maintenir l'écoute du service.</span><span class="sxs-lookup"><span data-stu-id="1f477-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="1f477-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f477-127">Example</span></span>  
 <span data-ttu-id="1f477-128">L'exemple suivant utilise la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> pour configurer un service avec un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="1f477-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f477-129">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="1f477-129">Compiling the Code</span></span>  
 <span data-ttu-id="1f477-130">Les espaces de noms suivants sont requis pour compiler le code :</span><span class="sxs-lookup"><span data-stu-id="1f477-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="1f477-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f477-131">See Also</span></span>  
 [<span data-ttu-id="1f477-132">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="1f477-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
