---
title: "Proc&#233;dure&#160;: demande de donn&#233;es &#224; l’aide de la classe WebRequest | Microsoft Docs"
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
  - "téléchargement de ressources Internet, étapes"
  - "demande de données à partir d’Internet, étapes"
  - "WebRequest (classe), réception de données"
  - "réception de données, à l’aide de la classe WebRequest"
  - "Internet, demande de données"
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# Proc&#233;dure&#160;: demande de donn&#233;es &#224; l’aide de la classe WebRequest
La procédure suivante décrit les étapes utilisées pour demander une ressource à partir d'un serveur, par exemple, une page Web ou d'un fichier.  La ressource doit être identifiée par un URI.  
  
### Pour demander des données d'un serveur hôte  
  
1.  Créez une instance d' <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l'URI de la ressource.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
  
    ```  
  
    > [!NOTE]
    >  Le.NET Framework fournit les classes spécifiques au protocole dérivées de **WebRequest** et de **WebResponse** pour les URI qui commencent par « http :  », « https:'', « FTP :  », et « fichier :  ».  Pour accéder à des ressources à d'autres protocoles, vous devez implémenter des classes spécifiques au protocole qui dérivent de **WebRequest** et de **WebResponse**.  Pour plus d'informations, consultez [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
2.  Définissez les valeurs de propriété dont vous avez besoin dans **WebRequest**.  Par exemple, pour activer l'authentification, affectez à la propriété de **Informations d'identification** à une instance de la classe d' <xref:System.Net.NetworkCredential> .  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Dans la plupart des cas, la classe de **WebRequest** est suffisante pour recevoir des données.  Toutefois, si vous devez définir les propriétés spécifiques au protocole, vous devez effectuer un cast **WebRequest** au type spécifique au fournisseur.  Par exemple, pour accéder aux propriétés de HTTP spécifiques d' <xref:System.Net.HttpWebRequest>, effectuez un cast **WebRequest** à une référence de **HttpWebRequest** .  L'exemple de code suivant montre comment définir la propriété d' <xref:System.Net.HttpWebRequest.UserAgent%2A> de HTTP spécifiques.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
  
    ```  
  
3.  Pour envoyer la demande au serveur, appelez <xref:System.Net.HttpWebRequest.GetResponse%2A>.  Le type réel de l'objet retourné par **WebResponse** est déterminé par le modèle de l'URI demandé.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  Après vous être terminé avec un objet d' <xref:System.Net.WebResponse> , vous devez le fermer en appelant la méthode d' <xref:System.Net.WebResponse.Close%2A> .  De même, si vous avez le flux de réponse de l'objet de réponse, vous pouvez fermer le flux de données en appelant la méthode d' <xref:System.IO.Stream.Close%2A?displayProperty=fullName> .  Si vous ne fermez pas la réponse ou le flux, votre application peut manquer de connexions au serveur et devenir impossible de traiter les requêtes supplémentaires.  
  
4.  Vous pouvez accéder aux propriétés de **WebResponse** ou caster **WebResponse** à une instance spécifique au fournisseur pour lire les propriétés spécifiques au protocole.  Par exemple, pour accéder aux propriétés de HTTP spécifiques d' <xref:System.Net.HttpWebResponse>, effectuez un cast **WebResponse** à une référence de **HttpWebResponse** .  L'exemple de code suivant montre comment afficher des informations d'état envoyées avec une réponse.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Pour obtenir le flux contenant les données de réponse l'a envoyé par le serveur, utilisez la méthode d' <xref:System.Net.HttpWebResponse.GetResponseStream%2A> de **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
  
    ```  
  
6.  Après avoir lu les données de la réponse, vous devez fermer le flux de réponse à l'aide de la méthode de **Stream.Close** ou fermer la réponse à l'aide de la méthode de **WebResponse.Close** .  Il n'est pas nécessaire d'appeler la méthode de **Fermer** sur le flux de réponse et le **WebResponse**, mais cela n'est pas préjudiciable.  Appels **Stream.Close** de**WebResponse.Close** en fermant la réponse.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
  
    ```  
  
## Exemple  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## Voir aussi  
 [Création de requêtes Internet](../../../docs/framework/network-programming/creating-internet-requests.md)   
 [Utilisation de flux sur le réseau](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)   
 [Comment : envoyer des données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)