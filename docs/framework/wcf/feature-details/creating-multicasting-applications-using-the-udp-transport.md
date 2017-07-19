---
title: "Cr&#233;ation d&#39;applications multidiffusion en utilisant le transport UDP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Cr&#233;ation d&#39;applications multidiffusion en utilisant le transport UDP
Les applications de multidiffusion envoient de petits messages à un grand nombre de destinataires à la fois sans établir de connexion point à point.Ces applications mettent l'accent sur la vitesse par rapport à la fiabilité.En d'autres termes, il est plus important d'envoyer des données en temps voulu pour garantir que tout message spécifique est reçu.WCF prend désormais en charge des applications de multidiffusion à l'aide de <xref:System.ServiceModel.UdpBinding>.Ce transport est utile dans les scénarios où un service doit envoyer de petits messages à plusieurs clients simultanément.Une application de cotations boursières est un exemple de ce service.  
  
## Implémentation d'une application de multidiffusion  
 Pour implémenter une application de multidiffusion, définissez un contrat de service et pour chaque composant logiciel qui doit répondre aux messages de multidiffusion, implémentez le contrat de service.Par exemple, une application de cotations boursières peut définir un contrat de service :  
  
```  
// Shared contracts between the client and the service  
    [ServiceContract]  
    interface IStockTicker  
    {  
        [OperationContract(IsOneWay = true)]  
        void SendStockInfo(StockInfo[] stockInfo);  
    }  
  
    [DataContract]  
    class StockInfo  
    {  
        [DataMember]  
        public string Symbol;  
  
        [DataMember]  
        public float Price;  
  
        public StockInfo(string symbol, float price)  
        {  
            this.Symbol = symbol;  
            this.Price = price;  
        }  
    }  
  
```  
  
 Chaque application qui souhaite recevoir des messages de multidiffusion doit héberger un service qui expose cette interface.Par exemple, voici un exemple de code qui montre comment recevoir des messages de multidiffusion :  
  
```  
// Service Address  
            string serviceAddress = "soap.udp://224.0.0.1:40000";  
            // Binding  
            UdpBinding myBinding = new UdpBinding();  
            // Host  
            ServiceHost host = new ServiceHost(typeof  
                (StockTickerService), new Uri(serviceAddress));  
            // Add service endpoint  
            host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);  
            // Openup the service host  
            host.Open();  
  
            Console.WriteLine("Start receiving stock information");  
            Console.ReadLine();  
  
```  
  
 L'application spécifie l'adresse UDP sur laquelle tous les services écouteront.Un nouveau <xref:System.ServiceModel.ServiceHost> est créé et un point de terminaison de service est exposé à l'aide de <xref:System.ServiceModel.UdpBinding>.<xref:System.ServiceModel.ServiceHost> est ensuite ouvert et commence à écouter les messages entrants.  
  
 Dans ce type de scénario, il s'agit du client qui envoie en fait des messages de multidiffusion.Chaque service qui écoute à l'adresse UDP appropriée recevra les messages de multidiffusion.Voici un exemple d'un client qui envoie des messages de multidiffusion :  
  
```  
// Multicast Address  
            string serviceAddress = "soap.udp://224.0.0.1:40000";  
  
            // Binding  
            UdpBinding myBinding = new UdpBinding();  
  
            // Channel factory  
            ChannelFactory<IStockTicker> factory  
                = new ChannelFactory<IStockTicker>(myBinding,  
                            new EndpointAddress(serviceAddress));  
  
            // Call service  
            IStockTicker proxy = factory.CreateChannel();  
  
            while (true)  
            {  
                // This will continue to mulicast stock information   
                proxy.SendStockInfo(GetStockInfo());  
                Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));  
                // Wait for one second before sending another update  
                System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));  
            }  
  
```  
  
 Ce code génère les informations boursières, puis utilise le contrat de service IStockTicker de façon à envoyer des messages de multidiffusion et appeler les services à l'écoute sur l'adresse UDP appropriée.  
  
### UDP et messagerie fiable  
 La liaison UDP ne prend pas en charge la messagerie fiable en raison de la nature légère du protocole UDP.Si vous devez vérifier que les messages sont reçus par un point de terminaison distant, utilisez un transport qui prend en charge la messagerie fiable telle que HTTP ou TCP.Pour plus d'informations sur la messagerie fiable, consultez http:\/\/go.microsoft.com\/fwlink\/?LinkId\=231830 \(page pouvant être en anglais\)  
  
### Messagerie de multidiffusion bidirectionnelle  
 Alors que les messages de multidiffusion sont généralement unidirectionnels, UdpBinding prend en charge l'échange de messages de demande\/réponse.Les messages envoyés à l'aide du transport UDP contiennent une adresse d'expéditeur et de destinataire.Il faut être prudent lors de l'utilisation de l'adresse de l'expéditeur car elle peut être modifiée de manière malveillante en route.L'adresse peut être vérifiée à l'aide de le code suivant :  
  
```  
if (address.AddressFamily == AddressFamily.InterNetwork)  
          {  
              // IPv4  
              byte[] addressBytes = address.GetAddressBytes();  
              return ((addressBytes[0] & 0xE0) == 0xE0);  
          }  
          else  
          {  
              // IPv6   
              return address.IsIPv6Multicast;  
          }  
  
```  
  
 Ce code contrôle le premier octet de l'adresse du destinataire pour voir si elle contient 0xE0, ce qui signifie que l'adresse est une adresse de multidiffusion.  
  
### Considérations relatives à la sécurité  
 Lors de l'écoute des messages de multidiffusion, un paquet ICMP est envoyé au routeur pour l'informer que vous écoutez sur l'adresse de multidiffusion.Toute personne sur le sous\-réseau local qui dispose des autorisations nécessaires peut écouter ces types de paquets et déterminer l'adresse de multidiffusion et le port sur lesquels vous écoutez.  
  
 N'utilisez pas l'adresse IP de l'expéditeur à des fins de sécurité.Ces informations peuvent être usurpées et peuvent provoquer l'envoi de réponses à un ordinateur incorrect.Une façon pour atténuer cette menace consiste à activer la sécurité au niveau du message.Au niveau du réseau IPSec \(Internet Protocol Security\) et\/ou NAP \(Network Access Protection\) peut également être utilisé.