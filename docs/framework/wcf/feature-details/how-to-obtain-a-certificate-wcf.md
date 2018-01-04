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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Comment : obtenir un certificat (WCF)
Pour exécuter l'une des fonctionnalités [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] qui utilisent des certificats X.509, vous devez d'abord obtenir des certificats.  
  
### <a name="to-obtain-an-x509-certificate"></a>Pour obtenir un certificat X.509  
  
1.  Choisissez l'une des valeurs suivantes :  
  
    -   Achetez un certificat auprès d'une autorité de certification, telle que VeriSign, Inc.  
  
    -   Installez votre propre service de certificats et faites en sorte qu'une autorité de certification signe les certificats. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter et Windows 2000 Datacenter Server incluent tous des services de certificat qui prennent en charge l'infrastructure à clé publique. Dans Windows Server 2008, utilisez le [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) rôle pour gérer une autorité de certification.  
  
    -   Installez votre propre service de certificats et ne faites pas signer les certificats.  
  
    > [!NOTE]
    >  Quelle que soit la méthode adoptée, le destinataire de la demande SOAP contenant le certificat X.509 doit approuver ce dernier. Cela signifie que le certificat X.509 ou un émetteur dans la chaîne de certificats se trouve dans le magasin de certificats Personnes de confiance et que le certificat X.509 ne se trouve pas dans le magasin de certificats non fiables.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Guide pratique pour créer des certificats temporaires à utiliser au cours du développement](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
