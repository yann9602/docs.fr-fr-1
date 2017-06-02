---
title: "Utilisation de flux sur le r&#233;seau | Microsoft Docs"
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
  - "requête de données à partir d’Internet, flux"
  - "Réseau"
  - "réponse à une requête Internet, flux"
  - "ressources réseau, capacités de flux"
  - "réception de données, capacités de flux"
  - "Ressources réseau"
  - "envoi de données, capacités de flux"
  - "téléchargement de ressources Internet, flux"
  - "flux, capacités"
  - "Internet, flux"
  - "flux"
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Utilisation de flux sur le r&#233;seau
Les ressources réseau sont représentées dans le.NET Framework en tant que flux.  En traitant les flux de manière générique, le.NET Framework offre les fonctionnalités suivantes :  
  
-   Un moyen courant d'envoyer et recevoir des données de site Web.  Celui qui le contenu réel du fichier \(HTML, XML, ou tout autre élément à votre application utilise <xref:System.IO.Stream.Write%2A?displayProperty=fullName> et <xref:System.IO.Stream.Read%2A?displayProperty=fullName> pour envoyer et recevoir des données.  
  
-   Compatibilité avec des flux à travers le .NET Framework.  Les flux sont utilisés partout dans .NET Framework, qui a une infrastructure riche pour les gérer.  Par exemple, vous pouvez modifier une application qui lit des données XML d' <xref:System.IO.FileStream> pour lire les données d' <xref:System.Net.Sockets.NetworkStream> à la place en modifiant uniquement les quelques lignes de code qui initialisent le flux.  Les principales différences entre la classe de **NetworkStream** et d'autres flux sont que **NetworkStream** n'est pas seekable, la propriété d' <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> retourne toujours **false**, et les méthodes d' <xref:System.Net.Sockets.NetworkStream.Seek%2A> et d' <xref:System.Net.Sockets.NetworkStream.Position%2A> lèvent <xref:System.NotSupportedException>.  
  
-   Traiter les données qu'il arrive.  Les flux permettent d'accéder aux données qu'il arrive du réseau, plutôt que forçant votre application d'attendre un groupe de données entier à télécharger.  
  
 L'espace de noms d' <xref:System.Net.Sockets> contient une classe de **NetworkStream** qui implémente la classe d' <xref:System.IO.Stream> spécifiquement pour une utilisation avec des ressources réseau.  Les classes de l'espace de noms d' <xref:System.Net.Sockets> utilisent la classe de **NetworkStream** pour représenter des flux.  
  
 Pour envoyer des données au réseau à l'aide de le flux de données retourné, appelle <xref:System.Net.WebRequest.GetRequestStream%2A> à votre <xref:System.Net.WebRequest>.  **WebRequest** envoie des en\-têtes de demande au serveur ; vous pouvez envoyer des données à la ressource réseau en appelant <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, ou la méthode d' <xref:System.IO.Stream.Write%2A> sur le flux de données retourné.  Certains fournisseurs, tels que HTTP, peut vous demander de définir les propriétés spécifiques au protocole avant d'envoyer des données.  L'exemple de code suivant montre comment définir des propriétés de HTTP spécifiques pour envoyer des données.  Il suppose qu' `sendData` variable contient les données à envoyer et qu' `sendLength` variable est le nombre d'octets de données à envoyer.  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 Pour recevoir les données du réseau, appelle <xref:System.Net.WebResponse.GetResponseStream%2A> à votre <xref:System.Net.WebResponse>.  Vous pouvez ensuite lire les données de la ressource réseau en appelant <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, ou la méthode d' <xref:System.IO.Stream.Read%2A> sur le flux de données retourné.  
  
 Lorsque vous utilisez des flux des ressources réseau, gardez à l'esprit les points suivants :  
  
-   La propriété de **CanSeek** retourne toujours **false** étant donné que la classe de **NetworkStream** ne peut pas modifier la position dans le flux.  Les méthodes de **Recherche** et de **Position** lèvent **NotSupportedException**.  
  
-   Lorsque vous utilisez **WebRequest** et **WebResponse**, les instances de flux créées en appelant **GetResponseStream** sont en lecture seule et les instances de flux créées en appelant **GetRequestStream** sont en écriture seule.  
  
-   Utilisez la classe d' <xref:System.IO.StreamReader> pour faciliter l'encodage.  L'exemple de code suivant utilise **StreamReader** pour lire un flux ASCII\- encodé de **WebResponse** \(l'exemple n'affiche pas créer l'application\).  
  
-   L'appel à **GetResponse** peut se bloquer si les ressources réseau sont pas disponibles.  Vous devez envisager d'utiliser une requête asynchrone avec les méthodes d' <xref:System.Net.WebRequest.BeginGetResponse%2A> et d' <xref:System.Net.WebRequest.EndGetResponse%2A> .  
  
-   L'appel à **GetRequestStream** peut se bloquer pendant que la connexion au serveur est créée.  Vous devez envisager d'utiliser une requête asynchrone pour le flux avec les méthodes d' <xref:System.Net.WebRequest.BeginGetRequestStream%2A> et d' <xref:System.Net.WebRequest.EndGetRequestStream%2A> .  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## Voir aussi  
 [Procédure : demande de données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)   
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)