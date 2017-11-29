---
title: Vue d'ensemble du flux de messages
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cbee0c387c4519858426a062d927ebffe9513c0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="message-flow-overview"></a>Vue d'ensemble du flux de messages
Dans un système distribué contenant des services interconnectés, il est nécessaire de déterminer les relations de causalité entre les services. Il est important de comprendre les différents composants faisant partie d'un flux de demandes pour prendre en charge des scénarios critiques, tels que le contrôle d'état, la résolution des problèmes et l'analyse de la cause première. Pour activer la corrélation des suivis entre différents services, la prise en prendre en charge des fonctionnalités suivantes a été ajoutée dans .NET Framework 4 :  
  
-   Traçage analytique : fonctionnalité de suivi très performante et à faible niveau de commentaires à l'aide du suivi d'événements Windows (ETW).  
  
-   Modèle d'activité de bout en bout pour les services WCF/WF : cette fonctionnalité prend en charge la corrélation des suivis générés par les espaces de noms  <xref:System.ServiceModel> et <xref:System.Workflow.ComponentModel>.  
  
-   Suivi ETW pour WF : cette fonctionnalité utilise les enregistrements de suivi générés par les services WF pour offrir plus de visibilité dans l'avancement et l'état actuel du workflow.  
  
 Les erreurs enregistrées dans un enregistrement de suivi peuvent être utilisées pour rechercher les erreurs de code ou les messages qui ne sont pas correctement formés. La propriété ActivityId du nœud Correlation dans l'en-tête de message de l'événement peut être utilisée pour déterminer l'activité générant une erreur. Pour activer le suivi du flux de messages par ID d’activité, consultez [configurer le suivi de flux de Message](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Cette rubrique montre comment activer le suivi de flux de messages dans le projet créé dans le didacticiel Mise en route.  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Pour activer le suivi de flux de messages dans le didacticiel Mise en route  
  
1.  Ouvrez l’Observateur d’événements en cliquant sur **Démarrer**, **exécuter**et en entrant `eventvwr.exe`.  
  
2.  Si vous n’avez pas activé le traçage analytique, développez **journaux des Applications et Services**, **Microsoft**, **Windows**, **serveur d’applications-Applications** . Sélectionnez **vue**, **afficher d’analyse et les journaux de débogage**. Avec le bouton droit **analyse** et sélectionnez **activer le journal**. Laissez l'Observateur d'événements ouvert pour visualiser les suivis.  
  
3.  Ouvrez l’exemple créé dans le [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Notez que vous devez exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en tant qu'administrateur pour pouvoir créer le service. Si vous avez le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemples installés, vous pouvez ouvrir le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé, créé dans le didacticiel.  
  
4.  Avec le bouton droit le **Service** de projet et sélectionnez **ajouter**, **un nouvel élément**. Sélectionnez **fichier de Configuration d’Application** et cliquez sur **OK**.  
  
5.  Ajoutez le code suivant au fichier App.Conf créé à l'étape précédente.  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  Exécutez l'application serveur sans déboguer en appuyant sur Ctrl+F5. Exécuter le projet client en cliquant sur le **Client** projet et en sélectionnant **déboguer**, **démarrer une nouvelle Instance**.  
  
7.  Pour suivre les événements du client vers le serveur, ajoutez le code suivant au fichier de configuration de l'application dans le projet Client.  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  Dans le fichier Program.cs du projet client, ajoutez l'instruction Using suivante.  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. Dans la méthode Main du fichier program.cs du projet client, définissez le GUID de suivi à propager dans le journal des événements.  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. Actualiser et examiner les **analyse** journal.  Recherchez un événement présentant l'ID 220.  Sélectionnez l’événement, puis cliquez sur le **détails** onglet dans le volet de visualisation. Cet événement contiendra l'ID de corrélation pour l'activité appelante.  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  Tous les événements ayant le même GUID dans l'ActivityID sont liés à une seule demande. Il peut être utilisé pour mettre en corrélation les messages d'un client spécifique avec un service spécifique. Si le client a appelé un autre service, ce même client peut être identifié par ActivityID.  
  
11. Dans certains cas, l'ActivityID peut varier du GUID d'origine au nouvel ActivityID. Le cas échéant, un événement de transfert est émis. Cet événement porte l'ID 499 et contiendra les données suivantes dans l'en-tête.  
  
    ```xml  
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">  
        <System>  
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />   
            <EventID>499</EventID>   
            ...  
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />   
            ...  
       </System>  
    </Event>  
    ```  
  
    > [!NOTE]
    >  L'événement de transfère enregistre la modification de l'ActivityID actif du GUID spécifié en tant qu'ActivityID dans le GUID spécifié comme RelatedActivityID. Une fois l'événement de transfert émis, tous les événements contiendront le nouveau GUID en tant qu'ActivityID.
