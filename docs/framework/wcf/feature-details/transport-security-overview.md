---
title: "Vue d&#39;ensemble de la s&#233;curit&#233; des transports | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# Vue d&#39;ensemble de la s&#233;curit&#233; des transports
Les mécanismes de sécurité de transport dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dépendent de la liaison et du transport utilisé. Par exemple, lorsque vous utilisez la <xref:System.ServiceModel.WSHttpBinding> (classe), le transport est HTTP, et le mécanisme principal utilisé pour sécuriser ce transport est Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire à HTTPS. Cette rubrique aborde les principaux mécanismes de sécurité de transport utilisés dans les liaisons [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournies par le système.  
  
> [!NOTE]
>  Lorsque la sécurité SSL est utilisée avec le .NET Framework version 3.5 et ultérieure, un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les certificats intermédiaires dans son magasin de certificats et les certificats intermédiaires reçus au cours de la négociation SSL pour effectuer la validation de chaîne de certificats sur le certificat du service. .NET Framework 3.0 n'utilise que les certificats intermédiaires installés dans le magasin de certificats local.  
  
> [!WARNING]
>  Lorsque la sécurité de transport est utilisée, le <xref:System.Treading.Thread.CurrentPrincipal%2A> propriété peut-être être remplacée. Pour éviter cela, affectez la <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> aucun. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> est un comportement de service qui peut être défini sur la description de service.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Par défaut, le <xref:System.ServiceModel.BasicHttpBinding> classe ne fournit pas de sécurité. Cette liaison est conçue pour assurer l’interopérabilité avec les fournisseurs de services Web, lesquels n’implémentent pas de sécurité. Toutefois, vous pouvez basculer sur la sécurité en définissant le <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> propriété n’importe quelle valeur sauf <xref:System.ServiceModel.BasicHttpSecurityMode>. Pour activer la sécurité de transport, définissez la propriété sur <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="interoperation-with-iis"></a>Interaction avec IIS  
 Le <xref:System.ServiceModel.BasicHttpBinding> classe est principalement utilisée pour interagir avec les services Web existants, et plusieurs de ces services sont hébergés par Internet Information Services (IIS). C’est pourquoi la sécurité de transport de cette liaison est conçue pour interagir de façon transparente avec les sites IIS. Pour ce faire, vous devez affecter le mode de sécurité <xref:System.ServiceModel.BasicHttpSecurityMode> , puis en définissant les type d’informations d’identification du client. Les valeurs de ce type correspondent aux mécanismes de sécurité du répertoire IIS. Dans l'exemple de code suivant, le mode est en cours de définition et la valeur Windows est affectée au type d'informations d'identification. Vous pouvez utiliser cette configuration lorsque le client et le serveur figurent tous les deux dans le même domaine Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 <!-- TODO: review snippet reference [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  -->  
  
 Ou dans la configuration :  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Les sections suivantes abordent d'autres types d'informations d'identification.  
  
#### <a name="basic"></a>De base  
 Il s'agit de la méthode d'authentification de base dans IIS. Lorsque ce mode est utilisé, le serveur IIS doit être configuré avec des comptes utilisateur Windows et les autorisations de système de fichiers NTFS adéquates. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consultez [l’activation de l’authentification de base et la configuration du nom de domaine](http://go.microsoft.com/fwlink/?LinkId=88592). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 bêta : configurer l’authentification de base](http://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>Certificat  
 Sur les services IIS, une option permet de spécifier que les clients doivent se connecter en utilisant un certificat. Cette fonctionnalité permet également aux services IIS de mapper les certificats clients aux comptes Windows correspondants. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consultez [activation des certificats Client dans IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 bêta : configuration des certificats de serveur dans IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Condensat  
 L’authentification Digest s’apparente à l’authentification de base tout en présentant l’avantage supplémentaire de permettre l’envoi des informations d’identification dans un texte haché plutôt qu’en texte clair. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consultez [l’authentification Digest dans IIS 6.0](http://go.microsoft.com/fwlink/?LinkID=88443). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 bêta : configurer l’authentification Digest](http://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Il s'agit de l'authentification Windows intégrée à IIS. Lorsque ce mode d'authentification est activé, le serveur doit également figurer dans un domaine Windows utilisant le protocole Kerberos comme contrôleur. Dans le cas contraire ou si le système Kerberos connaît une défaillance, vous pouvez utiliser l'authentification NT LAN Manager (NTLM), abordée dans la section suivante. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consultez [l’authentification Windows intégrée dans IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88597). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consultez [IIS 7.0 bêta : configuration des certificats de serveur dans IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Cela permet au serveur d'utiliser NTLM pour l'authentification si le fournisseur Kerberos échoue. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]configuration d’IIS dans [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consultez [authentification NTLM forcée](http://go.microsoft.com/fwlink/?LinkId=88598). Pour [!INCLUDE[iisver](../../../../includes/iisver-md.md)], l'authentification Windows intègre l'authentification NTLM. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS 7.0 bêta : configuration des certificats de serveur dans IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 Le <xref:System.ServiceModel.WSHttpBinding> classe est conçue pour interagir avec les services qui implémentent WS-* spécifications. La sécurité de transport de cette liaison correspond à Secure Sockets Layer (SSL) sur HTTP, c’est-à-dire à HTTPS. Pour créer une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui utilise SSL, utilisez les services IIS afin d'héberger cette application. Si vous créez une application auto-hébergée, vous pouvez également utiliser l'outil HttpCfg.exe afin d'attribuer un certificat X.509 à un port spécifique de l'ordinateur. Ce numéro de port est spécifié dans le cadre d'une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sous forme d'adresse de point de terminaison. Lorsqu'un mode de transport est utilisé, l'adresse de point de terminaison doit comporter le protocole HTTPS. Dans le cas contraire, une exception sera levée pendant l'exécution. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Sécurité de Transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Pour l’authentification du client, définissez la <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> propriété de la <xref:System.ServiceModel.HttpTransportSecurity> classe à l’un de la <xref:System.ServiceModel.HttpClientCredentialType> valeurs d’énumération. Les valeurs d’énumération sont identiques aux types d’informations d’identification client pour <xref:System.ServiceModel.BasicHttpBinding> et sont conçues pour être hébergées dans les services IIS.  
  
 Dans l’exemple suivant, une liaison est utilisée avec un type d’informations d’identification client de Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Cette liaison offre uniquement une sécurité de niveau message et non une sécurité de niveau transport.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 Le <xref:System.ServiceModel.NetTcpBinding> classe utilise TCP pour le transport de messages. La sécurité de niveau transport est assurée par l'implémentation de la sécurité Transport Layer Security (TLS) sur TCP. L'implémentation TLS est assurée par le système d'exploitation.  
  
 Vous pouvez également spécifier le type d’informations d’identification du client en définissant le <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> propriété de la <xref:System.ServiceModel.TcpTransportSecurity> classe à l’un de la <xref:System.ServiceModel.TcpClientCredentialType> des valeurs, comme indiqué dans le code suivant.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Client  
 Sur le client, vous devez spécifier un certificat à l’aide de la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> procédé de la <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> (classe).  
  
> [!NOTE]
>  Si vous utilisez la sécurité Windows, aucun certificat n'est requis.  
  
 Le code suivant utilise l'empreinte numérique de certificat, propre à chaque certificat. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]certificats, consultez [utilisation des certificats](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Vous pouvez également spécifier un certificat dans la configuration du client à l’aide un [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) élément dans la section des comportements.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 Le <xref:System.ServiceModel.NetNamedPipeBinding> classe est conçue pour une communication efficace au sein des ordinateurs ; autrement dit, pour les processus en cours d’exécution sur le même ordinateur, bien que les canaux nommés peuvent être créés entre deux ordinateurs sur le même réseau. Cette liaison offre uniquement une sécurité de niveau transport. Lorsque des applications sont créées à l'aide de cette liaison, les adresses de point de terminaison doivent comporter « net.pipe » dans leur protocole.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Lorsque vous utilisez la sécurité du transport, cette liaison utilise SSL sur HTTP, c'est-à-dire HTTPS avec un jeton émis (<xref:System.ServiceModel.WSFederationHttpSecurityMode>). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pair à pair, consultez [fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 Le <xref:System.ServiceModel.NetPeerTcpBinding> classe est un transport sécurisé est conçu pour une communication efficace à l’aide de la fonctionnalité de mise en réseau pair à pair. Comme indiqué par le nom de la classe et de la liaison, TCP correspond au protocole. Lorsque le mode de sécurité a la valeur transport, la liaison implémente TLS sur TCP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]la fonctionnalité pair à pair, consultez [mise en réseau pair à pair](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding et NetMsmqBinding  
 Pour une description complète de transport de sécurité avec Message Queuing (précédemment appelé MSMQ), consultez [sécurisation des Messages à l’aide de sécurité du Transport](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de la sécurité WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)