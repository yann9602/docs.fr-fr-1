---
title: "Comment : obtenir un certificat (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 468298c7a0ea673a90e0cde9d481333fad60e4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="a52da-102">Comment : obtenir un certificat (WCF)</span><span class="sxs-lookup"><span data-stu-id="a52da-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="a52da-103">Pour exécuter l'une des fonctionnalités [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats X.509, vous devez d'abord obtenir des certificats.</span><span class="sxs-lookup"><span data-stu-id="a52da-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="a52da-104">Pour obtenir un certificat X.509</span><span class="sxs-lookup"><span data-stu-id="a52da-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="a52da-105">Choisissez l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="a52da-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="a52da-106">Achetez un certificat auprès d'une autorité de certification, telle que VeriSign, Inc.</span><span class="sxs-lookup"><span data-stu-id="a52da-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="a52da-107">Installez votre propre service de certificats et faites en sorte qu'une autorité de certification signe les certificats.</span><span class="sxs-lookup"><span data-stu-id="a52da-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="a52da-108">, Windows 2000 Server, Windows 2000 Server Datacenter et Windows 2000 Datacenter Server incluent tous des services de certificat qui prennent en charge l'infrastructure à clé publique.</span><span class="sxs-lookup"><span data-stu-id="a52da-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="a52da-109">Dans Windows Server 2008, utilisez le [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) rôle pour gérer une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="a52da-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="a52da-110">Installez votre propre service de certificats et ne faites pas signer les certificats.</span><span class="sxs-lookup"><span data-stu-id="a52da-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a52da-111">Quelle que soit la méthode adoptée, le destinataire de la demande SOAP contenant le certificat X.509 doit approuver ce dernier.</span><span class="sxs-lookup"><span data-stu-id="a52da-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="a52da-112">Cela signifie que le certificat X.509 ou un émetteur dans la chaîne de certificats se trouve dans le magasin de certificats Personnes de confiance et que le certificat X.509 ne se trouve pas dans le magasin de certificats non fiables.</span><span class="sxs-lookup"><span data-stu-id="a52da-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52da-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a52da-113">See Also</span></span>  
 [<span data-ttu-id="a52da-114">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="a52da-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="a52da-115">Comment : créer des certificats temporaires à utiliser pendant le développement</span><span class="sxs-lookup"><span data-stu-id="a52da-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
