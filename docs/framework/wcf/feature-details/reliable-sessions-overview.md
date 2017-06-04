---
title: "Vue d&#39;ensemble des sessions fiables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: 30
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 30
---
# Vue d&#39;ensemble des sessions fiables
La messagerie fiable SOAP de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit une fiabilité de transfert de messages de bout en bout entre des points de terminaison SOAP.Elle permet cela sur des réseaux peu fiables en remédiant aux échecs de transport et aux échecs au niveau du message SOAP.Notamment, elle fournit une remise basée sur session, unique et ordonnée \(facultativement\) pour les messages envoyés via SOAP ou des intermédiaires de transport.La remise basée sur session groupe des messages dans une session et permet l'ordonnancement facultatif des messages.  
  
 La discussion suivante explique ce qu'est une session fiable, comment et quand l'utiliser, et comment la sécuriser.  
  
## Sessions fiables WCF  
 Les sessions fiables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont une implémentation de la messagerie fiable SOAP, comme défini par le protocole WS\-ReliableMessaging.  
  
 La messagerie fiable SOAP de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une session fiable de bout en bout entre deux points de terminaison, indépendamment du nombre ou du type des intermédiaires qui séparent les points de terminaison de messagerie.Au rang de ces intermédiaires figurent notamment tous les transports qui n'utilisent pas le protocole SOAP \(par exemple, les proxys HTTP\) ou les intermédiaires qui utilisent SOAP \(par exemple, les routeurs ou les ponts SOAP\), nécessaires à la circulation des messages entre les points de terminaison.Un canal de session fiable prend en charge la communication « interactive » afin que les services connectés par ce canal s'exécutent concurremment et puissent échanger et traiter des messages dans des conditions de latence basse, autrement dit, dans des intervalles relativement courts.Ce couplage signifie que ces composants progressent ensemble ou échouent ensemble, donc ils ne sont pas isolés les uns des autres.  
  
 Une session fiable masque deux types d'échecs :  
  
-   Échecs au niveau du message SOAP, incluant les messages perdus ou dupliqués et les messages qui arrivent dans un ordre différent de l'ordre dans lequel ils ont été envoyés.  
  
-   Échecs de transport  
  
 Une session fiable implémente le protocole WS\-ReliableMessaging et une fenêtre de transfert en mémoire pour masquer les échecs au niveau du message SOAP et rétablit des connexions en cas d'échecs de transport.  
  
 Une session fiable gère les messages SOAP de la même façon que TCP gère les paquets IP.Une connexion de socket TCP fournit un transfert unique et symétrique des paquets IP entre les nœuds.Le canal fiable fournit le même type de transfert fiable, mais il diffère de la fiabilité fournie par le socket TCP des façons suivantes :  
  
-   La fiabilité est fournie au niveau du message SOAP, non pour un paquet d'octets arbitrairement dimensionné.  
  
-   La fiabilité est fournie dans le cadre d'un transport neutre, pas seulement pour le transfert sur TCP.  
  
-   La fiabilité n'est pas attachée à une session de transport particulière \(par exemple, la session qu'une connexion TCP fournit\) et peut utiliser simultanément ou séquentiellement des sessions de transport multiples sur la durée de vie de la session fiable.  
  
-   La session fiable existe entre les points de terminaison SOAP de l'expéditeur et du récepteur, indépendamment du nombre de connexions de transport requis pour la connectivité entre eux.En résumé, la fiabilité TCP termine là où la connexion de transport s'arrête, alors qu'une session fiable fournit une fiabilité de bout en bout.  
  
## Sessions et liaisons fiables  
 Comme mentionné précédemment, une session fiable est un transport neutre et elle peut, par conséquent, être implémentée sur de nombreux transports.Par ailleurs, une session fiable peut être établie selon de nombreux modèles d'échange de messages, tels que la demande\-réponse ou le duplex.La session fiable de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est par conséquent exposée comme une propriété d'un jeu de liaisons.  
  
 Vous pouvez utiliser une session fiable sur les points de terminaison qui utilisent :  
  
-   Des liaisons standard de transport basées sur HTTP :  
  
    -   `WsHttpBinding` et expose des contrats demande\-réponse ou unidirectionnels.  
  
    -   Peut être utilisé lors de l'utilisation de la session fiable sur un contrat de service demande\-réponse ou unidirectionnel simple.  
  
    -   `WsDualHttpBinding` et expose des contrats duplex, demande\-réponse ou unidirectionnels.  
  
    -   `WsFederationHttpBinding` et expose des contrats demande\-réponse ou unidirectionnels.  
  
-   Des liaisons standard de transport basées sur TCP :  
  
    -   `NetTcpBinding` et expose des contrats duplex, demande\-réponse ou unidirectionnels.  
  
 Vous pouvez également utiliser une session fiable sur tout autre type de liaison en créant une liaison personnalisée, telle qu'une liaison HTTPS \(pour plus d'informations à ce sujet, consultez « Sessions fiables et sécurité », plus loin dans cette rubrique\) ou une liaison de canal nommée.  
  
 Une session fiable peut être empilée sur différents types de canaux sous\-jacents et la forme du canal de session fiable résultante varie.Sur le client et sur le serveur, le type de canal de session fiable pris en charge dépend du type de canal sous\-jacent qui est utilisé.Le tableau suivant répertorie les types de canaux de session pris en charge sur le client en fonction du type de canal sous\-jacent.  
  
|Types de canaux de session fiable pris en charge \(valeurs prises en charge de `TChannel` en fonction du type de canal sous\-jacent\)|`IRequestChannel`|`IRequestSessionChanne`l|`IDuplexChannel`|`IDuplexSessionChannel`|  
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|------------------------------|----------------------|-----------------------------|  
|`IOutputSessionChannel`|Oui|Oui|Oui|Oui|  
|`IRequestSessionChannel`|Oui|Oui|Non|Non|  
|`IDuplexSessionChannel`|Non|Non|Oui|Oui|  
  
 Les types de canaux pris en charge sont les valeurs disponibles pour la valeur de paramètre `TChannel` générique passée dans la méthode <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29>.  
  
 Le tableau suivant répertorie les types de canaux de session pris en charge sur le serveur en fonction du type de canal sous\-jacent.  
  
|Types de canaux de session fiable pris en charge \(valeurs prises en charge de `TChannel` en fonction du type de canal sous\-jacent\)|`IReplyChannel`|`IReplySessionChannel`|`IDuplexChannel`|`IDuplexSessionChannel`|  
|-------------------------------------------------------------------------------------------------------------------------------------------|---------------------|----------------------------|----------------------|-----------------------------|  
|`IInputSessionChannel`|Oui|Oui|Oui|Oui|  
|`IReplySessionChannel`|Oui|Oui|Non|Non|  
|`IDuplexSessionChannel`|Non|Non|Oui|Oui|  
  
 Les types de canaux pris en charge sont les valeurs disponibles pour la valeur de paramètre `TChannel` générique passée dans la méthode <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29>.  
  
## Sessions fiables et sécurité  
 La sécurisation d'une session fiable est importante pour garantir que les participants à la communication \(service et client\) sont authentifiés et que les messages échangés dans la session ne sont pas falsifiés.En outre, il est important de garantir l'intégrité de chaque session fiable.Une session fiable est sécurisée en la liant à un contexte de sécurité qui est représenté et géré par un canal de session de sécurité.Le canal de sécurité fournit une session de sécurité.Les jetons de sécurité échangés pendant l'établissement de la session sont ensuite utilisés pour sécuriser les messages dans la session fiable.  
  
 Lorsque la session fiable est sur TCP\-S, la session TCP est attachée à la session fiable et, par conséquent, la sécurité de transport garantit que la sécurité est également attachée à la session fiable.Dans ce cas, le rétablissement de la connexion est désactivé.  
  
 La seule exception est l'utilisation du protocole HTTPS.La session SSL \(Secure Sockets Layer\) n'est pas liée à la session fiable.Cela constitue une menace parce que les sessions qui partagent un contexte de sécurité \(la session SSL\) ne sont pas protégées l'une par rapport à l'autre ; cela peut représenter ou non une véritable menace, selon l'application.  
  
## Utilisation de sessions fiables  
 Pour utiliser les sessions fiables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], créez un point de terminaison avec une liaison prenant en charge une session fiable.Utilisez l'une des liaisons fournies par le système que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit avec la session fiable activée, ou créez votre propre liaison personnalisée.Les liaisons définies par le système qui prennent en charge et activent une session fiable par défaut incluent :  
  
-   <xref:System.ServiceModel.WSDualHttpBinding>  
  
 Les liaisons fournies par le système qui prennent en charge une session fiable en option mais qui n'activent pas de session fiable par défaut incluent :  
  
-   <xref:System.ServiceModel.WSHttpBinding>  
  
-   <xref:System.ServiceModel.WSFederationHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
 Pour un exemple de création d'une liaison personnalisée, consultez [Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).  
  
 Pour en savoir plus sur les liaisons [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui prennent en charge des sessions fiables, consultez [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## Quand utiliser des sessions fiables  
 Il est important de comprendre quand utiliser des sessions fiables dans votre application.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge des sessions fiables entre les points de terminaison qui sont actifs en même temps.Si votre application requiert que l'un des points de terminaison soit indisponible pour une certaine durée, vous pouvez utiliser des files d'attente pour assurer la fiabilité.  
  
 Si le scénario requiert que deux points de terminaison soient connectés sur TCP, alors TCP peut suffire à fournir l'échange fiable des messages, bien qu'il ne soit pas nécessaire d'utiliser une session fiable ; TCP garantit que les paquets arrivent dans l'ordre et uniquement une fois.  
  
 Si votre scénario présente l'une des caractéristiques suivantes, vous devez sérieusement envisager d'utiliser une session fiable :  
  
-   Intermédiaires SOAP, tels que les routeurs SOAP.  
  
-   Intermédiaires proxy ou ponts de transport.  
  
-   Connectivité intermittente.  
  
-   Sessions sur HTTP.  
  
## Voir aussi  
 [Utilisation de liaisons pour configurer des services et des clients](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md)