---
title: "Surveillance des échecs d'opération de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42506f7f32d0174b4f980f4e94d370cf4c137276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="monitoring-service-operation-failures"></a>Surveillance des échecs d'opération de service
Si le traçage analytique est activé pour une application, les échecs de service peuvent facilement être surveillés dans l'Observateur d'événements.  Cette rubrique montre comment déterminer quand une opération de service échoue et comment déterminer la cause de cet échec.  
  
### <a name="determining-service-operation-failure-information"></a>Indentification des informations d'échec d'une opération de service  
  
1.  Ouvrez l’Observateur d’événements en cliquant sur **Démarrer**, **exécuter**et en entrant `eventvwr.exe`.  
  
2.  Si vous n’avez pas activé le traçage analytique, développez **journaux des Applications et Services**, **Microsoft**, **Windows**, **serveur d’applications-Applications** . Sélectionnez **vue**, **afficher d’analyse et les journaux de débogage**. Avec le bouton droit **analyse** et sélectionnez **activer le journal**. Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'échec de l'opération de service.  
  
3.  Ensuite, ouvrez l’exemple créé dans le [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) dans [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Remarque : vous devez exécuter [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] en tant qu’administrateur afin que le service peut être créé. Si vous avez le [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemples installés, vous pouvez ouvrir le [mise en route](../../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé, créé dans le didacticiel.  
  
4.  Dans le fichier Program.cs du projet serveur, ajoutez la ligne de code suivante au début de la méthode `Divide` dans la classe `CalculatorService` :  
  
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
  
6.  Exécutez l’application serveur sans déboguer en appuyant sur **Ctrl + F5**.  
  
7.  Ouvrez une invite de commandes de Visual Studio.  Accédez au répertoire qui contient le client et exécutez ce dernier à partir de la ligne de commande.  
  
8.  Dans l'Observateur d'événements, désactivez et actualisez le journal Analyse et triez les événements par ID d'événement.  Rechercher un événement avec l’ID d’événement [ServiceException 219 -](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), qui décrit l’échec du service.  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  Les événements sont mis en mémoire tampon lors de leur envoi à l'Observateur d'événements ; l'événement d'échec peut ne pas apparaître immédiatement.
