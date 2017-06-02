---
title: "Proc&#233;dure : cr&#233;er un participant de persistance personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Proc&#233;dure : cr&#233;er un participant de persistance personnalis&#233;
La procédure suivante permet de créer un participant de persistance.Pour obtenir des exemples d'implémentations de participants de persistance, consultez l'exemple [Participating in Persistence](http://go.microsoft.com/fwlink/?LinkID=177735) \(en anglais\) et la rubrique [Stocker l'extensibilité](../../../docs/framework/windows-workflow-foundation//store-extensibility.md).  
  
1.  Créez une classe dérivant des classes <xref:System.Activities.Persistence.PersistenceParticipant> ou <xref:System.Activities.Persistence.PersistenceIOParticipant>.En plus de pouvoir participer aux opérations IO, la classe PersistenceIOParticipant offre les mêmes points d'extensibilité que la classe PersistenceParticipant.Effectuez l'une ou l'ensemble des étapes suivantes :  
  
2.  Implémentez la méthode <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>.La méthode **CollectValues** comprend deux paramètres de dictionnaire : l'un pour le stockage des valeurs accessibles en lecture\/écriture et l'autre pour le stockage des valeurs en écriture seule \(utilisé ultérieurement dans les requêtes\).Dans cette méthode, vous devez remplir ces dictionnaires avec les données propres à un participant de persistance.Chaque dictionnaire contient le nom de la valeur comme clé et la valeur elle\-même comme un objet <xref:System.Runtime.DurableInstancing.InstanceValue>.  
  
     Les valeurs du dictionnaire readWriteValues sont fournies comme objets **InstanceValue**.Les valeurs du dictionnaire en écriture seule sont fournies comme objets **InstanceValue** avec les valeurs InstanceValueOptions.Optional et InstanceValueOption.WriteOnly définies.Chaque objet **InstanceValue** fourni par les implémentations **CollectValues** de l'ensemble des participants de persistance doit avoir un nom unique.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
  
    ```  
  
3.  Implémentez la méthode <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>.La méthode **MapValues** prend deux paramètres semblables aux paramètres reçus par la méthode **CollectValues**.Toutes les valeurs recueillies à l'étape **CollectValues** sont passées par ces paramètres de dictionnaire.Les nouvelles valeurs ajoutées par l'étape **MapValues** sont ajoutées aux valeurs en écriture seule.Le dictionnaire en écriture seule est utilisé pour fournir des données à une source externe qui n'est pas directement associée aux valeurs d'instance.Chaque valeur fournie par les implémentations de la méthode **MapValues** de l'ensemble des participants de persistance doit avoir un nom unique.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     La méthode <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> fournit des fonctionnalités non fournies par la méthode <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>, car elle permet une dépendance sur une autre valeur fournie par un autre participant de persistance qui n'a pas encore été traité par <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A>.  
  
4.  Implémentez la méthode **PublishValues**.La méthode **PublishValues** reçoit un dictionnaire contenant toutes les valeurs chargées depuis le magasin de persistance.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
  
    ```  
  
5.  Implémentez la méthode **BeginOnSave** si le participant est un participant IO de persistance.Cette méthode est appelée lors d'une opération d'enregistrement.Dans cette méthode, vous devez effectuer l'adjonction IO à la persistance \(l'enregistrement\) des instances de workflow.Si l'hôte utilise une transaction pour la commande de persistance correspondante, la même transaction est fournie dans Transaction.Current.En outre, les PersistenceIOParticipants peuvent rendre publique une spécification de cohérence transactionnelle. Dans ce cas, l'hôte crée une transaction pour l'épisode de persistance si aucune transaction ne serait utilisée sinon.  
  
    ```  
  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implémentez la méthode **BeginOnLoad** si le participant est un participant IO de persistance.Cette méthode est appelée lors d'une opération de chargement.Dans cette méthode, vous devez effectuer l'adjonction IO au chargement d'instances de workflow.Si l'hôte utilise une transaction pour la commande de persistance correspondante, la même transaction est fournie dans Transaction.Current.En outre, les participants IO de persistance peuvent rendre publique une spécification de cohérence transactionnelle. Dans ce cas, l'hôte crée une transaction pour l'épisode de persistance si aucune transaction ne serait utilisée sinon.  
  
    ```  
  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
  
    ```