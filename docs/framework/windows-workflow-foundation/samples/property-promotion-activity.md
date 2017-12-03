---
title: "Activité de promotion de propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e1237c0732b5422034db7c83c665c57c48486d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="property-promotion-activity"></a>Activité de promotion de propriétés
Cet exemple fournit une solution de bout en bout qui intègre la fonctionnalité Promotion de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> directement dans l'interface de création de workflow. Une collection d'éléments de configuration, des activités de workflow et des extensions de workflow qui simplifient l'utilisation de la fonctionnalité Promotion sont fournies. En outre, l'exemple contient un workflow simple qui montre comment utiliser cette collection.  
  
> [!NOTE]
>  Les exemples sont fournis à titre éducatif uniquement. Ils ne sont pas destinés à être utilisés dans un environnement de production et n'ont pas été testés à cet usage. Microsoft ne fournit aucun support technique pour ces exemples.  
  
## <a name="prerequisites"></a>Composants requis  
  
-   Base de données <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> initialisée  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Exemples de projet  
  
-   Le **PropertyPromotionActivity** projet contient des fichiers pour les éléments de configuration spécifiques à la promotion, activités de workflow et extensions de flux de travail.  
  
-   Le **CounterServiceApplication** projet contient un exemple de workflow qui utilise le **SqlWorkflowInstanceStorePromotion** projet.  
  
-   Script SQL (PropertyPromotionActivitySQLSample.sql) qui doit être exécuté sur la base de données <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
-   Un fichier solution qui lie les deux projets [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Pour configurer et exécuter l'exemple  
  
1.  Initialisez une base de données de persistance de workflow.  
  
    1.  Accédez au répertoire de l'exemple (\WF\Basic\Persistence\PropertyPromotionActivity) et exécutez CreateInstanceStore.cmd.  
  
    2.  Si les privilèges d'administrateur ne sont pas disponibles, créez une connexion SQL Server. Dans SQL Server Management Studio, accédez à **sécurité**, **connexions**. Avec le bouton droit **connexions** et créez une nouvelle connexion. Ajoutez votre utilisateur ACL au rôle SQL en ouvrant **bases de données**, **InstanceStore**, **sécurité**. Avec le bouton droit **utilisateurs** et sélectionnez **nouvel utilisateur**. Définir le **nom de connexion** à l’utilisateur créé ci-dessus. Ajoutez l'utilisateur à l'appartenance au rôle de base de données System.Activities.DurableInstancing.InstanceStoreUsers (et autres). Notez qu'il est possible que l'utilisateur existe déjà (par exemple, l'utilisateur dbo).  
  
2.  Ouvrez le fichier solution PropertyPromotionActivity.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Si vous avez créé le magasin d'instances dans une base de données autre que celle d'une installation locale de SQL Server Express, mettez à jour la chaîne de connexion à la base de données. Modifiez le fichier App.config sous le **CounterServiceApplication** en définissant la valeur de la `connectionString` de l’attribut le `sqlWorkflowInstanceStorePromotion` nœud afin qu’il pointe vers la base de données de persistance qui a été initialisé dans l’étape 1.  
  
4.  Générez et exécutez la solution. Le service WF Compteur et une instance du workflow démarrent ainsi automatiquement.  
  
5.  Sélectionnez rapidement toutes les lignes dans la vue [dbo].[CounterService] de votre base de données de persistance (cette vue a été ajoutée en exécutant CreateInstanceStore.cmd à l'étape 1). Un ensemble de résultats semblable au suivant s'affiche :  
  
    |InstanceId|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     À mesure que vous actualisez la vue, vous noterez que CounterValue et CounterValueLastUpdated changent toutes les deux secondes. Il s'agit de l'intervalle auquel le compteur se met à jour. CounterValue et CounterValueLastUpdated représentent les propriétés promues de ce workflow.  
  
## <a name="to-remove-the-sample"></a>Pour supprimer l'exemple  
  
-   Exécutez RemoveInstanceStore.cmd dans le répertoire de l'exemple (\WF\Basic\Persistence\PropertyPromotionActivity).  
  
## <a name="understanding-this-sample"></a>Présentation de l'exemple  
 Cet exemple contient deux projets et un fichier SQL :  
  
-   **CounterServiceApplication** est une application console qui héberge un service WF compteur simple. Lors de la réception d'un message unidirectionnel par le biais du point de terminaison `Start`, le workflow compte de 0 à 29, incrémentant une variable de compteur toutes les deux secondes. Après chaque incrément du compteur, le workflow est persistant et les propriétés promues sont mises à jour dans la vue [dbo].[CounterService]. Si l'application console s'exécute, elle héberge le service WF et envoie un message au point de terminaison `Start`, ce qui crée une instance WF Compteur.  
  
-   **PropertyPromotionActivity** est une bibliothèque de classes qui contient les éléments de configuration, activités de workflow et extensions de workflow qui les **CounterServiceApplication** utilise.  
  
-   **PropertyPromotionActivitySQLSample.sql** crée et ajoute la vue [dbo]. [ CounterService] à la base de données.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Utilisation de l'élément de configuration SqlWorkflowInstanceStorePromotion  
 L'élément de configuration `SqlWorkflowInstanceStorePromotion` hérite de l'élément de configuration `SqlWorkflowInstanceStore`, mais ajoute un élément de configuration supplémentaire nommé `promotionSets`. L'élément `promotionSets` permet de spécifier les propriétés promues via la configuration. Il s'agit du fichier de configuration utilisé par l'exemple :  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 Examinez la définition de la vue [dbo].[CounterService].  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Si une instance de workflow est persistante, une ligne est insérée dans la vue `InstancePromotedProperties` pour chaque `PromotionSet` defini dans la configuration. Cette ligne contient toutes les propriétés promues de `PromotionSet` (une propriété promue par colonne). Ce `PromotionSet` est indexé par le tuple : `InstanceId, PromotionName`. Dans cet exemple, un `PromotionSet` est défini dans la configuration dont l'attribut name est `CounterService`. Notez que la colonne de valeur `PromotionName` correspond à l'attribut name de l'élément `PromotionSet`.  
  
 L'ordre des éléments `promotedValue` correspond à la position des propriétés promues dans la vue `InstancePromotedProperties`. `Count` est le premier élément `promotedValue`. Par conséquent, il est mappé à la colonne `Value1` dans la vue `InstancePromotedProperties`. `LastIncrementedAt` est le deuxième élément `promotedValue`. Par conséquent, il est mappé à la colonne `Value2` dans la vue `InstancePromotedProperties`.  
  
#### <a name="using-the-promotevalue-activity"></a>Utilisation de l'activité PromoteValue  
 Examinez le fichier CounterService.xamlx dans le Concepteur [!INCLUDE[wf2](../../../../includes/wf2-md.md)]. Notez qu'il existe deux activités spécifiques dans la définition WF : `PromoteValue<DateTime>` et `PromoteValue<Int32>`.  
  
 L'activité `PromoteValue<Int32>` a son membre `Name` défini comme `Count`. Cela correspond au premier élément `promotedValue` dans la configuration, et son membre `Value` est défini comme variable de workflow `Counter`. Si le workflow est persistant, la variable de workflow `Counter` est persistante en tant que propriété promue dans la colonne `Value1` de la vue `InstancePromotedProperties`.  
  
 L'activité `PromoteValue<DateTime>` a son membre `Name` défini comme `LastIncrementedAt`. Cela correspond au deuxième élément `promotedValue` dans la configuration, et son membre `Value` est défini comme variable de workflow `TimeLastIncremented`. En d'autres termes, si le workflow est persistant, la valeur pour la variable de workflow `TimeLastIncremented` est persistante en tant que propriété promue dans la colonne `Value2` de la vue `InstancePromotedProperties`.  
  
 Notez que l'activité `PromotedValue` contient aussi un membre Boolean nommé `ClearExistingPromotedData`. Si la valeur `true` est affectée à ce membre, toutes les valeurs de propriété promue sont supprimées jusqu'à ce point dans le workflow. Par exemple, si une activité Sequence est définie comme suit :  
  
1.  PromoteValue {nom = « Count », valeur = 3}  
  
2.  PromoteValue {nom = « LastIncrementedAt », valeur = 1-1-2000}  
  
3.  Persister  
  
4.  PromoteValue {nom = « Count », valeur = 4, ClearExistingPromotedData = true}  
  
5.  Persister  
  
 Sur la deuxième persistance, la valeur promue pour `Count` sera 4. Toutefois, la valeur promue pour `LastIncrementedAt` sera `NULL`. Si la valeur `ClearExistingPromotedData` n'a pas été affectée à `true` à l'étape 4, après la deuxième persistance, la valeur promue pour Count sera 4. Par conséquent, la valeur promue pour `LastIncrementedAt` sera toujours 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Cette bibliothèque de classes contient les classes publiques suivantes pour simplifier l'utilisation de la fonctionnalité Promotion de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.  
  
#### <a name="promotevalue-class"></a>Classe PromoteValue  
 Cette classe promeut une seule propriété. Le nom de la propriété promue doit correspondre à l'attribut name d'un élément `promotedValue` dans la configuration. Cette activité peut être utilisée dans le Concepteur de Workflow. Pour obtenir un exemple d'utilisation, consultez CounterServiceApplication.  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (Bool)  
 Supprime toutes les valeurs qui ont été promues avant cette activité.  
  
 Name (string)  
 Nom représentant cette propriété. Il doit correspondre à l’attribut de nom d’un \<promotedValue > élément dans la configuration.  
  
 Valeur (InArgument\<T >)  
 Variable/valeur à stocker dans la colonne.  
  
#### <a name="promotevalues-class"></a>Classe PromoteValues  
 Promeut plusieurs propriétés. Les noms des propriétés promues doivent correspondre à tous les attributs name des éléments `promotedValue` dans la configuration. L'utilisation est similaire à celle de l'activité `PromoteValue`, excepté que plusieurs propriétés peuvent être promues simultanément. Cette activité ne peut pas être utilisée dans le Concepteur de Workflow.  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 Dérive de `SqlWorkflowInstanceStoreBehavior`. Cette classe dérivée ajoute un participant de persistance personnalisé (qui fait également partie de cette bibliothèque) en tant qu'extension de workflow. L'implémentation des deux activités de workflow précédentes repose sur ce participant de persistance personnalisé.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Cette bibliothèque de classes contient l'implémentation de `ConfigurationElement` pour le `SqlWorkflowInstanceStorePromotionElement` et un participant de persistance personnalisé utilisé par les activités de promotion précédentes.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Ce fichier SQL crée une vue `[dbo].[CounterService]` en plus de la vue `[InstancePromotedProperties]` pour interroger toutes les instances qui ont un CounterService Promotion défini.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
