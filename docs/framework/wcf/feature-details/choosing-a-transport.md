---
title: "Choix d&#39;un transport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "choisir les transports [WCF]"
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# Choix d&#39;un transport
Cette rubrique traite des critères permettant de choisir parmi les trois principaux transports inclus dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] : HTTP, TCP et canaux nommés.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut également un transport de mise en file d'attente de messages \(également appelé MSMQ\), mais ce document n'inclut pas la mise en file d'attente de messages.  
  
 Le modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sépare des opérations de point de terminaison \(exprimées dans un contrat de service\) du mécanisme de transport qui connecte deux points de terminaison.Vous pouvez ainsi décider du mode d'exposition de vos services sur le réseau.  
  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous spécifiez comment transférer des données sur un réseau entre des points de terminaison en utilisant une *liaison* qui se compose d'une séquence d'*éléments de liaison*.Un transport est représenté par un élément de liaison de transport qui fait partie de la liaison.Une liaison inclut des éléments de liaison de protocole facultatifs \(la sécurité par exemple\), un élément de liaison d'encodeur de message requis et un élément de liaison de transport requis.Un transport envoie ou reçoit la forme sérialisée d'un message depuis ou vers une autre application.  
  
 Si vous devez vous connecter à un client ou un serveur existant, vous n'aurez peut\-être pas le choix d'utiliser un transport particulier.Toutefois, les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être accessibles par l'intermédiaire de plusieurs points de terminaison, chacun avec un transport différent.Lorsqu'un transport unique ne couvre pas l'audience prévue pour votre service, vous pouvez exposer le service sur plusieurs points de terminaison.Les applications clientes peuvent utiliser ensuite le point de terminaison le mieux adapté.  
  
 Après avoir choisi un transport, vous devez sélectionner une liaison qui l'utilise.Vous pouvez choisir une liaison fournie par le système \(consultez [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)\), ou vous pouvez générer votre propre liaison personnalisée \(consultez [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)\).Vous pouvez également créer votre propre liaison.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## Avantages de chaque transport  
 Cette section décrit les raisons principales motivant le choix d'un des trois principaux transports, ainsi qu'un tableau de prise de décision détaillé pour effectuer ce choix.  
  
### Quand utiliser le transport HTTP  
 HTTP est un protocole de demande\/réponse entre clients et serveurs.L'application la plus courante se compose de clients de navigateur Web qui communiquent avec un serveur Web.Le client envoie une demande à un serveur qui écoute les messages de demande du client.Lorsque le serveur reçoit une demande, il renvoie une réponse qui contient l'état de la demande.Si cette demande aboutit, des données facultatives, telles qu'une page Web, un message d'erreur ou autres informations, sont retournées.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] le protocole HTTP, consultez [Protocole HTTP \(Hypertext Transfer Protocol\)](http://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Le protocole HTTP n'est pas basé sur une connexion ; une fois la réponse envoyée, aucun état n'est maintenu.Pour gérer des transactions de plusieurs pages, l'application doit rendre persistant tout état nécessaire.  
  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], la liaison de transport HTTP est optimisée pour l'interopérabilité avec les systèmes hérités non\-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Si tous les correspondants utilisent [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les liaisons basées sur des canaux nommés ou sur TCP sont plus rapides.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.NetTcpBinding> et <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### Quand utiliser le transport TCP  
 TCP est un service de remise basé sur une connexion, orienté flux qui permet la détection et la correction d'erreurs de bout en bout.*Basé sur une connexion* signifie qu'une session de communication entre des hôtes est établie avant l'échange des données.Un hôte est un périphérique sur un réseau TCP\/IP identifié par une adresse IP logique.  
  
 TCP permet une remise fiable des données tout en étant simple d'utilisation.En particulier, TCP notifie l'expéditeur de la remise de paquets, s'assure que les paquets sont remis dans le même ordre dans lequel ils sont envoyés, retransmet les paquets perdus et garantit que les paquets de données ne sont pas dupliqués.Notez que cette remise fiable s'applique entre deux nœuds TCP\/IP et ne s'apparente pas à la norme *WS\-ReliableMessaging* qui, elle, s'applique entre des points de terminaison indépendamment du nombre de nœuds intermédiaires pouvant être inclus.  
  
 Le transport TCP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est optimisé pour le scénario où les deux extrémités de la communication font appel à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Cette liaison est la liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] la plus rapide pour les scénarios qui impliquent des communications entre des ordinateurs différents.Les échanges de messages utilisent le <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> pour le transfert de messages optimisé.TCP fournit une communication duplex et peut être ainsi utilisé pour implémenter des contrats duplex, même si le client est placé derrière une traduction d'adresses réseau \(NAT\).  
  
### Quand utiliser le transport de canal nommé  
 Un canal nommé est un objet dans le noyau du système d'exploitation Windows, tel qu'une portion de mémoire partagée utilisée par les processus pour la communication.Un canal nommé possède un nom et peut être utilisé pour la communication unidirectionnelle ou duplex entre des processus sur un ordinateur unique.  
  
 Lorsque la communication est requise entre des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] différentes sur un ordinateur unique, et que vous souhaitez empêcher toute communication provenant d'un autre ordinateur, utilisez le transport de canaux nommés.Une restriction supplémentaire est que les processus qui s'exécutent du Bureau à distance Windows peuvent être limités à la même session de Bureau à distance Windows sauf s'ils possèdent des privilèges élevés.  
  
> [!WARNING]
>  Si vous utilisez le transport de canal nommé avec une réservation d'URL WeakWildcard sur plusieurs sites hôtes hébergés dans IIS, l'erreur suivante peut se produire : Une ereur s'est produite dans le service d'activation « NetPipeActivator » du protocole « net.pipe » lors d'une tentative d'écoute du site « 2 » ; le protocole est par conséquent désactivé momentanément pour le site. Pour plus d'informations, consultez le message d'exception. URL : WeakWildcard:net.pipe:\/\<ordinateur\>\/ État : ConflictingRegistration Exception :  Nom du processus : SMSvcHost ID de processus : 1076\\  
  
## Points de décision permettant de choisir un transport  
 Le tableau suivant décrit les points de décision courants permettant de choisir un transport.Vous devez considérer tous les attributs et les transports supplémentaires qui s'appliquent à votre application.Identifiez les attributs qui sont importants pour votre application, les transports qui s'associent le mieux à chacun de vos attributs, puis sélectionnez les transports qui fonctionnent le mieux avec votre jeu d'attributs.  
  
|Attribut|Description|Transports préconisés|  
|--------------|-----------------|---------------------------|  
|Diagnostics|Les diagnostics vous permettent de détecter automatiquement les problèmes de connectivité de transport.Tous les transports prennent en charge la possibilité de renvoyer des informations de panne qui décrivent la connectivité.Cependant, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'inclut pas d'outils de diagnostics pour analyser les problèmes de réseau.|Aucun|  
|Hébergement|Tous les points de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doivent être hébergés dans une application.[!INCLUDE[iis601](../../../../includes/iis601-md.md)] et les versions antérieures ne prennent en charge que l'hébergement des applications qui utilisent le transport HTTP.Sur [!INCLUDE[wv](../../../../includes/wv-md.md)], une prise en charge est ajoutée pour héberger tous les transports [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], notamment les transports TCP et canaux nommés.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Hébergement dans les services IIS \(Internet Information Services\)](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) et [Hébergement dans le service d'activation de processus de Windows \(WAS, Windows Process Activation Service\)](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Inspection|L'inspection est la capacité d'extraire et de traiter les informations des messages au cours de la transmission.Le protocole HTTP effectue le tri entre les informations de routage et de contrôle, et les données, ce qui simplifie la création d'outils chargés d'inspecter et d'analyser des messages.Les transports qui sont faciles à inspecter peuvent également nécessiter une puissance de traitement moindre dans les appareils de réseau.Le niveau de sécurité utilisé détermine la possibilité d'inspecter ou non les messages.|HTTP|  
|Latence|La latence est la durée minimale requise pour procéder à un échange de messages.Toutes les opérations de réseau offrent plus ou moins de latence selon le choix de transport.L'utilisation de la communication en duplex ou unidirectionnelle avec un transport dont le modèle d'échange de messages natif est demande\/réponse \(HTTP, par exemple\) peut provoquer une latence supplémentaire en raison de la corrélation forcée des messages.Dans ce cas, vous pouvez utiliser un transport dont le modèle d'échange de messages natif est duplex, tel que TCP.|TCP, Canal<br /><br /> nommé|  
|Portée|La portée d'un transport décrit la capacité de connexion de ce transport avec d'autres systèmes.Le transport de canal nommé a une portée très réduite ; il peut se connecter uniquement aux services qui s'exécutent sur le même ordinateur.Les transports TCP et HTTP ont une portée excellente et peuvent pénétrer des configurations NAT et de pare\-feu.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Utilisation des NAT et des pare\-feu](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Sécurité|La sécurité est la capacité à protéger des messages au cours du transfert en fournissant la confidentialité, l'intégrité ou l'authentification.La confidentialité empêche l'analyse d'un message, l'intégrité empêche sa modification et l'authentification garantit l'expéditeur ou le destinataire du message.<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge la sécurité à la fois au niveau du message et au niveau du transport.La sécurité du message compose avec un transport si le transport prend en charge un mode de transfert mis en mémoire tampon.La prise en charge de la sécurité du transport varie selon le choix du transport.Les transports HTTP, TCP et de canal nommé gèrent de manière similaire la prise en charge de la sécurité du transport.|Tous|  
|Débit|Le débit mesure la quantité de données qui peuvent être transmises et traitées dans une période spécifiée.Comme pour la latence, le choix du transport peut affecter le débit pour les opérations de service.Pour augmenter le débit pour un transport, il est nécessaire de réduire à la fois les charges mémoire de transmission du contenu et la durée d'attente pour les échanges de messages.Les transports TCP et de canaux nommés ajoutent peu de charges mémoire au corps du message et prennent en charge une forme duplex native qui réduit le temps de réponse des messages.|TCP, canal nommé|  
|Outillage|L'outillage correspond à la prise en charge par des applications tierces d'un protocole pour le développement, le diagnostic, l'hébergement et autres activités.Le développement d'outils et de logiciels compatibles avec le protocole HTTP implique un investissement particulièrement important.|HTTP|  
  
## Voir aussi  
 <xref:System.ServiceModel.BasicHttpBinding>   
 <xref:System.ServiceModel.WsHttpBinding>   
 <xref:System.ServiceModel.WsDualHttpBinding>   
 <xref:System.ServiceModel.WsFederationHttpBinding>   
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>   
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>   
 <xref:System.ServiceModel.NetNamedPipeBinding>   
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
 [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)   
 [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)   
 [Création de liaisons définies par l'utilisateur](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)