---
title: "Surveillance des &#233;checs d&#39;op&#233;ration de service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Surveillance des &#233;checs d&#39;op&#233;ration de service
Si le traçage analytique est activé pour une application, les échecs de service peuvent facilement être surveillés dans l'Observateur d'événements.Cette rubrique montre comment déterminer quand une opération de service échoue et comment déterminer la cause de cet échec.  
  
### Indentification des informations d'échec d'une opération de service  
  
1.  Ouvrez l'Observateur d'événements en cliquant sur **Démarrer**, puis sur **Exécuter** et en entrant `eventvwr.exe`.  
  
2.  Si vous n'avez pas activé le traçage analytique, développez **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.Sélectionnez **Afficher** et **Afficher les journaux d'analyse et de débogage**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'échec de l'opération de service.  
  
3.  Ensuite, ouvrez l'exemple créé dans le [Didacticiel de mise en route](../../../../../docs/framework/wcf/getting-started-tutorial.md) de [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)]. Notez que vous devez exécuter [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] en tant qu'administrateur afin que le service puisse être créé.Si les exemples [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont installés, vous pouvez ouvrir [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé créé dans le didacticiel.  
  
4.  Dans le fichier Program.cs du projet serveur, ajoutez la ligne de code suivante au début de la méthode `Divide` dans la classe `CalculatorService` :  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
  
    ```  
  
5.  Dans le fichier Program.cs du projet client, remplacez la valeur de value2 par zéro :  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
  
    ```  
  
6.  Exécutez l'application serveur sans déboguer en appuyant sur **Ctrl\+F5**.  
  
7.  Ouvrez une invite de commandes de Visual Studio.Accédez au répertoire qui contient le client et exécutez ce dernier à partir de la ligne de commande.  
  
8.  Dans l'Observateur d'événements, désactivez et actualisez le journal Analyse et triez les événements par ID d'événement.Recherchez l'événement assorti de l'ID [219 \- ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), qui décrit l'échec du service.  
  
    ```Output  
    Une exception non gérée de type 'System.DivideByZeroException' a été rencontrée lors du traitement du message.ToString de l'exception totale : System.DivideByZeroException : Tentative de division par zéro.  
    ```  
  
    > [!NOTE]
    >  Les événements sont mis en mémoire tampon lors de leur envoi à l'Observateur d'événements ; l'événement d'échec peut ne pas apparaître immédiatement.