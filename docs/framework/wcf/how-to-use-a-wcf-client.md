---
title: "Comment&#160;: utiliser un client Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF (clients WCF), using"
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: 38
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 38
---
# Comment&#160;: utiliser un client Windows Communication Foundation
Il s'agit de la dernière des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  Pour disposer d'une vue d'ensemble des six tâches, consultez la rubrique [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
 Une fois qu'un proxy [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] a été créé et configuré, une instance client peut être créée, et l'application cliente peut être compilée et utilisée pour communiquer avec le service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Cette rubrique décrit les procédures pour l'instanciation et l'utilisation d'un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Cette procédure accomplit trois tâches :  
  
1.  Instancie un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
2.  Appelle les opérations de service à partir du proxy généré.  
  
3.  Ferme le client une fois que l'appel de l'opération est terminé.  
  
### Pour utiliser un client Windows Communication Foundation  
  
1.  Ouvrez le fichier Program.cs ou Program.vb du projet GettingStartedClient et remplacez le code existant par le code suivant :  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
                // Call the Add service operation.  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                value1 = 145.00D;  
                value2 = 76.54D;  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                value1 = 9.00D;  
                value2 = 81.25D;  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                value1 = 22.00D;  
                value2 = 7.00D;  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
  
    ```  
  
     Notez l'utilisation ou importez l'instruction qui importe le GettingStartedClient.ServiceReference1.  Cette opération importe le code généré par Ajouter une référence de service dans Visual Studio.  Le code instancie le proxy WCF, puis appelle chacune des opérations de service exposées par le service de calculatrice, ferme le proxy et se termine.  
  
 Vous avez maintenant terminé le didacticiel.  Vous avez défini un contrat de service, implémenté le contrat de service, généré un proxy WCF, configuré une application cliente WCF, puis utilisé le proxy pour appeler des opérations de service.  Pour tester l'application, exécutez d'abord GettingStartedHost pour démarrer le service, puis exécutez GettingStartedClient.  La sortie de GettingStartedHost doit ressembler à ceci :  
  
```Output  
  
            Le service est prêt.  Appuyez sur <Entrée> pour arrêter le service.  Received Add(100,15.99)  
Return: 115.99  
Received Subtract(145,76.54)  
Return: 68.46  
Received Multiply(9,81.25)  
Return: 731.25  
Received Divide(22,7)  
Return: 3.14285714285714    
```  
  
 La sortie de GettingStartedClient doit ressembler à ceci :  
  
```Output  
  
            Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Appuyez sur <Entrée> pour arrêter le client.  
  
```  
  
## Voir aussi  
 [Génération de clients](../../../docs/framework/wcf/building-clients.md)   
 [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md)   
 [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Comment : créer un contrat duplex](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)   
 [Comment : accéder aux services ayant un contrat duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [Self\-Host](../../../docs/framework/wcf/samples/self-host.md)