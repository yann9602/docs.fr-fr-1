---
title: "d&#233;rivation de WebRequest | Microsoft Docs"
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
  - "WebRequest (classe), protocoles enfichables"
  - "gestionnaire de requêtes spécifique au protocole"
  - "envoi de données, protocoles enfichables"
  - "protocoles enfichables, critères de classe"
  - "Internet, protocoles enfichables"
  - "réception de données, protocoles enfichables"
  - "protocoles, enfichables"
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# d&#233;rivation de WebRequest
La classe d' <xref:System.Net.WebRequest> est une classe de base abstraite qui fournit les méthodes et les propriétés de base pour créer un gestionnaire spécifique au fournisseur de requête qui ajuste le modèle enfichables de protocole .NET Framework.  Les applications qui utilisent la classe de **WebRequest** peuvent demander des données à l'aide de n'importe quel protocole charge sans devoir spécifier le protocole utilisé.  
  
 Deux critères doivent être remplis pour qu'une classe spécifique au fournisseur est utilisée comme protocole enfichable : La classe doit implémenter l'interface d' <xref:System.Net.IWebRequestCreate> , et elle doit enregistrer avec la méthode d' <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> .  La classe doit substituer les méthodes et propriétés abstraites de **WebRequest** pour fournir l'interface enfichables.  
  
 Les instances de**WebRequest** sont conçues pour utiliser une fois ; si vous souhaitez effectuer une autre application, créez **WebRequest**.  **WebRequest** prend en charge l'interface d' <xref:System.Runtime.Serialization.ISerializable> pour permettre aux développeurs de sérialiser un modèle **WebRequest** puis de régénérer le modèle pour les requêtes supplémentaires.  
  
## Méthode de création d'IWebRequest  
 La méthode d' <xref:System.Net.IWebRequestCreate.Create%2A> est chargé d'initialiser une nouvelle instance de la classe spécifique au fournisseur.  Lorsque nouveau **WebRequest** est créé, la méthode d' <xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> correspond à l'URI demandé avec les préfixes d'URI enregistrés avec la méthode de **RegisterPrefix** .  La méthode de **Créer** descendants spécifique au fournisseur approprié doit retourner une instance initialisée du descendant capable d'effectuer une transaction standard de demande\/réponse pour le protocole sans avoir besoin d'un champ spécifique au protocole modifié.  
  
## Propriété de ConnectionGroupName  
 La propriété d' <xref:System.Net.WebRequest.ConnectionGroupName%2A> est utilisée pour nommer un groupe de connexions à une ressource afin que plusieurs demandes peuvent être effectuées sur une connexion unique.  Pour implémenter le connexion\- partage, vous devez utiliser une méthode spécifique au fournisseur de regroupement et de connexions d'assignation.  Par exemple, la classe fournie d' <xref:System.Net.ServicePointManager> implémente le partage de connexion pour la classe d' <xref:System.Net.HttpWebRequest> .  La classe de **ServicePointManager** crée <xref:System.Net.ServicePoint> qui fournit une connexion à un serveur spécifique pour chaque groupe de connexions.  
  
## Propriété de ContentLength  
 La propriété d' <xref:System.Net.WebRequest.ContentLength%2A> spécifie le nombre d'octets de données qui doivent être envoyées au serveur en téléchargeant des données.  
  
 En général la propriété d' <xref:System.Net.WebRequest.Method%2A> doit être définie pour indiquer qu'un téléchargement a lieu lorsque la propriété de **ContentLength** a une valeur supérieure à zéro.  
  
## Propriété de ContentType  
 La propriété d' <xref:System.Net.WebRequest.ContentType%2A> fournit toutes les informations particulières que votre fournisseur requiert que vous de l'envoyer au serveur pour identifier le type de contenu que vous envoyez.  En général il s'agit du type de contenu MIME de toutes les données téléchargées.  
  
## Propriété des informations d'identification  
 La propriété d' <xref:System.Net.WebRequest.Credentials%2A> contient les informations nécessaires pour authentifier la demande au serveur.  Vous devez implémenter les détails de la procédure d'authentification de votre fournisseur.  La classe d' <xref:System.Net.AuthenticationManager> est chargé d'authentifier des applications et de fournir un jeton d'authentification.  La classe qui fournit les informations d'identification utilisées par votre fournisseur doit implémenter l'interface d' <xref:System.Net.ICredentials> .  
  
## Propriété d'en\-têtes  
 La propriété d' <xref:System.Net.WebRequest.Headers%2A> contient une collection de paires nom\/valeur arbitraire de métadonnées associées à la demande.  Toutes les métadonnées nécessaires par le fournisseur qui peut être exprimé en tant que paire nom\/valeur peuvent être incluses dans la propriété de **En\-têtes** .  Généralement ces informations doivent être placées avant d'appeler les méthodes d' <xref:System.Net.WebRequest.GetRequestStream%2A> ou d' <xref:System.Net.WebRequest.GetResponse%2A> ; une fois la demande a été effectuée, les métadonnées est considérée comme étant en lecture seule.  
  
 Vous n'êtes pas obligé d'utiliser la propriété de **En\-têtes** pour utiliser des métadonnées d'en\-tête.  Les métadonnées spécifiques au protocole peuvent être exposées comme propriétés ; par exemple, la propriété d' <xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=fullName> expose l'en\-tête d' **User\-Agent** HTTP.  Lorsque vous exposez les métadonnées d'en\-tête en tant que propriété, vous ne devez pas autoriser la même propriété à définir à l'aide de la propriété de **En\-têtes** .  
  
## Propriété de méthode  
 La propriété d' <xref:System.Net.WebRequest.Method%2A> contient le verbe ou l'action que la demande demande au serveur à exécuter.  La valeur par défaut de la propriété de **Méthode** doit permettre une action standard de demande\/réponse sans nécessiter d'aucune propriété spécifique au protocole d'être définie.  Par exemple, la méthode de [HttpWebResponse](frlrfSystemNetHttpWebResponseClassMethodTopic) a comme valeur par défaut POUR OBTENIR, qui demande une ressource d'un serveur Web et retourne la réponse.  
  
 En général la propriété de **ContentLength** doit avoir une valeur supérieure à zéro lorsque la propriété de **Méthode** a pour valeur un verbe ou à une action qui indique qu'un téléchargement a lieu.  
  
## Propriété de PreAuthenticate  
 Les applications affectez à la propriété d' <xref:System.Net.WebRequest.PreAuthenticate%2A> pour indiquer que les informations d'identification doivent être envoyées avec la demande initiale plutôt qu'en attente d'un défi d'authentification.  La propriété de **PreAuthenticate** est uniquement explicite si les informations d'identification de prend en charge des protocoles les envoyaient avec la requête initiale.  
  
## Propriété de proxy  
 La propriété d' <xref:System.Net.WebRequest.Proxy%2A> contient une interface d' <xref:System.Net.IWebProxy> utilisée pour accéder à la ressource demandée.  La propriété de **Proxy** est pertinent uniquement si votre application prend en charge des protocoles proxied des demandes.  Vous devez définir le proxy par défaut si un est requis par votre fournisseur.  
  
 Dans certains environnements, tels que derrière un pare\-feu d'entreprise, votre fournisseur peut être requis pour utiliser un proxy.  Dans ce cas, vous devez implémenter l'interface d' **IWebProxy** pour créer une classe proxy qui s'exécutera pour votre fournisseur.  
  
## Propriété de RequestUri  
 La propriété d' <xref:System.Net.WebRequest.RequestUri%2A> contient l'URI passé à la méthode de **WebRequest.Create** .  Il est en lecture seule et ne peut pas être modifié une fois que **WebRequest** a été créé.  Si la redirection de prend en charge des protocoles, la réponse peut provenir d'une ressource identifiée par un URI différent.  Si vous devez fournir l'accès à l'URI qui a répondu, vous devez fournir une propriété supplémentaire contenant qu'un URI.  
  
## Propriété de délai d'attente  
 La propriété d' <xref:System.Net.WebRequest.Timeout%2A> contient la durée, en millisecondes, d'attendre avant l'expiration d'application et lève une exception.  **Délai d'attente** s'applique uniquement aux demandes synchrones effectuées avec la méthode d' <xref:System.Net.WebRequest.GetResponse%2A> ; les demandes asynchrones doivent utiliser la méthode d' <xref:System.Net.WebRequest.Abort%2A> pour annuler une requête en attente.  
  
 La définition de la propriété de **Délai d'attente** est pertinent uniquement si la classe spécifique au fournisseur implémente un processus de minuterie.  
  
## Méthode d'arrêt  
 La méthode d' <xref:System.Net.WebRequest.Abort%2A> annuler une requête asynchrone en attente à un serveur.  Une fois la demande a été annulée, l'appel **GetResponse**, **BeginGetResponse**, **EndGetResponse**, **GetRequestStream**, **BeginGetRequestStream**, ou **EndGetRequestStream** lèveront <xref:System.Net.WebException> avec le jeu de propriétés d' <xref:System.Net.WebException.Status%2A> à [RequestCanceled](frlrfSystemNetWebExceptionStatusClassTopic).  
  
## Méthodes de BeginGetRequestStream et d'EndGetRequestStream  
 La méthode d' <xref:System.Net.WebRequest.BeginGetRequestStream%2A> démarre une requête asynchrone à partir de le flux utilisé pour télécharger des données au serveur.  La méthode d' <xref:System.Net.WebRequest.EndGetRequestStream%2A> remplit la demande asynchrone et retourne le flux demandé.  Ces méthodes appliquent la méthode de **GetRequestStream** à l'aide de le modèle asynchrone standard du .NET Framework.  
  
## Méthodes de BeginGetResponse et d'EndGetResponse  
 La méthode d' <xref:System.Net.WebRequest.BeginGetResponse%2A> démarre une requête asynchrone à un serveur.  La méthode d' <xref:System.Net.WebRequest.EndGetResponse%2A> remplit la demande asynchrone et retourne la réponse demandée.  Ces méthodes appliquent la méthode de **GetResponse** à l'aide de le modèle asynchrone standard du .NET Framework.  
  
## Méthode de GetRequestStream  
 La méthode d' <xref:System.Net.WebRequest.GetRequestStream%2A> retourne un flux qui est utilisé pour écrire des données au serveur demandé.  Le flux de données retourné doit être un flux en écriture seule qui ne le trouve pas ; il est attendu flux de données unidirectionnel écrites sur le serveur.  Le flux de données retourne la valeur false pour les propriétés d' <xref:System.IO.Stream.CanRead%2A> et d' <xref:System.IO.Stream.CanSeek%2A> et le rectifie pour la propriété d' <xref:System.IO.Stream.CanWrite%2A> .  
  
 La méthode de **GetRequestStream** généralement ouvre une connexion au serveur et, avant de retourner le flux, envoie les informations d'en\-tête qui indiquent ces données sont envoyées au serveur.  Étant donné que **GetRequestStream** commence la demande, il n'est généralement pas la définition d'une propriété de **En\-tête** ou de la propriété de **ContentLength** après avoir appelé **GetRequestStream**.  
  
## Méthode de GetResponse  
 La méthode d' <xref:System.Net.WebRequest.GetResponse%2A> retourne un descendant spécifique au fournisseur de la classe d' <xref:System.Net.WebResponse> qui représente la réponse du serveur.  À moins que la demande a déjà été initialisée par la méthode de **GetRequestStream** , la méthode de **GetResponse** crée une connexion à la ressource identifiée par **RequestUri**, envoie les informations d'en\-tête indiquant le type de demande effectuée, puis reçoit une réponse de la ressource.  
  
 Une fois que la méthode de **GetResponse** est appelée, les propriétés doivent être considérées comme étant en lecture seule.  Les instances de**WebRequest** sont conçues pour utiliser une fois ; si vous souhaitez effectuer une autre application, vous devez créer **WebRequest**.  
  
 La méthode de **GetResponse** est chargé de créer un descendant approprié de **WebResponse** pour contenir la réponse entrante.  
  
## Voir aussi  
 <xref:System.Net.WebRequest>   
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.FileWebRequest>   
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [Dérivation à partir de WebResponse](../../../docs/framework/network-programming/deriving-from-webresponse.md)