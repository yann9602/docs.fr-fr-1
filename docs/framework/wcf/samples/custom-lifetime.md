---
title: "Custom Lifetime | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Custom Lifetime
Cet exemple montre comment écrire une extension [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] afin de fournir des services de durée de vie personnalisés pour des instances de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] partagées.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
## Instanciation partagée  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] propose plusieurs modes d'instanciation pour vos instances de service.Le mode d'instanciation partagée présenté dans cette rubrique offre un moyen de partager une instance du service entre plusieurs canaux.Le client peut soit résoudre localement l'adresse du point de terminaison de l'instance, soit contacter une méthode de fabrique du service pour obtenir l'adresse du point de terminaison d'une instance en cours d'exécution.Une fois qu'il a l'adresse du point de terminaison, il peut créer un canal et démarrer la communication.L'extrait de code suivant montre comment une application cliente crée un canal vers une instance existante du service.  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
  
```  
  
 Contrairement aux autres modes d'instanciation, l'instanciation partagée a une façon unique de libérer des instances de service.Lorsque tous les canaux sont fermés pour une instance, l'exécution [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] du service démarre un minuteur.Si personne n'établit de connexion avant l'expiration du délai d'attente, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] libère l'instance et réclame les ressources.Dans le cadre de la procédure de démontage, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] appelle la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A> de toutes les implémentations d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> avant de libérer l'instance.Si toutes retournent la valeur `true`, l'instance est libérée.Sinon, l'implémentation d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> est chargée de notifier l'état inactif au `Dispatcher` à l'aide d'une méthode de rappel.  
  
 Par défaut, le délai d'inactivité d'<xref:System.ServiceModel.InstanceContext> est d'une minute.Cependant, cet exemple montre comment étendre ce délai à l'aide d'une extension personnalisée.  
  
## Extension de l'InstanceContext  
 Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> est le lien entre l'instance du service et le `Dispatcher`.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet d'étendre ce composant d'exécution en ajoutant un nouvel état ou comportement à l'aide de son modèle d'objet extensible.Le modèle d'objet extensible est utilisé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour étendre des classes d'exécution existantes avec de nouvelles fonctionnalités ou pour ajouter de nouvelles fonctionnalités d'état à un objet.Le modèle d'objet extensible contient trois interfaces : `IExtensibleObject<T>`, `IExtension<T>` et `IExtensionCollection<T>`.  
  
 L'interface `IExtensibleObject<T>` est implémentée par des objets pour autoriser des extensions qui personnalisent leurs fonctionnalités.  
  
 L'interface `IExtension<T>` est implémentée par des objets qui peuvent être des extensions de classes de type `T`.  
  
 Et enfin, l'interface `IExtensionCollection<T>` est une collection d'`IExtensions` qui permet de récupérer les `IExtensions` par leur type.  
  
 Par conséquent, pour étendre l'<xref:System.ServiceModel.InstanceContext>, vous devez implémenter l'interface `IExtension`.Dans cet exemple de projet, la classe `CustomLeaseExtension` contient cette implémentation.  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
  
```  
  
 L'interface `IExtension` possède deux méthodes : `Attach` et `Detach`.Comme leur nom le laisse supposer, ces deux méthodes sont appelées lorsque le runtime attache l'extension à une instance de la classe <xref:System.ServiceModel.InstanceContext> et l'en détache.Dans cet exemple, la méthode `Attach` est utilisée pour effectuer le suivi de l'objet <xref:System.ServiceModel.InstanceContext> qui appartient à l'instance actuelle de l'extension.  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 En outre, vous devez ajouter l'implémentation dont l'extension a besoin pour fournir la prise en charge de la durée de vie étendue.Par conséquent, l'interface `ICustomLease` est déclarée avec les méthodes voulues et est implémentée dans la classe `CustomLeaseExtension`.  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
  
```  
  
 Lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] appelle la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A> dans l'implémentation d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime>, cet appel est routé vers la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A> de `CustomLeaseExtension`.`CustomLeaseExtension` vérifie ensuite son état privé pour voir si <xref:System.ServiceModel.InstanceContext> est inactive.Si elle l'est, elle retourne `true`.Sinon, elle démarre un minuteur pour l'extension spécifiée de la durée de vie.  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
  
```  
  
 Dans l'événement `Elapsed` du minuteur, la fonction de rappel du répartiteur \(Dispatcher\) est appelée pour démarrer un autre cycle de nettoyage.  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
  
```  
  
 Il n'existe pas de moyen de renouveler le minuteur en cours d'exécution lorsqu'un nouveau message arrive pour l'instance qui passe à l'état inactif.  
  
 L'exemple implémente <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> pour intercepter les appels à la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A> et les router vers `CustomLeaseExtension`.L'implémentation d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> est contenue dans la classe `CustomLifetimeLease`.La méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A> est appelée lorsque [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est sur le point de libérer l'instance du service.Toutefois, il n'existe qu'une instance d'une implémentation d'`ISharedSessionInstance` particulière dans la collection <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes%2A> du ServiceBehavior.Cela signifie qu'il n'est pas possible de savoir quel <xref:System.ServiceModel.InstanceContext> est en cours de fermeture au moment où [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vérifie la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A>.Par conséquent, cet exemple utilise le verrouillage de threads pour sérialiser les requêtes adressées à la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.IsIdle%2A>.  
  
> [!IMPORTANT]
>  Le recours au verrouillage de threads n'est pas une approche recommandée, car la sérialisation peut considérablement affecter les performances de votre application.  
  
 Une variable membre privé est utilisée dans la classe `CustomLeaseExtension` pour effectuer le suivi de la valeur `IsIdle`.À chaque récupération de la valeur d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime>, le membre privé `IsIdle` est retourné et réinitialisé à `false`.L'affectation de `false` à cette valeur est indispensable pour que le répartiteur appelle la méthode <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime.NotifyIdle%2A>.  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
  
```  
  
 Si la propriété `ISharedSessionLifetime.IsIdle` retourne `false`, le répartiteur inscrit une fonction de rappel à l'aide de la méthode `NotifyIdle`.Cette méthode reçoit une référence à l'<xref:System.ServiceModel.InstanceContext> libéré.Par conséquent, l'exemple de code peut interroger l'extension de type `ICustomLease` et vérifier la propriété `ICustomLease.IsIdle` dans l'état étendu.  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
  
```  
  
 Avant que la propriété `ICustomLease.IsIdle` ne soit vérifiée, la propriété Callback doit être définie, condition essentielle pour que `CustomLeaseExtension` puisse indiquer au répartiteur le moment où elle devient inactive.Si `ICustomLease.IsIdle` retourne `true`, le membre privé `isIdle` reçoit simplement dans `CustomLifetimeLease` la valeur `true` et appelle la méthode de rappel.Étant donné que le code maintient un verrou, d'autres threads ne peuvent pas modifier la valeur de ce membre privé.Et la prochaine fois que le répartiteur vérifie l'`ISharedSessionLifetime.IsIdle`, il retourne `true` et laisse le répartiteur libérer l'instance.  
  
 Le travail préparatoire étant à présent terminé, l'extension personnalisée doit être raccordée au modèle de service.Pour raccorder l'implémentation de `CustomLeaseExtension` au <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit l'interface <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> qui permet d'effectuer le l'initialisation d'<xref:System.ServiceModel.InstanceContext>.Dans l'exemple, la classe `CustomLeaseInitializer` implémente cette interface et ajoute une instance de `CustomLeaseExtension` à la collection <xref:System.ServiceModel.InstanceContext.Extensions%2A> à partir de la seule initialisation de la méthode.Cette méthode est appelée par le répartiteur en initialisant l'<xref:System.ServiceModel.InstanceContext>.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 Enfin, les implémentations d'<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> et d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> sont raccordées au modèle de service à l'aide de l'implémentation d'<xref:System.ServiceModel.Description.IServiceBehavior>.Cette implémentation est placée dans la classe `CustomLeaseTimeAttribute` et dérive également de la classe de base `Attribute` pour exposer ce comportement en tant qu'attribut.Dans la méthode `IServiceBehavior.ApplyBehavior`, les instances d'<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> et les implémentations d'<xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> sont ajoutées respectivement aux collections <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes%2A> et <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> du <xref:System.ServiceModel.Dispatcher>.  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
  
```  
  
 Ce comportement peut être ajouté à une classe de l'exemple de service en l'annotant avec l'attribut `CustomLeaseTime`.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client.Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## Voir aussi