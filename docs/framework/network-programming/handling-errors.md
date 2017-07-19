---
title: "Gestion des erreurs | Microsoft Docs"
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
  - "Internet, WebRequest et WebResponse (exceptions des classes)"
  - "Status (propriété)"
  - "WebExceptions (classe), à propos de la classe WebExceptions"
  - "Timeout (membre d’énumération)"
  - "ConnectFailure (membre d’énumération)"
  - "TrustFailure (membre d’énumération)"
  - "WebRequest (classe), exceptions"
  - "demande de données à partir d’Internet, gestion des erreurs"
  - "Success (membre d’énumération)"
  - "réception de données, erreurs"
  - "ProtocolError (membre d’énumération)"
  - "téléchargement de ressources Internet, gestion des erreurs"
  - "WebResponse (classe), exceptions"
  - "SendFailure (membre d’énumération)"
  - "erreurs (.NET Framework), exceptions des classes WebRequest et WebResponse"
  - "envoi de données, erreurs"
  - "réponse à une requête Internet, gestion des erreurs"
  - "NameResolutionFailure (membre d’énumération)"
  - "KeepAliveFailure (membre d’énumération)"
  - "ressources réseau , WebRequest et WebResponse (exceptions des classes)"
  - "RequestCanceled (membre d’énumération)"
  - "ReceiveFailure (membre d’énumération)"
  - "ServerProtocolViolation (membre d’énumération)"
  - "ConnectionClosed (membre d’énumération)"
  - "SecureChannelFailure (membre d’énumération)"
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Gestion des erreurs
Les classes d' <xref:System.Net.WebRequest> et d' <xref:System.Net.WebResponse> lèvent les exceptions de système \(comme <xref:System.ArgumentException>\) et les exceptions de web particulier \(qui sont [WebExceptions](frlrfsystemnetwebexceptionclasstopic) levée par la méthode d' <xref:System.Net.WebRequest.GetResponse%2A> \).  
  
 Chaque **WebException** inclut une propriété d' <xref:System.Net.WebException.Status%2A> qui contient une valeur de l'énumération d' <xref:System.Net.WebExceptionStatus> .  Vous pouvez examiner la propriété de **État** pour déterminer l'erreur qui s'est produite et prenez les mesures appropriées pour corriger l'erreur.  
  
 Le tableau suivant décrit les valeurs possibles pour la propriété de **État** .  
  
|État|Description|  
|----------|-----------------|  
|ConnectFailure|Le service distant n'a pas pu être contacté au niveau de transport.|  
|ConnectionClosed|La connexion a été fermée. prématurément|  
|KeepAliveFailure|Le serveur a fermé une connexion établie avec le jeu Conserver\- actif d'en\-tête.|  
|NameResolutionFailure|Le service de nom ne peut pas résoudre le nom d'hôte.|  
|ProtocolError|La réponse reçue du serveur était complète mais a indiqué une erreur au niveau de le protocole.|  
|ReceiveFailure|Une réponse complète n'a pas été reçue du serveur distant.|  
|RequestCanceled|La requête a été annulée.|  
|SecureChannelFailure|Une erreur s'est produite dans un lien de canal sécurisé.|  
|SendFailure|Une demande complète n'a pas pu être envoyée au serveur distant.|  
|ServerProtocolViolation|La réponse du serveur n'était pas une réponse HTTP valide.|  
|Succès|Aucune erreur n'a été rencontrée.|  
|Dépassement de délai|La réponse négative a été reçue dans le jeu de minuterie pour la demande.|  
|TrustFailure|Un certificat de serveur n'a pas pu être validé.|  
|MessageLengthLimitExceeded|Le message reçu dépassait la limite spécifiée lors de l'envoi d'une demande ou de la réception d'une réponse du serveur.|  
|En attente|Une demande asynchrone interne est en attente.|  
|PipelineFailure|Cette valeur en charge l'infrastructure. NET Framework et n'est pas destinée à être utilisée directement dans votre code.|  
|ProxyNameResolutionFailure|Le service de résolution des noms n'a pas pu résoudre le nom d'hôte du proxy.|  
|UnknownError|Une exception d'un type inconnu s'est produite.|  
  
 Lorsque la propriété de **État** est **WebExceptionStatus.ProtocolError**, **WebResponse** qui contient la réponse du serveur est disponible.  Vous pouvez examiner la réponse pour déterminer la source réel d'erreur du protocole.  
  
 l'exemple suivant montre comment intercepter **WebException**.  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
 Applications qui utilisent le jet [SocketExceptions](frlrfsystemnetsocketssocketexceptionclasstopic) de classe d' <xref:System.Net.Sockets.Socket> lorsque des erreurs se produisent sur le Winsock.  Les classes de [TCPClient](frlrfsystemnetsocketstcpclientclasstopic), de [TCPListener](frlrfsystemnetsocketstcplistenerclasstopic), et d' [UDPClient](frlrfsystemnetsocketsudpclientclasstopic) reposent sur la classe de **Socket** et lèvent **SocketExceptions** également.  
  
 Lorsque **SocketException** est levée, la classe de **SocketException** définit la propriété d' <xref:System.Net.Sockets.SocketException.ErrorCode%2A> à la dernière erreur du système d'exploitation de socket qui s'est produite.  Pour plus d'informations sur les codes d'erreur de socket, consultez la documentation de code d'erreur API du Winsock 2,0 dans MSDN.  
  
## Voir aussi  
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)