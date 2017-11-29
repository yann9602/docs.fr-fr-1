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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Différences entre la validation de certificat de service effectuée par Internet Explorer et celle effectuée par WCF
En raison de la différence entre la façon dont Internet Explorer et [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] valident des certificats de service lorsque le protocole HTTPS est utilisé, il est possible qu'Internet Explorer ne soit pas en mesure d'accéder à la page d'aide ou au langage WSDL (Web Services Description Language) d'un service bien qu'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] soit en mesure d'envoyer avec succès des messages aux points de terminaison du service. Cela est dû au fait qu'Internet Explorer vérifie si le certificat de service a les identificateurs d'objet (OID) `ServerAuthentication` dans les indicateurs d'utilisation améliorés, alors que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'applique pas une telle contrainte. Si Internet Explorer ne peut pas accéder à la page d’aide ou le WSDL pour le service, utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour accéder aux métadonnées de service.  
  
## <a name="see-also"></a>Voir aussi  
 [Différences de Validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Comment : récupérer les métadonnées et implémenter un Service conforme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
