---
title: "configuration de valeurs du d&#233;lai d&#39;attente sur une liaison | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# configuration de valeurs du d&#233;lai d&#39;attente sur une liaison
Il existe plusieurs paramètres de délai d'attente disponibles dans les liaisons WCF.  Définir ces paramètres de délai d'attente correctement peut non seulement améliorer les performances de votre service, mais également jouer un rôle dans la facilité d'utilisation et la sécurité de ce dernier.  Les délais d'attente suivants sont disponibles sur les liaisons WCF :  
  
1.  OpenTimeout  
  
2.  CloseTimeout  
  
3.  SendTimeout  
  
4.  ReceiveTimeout  
  
## Délais d'attente de liaison WCF  
 Chacun des paramètres décrits dans cette rubrique sont créés sur la liaison elle\-même, dans le code ou la configuration.  Le code suivant montre comment définir des délais d'attente par programme sur une liaison WCF dans le contexte d'un service auto\-hébergé.  
  
```csharp  
public static void Main()  
        {  
            Uri baseAddress = new Uri("http://localhost/MyServer/MyService");  
  
            try  
            {  
                ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));  
  
                WSHttpBinding binding = new WSHttpBinding();  
                binding.OpenTimeout = new TimeSpan(0, 10, 0);  
                binding.CloseTimeout = new TimeSpan(0, 10, 0);  
                binding.SendTimeout = new TimeSpan(0, 10, 0);  
                binding.ReceiveTimeout = new TimeSpan(0, 10, 0);  
  
                serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
            }  
            catch (CommunicationException ex)  
            {  
                // Handle exception ...  
            }  
        }  
  
```  
  
 L'exemple suivant montre comment configurer des délais d'attente sur une liaison dans un fichier de configuration.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding openTimeout="00:10:00"   
                 closeTimeout="00:10:00"   
                 sendTimeout="00:10:00"   
                 receiveTimeout="00:10:00">  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
```  
  
 Plus d'informations sur ces paramètres se trouvent dans la documentation de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
### Délais d'attente côté client  
 Du côté client :  
  
1.  SendTimeout – utilisé pour initialiser OperationTimeout, qui détermine le processus entier pour envoyer un message, y compris recevoir un message de réponse pour une opération de service de demande\/réponse.  Ce délai d'attente s'applique également lors de l'envoi des messages de réponse d'une méthode du contrat de rappel.  
  
2.  OpenTimeout – utilisé lors de l'ouverture de canaux lorsqu'aucune valeur du délai d'attente explicite n'est spécifiée  
  
3.  CloseTimeout – utilisé lors de la fermeture des canaux lorsqu'aucune valeur de délai d'attente explicite n'est spécifiée  
  
4.  ReceiveTimeout \- n'est pas utilisé  
  
### Délais d'attente côté client  
 Du côté service :  
  
1.  SendTimeout, OpentTimeout et CloseTimeout sont les mêmes que sur le client  
  
2.  ReceiveTimeout – utilisé par la couche d'infrastructure de service pour initialiser le délai d'inactivité de session qui contrôle la durée pendant laquelle une session peut être inactive avant expiration.