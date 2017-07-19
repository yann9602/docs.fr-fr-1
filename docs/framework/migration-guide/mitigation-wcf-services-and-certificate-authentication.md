---
title: "Atténuation : Services WCF et authentification par certificat | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: 0b32fa96cd002e927fa00e8c2a797d1ff6b17cb8
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---
<a id="mitigation-wcf-services-and-certificate-authentication" class="xliff"></a>

# Atténuation : Services WCF et authentification par certificat
Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut. Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.  
  
<a id="impact" class="xliff"></a>

## Impact  
 TLS 1.2 ne prend pas en charge l’authentification par certificat MD5. Par conséquent, si un client utilise un certificat SSL employant MD5 comme algorithme de hachage, le client WCF ne parvient pas à se connecter au service WCF. Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
<a id="mitigation" class="xliff"></a>

## Atténuation  
 Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :  
  
-   Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5. Il s'agit de la solution recommandée.  
  
-   Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole. Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.  
  
    > [!CAUTION]
    >  Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.  
  
     Le fichier de configuration suivant effectue ceci :  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=fullName>) ou une version antérieure du protocole dans le code source.  
  
    > [!CAUTION]
    >  Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.  
  
<a id="see-also" class="xliff"></a>

## Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)

