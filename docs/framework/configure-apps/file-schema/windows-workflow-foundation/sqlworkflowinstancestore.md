---
title: "&lt;sqlWorkflowInstanceStore&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;sqlWorkflowInstanceStore&gt;
Comportement de service qui vous permet de configurer la fonctionnalité <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, qui prend en charge les informations d'état persistantes pour les instances de service de flux de travail dans une base de données SQL Server 2005 ou SQL Server 2008.  Pour plus d'informations sur cette fonctionnalité, consultez [Magasin d'instances de workflow SQL](../../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md).  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <sqlWorkflowInstanceStore   
          connectionStringName=”String”   
          honstLockRenewalPeriod=”TimeSpan”  
          instanceCompletionAction=”DeleteNothing/DeleteAll”  
          instanceEncodingAction=”None/GZip”  
          instanceLockedExceptionAction=”NoRetry/BasicRetry/AggressiveRetry”  
          runnableInstancesDetectionPeriod=”TimeSpan” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|connectionString|Chaîne qui contient une chaîne de connexion permettant de se connecter à une base de données de persistance sous\-jacente.|  
|connectionStringName|Chaîne qui contient une chaîne de connexion nommée au serveur de base de données.  « DefaultConnectionString » est un exemple de chaîne de connexion nommée.|  
|honstLockRenewalPeriod|Valeur Timespan qui spécifie la période pendant laquelle l'hôte doit renouveler le verrou sur une instance.  Si l'hôte ne renouvelle pas le verrou pendant la période spécifiée, l'instance est déverrouillée et peut être choisie par un autre hôte.<br /><br /> Le déchargement d'un flux de travail implique qu'il soit également rendu persistant.  Si cet attribut a la valeur zéro, l'instance de flux de travail est rendue persistante et immédiatement déchargée une fois que le flux de travail devient inactif.  Affecter à cet attribut la valeur TimeSpan.MaxValue désactive l'opération de déchargement.  Les instances de flux de travail inactives ne sont jamais déchargées.|  
|instanceCompletionAction|Valeur indiquant si les données de l'instance du flux de travail sont conservées dans le magasin de persistance une fois l'instance du flux de travail terminée ou si elles sont supprimées à ce stade.  Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceCompletionAction>.<br /><br /> Les actions énumérées consistent en la suppression ou la non\-suppression des données de l'instance du magasin de persistance, lorsque l'instance a terminé son opération.<br /><br /> La conservation des instances après leur achèvement engendre une croissance rapide de la base de données de persistance, ce qui en affecte les performances.  Vous devez configurer une stratégie de vidage de la base de données pour supprimer régulièrement ces enregistrements afin de veiller à ce que les performances de la base de données soient à un niveau satisfaisant pour vos besoins.|  
|instanceEncodingOption|Valeur facultative qui indique si les informations d'état de l'instance sont compressées à l'aide de l'algorithme Gzip avant l'enregistrement des informations dans le magasin de persistance.  Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceEncodingAction>.  Les valeurs possibles pour cette propriété sont « None », qui ne spécifie aucune compression et « Gzip », qui spécifie que les données de l'instance sont compressées à l'aide de l'algorithme gzip.|  
|instanceLockedExceptionAction|Valeur qui spécifie l'action qui se produit en réponse à une exception levée lorsque l'hôte essaie de verrouiller une instance déjà verrouillée par un autre hôte.  Cette valeur est de type <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction>.<br /><br /> Les options autorisées pour ce champ sont : None, Basic Retry et Aggressive Retry.  La valeur par défaut est None.  La liste suivante fournit les descriptions de ces trois options :<br /><br /> -   Aucun  L'hôte de service n'essaie pas de verrouiller l'instance et passe l'objet <xref:System.Runtime.Persistence.InstanceLockedException> à l'appelant.<br />-   Basic Retry.  L'hôte de service réessaie de verrouiller l'instance avec un intervalle de tentative linéaire et passe l'exception à l'appelant à la fin de la séquence.<br />-   Aggressive Retry.  L'hôte de service réessaie de verrouiller l'instance avec un délai exponentiellement croissant et passe l'objet <xref:System.Runtime.Persistence.InstanceLockedException> à l'appelant à la fin de la séquence.|  
|runnableInstancesDetectionPeriod||  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>   
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>   
 [Magasin d'instances de workflow SQL](../../../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)