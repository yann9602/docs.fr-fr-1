---
title: "Demande de donn&#233;es | Microsoft Docs"
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
  - "envoyer des données"
  - "classe WebRequest, envoyer et recevoir des données"
  - "demander des données à partir d’Internet, à propos de la demande de données"
  - "classe WebClient, envoyer et recevoir des données"
  - "réseau, demander des données"
  - "recevoir des données"
  - "envoyer des données, à propos de l’envoi de données"
  - "répondre à une requête Internet, à propos de la réponse à des requêtes Internet"
  - "demandes de données"
  - "recevoir des données, à propos de la réception de données"
  - "Internet, demander des données"
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Demande de donn&#233;es
Développer des applications qui s'exécutent dans l'environnement distribué opérationnel de Internet d'aujourd'hui requiert une méthode efficace et facile à utiliser pour récupération de données des ressources de tous les types.  Les protocoles enfichables vous permettent de développer des applications qui utilisent une interface unique pour récupérer des données de plusieurs protocoles Internet.  
  
## Téléchargement et téléchargement de données d'un serveur Web  
 Pour les transactions simples de demande et de réponse, la classe d' <xref:System.Net.WebClient> fournit la méthode simple pour transférer les données vers ou télécharger des données d'un serveur Web.  **WebClient** fournit des méthodes pour télécharger et télécharger des fichiers, l'envoyer et recevoir des flux, et envoyer une mémoire tampon de données au serveur et recevoir une réponse.  **WebClient** utilise les classes d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse> pour que la ressource réelle en connexions à Internet, donc n'importe quel protocole enfichable inscrit est disponible.  
  
 Les applications clientes qui doivent effectuer des transactions plus complexes demandent des données de serveur à l'aide de la classe de **WebRequest** et de ses descendants.  **WebRequest** encapsule les informations de connexion au serveur, d'envoyer la demande, et accepter la réponse.  **WebRequest** est une classe abstraite qui définit un ensemble de propriétés et méthodes disponibles à toutes les applications qui utilisent des protocoles enfichables.  Les descendants de **WebRequest**, tel qu' <xref:System.Net.HttpWebRequest>, implémentent les propriétés et les méthodes définies par **WebRequest** d'une façon qui est compatible avec le fournisseur sous\-jacent.  
  
 La classe de **WebRequest** crée des instances spécifiques au protocole des descendants de **WebRequest** , à l'aide de la valeur de l'URI passé à la méthode d' <xref:System.Net.WebRequest.Create%2A> pour déterminer l'instance classe dérivée spécifique pour créer.  Les applications indiquent que le descendant de **WebRequest** doit être utilisé pour traiter une requête en enregistrant le constructeur du descendant avec la méthode d' <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> .  
  
 Une demande est adressée à la ressource Internet en appelant la méthode d' <xref:System.Net.WebRequest.GetResponse%2A> sur **WebRequest**.  La méthode de **GetResponse** construit la demande spécifique au fournisseur des propriétés de **WebRequest**, connexion fait TCP ou d'UDP socket au serveur, puis envoie la demande.  Pour les demandes qui envoient des données au serveur, comme les demandes HTTP **Post** ou FTP **Put** , la méthode d' <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=fullName> fournit un flux de réseau dans lequel envoyer des données.  
  
 La méthode de **GetResponse** retourne **WebResponse** spécifique au fournisseur qui correspond **WebRequest.**  
  
 La classe de **WebResponse** est également une classe abstraite qui définit les propriétés et les méthodes qui sont disponibles pour toutes les applications qui utilisent des protocoles enfichables.  Les descendants de**WebResponse** appliquent les propriétés et méthodes pour le fournisseur sous\-jacent.  La classe d' <xref:System.Net.HttpWebResponse> , par exemple, implémente la classe de **WebResponse** pour HTTP.  
  
 Les données retournées par le serveur sont présentées à l'application dans le flux de données retourné par la méthode d' <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=fullName> .  Vous pouvez utiliser ce flux comme tout autre, comme indiqué dans l'exemple suivant.  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## Voir aussi  
 [Programmation réseau dans le .NET Framework](../../../docs/framework/network-programming/index.md)   
 [Comment : demander une page web et récupérer les résultats sous forme de flux](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)   
 [Comment : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)