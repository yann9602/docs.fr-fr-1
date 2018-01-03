---
title: "Procédure : demande de données à l’aide de la classe WebRequest"
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
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bd714a9e006f87a817ca931757aaaaed920f50f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Procédure : demande de données à l’aide de la classe WebRequest
La procédure suivante décrit les étapes nécessaires pour demander une ressource d’un serveur, par exemple, une page web ou un fichier. La ressource doit être identifiée par un URI.  
  
### <a name="to-request-data-from-a-host-server"></a>Pour demander des données à partir d’un serveur hôte  
  
1.  Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l’URI de la ressource.  
  
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
  
     Dans la plupart des cas, la classe **WebRequest** est suffisante pour recevoir des données. Toutefois, si vous devez définir des propriétés spécifiques au protocole, effectuez un cast de **WebRequest** en un type de protocole spécifique. Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebRequest>, effectuez un cast de **WebRequest** en une référence **HttpWebRequest**. L’exemple de code suivant montre comment définir la propriété <xref:System.Net.HttpWebRequest.UserAgent%2A> spécifique au protocole HTTP.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Pour envoyer la demande au serveur, appelez <xref:System.Net.HttpWebRequest.GetResponse%2A>. Le type de l’objet **WebResponse** retourné est déterminé par le schéma de l’URI demandé.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Quand vous n’avez plus besoin d’un objet <xref:System.Net.WebResponse>, vous devez le fermer en appelant la méthode <xref:System.Net.WebResponse.Close%2A>. Si vous avez obtenu le flux de la réponse à partir de l’objet réponse, vous pouvez également fermer le flux en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.  
  
4.  Vous pouvez accéder aux propriétés de **WebResponse** ou effectuer un cast de **WebResponse** en une instance spécifique au protocole pour lire les propriétés propres au protocole. Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, effectuez un cast de **WebResponse** en une référence **HttpWebResponse**. L’exemple de code suivant montre comment afficher les informations d’état envoyées avec une réponse.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Pour obtenir le flux contenant les données de réponse envoyées par le serveur, utilisez la méthode <xref:System.Net.HttpWebResponse.GetResponseStream%2A> de **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Après avoir lu les données de la réponse, vous devez fermer le flux de la réponse à l’aide de la méthode **Stream.Close** ou fermer la réponse en utilisant la méthode **WebResponse.Close**. Vous n’avez pas besoin d’appeler la méthode **Close** à la fois sur le flux de la réponse et sur **WebResponse**, mais si vous le faites, cela n’a pas d’incidence. **WebResponse.Close** appelle **Stream.Close** au moment de la fermeture de la réponse.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Création de requêtes Internet](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Utilisation de flux sur le réseau](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)  
 [Guide pratique pour envoyer des données à l’aide de la classe WebRequest](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
