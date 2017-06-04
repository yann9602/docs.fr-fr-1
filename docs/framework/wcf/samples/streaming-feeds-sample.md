---
title: "Streaming Feeds, exemple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Streaming Feeds, exemple
Cet exemple indique comment gérer des flux de syndication qui contiennent de grandes quantités d'éléments.Sur le serveur, l'exemple décrit comment différer la création d'objets <xref:System.ServiceModel.Syndication.SyndicationItem> individuels dans le flux jusqu'au moment précédant immédiatement l'écriture de l'élément dans le flux de données réseau.  
  
 Sur le client, l'exemple décrit comment un module de formatage de flux de syndication personnalisé peut être utilisé pour lire des éléments du flux de données réseau, afin que le flux qui est lu ne soit jamais complètement mis en mémoire tampon.  
  
 Pour mieux illustrer la fonction de diffusion en continu de l'API de syndication, cet exemple utilise un scénario quelque peu improbable dans lequel le serveur expose un flux qui contient un nombre infini d'éléments.Dans ce cas, le serveur continue à générer de nouveaux éléments dans le flux jusqu'à ce qu'il détermine que le client a lu un nombre spécifié d'éléments du flux \(10 par défaut\).Pour plus de simplicité, le client et le serveur sont tous deux implémentés dans le même processus et utilisent un objet `ItemCounter` partagé pour assurer le suivi du nombre d'éléments que le client a générés.Le type `ItemCounter` existe uniquement pour permettre à l'exemple de scénario de se terminer convenablement et n'est pas un élément essentiel du modèle qui est illustré.  
  
 La démonstration utilise des itérateurs [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] \(à l'aide de la génération du mot clé `yield``return`\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les itérateurs, consultez la rubrique « Utilisation d'itérateurs » sur MSDN.  
  
## Service  
 Le service implémente un contrat <xref:System.ServiceModel.Web.WebGetAttribute> de base qui se compose d'une opération, comme l'illustre le code suivant.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
  
```  
  
 Le service implémente ce contrat en utilisant une classe `ItemGenerator` pour créer un flux potentiellement infini d'instances <xref:System.ServiceModel.Syndication.SyndicationItem> à l'aide d'un itérateur, comme l'illustre le code suivant.  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
  
```  
  
 Lorsque l'implémentation de service crée le flux, la sortie de `ItemGenerator.GenerateItems()` est utilisée à la place d'une collection d'éléments mise en mémoire tampon.  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
  
```  
  
 En conséquence, le flux d'éléments n'est jamais complètement mis en mémoire tampon.Vous pouvez observer ce comportement en définissant un point d'arrêt sur l'instruction `yield``return` dans la méthode `ItemGenerator.GenerateItems()` et en remarquant que ce point d'arrêt est rencontré pour la première fois après que le service a retourné le résultat de la méthode `StreamedFeed()`.  
  
## Client  
 Le client de cet exemple utilise une implémentation <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> personnalisée qui diffère la matérialisation d'éléments individuels dans le flux au lieu de les mettre en mémoire tampon.L'instance `StreamedAtom10FeedFormatter` personnalisée est utilisée comme suit.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
  
```  
  
 Normalement, un appel à <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> ne retourne rien jusqu'à ce que le contenu entier du flux ait été lu depuis le réseau et mis en mémoire tampon.Toutefois, l'objet `StreamedAtom10FeedFormatter` substitue <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> pour retourner un itérateur au lieu d'une collection mise en mémoire tampon, comme l'illustre le code suivant.  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
  
```  
  
 En conséquence, aucun élément n'est lu depuis le réseau avant que l'application cliente qui parcourt les résultats de `ReadItems()` ne soit prête à l'utiliser.Vous pouvez observer ce comportement en définissant un point d'arrêt sur l'instruction `yield``return` dans `StreamedAtom10FeedFormatter.DelayReadItems()` et en remarquant que ce point d'arrêt est rencontré pour la première fois après que l'appel à `ReadFrom()` se soit terminé.  
  
 Les instructions suivantes indiquent comment générer et exécuter l'exemple.Notez que bien que le serveur cesse de générer des éléments après que le client a lu 10 éléments, la sortie indique que le client lit bien plus que 10 éléments.Cela est dû au fait que la liaison de mise en réseau utilisée par l'exemple transmet les données dans des segments de quatre kilo\-octets \(Ko\).Le client reçoit donc 4 Ko de données d'éléments avant qu'il ait la possibilité de lire ne serait\-ce qu'un élément.Il s'agit du comportement normal \(l'envoi de données HTTP diffusées en continu dans des segments de taille raisonnable améliore les performances\).  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure figurant à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## Voir aussi  
 [Stand\-Alone Diagnostics Feed](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)