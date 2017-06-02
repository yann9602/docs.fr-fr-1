---
title: "S&#233;curit&#233; des applications distribu&#233;es | Microsoft Docs"
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
helpviewer_keywords: 
  - "sécurité des applications distribuées (WCF)"
  - "sécurité (WCF), transfert"
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: 32
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 32
---
# S&#233;curit&#233; des applications distribu&#233;es
La sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est divisée en trois domaines fonctionnels principaux : la sécurité de transfert, le contrôle d'accès et l'audit.La sécurité de transfert fournit l'intégrité, la confidentialité et l'authentification.La sécurité de transfert est fournie par l'un des éléments suivants : sécurité de transport, sécurité de message ou `TransportWithMessageCredential`.  
  
 Pour une vue d'ensemble de la sécurité de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les deux autres éléments de la sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) et [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## Scénarios de sécurité de transfert  
 Les scénarios courants qui utilisent la sécurité de transfert [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont les suivants :  
  
-   Transfert sécurisé à l'aide de Windows.Un service et un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont déployés dans un domaine Windows \(ou forêt Windows\).Les messages contenant des données personnelles, les spécifications incluent donc l'authentification mutuelle du client et du service, l'intégrité et la confidentialité des messages.En outre, la preuve est requise qu'une transaction spécifique s'est produite ; à titre d'exemple, le récepteur du message doit enregistrer les informations de signature.  
  
-   Transfert sécurisé à l'aide de `UserName` et HTTPS.Un service et un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doivent être développés pour fonctionner sur Internet.Les informations d'identification du client permettent d'effectuer l'authentification par rapport à une base de données de paires nom d'utilisateur\/mot de passe.Le service est déployé à une adresse HTTPS à l'aide d'un certificat SSL \(Secure Sockets Layer\) approuvé.Les messages transitant sur Internet, le client et le service doivent donc être mutuellement authentifiés, et la confidentialité et l'intégrité des messages doivent être conservées pendant le transfert.  
  
-   Transfert sécurisé à l'aide de certificats.Un service et un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doivent être développés pour fonctionner sur Internet.Le client et le service ont tous deux des certificats qui permettent de sécuriser les messages.Le client et le service utilisent Internet pour communiquer l'un avec l'autre et exécuter des transactions à forte valeur qui requièrent l'intégrité des messages, la confidentialité et l'authentification mutuelle.  
  
## Intégrité, confidentialité et authentification  
 Ces trois fonctions \(intégrité, confidentialité et authentification\) forment ensemble la « sécurité de transfert ».La sécurité de transfert fournit les fonctions permettant de limiter les menaces auxquelles est exposée une application distribuée.Le tableau suivant décrit brièvement les trois fonctions qui composent la sécurité de transfert.  
  
|Fonction|Description|  
|--------------|-----------------|  
|Intégrité|L'*intégrité* est l'assurance que les données sont complètes et exactes, tout particulièrement après qu'elles aient transité d'un point vers un autre, et éventuellement qu'elles aient été lues par de nombreux acteurs.L'intégrité doit être maintenue afin d'empêcher toute falsification à l'aide des données, et elle est généralement assurée par la signature numérique d'un message.|  
|Confidentialité|La *confidentialité* est l'assurance qu'un message n'a pas été lu par une personne autre que le lecteur prévu.Par exemple, un numéro de carte de crédit doit rester confidentiel lorsqu'il est envoyé sur Internet.La confidentialité est souvent fournie par le chiffrement des données à l'aide d'un schéma de clé publique\/clé privée.|  
|Authentification|L'*authentification* est la vérification d'une identité déclarée.Par exemple, lors de l'utilisation d'un compte bancaire, il est impératif que seul le propriétaire réel de ce compte soit autorisé à retirer des fonds.L'authentification peut être fournie par divers moyens.L'une des méthodes fréquemment utilisées est le système nom d'utilisateur\/mot de passe.Une autre consiste à utiliser un certificat X.509 fourni par un tiers.|  
  
## Modes de sécurité  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a plusieurs modes de sécurité de transfert décrits dans le tableau suivant.  
  
|Mode|Description|  
|----------|-----------------|  
|None|Aucune sécurité n'est fournie au niveau de la couche de transport ou de la couche de message.Aucune des liaisons prédéfinies n'utilisent ce mode par défaut à l'exception de l'élément [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) ou, lors de l'utilisation du code, de la classe <xref:System.ServiceModel.BasicHttpBinding>.|  
|Transport|Utilise un transport sécurisé tel que HTTPS pour l'intégrité, la confidentialité et l'authentification mutuelle.|  
|Message|Utilise la sécurité de message SOAP pour l'intégrité, la confidentialité et l'authentification mutuelle.Les messages SOAP sont sécurisés conformément aux standards WS\-Security.|  
|Mixed Mode|Utilise la sécurité de transport pour l'intégrité, la confidentialité et l'authentification du serveur.Utilise la sécurité de message \(WS\-Security et autres standards\) pour l'authentification du client.<br /><br /> \(Cette énumération pour ce mode est `TransportWithMessageCredential`.\)|  
|Both|Effectue la protection et l'authentification aux deux niveaux.Ce mode est uniquement disponible dans l'élément [\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).|  
  
## Informations d'identification et sécurité de transfert  
 Les *informations d'identification* sont des données présentées pour établir une identité ou des fonctions déclarées.La présentation d'informations d'identification implique la présentation à la fois des données et la preuve de la propriété de ces données.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge divers types d'informations d'identification au niveau de la sécurité du transport et des messages.Vous pouvez spécifier un type d'information d'identification pour une liaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Dans de nombreux pays ou régions, le permis de conduire est un exemple d'information d'identification.Un permis contient des données qui représentent l'identité d'une personne et des fonctions.Il contient la preuve de la propriété sous la forme de la photographie du propriétaire.Le permis est délivré par une autorité approuvée, généralement un service public chargé de cette fonction.Le permis est scellé, et peut contenir un hologramme indiquant qu'il n'a pas été falsifié.  
  
 Examinons par exemple deux types d'informations d'identification pris en charge dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] : informations d'identification de nom d'utilisateur et de certificat \(X.509\).  
  
 Concernant les informations d'identification de nom d'utilisateur, le nom d'utilisateur représente l'identité déclarée et le mot de passe présente la preuve de la propriété.L'autorité approuvée dans ce cas est le système qui valide le nom d'utilisateur et le mot de passe.  
  
 Dans l'information d'identification de certificat, le nom du sujet, le nom de substitution du sujet ou des champs spécifiques inclus dans le certificat peuvent être utilisés pour représenter l'identité déclarée et\/ou les fonctions.La preuve de la propriété des données dans l'information d'identification est établie en utilisant la clé privée associée pour générer une signature.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la programmation de la sécurité de transfert et la spécification des informations d'identification, consultez [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) et [Comportements de sécurité](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### Types d'informations d'identification du client de transport  
 Le tableau suivant présente les valeurs possibles utilisées lors de la création d'une application utilisant la sécurité de transfert.Vous pouvez utiliser ces valeurs dans le code ou les paramètres de liaison.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|Aucune|Spécifie que le client n'a pas besoin de présenter d'information d'identification.Cela se traduit en un client anonyme.|  
|Basic|Spécifie l'authentification de base.Pour plus d'informations, consultez la RFC 2617 « [Authentification HTTP : Authentification de base et Digest](http://go.microsoft.com/fwlink/?LinkId=88313) » \(page pouvant être en anglais\).|  
|Digest|Spécifie l'authentification Digest.Pour plus d'informations, consultez la RFC 2617 « [Authentification HTTP : Authentification de base et Digest](http://go.microsoft.com/fwlink/?LinkId=88313) » \(page pouvant être en anglais\).|  
|Ntlm|Spécifie l'authentification Windows à l'aide de la négociation SSPI sur un domaine Windows.<br /><br /> La négociation SSPI entraîne l'utilisation du protocole Kerberos ou NTLM \(NT LanMan\).|  
|Windows|Spécifie l'authentification Windows à l'aide de SSPI sur un domaine Windows.SSPI sélectionne le protocole Kerberos ou NTLM comme service d'authentification.<br /><br /> SSPI tente d'abord d'utiliser le protocole Kerberos ; en cas d'échec, il utilise NTLM.|  
|Certificate|Exécute l'authentification du client à l'aide d'un certificat, en général X.509.|  
  
### Types d'informations d'identification du client de message  
 Le tableau suivant présente les valeurs possibles utilisées lors de la création d'une application utilisant la sécurité de message.Vous pouvez utiliser ces valeurs dans le code ou les paramètres de liaison.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|Aucune|Autorise le service à interagir avec des clients anonymes.|  
|Authentification Windows|Autorise les échanges de messages SOAP à se produire sous le contexte authentifié d'une information d'identification Windows.Utilise le mécanisme de négociation SSPI pour sélectionner le protocole Kerberos ou NTLM comme service d'authentification.|  
|Username|Autorise le service à imposer que le client soit authentifié à l'aide d'une information d'identification de nom d'utilisateur.Notez que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'autorise pas d'opération de chiffrement avec le nom d'utilisateur, telle que la génération d'une signature ou le chiffrement de données.De ce fait, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que le transport est sécurisé lors de l'utilisation d'informations d'identification de nom d'utilisateur.|  
|Certificat|Autorise le service à imposer que le client soit authentifié à l'aide d'un certificat.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Autorise le service à imposer que le client soit authentifié à l'aide d'un [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### Programmation d'informations d'identification  
 Pour chacun des types d'informations d'identification du client, le modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet de spécifier les valeurs et validateurs d'informations d'identification en utilisant des comportements de service et de canal.  
  
 La sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a deux types d'informations d'identification : comportements d'informations d'identification de service et comportements d'informations d'identification de canal.Les comportements d'informations d'identification dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifient les données réelles, à savoir, les informations d'identification utilisées pour satisfaire les conditions de sécurité exprimées par les liaisons.Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], une classe de client est le composant runtime qui effectue la conversion entre l'appel d'opération et les messages.Tous les clients héritent de la classe <xref:System.ServiceModel.ClientBase%601>.La propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> sur la classe de base vous permet de spécifier différentes valeurs d'informations d'identification du client.  
  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les comportements de service sont des attributs appliqués à la classe qui implémente un contrat de service \(interface\) pour contrôler le service par programme.La classe <xref:System.ServiceModel.Description.ServiceCredentials> vous permet de spécifier des certificats pour les informations d'identification du service et des paramètres de validation de client pour divers types d'informations d'identification du client.  
  
### Modèle de négociation pour la sécurité de message  
 Le mode de sécurité du message vous permet d'exécuter la sécurité de transfert afin que les informations d'identification du service soient configurées au niveau du client hors bande.Par exemple, si vous utilisez un certificat stocké dans le magasin de certificats Windows, vous devez utiliser un outil tel qu'un composant logiciel enfichable MMC \(Microsoft Management Console\).  
  
 Le mode de sécurité du message vous permet également d'exécuter la sécurité de transfert afin que les informations d'identification du service soient échangées avec le client dans le cadre d'une négociation initiale.Pour activer la négociation, affectez `true` à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A>.  
  
## Voir aussi  
 [Vue d'ensemble de la création de points de terminaison](../../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)   
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)