---
title: "Utilisation des services TCP | Microsoft Docs"
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
  - "demander des données à partir d’Internet, TCP"
  - "recevoir des données, TCP"
  - "classe TcpClient, à propos de la classe TcpClient"
  - "demandes de données, TCP"
  - "protocoles d’application, TCP"
  - "ressources réseau, TCP"
  - "envoyer des données, TCP"
  - "TCP"
  - "protocoles, TCP"
  - "Internet, TCP"
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Utilisation des services TCP
La classe d' <xref:System.Net.Sockets.TcpClient> demande des données d'une ressource Internet à TCP.  Les méthodes et les propriétés de **TcpClient** résument les détails pour créer <xref:System.Net.Sockets.Socket> pour demander et recevoir les données à l'aide de le TCP.  La connexion à l'appareil distant est représentée sous la forme d'un flux, les données peuvent être lues et écrites avec les techniques de flot\- gestion du .NET Framework.  
  
 Le protocole TCP établit une connexion avec un point de terminaison distant puis utilise qui connexion pour envoyer et recevoir des paquets de données.  TCP est chargé de vérifier que les packs de données sont envoyés au point de terminaison et réunis dans l'ordre approprié lorsqu'ils arrivent.  
  
 Pour établir une connexion TCP, vous devez connaître l'adresse du périphérique réseau héberger le service que vous avez besoin et vous devez connaître le port TCP requis par le service utilise pour communiquer.  Internet Assigned Numbers Authority \(Iana\) définit les numéros de port pour les services communs \(consultez www.iana.org\/assignments\/port\-numbers\).  Les services pas dans la liste d'IANA peuvent avoir des numéros de port dans la plage 1.024 à 65.535.  
  
 L'exemple suivant montre comment installer **TcpClient** pour se connecter à un serveur de temps sur le port TCP 13.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <xref:System.Net.Sockets.TcpListener> est utilisé pour surveiller un port TCP pour les requêtes entrantes puis pour créer **Socket** ou **TcpClient** qui gère la connexion au client.  La méthode d' <xref:System.Net.Sockets.TcpListener.Start%2A> écoute active, et la méthode d' <xref:System.Net.Sockets.TcpListener.Stop%2A> désactive écouter sur le port.  La méthode d' <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> accepte les demandes de connexion entrante et crée **TcpClient** pour traiter la demande, et la méthode d' <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> accepte les demandes de connexion entrante et crée **Socket** pour traiter la demande.  
  
 L'exemple suivant montre comment créer un serveur de temps de réseau à l'aide de **TcpListener** au port TCP 13 du moniteur.  Lorsqu'une demande de connexion entrante est reçue, le serveur de temps répond à la date et l'heure actuelles du serveur hôte.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## Voir aussi  
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)