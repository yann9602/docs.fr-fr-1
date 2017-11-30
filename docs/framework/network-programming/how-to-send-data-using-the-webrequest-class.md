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
ms.openlocfilehash: 2102fce150f512a49093eb2b214258ac35e276e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="09d93-102">Comment : envoyer des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="09d93-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="09d93-103">La procédure suivante décrit les étapes nécessaires pour envoyer des données à un serveur.</span><span class="sxs-lookup"><span data-stu-id="09d93-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="09d93-104">Cette procédure est couramment utilisée pour publier des données sur une page web.</span><span class="sxs-lookup"><span data-stu-id="09d93-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="09d93-105">Pour envoyer des données à un serveur hôte</span><span class="sxs-lookup"><span data-stu-id="09d93-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="09d93-106">Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l’URI de la ressource qui accepte les données, par exemple, un script ou une page ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="09d93-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="09d93-107">.NET Framework fournit des classes spécifiques au protocole dérivées de **WebRequest** et de **WebResponse** pour les URI qui commencent par « http: », « https: », « ftp: » et « file: ».</span><span class="sxs-lookup"><span data-stu-id="09d93-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="09d93-108">Pour accéder aux ressources à l’aide d’autres protocoles, vous devez implémenter des classes spécifiques au protocole qui sont dérivées de **WebRequest** et de **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="09d93-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="09d93-109">Pour plus d’informations, consultez [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="09d93-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="09d93-110">Définissez les valeurs des propriétés dont vous avez besoin dans **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="09d93-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="09d93-111">Par exemple, pour activer l’authentification, définissez la propriété **Credentials** sur une instance de la classe <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="09d93-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="09d93-112">Dans la plupart des cas, l’instance **WebRequest** est suffisante pour envoyer des données.</span><span class="sxs-lookup"><span data-stu-id="09d93-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="09d93-113">Toutefois, si vous devez définir des propriétés spécifiques au protocole, effectuez un cast de **WebRequest** en un type de protocole spécifique.</span><span class="sxs-lookup"><span data-stu-id="09d93-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="09d93-114">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebRequest>, effectuez un cast de **WebRequest** en une référence **HttpWebRequest**.</span><span class="sxs-lookup"><span data-stu-id="09d93-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="09d93-115">L’exemple de code suivant montre comment définir la propriété <xref:System.Net.HttpWebRequest.UserAgent%2A> spécifique au protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="09d93-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="09d93-116">Spécifiez une méthode de protocole qui autorise l’envoi de données à l’aide d’une demande, telle que la méthode **POST** HTTP.</span><span class="sxs-lookup"><span data-stu-id="09d93-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="09d93-117">Définissez la propriété **ContentLength**.</span><span class="sxs-lookup"><span data-stu-id="09d93-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="09d93-118">Définissez la propriété **ContentType** avec une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="09d93-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="09d93-119">Obtenez le flux qui contient les données de la demande en appelant la méthode <xref:System.Net.WebRequest.GetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="09d93-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="09d93-120">Écrivez les données dans l’objet <xref:System.IO.Stream> retourné par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="09d93-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="09d93-121">Fermez le flux de la demande en appelant la méthode **Stream.Close**.</span><span class="sxs-lookup"><span data-stu-id="09d93-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="09d93-122">Envoyez la demande au serveur en appelant <xref:System.Net.WebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="09d93-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="09d93-123">Cette méthode retourne un objet contenant la réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="09d93-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="09d93-124">Le type de l’objet <xref:System.Net.WebResponse> retourné est déterminé par le schéma d’URI de la demande.</span><span class="sxs-lookup"><span data-stu-id="09d93-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="09d93-125">Quand vous n’avez plus besoin d’un objet <xref:System.Net.WebResponse>, vous devez le fermer en appelant la méthode <xref:System.Net.WebResponse.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="09d93-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="09d93-126">Si vous avez obtenu le flux de la réponse à partir de l’objet réponse, vous pouvez également fermer le flux en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09d93-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09d93-127">Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="09d93-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="09d93-128">Vous pouvez accéder aux propriétés de **WebResponse** ou effectuer un cast de **WebResponse** en une instance spécifique au protocole pour lire les propriétés propres au protocole.</span><span class="sxs-lookup"><span data-stu-id="09d93-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="09d93-129">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, effectuez un cast de **WebResponse** en une référence **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="09d93-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="09d93-130">Pour obtenir le flux contenant les données de réponse envoyées par le serveur, appelez la méthode <xref:System.Net.WebResponse.GetResponseStream%2A> de **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="09d93-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="09d93-131">Après avoir lu les données de la réponse, vous devez fermer le flux de la réponse à l’aide de la méthode **Stream.Close** ou fermer la réponse en utilisant la méthode **WebResponse.Close**.</span><span class="sxs-lookup"><span data-stu-id="09d93-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="09d93-132">Vous n’avez pas besoin d’appeler la méthode **Close** à la fois sur le flux de la réponse et sur **WebResponse**, mais si vous le faites, cela n’a pas d’incidence.</span><span class="sxs-lookup"><span data-stu-id="09d93-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="09d93-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="09d93-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09d93-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09d93-134">See Also</span></span>  
 [<span data-ttu-id="09d93-135">Création de requêtes Internet</span><span class="sxs-lookup"><span data-stu-id="09d93-135">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="09d93-136">Utilisation de flux sur le réseau</span><span class="sxs-lookup"><span data-stu-id="09d93-136">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="09d93-137">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="09d93-137">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="09d93-138">Demande de données</span><span class="sxs-lookup"><span data-stu-id="09d93-138">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="09d93-139">Guide pratique pour demander des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="09d93-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
