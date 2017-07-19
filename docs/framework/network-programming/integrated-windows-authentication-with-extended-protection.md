---
title: "Authentification Windows int&#233;gr&#233;e avec protection &#233;tendue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# Authentification Windows int&#233;gr&#233;e avec protection &#233;tendue
Les améliorations ont été apportées à cet affectent la façon dont l'authentification Windows intégrée est gérée par <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, et les classes associées dans <xref:System.Net> et les espaces de noms associés.  La prise en charge a été ajouté pour la protection étendue améliore la sécurité.  
  
 Ces modifications peuvent affecter les applications qui utilisent ces classes pour faire des demandes de site Web et de recevoir des réponses où l'authentification Windows intégrée est utilisée.  Cette modification peut également effectuer les serveurs Web et des applications clientes qui sont configurés pour utiliser l'authentification Windows intégrée.  
  
 Ces modifications peuvent également affecter les applications qui utilisent ces classes pour effectuer d'autres types d'applications et de recevoir des réponses où l'authentification Windows intégrée est utilisée.  
  
 Les modifications pour prendre en charge la protection étendue sont uniquement disponibles pour les applications sous Windows 7 et Windows Server 2008 R2.  Les fonctionnalités de protection étendues ne sont pas disponibles dans les versions antérieures de Windows.  
  
## Vue d'ensemble  
 La conception de l'authentification Windows intégrée permet à quelques réponses aux demandes d'informations d'identification d'être universelles, ce qui signifie qu'elles peuvent être réutilisées ou transférées.  Les réponses de difficulté doivent être construites au minimum avec des informations spécifiques cibles et de préférence également avec des informations spécifiques du canal.  Les services peuvent ensuite assurer la protection étendue pour garantir que les réponses informations d'identification de difficulté contiennent des informations spécifiques de service telles qu'un nom de clé du service \(SPN\).  Avec ces informations dans les échanges d'identification, les services peuvent mieux protéger contre une utilisation malveillante des réponses informations d'identification de difficulté qui auraient pu être utilisées de manière incorrecte.  
  
 La conception étendue de protection est une amélioration aux fournisseurs d'authentification conçus pour atténuer les attaques suivre d' authentification.  Il tourne autour de le concept des informations de liaison de canal et de service.  
  
 Les objectifs globaux sont les suivants :  
  
1.  Si le client est mis à jour pour prendre en charge la protection étendue, les applications doivent fournir les informations de liaison de liaison et de service de canal à tous les fournisseurs d'authentification pris en charge.  Les informations de liaison de canal la peuvent être fournies lorsqu'il existe un canal \(TLS\) à la liaison.  Les informations de liaison de service doit toujours être fournies.  
  
2.  Les serveurs mis à jour qui sont correctement configurés peuvent vérifier les informations de liaison de canal et de service lorsqu'elles sont présentes dans le jeton d'authentification du client et rejeter la tentative d'authentification si les liaisons de canal ne correspondent pas.  Selon le scénario de déploiement, les serveurs peuvent vérifier la liaison de canal, la liaison de service ou les deux.  
  
3.  Les serveurs mis à jour ont la capacité d'accepter ou de rejeter les demandes du client de bas niveau qui ne contiennent pas d'informations de liaison de canal selon la stratégie.  
  
 Les informations utilisées par la protection étendue se composent d'une ou des deux deux parties suivantes :  
  
1.  Un jeton de liaison de canal ou FAO.  
  
2.  Les informations de liaison de service sous la forme d'un nom de clé du service ou de SPN.  
  
 Les informations de liaison de service sont une indication de l'intention d'un client d'authentifier à un point de terminaison de service particulier.  Elles sont communiquées du client au serveur avec les propriétés suivantes :  
  
-   La valeur de SPN doit être disponible pour le serveur exécutant l'authentification du client sous forme de texte clair.  
  
-   La valeur du SPN est publique.  
  
-   Le SPN fort doit être protégé en transit tels qu'une attaque de l'intercepteur ne peut pas insérer, supprimer ou modifier sa valeur.  
  
 FAO est une propriété du canal sécurisé externe \(tel que le TLS\) utilisé pour lier l'\(liaison\) à une conversation sur un canal interne et client authentifié.  FAO doit avoir les propriétés suivantes \(également définies par la norme RFC 5056 d'IETF\) :  
  
-   Lorsqu'un canal externe existe, la valeur de FAO doit être une propriété identificateur le canal externe ou le point de terminaison de serveur, indépendamment atteint par les deux côtés de client et serveur d'une conversation.  
  
-   La valeur de FAO envoyé par le client ne doit pas être quelque chose qu'un agresseur peut influencer.  
  
-   Aucune garantie n'est effectuée sur le secret de la valeur de FAO.  Toutefois cela ne signifie pas que la valeur des informations de liaison de liaison ainsi que de canal de service peut toujours être inspectée par tout autre mais le serveur exécutant l'authentification, comme protocole acheminant FAO peut l'chiffrer.  
  
-   FAO doit être fort état est protégé en transit tels qu'un intrus ne peut pas insérer, supprimer ou modifier sa valeur.  
  
 La liaison de canal la est accomplie par le client en transférant le SPN et le FAO au serveur de façon inaltérable.  Le serveur valide les informations de liaison de canal conformément à sa stratégie et rejette les tentatives d'authentification pour lesquelles elle ne se pense pas avoir été la cible attendue.  Ainsi, les deux canaux sont fort liée ensemble.  
  
 Pour conserver la compatibilité avec les clients existants et les applications, un serveur peut être configuré pour autoriser les tentatives d'authentification par les clients qui ne prennent pas encore la protection étendue.  On parle alors un paramètre « partiellement renforcée », contrairement à une configuration « entièrement renforcée ».  
  
 Plusieurs composants dans <xref:System.Net> et les espaces de noms d' <xref:System.Net.Security> exécutent l'authentification Windows intégrée de la part d'une application appelante.  Cette section décrit les composants de System.Net pour ajouter une protection étendue dans leur utilisation de l'authentification Windows intégrée.  
  
 La protection étendue est actuellement pris en charge sous Windows 7.  Un mécanisme est fourni par une application peut déterminer si le système d'exploitation prend en charge la protection étendue.  
  
## Modifications pour prendre en charge la protection étendue  
 La procédure d'authentification utilisée avec l'authentification Windows intégrée, selon le fournisseur d'authentification utilisé, comprend généralement un défi émise par l'ordinateur de destination et en arrière envoyé à l'ordinateur client.  La protection étendue ajoute de nouvelles fonctionnalités à cette procédure d'authentification  
  
 L'espace de noms <xref:System.Security.Authentication.ExtendedProtection> fournit une prise en charge pour l'authentification à l'aide de la protection étendue pour les applications.  La classe d' <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> dans cet espace de noms représente une liaison du canal.  La classe d' <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> dans cet espace de noms représente la stratégie de protection étendue utilisée par le serveur pour valider les connexions entrantes cliente.  d'autres membres de classe sont utilisés avec la protection étendue.  
  
 Pour les applications serveur, ces classes sont les suivants :  
  
 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> qui possède les éléments suivants :  
  
-   Une propriété d' <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> qui indique si le système d'exploitation prend en charge l'authentification intégrée de windows avec la protection étendue.  
  
-   Valeur <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> qui indique quand la stratégie de protection étendue doit être appliquée.  
  
-   Une valeur d' <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> qui indique le cas de déploiement.  Cela influences comment la protection étendue est activée.  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> facultatif qui contient la liste de le personnalisé SPN utilisée pour correspondre à la SPN a fourni par le client comme cible attendue de l'authentification.  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> facultatif qui contient une liaison personnalisée de canal à utiliser pour la validation.  Ce scénario n'est pas un cas courant  
  
 L'espace de noms <xref:System.Security.Authentication.ExtendedProtection.Configuration> fournit une prise en charge pour la configuration de l'authentification à l'aide de la protection étendue pour les applications.  
  
 Plusieurs modifications de fonctionnalités étaient font prendre en charge la protection étendue dans l'espace de noms existant d' <xref:System.Net> .  Ces modifications sont les suivants :  
  
-   Une nouvelle classe d' <xref:System.Net.TransportContext> a été ajoutée à l'espace de noms d' <xref:System.Net> qui représente un contexte de transport.  
  
-   Nouvel <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> les méthodes et de la surcharge d' <xref:System.Net.HttpWebRequest.GetRequestStream%2A> dans <xref:System.Net.HttpWebRequest> classe qui permettent de récupérer <xref:System.Net.TransportContext> pour prendre en charge la protection étendue pour les applications clientes.  
  
-   Ajouts aux classes d' <xref:System.Net.HttpListener> et d' <xref:System.Net.HttpListenerRequest> pour prendre en charge les applications serveur.  
  
 Une modification de fonctionnalité a été faite pour prendre en charge la protection étendue pour les applications clientes SMTP dans l'espace de noms existant d' <xref:System.Net.Mail> :  
  
-   Une propriété d' <xref:System.Net.Mail.SmtpClient.TargetName%2A> dans la classe d' <xref:System.Net.Mail.SmtpClient> qui représente le SPN à utiliser pour l'authentification à l'aide d'un étendu la protection pour les applications clientes SMTP.  
  
 Plusieurs modifications de fonctionnalités étaient font prendre en charge la protection étendue dans l'espace de noms existant d' <xref:System.Net.Security> .  Ces modifications sont les suivants :  
  
-   Nouvel <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> les méthodes et de la surcharge d' <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> dans <xref:System.Net.Security.NegotiateStream> classe qui permettent de passer FAO pour prendre en charge la protection étendue pour les applications clientes.  
  
-   Nouvel <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> les méthodes et de la surcharge d' <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> dans <xref:System.Net.Security.NegotiateStream> classe qui permettent de passer <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> pour prendre en charge la protection étendue pour les applications serveur.  
  
-   Une nouvelle propriété d' <xref:System.Net.Security.SslStream.TransportContext%2A> dans la classe d' <xref:System.Net.Security.SslStream> pour prendre en charge la protection étendue pour les applications de client et serveur.  
  
 Une propriété d' <xref:System.Net.Configuration.SmtpNetworkElement> a été ajoutée à la configuration de prise en charge de la protection étendue pour les clients SMTP dans l'espace de noms d' <xref:System.Net.Security> .  
  
## Protection étendue pour les applications clientes  
 La prise en charge étendue de protection de la plupart des applications clientes se produit automatiquement.  La prise en charge des classes d' <xref:System.Net.HttpWebRequest> et d' <xref:System.Net.Mail.SmtpClient> a étendu la protection chaque fois que la version de Windows sous\-jacente prend en charge la protection étendue.  Une instance d' <xref:System.Net.HttpWebRequest> envoie un SPN construit d' <xref:System.Uri>.  Par défaut, une instance d' <xref:System.Net.Mail.SmtpClient> envoie un SPN construit du nom d'hôte du Serveur de messagerie SMTP.  
  
 Pour l'authentification personnalisée, les applications clientes peuvent utiliser <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=fullName> ou les méthodes d' <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=fullName> dans <xref:System.Net.HttpWebRequest> classe qui permettent de récupérer <xref:System.Net.TransportContext> et FAO à l'aide de la méthode d' <xref:System.Net.TransportContext.GetChannelBinding%2A> .  
  
 Le SPN à utiliser pour l'authentification Windows intégrée envoyée par une instance d' <xref:System.Net.HttpWebRequest> à un service donné peut être substituée en affectant à la propriété d' <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> .  
  
 La propriété d' <xref:System.Net.Mail.SmtpClient.TargetName%2A> peut être utilisée pour définir un personnalisé SPN à utiliser pour l'authentification Windows intégrée de la connexion SMTP.  
  
## Protection étendue pour les applications serveur  
 <xref:System.Net.HttpListener> fournit automatiquement des mécanismes pour valider des liaisons de service en exécutant l'authentification HTTP.  
  
 Le scénario le plus sécurisé est d'activer la protection étendue pour les préfixes de HTTPS:\/\/.  Dans ce cas, affectez <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName> à <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> avec <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> affectez à <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> ou à <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>, et <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> défini à la valeur d' <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> Un d' <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> met <xref:System.Net.HttpListener> en mode partiellement renforcé, tandis que <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> correspond au mode entièrement renforcé.  
  
 Dans cette configuration lorsqu'une demande est envoyée au serveur via un canal sécurisé externe, le canal externe est interrogé pour une liaison du canal.  Cette liaison de canal est passée aux appels de SSPI d'authentification, qui vérifient que la liaison de canal dans l'objet blob d'authentification correspond.  Il existe trois conséquences possibles :  
  
1.  Le système d'exploitation sous\-jacent du serveur ne prend pas en charge la protection étendue.  La requête n'est pas exposée à l'application, et \(401\) des réponses non \- autorisée seront retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
2.  L'appel de SSPI échoue indiquer que le client a indiqué une liaison de canal qui ne correspond pas à la valeur attendue extraite du canal externe ou du client pour fournir une liaison de canal lorsque la stratégie de protection étendue sur le serveur a été configurée pour <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>.  Dans les deux cas, la demande n'est pas exposée à l'application, et \(401\) des réponses non \- autorisée seront retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
3.  Le client spécifie la liaison correcte de canal ou est laissé se connecter sans spécifier une liaison de canal la stratégie de protection étendue sur le serveur est configurée avec <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> que la demande est retournée à la demande de traitement.  Aucun contrôle de nom du service n'est effectuée automatiquement.  Une application peut choisir d'effectuer sa propre validation de nom du service à l'aide de la propriété d' <xref:System.Net.HttpListenerRequest.ServiceName%2A> , mais dans ces circonstances elle est redondante.  
  
 Si une application a ses propres appels de SSPI pour exécuter l'authentification basée sur les objets blobs passés dans les deux sens dans le corps d'une requête HTTP et souhaite à la liaison de canal de charge, elle doit extraire la liaison prévue de canal de canal sécurisé externe à l'aide de <xref:System.Net.HttpListener> afin de les passer à la fonction Win32 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) natives.  Pour ce faire, utilisez la propriété d' <xref:System.Net.HttpListenerRequest.TransportContext%2A> et appelez la méthode d' <xref:System.Net.TransportContext.GetChannelBinding%2A> pour récupérer FAO.  Seuls les liaisons de point de terminaison sont prises en charge.  Si quelque chose l'autre <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind> est spécifié, <xref:System.NotSupportedException> sera levée.  Si le prend en charge du système d'exploitation sous\-jacents canalisent la liaison, la méthode d' <xref:System.Net.TransportContext.GetChannelBinding%2A> retourne <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding><xref:System.Runtime.InteropServices.SafeHandle> encapsulant un pointeur à lier de canal approprié pour passer [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) s'exécute lorsque le membre de pvBuffer d'une structure de SecBuffer réussi dans le paramètre d' `pInput` .  La propriété d' <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> contient la longueur, en octets, de la liaison de canal.  Si le système d'exploitation sous\-jacent ne prend pas en charge les liaisons de canal, la fonction retourne `null`.  
  
 Un autre scénario est possible d'activer la protection étendue pour les préfixes de HTTP:\/\/ lorsque les proxies ne sont pas utilisés.  Dans ce cas, affectez <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName> à <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> avec <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> affectez à <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> ou à <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>, et <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> défini à la valeur d' <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> Un d' <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> met <xref:System.Net.HttpListener> en mode partiellement renforcé, tandis que <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> correspond au mode entièrement renforcé.  
  
 Une liste par défaut de noms du service autorisé est créée en fonction de les préfixes enregistrés avec <xref:System.Net.HttpListener>.  Cette liste par défaut peut être inspectée via la propriété d' <xref:System.Net.HttpListener.DefaultServiceNames%2A> .  Si cette liste n'est pas terminée, une application peut spécifier une collection personnalisée de nom du service dans le constructeur de la classe d' <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> qui sera utilisée au lieu de la liste par défaut du nom du service.  
  
 Dans cette configuration, lorsqu'une demande est envoyée au serveur sans quantité externe d'une authentification de canal sécurisé normalement sans contrôle de liaison de canal.  Si l'authentification aboutit, le contexte est interrogé pour le nom du client de service fourni et a validé par rapport à la liste de noms de service acceptables.  Il existe quatre effets possibles :  
  
1.  Le système d'exploitation sous\-jacent du serveur ne prend pas en charge la protection étendue.  La requête n'est pas exposée à l'application, et \(401\) des réponses non \- autorisée seront retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
2.  Le système d'exploitation sous\-jacent du client ne prend pas en charge la protection étendue.  Dans la configuration d' <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> , la tentative d'authentification réussira et la requête est retournée à l'application.  Dans la configuration d' <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> , la tentative d'authentification échoue.  La requête n'est pas exposée à l'application, et \(401\) des réponses non \- autorisée seront retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
3.  Le système d'exploitation sous\-jacent du client prend en charge la protection étendue, mais l'application n'a pas spécifié une liaison de service.  La requête n'est pas exposée à l'application, et \(401\) des réponses non \- autorisée seront retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
4.  Le client a indiqué une liaison de service.  La liaison de service est comparée à la liste de liaisons autorisées de service.  Si elle correspond, la requête est retournée à l'application.  Sinon, la requête ne sera pas exposée à l'application, et \(401\) des réponses non \- autorisée seront automatiquement retournées au client.  Un message est stocké dans la source de trace de <xref:System.Net.HttpListener> spécifiant la raison de l'échec.  
  
 Si cette approche simple à une liste autorisée de noms du service acceptables est insuffisante, une application peut fournir sa propre validation de nom du service en interrogeant la propriété d' <xref:System.Net.HttpListenerRequest.ServiceName%2A> .  Dans les cas 1 et 2 ci\-dessus, la propriété retourne `null`.  Dans le cas 3, qui retournent une chaîne vide.  Dans le cas 4, le nom du service spécifié par le client sont retournés.  
  
 Ces fonctionnalités de protection étendues peuvent également être utilisées par les applications serveur pour l'authentification avec d'autres types d'applications et lorsque les proxies approuvés sont utilisés.  
  
## Voir aussi  
 <xref:System.Security.Authentication.ExtendedProtection>   
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>