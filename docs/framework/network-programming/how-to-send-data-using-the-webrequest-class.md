---
title: "Comment&#160;: envoyer des donn&#233;es &#224; l’aide de la classe WebRequest | Microsoft Docs"
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
  - "WebRequest (classe), envoi de données à un hôte"
  - "Envoi de données à un hôte, à l’aide de la classe WebRequest"
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Comment&#160;: envoyer des donn&#233;es &#224; l’aide de la classe WebRequest
La procédure suivante décrit les étapes utilisées pour envoyer des données vers un serveur.  Cette procédure est fréquemment utilisée pour publier des données sur une page Web.  
  
### Pour envoyer des données vers un serveur hôte  
  
1.  Créez une instance d' <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l'URI de la ressource qui reçoit des données, par exemple, un script ou une page ASP.NET.  
  
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
  
     Dans la plupart des cas, l'instance de **WebRequest** elle\-même est suffisante pour envoyer des données.  Toutefois, si vous devez définir les propriétés spécifiques au protocole, vous devez effectuer un cast **WebRequest** au type spécifique au fournisseur.  Par exemple, pour accéder aux propriétés de HTTP spécifiques d' <xref:System.Net.HttpWebRequest>, effectuez un cast **WebRequest** à une référence de **HttpWebRequest** .  L'exemple de code suivant montre comment définir la propriété d' <xref:System.Net.HttpWebRequest.UserAgent%2A> de HTTP spécifiques.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Spécifiez une méthode de fournisseur qui permet aux données d'être envoyées à une requête, telle que la méthode HTTP **POST** .  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Affectez à la propriété de **ContentLength** .  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Affectez à la propriété de **ContentType** à une valeur appropriée.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Obtenez le flux de données qui contient des données de requête en appelant la méthode d' <xref:System.Net.WebRequest.GetRequestStream%2A> .  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Entrez les données à l'objet d' <xref:System.IO.Stream> retourné par cette méthode.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Fermez le flux de demande en appelant la méthode de **Stream.Close** .  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A>.  Cette méthode retourne un objet contenant la réponse du serveur.  Le type d'objet retourné d' <xref:System.Net.WebResponse> est déterminé par le modèle des URI demandés.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
  
    ```  
  
    > [!NOTE]
    >  Après vous être terminé avec un objet d' <xref:System.Net.WebResponse> , vous devez le fermer en appelant la méthode d' <xref:System.Net.WebResponse.Close%2A> .  De même, si vous avez le flux de réponse de l'objet de réponse, vous pouvez fermer le flux de données en appelant la méthode d' <xref:System.IO.Stream.Close%2A?displayProperty=fullName> .  Si vous ne fermez pas la réponse ou le flux, votre application peut manquer de connexions au serveur et devenir impossible de traiter les requêtes supplémentaires.  
  
10. Vous pouvez accéder aux propriétés de **WebResponse** ou caster **WebResponse** à une instance spécifique au fournisseur pour lire les propriétés spécifiques au protocole.  Par exemple, pour accéder aux propriétés de HTTP spécifiques d' <xref:System.Net.HttpWebResponse>, effectuez un cast **WebResponse** à une référence de **HttpWebResponse** .  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Pour obtenir le flux contenant les données de réponse l'a envoyé par le serveur, appelez la méthode d' <xref:System.Net.WebResponse.GetResponseStream%2A> de **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Après avoir lu les données de la réponse, vous devez fermer le flux de réponse à l'aide de la méthode de **Stream.Close** ou fermer la réponse à l'aide de la méthode de **WebResponse.Close** .  Il n'est pas nécessaire d'appeler la méthode de **Fermer** sur le flux de réponse et le **WebResponse**, mais cela n'est pas préjudiciable.  
  
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
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
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
 [Procédure : demande de données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)