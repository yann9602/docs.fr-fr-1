---
title: "Introduction aux protocoles enfichables | Microsoft Docs"
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
helpviewer_keywords: 
  - "demandes de données, protocoles enfichables"
  - "WebRequest (classe), protocoles enfichables"
  - "réponse à une demande Internet, protocoles enfichables"
  - "URI"
  - "Windows Sockets"
  - "modèle demande/réponse"
  - "envoi de données, protocoles enfichables"
  - "protocoles enfichables"
  - "WebClient (classe), à propos de la classe WebClient"
  - "protocoles enfichables, à propos des protocoles enfichables"
  - "Internet, protocoles enfichables"
  - "identificateurs de chemin d’accès"
  - "Uniform Resource Identifier"
  - "développement d’applications (.NET Framework), protocoles enfichables"
  - "demande de données en provenance d’Internet, protocoles enfichables"
  - "réception de données, protocoles enfichables"
  - "protocoles, enfichables"
  - "identificateurs de serveurs"
  - "identificateurs de schémas"
ms.assetid: 4b48e22d-e4e5-48f0-be80-d549bda97415
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Introduction aux protocoles enfichables
Microsoft .NET Framework fournit une implémentation superposée, extensible et managée, des services Internet qui peuvent être intégrés rapidement et facilement dans vos applications.  Les classes d'accès Internet dans <xref:System.Net> et les espaces de noms d' <xref:System.Net.Sockets> peuvent être utilisés pour implémenter des applications Web et basées sur Internet.  
  
## Applications Web  
 Les applications Web peuvent être classées largement en deux types : les applications clientes qui les demandent des informations et des applications serveur qui répondent aux informations demande aux clients.  L'application cliente serveur Internet classique est le World Wide Web, où les personnes de navigateurs d'utilisation des documents d'accès et d'autres données stockées sur des serveurs Web dans le monde.  
  
 Les applications ne sont pas limitées simplement à l'une de ces rôles ; par exemple, le serveur d'application intermédiaire familier répond aux demandes des clients par demande des données d'un autre serveur, auquel cas il joue le rôle d'un serveur et client.  
  
 L'application cliente effectue une demande en identifiant la ressource Internet demandée et le protocole de communication à utiliser pour la demande et la réponse.  Si nécessaire, le client fournit également des informations supplémentaires requises pour exécuter la requête, telle que l'emplacement de proxy ou les informations d'identification \(nom d'utilisateur, un mot de passe, etc.\).  Une fois la demande est formée, la demande peut être envoyée au serveur.  
  
## Identifier des ressources  
 .NET Framework utilise un URI \(URI\) pour identifier la ressource Internet et le protocole de communication demandés.  L'URI est constitué d'au moins de trois, et éventuellement de quatre, fragments : l'identificateur de modèle, qui identifie le protocole de communication pour la demande et la réponse ; l'identificateur de serveur, qui se compose d'un nom d'hôte de \(DNS\) DNS ou d'une adresse TCP qui identifie le serveur sur Internet ; l'identificateur de chemin d'accès, qui localise les informations demandées sur le serveur ; et une chaîne de requête facultative, qui passe les informations du client au serveur.  Par exemple, l'URI « http:\/\/www.contoso.com\/whatsnew.aspx?date\=today » inclut l'identificateur « http » de modèle, l'identificateur « www.contoso.com » de serveur, le chemin d'accès « \/whatsnew.aspx », et la chaîne de requête « ? date\=today ».  
  
 Une fois que le serveur a reçu la demande et a traité la réponse, elle retourne la réponse à l'application cliente.  La réponse inclut des informations supplémentaires, telles que le type de contenu \(texte brut ou données XML, par exemple\).  
  
## Demandes et les réponses dans le.NET Framework  
 Les classes spécifiques d'utilisation du .NET Framework pour fournir les trois informations requises pour accéder aux ressources Internet via un modèle de requête\/réponse : la classe d' <xref:System.Uri> , qui contient l'URI de la ressource Internet vous recherchez ; la classe d' <xref:System.Net.WebRequest> , qui contient une demande de ressources ; et la classe d' <xref:System.Net.WebResponse> , qui fournit un conteneur pour la réponse entrante.  
  
 Les applications clientes créent des instances d' `WebRequest` en passant l'URI de la ressource réseau à la méthode d' <xref:System.Net.WebRequest.Create%2A> .  Cette méthode statique crée `WebRequest` pour un fournisseur spécifique, tel que HTTP.  `WebRequest` qui est retourné donne accès aux propriétés qui contrôlent la demande au serveur et l'accès au flux de données qui est envoyé lorsque la demande est effectuée.  La méthode d' <xref:System.Net.WebRequest.GetResponse%2A> sur `WebRequest` envoie la demande de l'application cliente au serveur identifié dans l'URI.  Dans les cas dans lesquels la réponse peut être différée, la demande peut être effectuée de façon asynchrone à l'aide de la méthode d' <xref:System.Net.WebRequest.BeginGetResponse%2A> sur **WebRequest**, et la réponse ne peut être retournée ultérieurement à l'aide de la méthode d' <xref:System.Net.WebRequest.EndGetResponse%2A> .  
  
 Les méthodes de **GetResponse** et d' **EndGetResponse** retournent **WebResponse** qui permet d'accéder aux données retournées par le serveur.  Étant donné que ces données sont fournies à l'application demandeuse flux par la méthode d' <xref:System.Net.WebResponse.GetResponseStream%2A> , elles peuvent être utilisées dans les flux de données d'une application n'importe où sont utilisées.  
  
 Les classes de **WebRequest** et de **WebResponse** constituent la base des protocoles enfichables — une implémentation services réseau qui vous permet de développer des applications qui utilisent des ressources Internet sans vous préoccuper des détails spécifiques du fournisseur utilise pour cette chaque ressource.  Les classes descendantes de **WebRequest** sont stockées avec la classe de **WebRequest** pour gérer les détails d'effectuer des connexions réelles aux ressources Internet.  
  
 Par exemple, la classe d' <xref:System.Net.HttpWebRequest> gère les détails de la connexion à une ressource Internet à l'aide de HTTP.  Par défaut, lorsque la méthode de **WebRequest.Create** rencontre un URI qui commence par « http :  » ou « https :  » \(les ID de protocole HTTP pour et HTTP sécurisé\), **WebRequest** qui est retourné peut être utilisé de même que, ou elle peut être converti le rôle à **HttpWebRequest** pour accéder aux propriétés spécifiques au protocole.  Dans la plupart des cas, **WebRequest** fournit toutes les informations nécessaires pour faire une demande.  
  
 Tout fournisseur qui peut être représenté comme transaction de demande\/réponse ne peut être utilisé dans **WebRequest**.  Vous pouvez dériver des classes spécifiques au protocole de **WebRequest** et de **WebResponse** puis les enregistrer en vue d'une utilisation par l'application avec la méthode statique d' <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> .  
  
 Lorsque l'autorisation cliente pour les applications Internet est requise, la propriété d' <xref:System.Net.WebRequest.Credentials%2A> de **WebRequest** fournit les informations d'identification requises.  Ces informations d'identification peuvent être des paires nom simple\/mot de passe pour HTTP de base ou assimiler l'authentification, ou un nom\/mot de passe\/champ défini pour l'authentification NTLM ou Kerberos.  Un ensemble d'informations d'identification peut être stocké dans une instance de [NetworkCredentials](frlrfsystemnetnetworkcredentialclasstopic) , ou plusieurs ensembles peuvent être enregistrés simultanément dans une instance d' <xref:System.Net.CredentialCache> .  **CredentialCache** utilise l'URI de la requête et du schéma d'authentification que le serveur en charge pour déterminer les informations d'identification à envoyer au serveur.  
  
## Demandes simples avec le client web  
 Pour les applications qui doivent faire des demandes simples de ressources Internet, la classe d' <xref:System.Net.WebClient> fournit des méthodes communes pour transférer les données vers ou télécharger des données d'un serveur Web.  **WebClient** repose sur la classe de **WebRequest** pour fournir l'accès aux ressources Internet ; par conséquent, la classe de **WebClient** peut utiliser n'importe quel protocole enfichable inscrit.  
  
 Pour les applications qui ne peuvent pas utiliser le modèle de requête\/réponse, ou d'applications qui doivent écouter sur le réseau ainsi qu'envoyer des demandes, l'espace de noms de **System.Net.Sockets** fournit les classes de [TCPClient](frlrfsystemnetsocketstcpclientclasstopic), de [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic), et d' [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) .  Ces classes gèrent les détails de l'établissement des connexions à l'aide de différents protocoles de transport et exposent la connexion réseau à l'application sous la forme d'un flux.  
  
 Les développeurs familiarisés avec Windows Sockets avec onglets ou ceux ayant besoin du contrôle fourni par programmation au niveau de socket constateront que les classes de **System.Net.Sockets** répondre à leurs besoins.  Les classes de **System.Net.Sockets** sont un point de transition du code managé au code natif dans les classes de **System.Net** .  Dans la plupart des cas, les classes de **System.Net.Sockets** marshalent des données dans leurs équivalents de windows 32 bits, ainsi que de gérer toutes les vérifications de sécurité nécessaires.  
  
## Voir aussi  
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)   
 [Exemples de mise en réseau pour le .NET sur MSDN Code Gallery](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)