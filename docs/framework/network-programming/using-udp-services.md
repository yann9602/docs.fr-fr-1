---
title: "Utilisation des services UDP | Microsoft Docs"
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
  - "protocoles, UDP"
  - "ressources réseau, UDP"
  - "demander des données à partir d’Internet, UDP"
  - "UDP"
  - "recevoir des données, UDP"
  - "Internet, UDP"
  - "diffuser des messages à plusieurs adresses"
  - "demandes de données, UDP"
  - "classe UdpClient, à propos de la classe UdpClient"
  - "envoyer des données, UDP"
  - "protocoles d’application, UDP"
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# Utilisation des services UDP
La classe d' <xref:System.Net.Sockets.UdpClient> communique avec les services réseau à UDP.  Les propriétés et les méthodes de classe <xref:System.Net.Sockets.UdpClient> le résumé des détails de créer <xref:System.Net.Sockets.Socket> pour demander et recevoir des données à l'aide de UDP.  
  
 Le protocole UDP \(UDP\) est un protocole simple qui permet un meilleur effort de fournir des données à un hôte distant.  Toutefois, étant donné que le protocole UDP d'est un protocole sans connexions, les datagrammes d'UDP envoyés au point de terminaison distant n'est pas garanti pour arriver, ni s'ils ont la garantie d'arriver dans le même ordre dans lequel ils sont envoyés.  Les applications qui utilisent UDP doivent être préparées gérer manquants, double, et les datagrammes de hors séquence.  
  
 Pour envoyer un datagramme à UDP, vous devez connaître l'adresse réseau du périphérique réseau héberger le service que vous avez besoin et le numéro de port UDP que le service utilise pour communiquer.  Internet Assigned Numbers Authority \(Iana\) définit les numéros de port pour les services communs \(consultez www.iana.org\/assignments\/port\-numbers\).  Les services pas dans la liste d'IANA peuvent avoir des numéros de port dans la plage 1.024 à 65.535.  
  
 Les adresses réseau spéciales sont utilisées pour prendre en charge des messages de distribution d'UDP sur les réseaux basés IP\-.  La discussion suivante utilise la famille d'adresses de la version 4 d'adresses utilisée sur Internet par exemple.  
  
 Les adresses de la version 4 d'adresses utilisent 32 bits pour spécifier une adresse réseau.  Pour les adresses C de classe à un netmask de 255.255.255.0, ces bits sont séparés dans quatre octets.  Une fois exprimés en décimale, les quatre octets forment la notation ponctuée à quatre nombres familière, par exemple 192.168.100.2.  Les deux premiers octets \(192,168 dans cet exemple\) constituent le network number, le troisième octet \(100\) définit le sous\-réseau, et l'octet final à \(2\) est l'identificateur hôte.  
  
 Définissant tous les bits d'une adresse IP à une, ou 255.255.255.255, formulaires l'adresse de distribution limitée.  Envoyant un datagramme d'UDP à cette adresse fournit le message à tout hôte du segment de réseau local.  Étant donné que les messages jamais en avant de routeurs les envoyés à cette adresse, seuls les hôtes sur le segment réseau reçoit le message de distribution.  
  
 Les diffusions peuvent être dirigées à des parties spécifiques d'un réseau en définissant tous les bits de l'identificateur hôte.  Par exemple, pour envoyer une distribution à tous les hôtes sur le réseau identifié par des adresses IP à partir 192.168.1, utilisez l'adresse 192.168.1.255.  
  
 L'exemple de code suivant utilise <xref:System.Net.Sockets.UdpClient> pour écouter les datagrammes d'UDP envoyés à l'adresse de distribution dirigée 192.168.1.255 sur le port 11.000.  Le client accepte une chaîne de message et écrit le message dans la console.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 L'exemple de code suivant utilise <xref:System.Net.Sockets.UdpClient> pour envoyer des datagrammes d'UDP à l'adresse de distribution dirigée 192.168.1.255, à l'aide de le port 11.000.  Le client envoie la chaîne de message spécifiée sur la ligne de commande.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Net.Sockets.UdpClient>   
 <xref:System.Net.IPAddress>   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)