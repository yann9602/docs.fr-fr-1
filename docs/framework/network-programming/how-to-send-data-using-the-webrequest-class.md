---
title: "Comment : envoyer des données à l’aide de la classe WebRequest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b4cc524b3b3c1dbe42f3fe3926ed44c1e917e871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Comment : envoyer des données à l’aide de la classe WebRequest
La procédure suivante décrit les étapes nécessaires pour envoyer des données à un serveur. Cette procédure est couramment utilisée pour publier des données sur une page web.  
  
### <a name="to-send-data-to-a-host-server"></a>Pour envoyer des données à un serveur hôte  
  
1.  Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l’URI de la ressource qui accepte les données, par exemple, un script ou une page ASP.NET.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  .NET Framework fournit des classes spécifiques au protocole dérivées de **WebRequest** et de **WebResponse** pour les URI qui commencent par « http: », « https: », « ftp: » et « file: ». Pour accéder aux ressources à l’aide d’autres protocoles, vous devez implémenter des classes spécifiques au protocole qui sont dérivées de **WebRequest** et de **WebResponse**. Pour plus d’informations, consultez [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
2.  Définissez les valeurs des propriétés dont vous avez besoin dans **WebRequest**. Par exemple, pour activer l’authentification, définissez la propriété **Credentials** sur une instance de la classe <xref:System.Net.NetworkCredential>.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Dans la plupart des cas, l’instance **WebRequest** est suffisante pour envoyer des données. Toutefois, si vous devez définir des propriétés spécifiques au protocole, effectuez un cast de **WebRequest** en un type de protocole spécifique. Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebRequest>, effectuez un cast de **WebRequest** en une référence **HttpWebRequest**. L’exemple de code suivant montre comment définir la propriété <xref:System.Net.HttpWebRequest.UserAgent%2A> spécifique au protocole HTTP.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Spécifiez une méthode de protocole qui autorise l’envoi de données à l’aide d’une demande, telle que la méthode **POST** HTTP.  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Définissez la propriété **ContentLength**.  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Définissez la propriété **ContentType** avec une valeur appropriée.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Obtenez le flux qui contient les données de la demande en appelant la méthode <xref:System.Net.WebRequest.GetRequestStream%2A>.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Écrivez les données dans l’objet <xref:System.IO.Stream> retourné par cette méthode.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Fermez le flux de la demande en appelant la méthode **Stream.Close**.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A>. Cette méthode retourne un objet contenant la réponse du serveur. Le type de l’objet <xref:System.Net.WebResponse> retourné est déterminé par le schéma d’URI de la demande.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Quand vous n’avez plus besoin d’un objet <xref:System.Net.WebResponse>, vous devez le fermer en appelant la méthode <xref:System.Net.WebResponse.Close%2A>. Si vous avez obtenu le flux de la réponse à partir de l’objet réponse, vous pouvez également fermer le flux en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.  
  
10. Vous pouvez accéder aux propriétés de **WebResponse** ou effectuer un cast de **WebResponse** en une instance spécifique au protocole pour lire les propriétés propres au protocole. Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, effectuez un cast de **WebResponse** en une référence **HttpWebResponse**.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A> de **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Après avoir lu les données de la réponse, vous devez fermer le flux de la réponse à l’aide de la méthode **Stream.Close** ou fermer la réponse en utilisant la méthode **WebResponse.Close**. Vous n’avez pas besoin d’appeler la méthode **Close** à la fois sur le flux de la réponse et sur **WebResponse**, mais si vous le faites, cela n’a pas d’incidence.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Création de requêtes Internet](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Utilisation de flux sur le réseau](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)  
 [Guide pratique pour demander des données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
