---
title: "Atténuation : Services WCF et authentification par certificat"
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
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb852719e3312b78b86621e3cb69fa8bf7267856
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="14d16-102">Atténuation : Services WCF et authentification par certificat</span><span class="sxs-lookup"><span data-stu-id="14d16-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="14d16-103">Le .NET Framework 4.6 ajoute TLS 1.1 et TLS 1.2 à la liste des protocoles WCF SSL par défaut.</span><span class="sxs-lookup"><span data-stu-id="14d16-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="14d16-104">Lorsque le .NET Framework 4.6 ou ultérieur est installé sur les ordinateurs clients et serveurs, TLS 1.2 est utilisé à des fins de négociation.</span><span class="sxs-lookup"><span data-stu-id="14d16-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="14d16-105">Impact</span><span class="sxs-lookup"><span data-stu-id="14d16-105">Impact</span></span>  
 <span data-ttu-id="14d16-106">TLS 1.2 ne prend pas en charge l’authentification par certificat MD5.</span><span class="sxs-lookup"><span data-stu-id="14d16-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="14d16-107">Par conséquent, si un client utilise un certificat SSL employant MD5 comme algorithme de hachage, le client WCF ne parvient pas à se connecter au service WCF.</span><span class="sxs-lookup"><span data-stu-id="14d16-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="14d16-108">Pour plus d’informations, consultez [Atténuation : Services WCF et authentification par certificat](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="14d16-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="14d16-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="14d16-109">Mitigation</span></span>  
 <span data-ttu-id="14d16-110">Vous pouvez contourner ce problème afin qu’un client WCF puisse se connecter à un serveur WCF en effectuant une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="14d16-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="14d16-111">Mettez à jour le certificat pour ne pas utiliser l’algorithme MD5.</span><span class="sxs-lookup"><span data-stu-id="14d16-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="14d16-112">Il s'agit de la solution recommandée.</span><span class="sxs-lookup"><span data-stu-id="14d16-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="14d16-113">Si la liaison n’est pas configurée dynamiquement dans le code source, mettez à jour le fichier de configuration de l’application pour utiliser TLS 1.1 ou une version antérieure du protocole.</span><span class="sxs-lookup"><span data-stu-id="14d16-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="14d16-114">Cela vous permet de continuer à utiliser un certificat avec l’algorithme de hachage MD5.</span><span class="sxs-lookup"><span data-stu-id="14d16-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="14d16-115">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="14d16-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="14d16-116">Le fichier de configuration suivant effectue ceci :</span><span class="sxs-lookup"><span data-stu-id="14d16-116">The following configuration file does this:</span></span>  
  
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
  
-   <span data-ttu-id="14d16-117">Si la liaison est configurée dynamiquement dans le code source, mettez à jour la propriété <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> pour utiliser TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou une version antérieure du protocole dans le code source.</span><span class="sxs-lookup"><span data-stu-id="14d16-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="14d16-118">Cette solution de contournement n’est pas recommandée, car un certificat avec l’algorithme de hachage MD5 est considéré comme non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="14d16-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d16-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14d16-119">See Also</span></span>  
 [<span data-ttu-id="14d16-120">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="14d16-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
