---
title: "Liaisons fournies par le système"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c5f8df31e31c9617fe7bcd92789671d220382a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="system-provided-bindings"></a>Liaisons fournies par le système
Les liaisons spécifient le mécanisme de communication à utiliser pour communiquer avec un point de terminaison et indiquer comment se connecter à un point de terminaison. Une liaison contient les éléments suivants :  
  
-   La pile de protocole détermine la sécurité, la fiabilité et les paramètres de flux de contexte à utiliser pour les messages envoyés au point de terminaison.  
  
-   Le transport détermine le protocole de transport sous-jacent à utiliser lors de l'envoi des messages au point de terminaison, par exemple, TCP ou HTTP.  
  
-   L'encodage détermine l'encodage de câble à utiliser pour les messages envoyés au point de terminaison, par exemple, texte/XML, binaire ou MTOM (Message Transmission Optimization Mechanism).  
  
 Cette rubrique présente toutes les liaisons [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] fournies par le système. Si aucune d’entre elles ne répond aux critères exacts pour votre application, créez une liaison personnalisée. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Création de liaisons personnalisées, consultez [des liaisons personnalisées](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Une liaison sécurisée et interopérable qui prend en charge le protocole WS-Federation permet aux organisations qui sont dans une fédération d’authentifier et d’autoriser efficacement les utilisateurs.  
  
> [!IMPORTANT]
>  Sélectionnez toujours une liaison qui inclut la sécurité. Par défaut, toutes les liaisons sauf le [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) élément ont la sécurité activée. Si vous ne sélectionnez pas de liaison sécurisée ou désactivez la sécurité, veillez à protéger vos données d'une manière ou d'une autre, telle que le stockage dans un centre de données sécurisé ou sur un réseau isolé.  
  
> [!IMPORTANT]
>  N'utilisez jamais des contrats duplex avec les liaisons qui ne prennent pas en charge la sécurité ou dont la sécurité est désactivée sauf si vous sécurisez les données d'un moyen ou un autre.  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  
 Les liaisons suivantes sont fournies avec [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Liaison|Élément de configuration|Description|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Une liaison qui est appropriée pour communiquer avec les services Web conformes à WS-Basic Profil, par exemple, les services basés sur les services Web ASP.NET (ASMX). Cette liaison utilise HTTP comme le transport et texte/XML comme encodage de message par défaut.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Une liaison sécurisée et interopérable adaptée aux contrats de service non duplex.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Une liaison sécurisée et interopérable appropriée pour les contrats de service duplex ou les communications par le biais des intermédiaires SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Une liaison sécurisée et interopérable qui prend en charge le protocole WS-Federation qui permet aux organisations dans une fédération d’authentifier et d’autoriser efficacement les utilisateurs.|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding >|Liaison conçue pour consommer des services HTTP ou WebSocket qui utilise l’encodage binaire par défaut.|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding >|Liaison sécurisée conçue pour consommer des services HTTP ou WebSocket qui utilise l’encodage binaire par défaut.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Une liaison sécurisée et optimisée appropriée pour la communication entre ordinateurs entre des applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Une liaison sécurisée, fiable, optimisée appropriée pour la communication sur les ordinateurs entre des applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Une liaison mise en file d'attente qui est appropriée pour la communication entre ordinateurs entre des applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Une liaison qui permet la communication sécurisée entre plusieurs ordinateurs.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding >](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Une liaison appropriée pour la communication entre ordinateurs entre une application [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] et des applications Message Queuing existantes.|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Une liaison qui est appropriée pour communiquer avec les services Web conformes avec WS-Basic Profile, qui active des cookies HTTP en vue de leur utilisation pour échanger le contexte.|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Une liaison sécurisée et optimisée qui convient à la communication entre ordinateurs entre les applications [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], qui active des en-têtes SOAP à utiliser pour échanger le contexte.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Une liaison utilisée pour configurer des points de terminaison pour les services Web [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] exposés par le biais de requêtes HTTP au lieu de messages SOAP.|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Sécurisée et |<xref:System.ServiceModel.UdpBinding>|\<udpBinding >|Liaison à utiliser lors de l’envoi d’une rafale de messages simples à un grand nombre de clients simultanément.|  
  
 Le tableau suivant affiche les fonctionnalités de chacune des liaisons fournies par le système. Les liaisons figurent dans les colonnes du tableau ; les fonctionnalités sont répertoriées dans les lignes et décrites dans un deuxième tableau. Le tableau suivant fournit une clé pour les abréviations de liaison utilisées. Pour sélectionner une liaison, déterminez quelle colonne satisfait toutes les fonctionnalités de ligne dont vous avez besoin.  
  
|Liaison|Interopérabilité|Sécurité (valeur par défaut)|Session<br /><br /> (Default)|Transactions|Duplex|Encodage (Valeur par défaut)|Diffusion en continu<br /><br /> (Default)|  
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Aucun), transport, message, mixte|(Aucun)|(Aucun)|N/A|Texte, (MTOM)|Oui<br /><br /> (mis en mémoire tampon)|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Transport, (message), mixte|(Aucun), session fiable, session de sécurité|(Aucun), oui|N/A|(Texte), MTOM|Non|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Message), aucun|(Session fiable), session de sécurité|(Aucun), oui|Oui|(Texte), MTOM|Non|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Message), mixte, aucun|(Aucun), session fiable, session de sécurité|(Aucun), oui|Non|(Texte), MTOM|Non|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(None), Transport, Message, TransportWithMessageCredential, TransportCredentialOnly|Voir la remarque ci-dessous|Aucun.|Voir la remarque ci-dessous|(Binary), Text,MTOM|Oui (mis en mémoire tampon)|  
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Transport), TransportWithMessageCredential|Voir la remarque ci-dessous|Aucun.|Voir la remarque ci-dessous|(Binary), Text,MTOM|Oui (mis en mémoire tampon)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Transport), message, aucun, mixte|(Transport), session fiable, session de sécurité|(Aucun), oui|Oui|Binaire|Oui<br /><br /> (mis en mémoire tampon)|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Transport), aucun|Aucun, (Transport)|(Aucun), oui|Oui|Binaire|Oui<br /><br /> (mis en mémoire tampon)|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Message, (Transport), Aucun|(Aucun), Transport|Aucun, (Oui)|Non|Binaire|Non|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Peer|(Transport)|(Aucun)|(Aucun)|Oui||Non|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Transport)|(Aucun)|Aucun, (Oui)|N/A|N/A|Non|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(Aucun), transport, message, mixte|(Aucun)|(Aucun)|N/A|Texte, (MTOM)|Oui<br /><br /> (mis en mémoire tampon)|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Transport), message, aucun, mixte|(Transport), session fiable, session de sécurité|(Aucun), oui|Oui|Binaire|Oui<br /><br /> (mis en mémoire tampon)|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Transport, (message), mixte|(Aucun), session fiable, session de sécurité|(Aucun), oui|N/A|Texte, (MTOM)|Non|  
|<xref:System.ServiceModel.UdpBinding>|.NET **Remarque :** l’interopérabilité peut être obtenue en implémentant la spécification standard SOAP sur UDP implémentée par cette liaison implémente.|(Aucun)|(Aucun)|(Aucun)|N/A|(Texte)|Non|  
  
> [!IMPORTANT]
>  <xref:System.ServiceModel.NetHttpBinding> est une liaison conçue pour consommer des services HTTP ou WebSocket et utilise l'encodage binaire par défaut. <xref:System.ServiceModel.NetHttpBinding> détecte si elle est utilisée avec un contrat demande-réponse ou un contrat duplex et modifie son comportement pour le faire correspondre - elle utilise HTTP pour les contrats de demande-réponse et WebSockets pour les contrats duplex. Ce comportement peut être substitué à l’aide de la <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A>--> `System.ServiceModel.NetHttpBinding.WebSocketTransportUsage` paramètre de liaison : Allowed - il s’agit de la valeur par défaut et se comporte comme décrit ci-dessus. Non autorisé - cela empêche le WebSocket. Toute tentative d’utilisation d’un contrat duplex avec ce paramètre entraîne une exception. Obligatoire - force l’utilisation de WebSockets même pour les contrats de demande-réponse. NetHttpBinding prend en charge les sessions fiables en mode HTTP et en mode WebSocket. Les sessions en mode WebSocket sont fournies par le transport.  
  
 Le tableau suivant explique les fonctionnalités répertoriées dans le tableau précédent.  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Type d'interopérabilité|Nomme le protocole ou la technologie avec laquelle la liaison garantit l'interopérabilité.|  
|Sécurité|Définit le mode de sécurisation du canal :<br /><br /> -None : Le message SOAP n’est pas sécurisé et le client n’est pas authentifié.<br />-Transport : Les exigences de sécurité sont satisfaites au niveau de la couche de transport.<br />-Message : Les exigences de sécurité sont satisfaites au niveau de la couche de message.<br />-Mixte : Les revendications sont contenues dans le message. spécifications de l’intégrité et la confidentialité sont satisfaites par la couche de transport.|  
|Session|Spécifie si cette liaison prend en charge des contrats de session.|  
|Transactions|Spécifie si les transactions sont activées.|  
|Duplex|Spécifie si les contrats duplex sont pris en charge. Notez que cette fonctionnalité requiert la prise en charge des sessions dans la liaison.|  
|Encodage|Spécifie le format de câble du message. Les valeurs autorisées incluent :<br /><br /> -Texte : par exemple, UTF-8.<br />-Binaire<br />-Message Transmission Optimization Mechanism (MTOM) : Une méthode permettant d’encoder efficacement des éléments XML binaires dans le contexte d’une enveloppe SOAP.|  
|Diffusion en continu|Spécifie si la diffusion en continu est prise en charge pour les messages entrants et sortants. Utilisez la propriété `TransferMode` sur la liaison pour définir la valeur. Les valeurs autorisées incluent :<br /><br /> -   <xref:System.ServiceModel.TransferMode.Buffered>: Les messages de demande et de réponse sont mis en mémoire tampon.<br />-   <xref:System.ServiceModel.TransferMode.Streamed>: Les messages de demande et de réponse sont transmis en continu.<br />-   <xref:System.ServiceModel.TransferMode.StreamedRequest>: Le message de demande est transmis en continu et le message de réponse est mis en mémoire tampon.<br />-   <xref:System.ServiceModel.TransferMode.StreamedResponse>: Le message de demande est mis en mémoire tampon et le message de réponse est transmis en continu.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)
