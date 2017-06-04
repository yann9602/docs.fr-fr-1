---
title: "D&#233;rivation &#224; partir de WebResponse | Microsoft Docs"
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
  - "Dérivation à partir de WebResponse"
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# D&#233;rivation &#224; partir de WebResponse
La classe d' <xref:System.Net.WebResponse> est une classe de base abstraite qui fournit les méthodes et les propriétés de base pour créer une réponse spécifique au fournisseur qui ajuste le modèle enfichables de protocole .NET Framework.  Les applications qui utilisent la classe d' <xref:System.Net.WebRequest> pour demander des données des ressources acceptent les réponses dans **WebResponse**.  Les descendants spécifiques au protocole de **WebResponse** doivent implémenter les membres abstraits de la classe de **WebResponse** .  
  
 La classe associée de **WebRequest** doit créer des descendants de **WebResponse** .  Par exemple, les instances d' <xref:System.Net.HttpWebResponse> sont créées uniquement comme résultat d'appeler <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=fullName> ou <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=fullName>.  Chaque **WebResponse** contient le résultat d'une requête à une ressource et n'est pas destiné à être réutilisé.  
  
## Propriété de ContentLength  
 La propriété d' <xref:System.Net.WebResponse.ContentLength%2A> indique le nombre d'octets de données qui sont disponibles dans le flux de données retourné par la méthode d' <xref:System.Net.WebResponse.GetResponseStream%2A> .  La propriété de **ContentLength** n'indique pas le nombre d'octets d'en\-tête ou d'informations de métadonnées retournées par le serveur ; elle indique que le nombre d'octets de données dans la ressource demandée lui\-même.  
  
## Propriété de ContentType  
 La propriété d' <xref:System.Net.WebResponse.ContentType%2A> fournit toutes les informations particulières que votre fournisseur requiert que vous de l'envoyer au client pour identifier le type de contenu envoyé par le serveur.  En général il s'agit du type de contenu MIME de toutes les données retournées.  
  
## Propriété d'en\-têtes  
 La propriété d' <xref:System.Net.WebResponse.Headers%2A> contient une collection de paires nom\/valeur arbitraire de métadonnées associées à la réponse.  Toutes les métadonnées nécessaires par le fournisseur qui peut être exprimé en tant que paire nom\/valeur peuvent être incluses dans la propriété de **En\-têtes** .  
  
 Vous n'êtes pas obligé d'utiliser la propriété de **En\-têtes** pour utiliser des métadonnées d'en\-tête.  Les métadonnées spécifiques au protocole peuvent être exposées comme propriétés ; par exemple, la propriété d' <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=fullName> expose l'en\-tête de **Last\-Modified** HTTP.  Lorsque vous exposez les métadonnées d'en\-tête en tant que propriété, vous ne devez pas autoriser la même propriété à définir à l'aide de la propriété de **En\-têtes** .  
  
## Propriété de ResponseUri  
 La propriété d' <xref:System.Net.WebResponse.ResponseUri%2A> contient l'URI de la ressource qui a fourni en fait la réponse.  Pour les fournisseurs qui ne prennent pas en charge la redirection, **ResponseUri** sont les mêmes que la propriété d' <xref:System.Net.WebRequest.RequestUri%2A> de **WebRequest** qui a créé la réponse.  Si l'application le prend en charge des protocoles redirigeant la demande, **ResponseUri** contiendront l'URI de la réponse.  
  
## Méthode fermés  
 La méthode d' <xref:System.Net.WebResponse.Close%2A> ferme tous les rapports générés par la requête et la réponse et nettoie les ressources utilisées par la réponse.  La méthode de **Fermer** ferme toutes les instances de flux de données utilisées par la réponse, mais ne lève pas d'exception si le flux de réponse était précédemment fermé par un appel à la méthode d' <xref:System.IO.Stream.Close%2A?displayProperty=fullName> .  
  
## Méthode de GetResponseStream  
 La méthode d' <xref:System.Net.WebResponse.GetResponseStream%2A> retourne un flux contenant la réponse de la ressource demandée.  Le flux de réponse contient uniquement les données retournées par la ressource ; tout l'en\-tête ou métadonnées incluses dans la réponse doit être éliminé de la réponse et être exposé à l'application via les propriétés spécifiques au protocole ou la propriété de **En\-têtes** .  
  
 L'instance de flux retournée par la méthode de **GetResponseStream** est possédée par l'application et peut être fermée sans fermer **WebResponse**.  Par convention, appelez la méthode de **WebResponse.Close** ferme également le flux de données retourné par **GetResponse**.  
  
## Voir aussi  
 <xref:System.Net.WebResponse>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.FileWebResponse>   
 [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [dérivation de WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)