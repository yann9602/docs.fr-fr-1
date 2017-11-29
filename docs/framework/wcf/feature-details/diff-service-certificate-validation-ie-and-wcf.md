---
title: "Différences entre la validation de certificat de service effectuée par Internet Explorer et celle effectuée par WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a58ea9f84571ede9943769e1f187a242383a88f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="609e3-102">Différences entre la validation de certificat de service effectuée par Internet Explorer et celle effectuée par WCF</span><span class="sxs-lookup"><span data-stu-id="609e3-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="609e3-103">En raison de la différence entre la façon dont Internet Explorer et [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] valident des certificats de service lorsque le protocole HTTPS est utilisé, il est possible qu'Internet Explorer ne soit pas en mesure d'accéder à la page d'aide ou au langage WSDL (Web Services Description Language) d'un service bien qu'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] soit en mesure d'envoyer avec succès des messages aux points de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="609e3-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="609e3-104">Cela est dû au fait qu'Internet Explorer vérifie si le certificat de service a les identificateurs d'objet (OID) `ServerAuthentication` dans les indicateurs d'utilisation améliorés, alors que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'applique pas une telle contrainte.</span><span class="sxs-lookup"><span data-stu-id="609e3-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="609e3-105">Si Internet Explorer ne peut pas accéder à la page d’aide ou le WSDL pour le service, utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour accéder aux métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="609e3-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="609e3-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="609e3-106">See Also</span></span>  
 [<span data-ttu-id="609e3-107">Différences de Validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP</span><span class="sxs-lookup"><span data-stu-id="609e3-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="609e3-108">Comment : récupérer les métadonnées et implémenter un Service conforme</span><span class="sxs-lookup"><span data-stu-id="609e3-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
