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
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="34aa0-102">Procédure : demande de données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="34aa0-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="34aa0-103">La procédure suivante décrit les étapes nécessaires pour demander une ressource d’un serveur, par exemple, une page web ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="34aa0-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="34aa0-104">La ressource doit être identifiée par un URI.</span><span class="sxs-lookup"><span data-stu-id="34aa0-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="34aa0-105">Pour demander des données à partir d’un serveur hôte</span><span class="sxs-lookup"><span data-stu-id="34aa0-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="34aa0-106">Créez une instance <xref:System.Net.WebRequest> en appelant <xref:System.Net.WebRequest.Create%2A> avec l’URI de la ressource.</span><span class="sxs-lookup"><span data-stu-id="34aa0-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="34aa0-107">.NET Framework fournit des classes spécifiques au protocole dérivées de **WebRequest** et de **WebResponse** pour les URI qui commencent par « http: », « https: », « ftp: » et « file: ».</span><span class="sxs-lookup"><span data-stu-id="34aa0-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="34aa0-108">Pour accéder aux ressources à l’aide d’autres protocoles, vous devez implémenter des classes spécifiques au protocole qui sont dérivées de **WebRequest** et de **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="34aa0-109">Pour plus d’informations, consultez [Programmation de protocoles enfichables](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="34aa0-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="34aa0-110">Définissez les valeurs des propriétés dont vous avez besoin dans **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="34aa0-111">Par exemple, pour activer l’authentification, définissez la propriété **Credentials** sur une instance de la classe <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="34aa0-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="34aa0-112">Dans la plupart des cas, la classe **WebRequest** est suffisante pour recevoir des données.</span><span class="sxs-lookup"><span data-stu-id="34aa0-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="34aa0-113">Toutefois, si vous devez définir des propriétés spécifiques au protocole, effectuez un cast de **WebRequest** en un type de protocole spécifique.</span><span class="sxs-lookup"><span data-stu-id="34aa0-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="34aa0-114">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebRequest>, effectuez un cast de **WebRequest** en une référence **HttpWebRequest**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="34aa0-115">L’exemple de code suivant montre comment définir la propriété <xref:System.Net.HttpWebRequest.UserAgent%2A> spécifique au protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="34aa0-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="34aa0-116">Pour envoyer la demande au serveur, appelez <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="34aa0-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="34aa0-117">Le type de l’objet **WebResponse** retourné est déterminé par le schéma de l’URI demandé.</span><span class="sxs-lookup"><span data-stu-id="34aa0-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="34aa0-118">Quand vous n’avez plus besoin d’un objet <xref:System.Net.WebResponse>, vous devez le fermer en appelant la méthode <xref:System.Net.WebResponse.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="34aa0-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="34aa0-119">Si vous avez obtenu le flux de la réponse à partir de l’objet réponse, vous pouvez également fermer le flux en appelant la méthode <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34aa0-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="34aa0-120">Si vous ne fermez pas la réponse ni le flux, votre application peut ne plus avoir suffisamment de connexions au serveur pour traiter des demandes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="34aa0-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="34aa0-121">Vous pouvez accéder aux propriétés de **WebResponse** ou effectuer un cast de **WebResponse** en une instance spécifique au protocole pour lire les propriétés propres au protocole.</span><span class="sxs-lookup"><span data-stu-id="34aa0-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="34aa0-122">Par exemple, pour accéder aux propriétés propres à HTTP de <xref:System.Net.HttpWebResponse>, effectuez un cast de **WebResponse** en une référence **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="34aa0-123">L’exemple de code suivant montre comment afficher les informations d’état envoyées avec une réponse.</span><span class="sxs-lookup"><span data-stu-id="34aa0-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="34aa0-124">Pour obtenir le flux contenant les données de réponse envoyées par le serveur, utilisez la méthode <xref:System.Net.HttpWebResponse.GetResponseStream%2A> de **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="34aa0-125">Après avoir lu les données de la réponse, vous devez fermer le flux de la réponse à l’aide de la méthode **Stream.Close** ou fermer la réponse en utilisant la méthode **WebResponse.Close**.</span><span class="sxs-lookup"><span data-stu-id="34aa0-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="34aa0-126">Vous n’avez pas besoin d’appeler la méthode **Close** à la fois sur le flux de la réponse et sur **WebResponse**, mais si vous le faites, cela n’a pas d’incidence.</span><span class="sxs-lookup"><span data-stu-id="34aa0-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="34aa0-127">**WebResponse.Close** appelle **Stream.Close** au moment de la fermeture de la réponse.</span><span class="sxs-lookup"><span data-stu-id="34aa0-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="34aa0-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="34aa0-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34aa0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34aa0-129">See Also</span></span>  
 [<span data-ttu-id="34aa0-130">Création de requêtes Internet</span><span class="sxs-lookup"><span data-stu-id="34aa0-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="34aa0-131">Utilisation de flux sur le réseau</span><span class="sxs-lookup"><span data-stu-id="34aa0-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="34aa0-132">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="34aa0-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="34aa0-133">Demande de données</span><span class="sxs-lookup"><span data-stu-id="34aa0-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="34aa0-134">Guide pratique pour envoyer des données à l’aide de la classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="34aa0-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
