---
title: "Fournisseurs de diffusion en continu (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fournisseur de données en continu [WCF Data Services]"
  - "Services de données WCF, données binaires"
  - "Services de données WCF, fournisseurs"
  - "Services de données WCF, flux"
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Fournisseurs de diffusion en continu (WCF Data Services)
Un service de données peut exposer des données Large Object Binary.  Ces données binaires peuvent représenter des flux vidéo et audio, des images, des fichiers de document ou d'autres types de supports binaires.  Lorsqu'une entité du modèle de données inclut une ou plusieurs propriétés binaires, le service de données retourne ces données binaires encodées en Base 64 au sein de l'entrée dans le flux de réponse.  Étant donné que ce type de chargement et de sérialisation de données binaires volumineuses peut affecter les performances, le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] définit un mécanisme de récupération des données binaires indépendant de l'entité à laquelle elles appartiennent.  Cela s'effectue en séparant l'entité et les données binaires de l'entité dans un ou plusieurs flux de données  
  
-   Ressource multimédia : données binaires qui appartiennent à une entité, telle qu'une vidéo, du son, une image ou d'autres types de flux de ressources multimédias.  
  
-   Entrée de lien média : une entité ayant une référence à un flux de ressources multimédias associé.  
  
 Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous définissez un flux de ressources binaires en implémentant un fournisseur de données en continu.  L'implémentation du fournisseur de diffusion en continu fournit le service de données avec le flux de ressources multimédias associé à une entité spécifique sous forme d'objet <xref:System.IO.Stream>.  Cette implémentation permet au service de données d'accepter et de retourner les ressources multimédias sur HTTP sous forme de flux de données binaires d'un type MIME spécifié.  
  
 La configuration d'un service de données afin de prendre en charge la diffusion en continu de données binaires requiert les étapes suivantes :  
  
1.  Attribuer une ou plusieurs entités dans le modèle de données comme entrées de lien média.  Ces entités ne doivent pas inclure les données binaires à transmettre en continu.  Les propriétés binaires d'une entité sont toujours retournées dans l'entrée comme des données binaires encodées Base 64.  
  
2.  Implémentation de l'interface T:System.Data.Services.Providers.IDataServiceStreamProvider  
  
3.  Définir un service de données qui implémente l'interface <xref:System.IServiceProvider>.  Le service de données utilise l'implémentation <xref:System.IServiceProvider.GetService%2A> pour accéder à l'implémentation du fournisseur de données en continu.  Cette méthode retourne l'implémentation de fournisseur de données en continu appropriée.  
  
4.  Autoriser des flux de messages volumineux dans la configuration de l'application Web.  
  
5.  Activer l'accès aux ressources binaires sur le serveur ou dans une source de données.  
  
 Les exemples de cette rubrique sont basés sur un exemple de service de diffusion de photos en continu, qui est décrit en détails dans le billet [Série Fournisseur de diffusion en continu de services de données : Implémentation d'un fournisseur de diffusion en continu \(Partie 1\)](http://go.microsoft.com/fwlink/?LinkID=198989).  Le code source pour cet exemple de service est disponible sur la [page Exemple de service de données de diffusion de photos en continu](http://go.microsoft.com/fwlink/?LinkID=198988) sur MSDN Code Gallery.  
  
## Définition d'une entrée de lien média dans le modèle de données  
 Le fournisseur de sources de données détermine la façon dont une entité est définie comme une entrée de lien média dans le modèle de données.  
  
 **Fournisseur Entity Framework**  
 Pour indiquer qu'une entité est une entrée de lien média, ajoutez l'attribut `HasStream` à la définition du type d'entité dans le modèle conceptuel, comme dans l'exemple suivant :  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Vous devez également ajouter l'espace de noms `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` à l'entité ou à la racine du fichier .edmx ou .csdl qui définit le modèle de données.  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)] service de données qui utilise le fournisseur [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] et expose une ressource multimédia, consultez le billet [Série Fournisseur de diffusion en continu de services de données : Implémentation d'un fournisseur de diffusion en continu \(Partie 1\)](http://go.microsoft.com/fwlink/?LinkID=198989).  
  
 **Fournisseur de réflexion**  
 Pour indiquer qu'une entité est une entrée de lien média, ajoutez l'objet <xref:System.Data.Services.Common.HasStreamAttribute> à la classe qui définit le type d'entité dans le fournisseur de réflexion.  
  
 **Fournisseur de services de données personnalisé**  
 Lorsque vous utilisez des fournisseurs de services personnalisés, vous implémentez l'interface <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> pour définir les métadonnées pour votre service de données.  Pour plus d'informations, consultez [Fournisseurs de services de données personnalisés](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  Vous indiquez qu'un flux de ressources binaires appartient à <xref:System.Data.Services.Providers.ResourceType> en définissant la propriété <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> sur `true` sur le <xref:System.Data.Services.Providers.ResourceType> qui représente le type d'entité, qui est une entrée de lien média.  
  
## Implémentation de l'interface IDataServiceStreamProvider  
 Pour créer un service de données qui prend en charge les flux de données binaires, vous devez implémenter l'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  Cette implémentation permet au service de données de retourner les données binaires comme un flux de données au client et de consommer les données binaires comme un flux de données transmis par le client.  Ce service de données crée une instance de cette interface chaque fois qu'il doit accéder aux données binaires sous forme de flux de données.  L'interface <xref:System.Data.Services.Providers.IDataServiceStreamProvider> spécifie les membres suivants.  
  
|Nom de membre|Description|  
|-------------------|-----------------|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|Cette méthode est appelée par le service de données pour supprimer la ressource multimédia correspondante lorsque son entrée de lien média est supprimée.  Lorsque vous implémentez <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, cette méthode contient le code qui supprime la ressource multimédia associé à l'entrée de lien média fournie.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|Cette méthode est appelée par le service de données pour retourner une ressource multimédia sous forme de flux de données.  Lorsque vous implémentez <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, cette méthode contient le code qui fournit un flux de données utilisé par le service de données pour retourner la ressource multimédia associée à l'entrée de lien média fournie.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|Cette méthode est appelée par le service de données pour retourner l'URI utilisé pour demander la ressource multimédia pour l'entrée de lien média.  Cette valeur est utilisée pour créer l'attribut `src` dans l'élément de contenu de l'entrée de lien média et qui est utilisé pour demander le flux de données.  Lorsque cette méthode retourne `null`, le service de données détermine automatiquement l'URI.  Utilisez cette méthode lorsque vous devez fournir aux clients un accès direct aux données binaires sans utiliser le fournisseur de flux.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|Cette méthode est appelée par le service de données pour retourner la valeur Content\-Type de la ressource multimédia associée à l'entrée de lien média spécifiée.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|Cette méthode est appelée par le service de données pour retourner l'eTag du flux de données associé à l'entité spécifiée.  Cette méthode est utilisée lorsque vous gérez l'accès concurrentiel des données binaires.  Lorsque cette méthode retourne la valeur null, le service de données ne suit pas l'accès concurrentiel.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|Cette méthode est appelée par le service de données pour obtenir le flux de données utilisé lors de la réception du flux de données transmis par le client.  Lorsque vous implémentez <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, vous devez retourner un flux de données accessible en écriture sur lequel le service de données écrit le flux de données reçues.|  
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|Retourne un nom de type qualifié par un espace de noms qui représente le type que le runtime du service de données doit créer pour l'entrée de lien média associée au flux de données pour la ressource multimédia insérée.|  
  
## Création du service de données en continu  
 Pour donner au runtime [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] accès à l'implémentation de <xref:System.Data.Services.Providers.IDataServiceStreamProvider>, le service de données que vous créez doit également implémenter l'interface <xref:System.IServiceProvider>.  L'exemple de code suivant illustre l'implémentation de la méthode <xref:System.IServiceProvider.GetService%2A> pour retourner une instance de classe `PhotoServiceStreamProvider` qui implémente <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
 [!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming service/cs/photodata.svc.cs#photoservicestreamingprovider)]
 [!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming service/vb/photodata.svc.vb#photoservicestreamingprovider)]  
  
 Pour plus d'informations générales sur la création d'un service de données, consultez [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
## Activation de flux binaires volumineux dans l'environnement d'hébergement  
 Lorsque vous créez un service de données dans une application Web, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est utilisé pour fournir l'implémentation du protocole HTTP. Par défaut, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limite la taille des messages HTTP à 65 kilo\-octets.  Pour pouvoir transmettre en continu des données binaires volumineuses depuis et vers le service de données, vous devez également configurer l'application Web pour autoriser les fichiers binaires volumineux et utiliser des flux de données pour le transfert.  Pour cela, ajoutez les éléments suivants dans l'élément `<configuration />` du fichier Web.config de l'application :  
  
  
  
> [!NOTE]
>  Vous devez utiliser un mode de transfert <xref:System.ServiceModel.TransferMode?displayProperty=fullName> pour vous assurer que les données binaires des messages de demande et de réponse sont transmis en continu et non mis en mémoire tampon par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Pour plus d’informations, consultez [Transfert des messages par diffusion en continu](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md) et [Quotas de transport](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Par défaut, Internet Information Services \(IIS\) limite également la taille des demandes à 4 Mo.  Pour activer votre service de données pour recevoir des flux supérieurs à 4 Mo lors d'une exécution sur IIS, vous devez également définir l'attribut `maxRequestLength` de l'[httpRuntime, élément \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/e9b81350-8aaf-47cc-9843-5f7d0c59f369) dans la section de configuration `<system.web />`, comme indiqué dans l'exemple suivant :  
  
  
  
## Utilisation de flux de données en continu dans une application cliente  
 La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de récupérer et de mettre à jour ces ressources exposées sous la forme de flux binaires sur le client.  Pour plus d'informations, consultez [Utilisation de données binaires](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## Remarques sur l'utilisation d'un fournisseur de diffusion en continu  
 Les éléments suivants sont à prendre en compte lorsque vous implémentez un fournisseur de diffusion en continu et lorsque vous accédez aux ressources multimédias d'un service de données.  
  
-   Les demandes MERGE ne sont pas prises en charge pour les ressources multimédias.  Utilisez une demande PUT pour modifier la ressource multimédia d'une entité existante.  
  
-   Une requête POST ne peut pas être utilisée pour créer une entrée de lien média.  Vous devez plutôt émettre une requête POST pour créer une ressource multimédia. Le service de données crée alors une entrée de lien média avec les valeurs par défaut.  Cette nouvelle entité peut être mise à jour par une demande MERGE ou PUT ultérieure.  Vous pouvez également envisager de mettre en cache l'entité et de faire des mises à jour dans le dispositif de nettoyage, par exemple d'affecter à la propriété la valeur de l'en\-tête Slug dans la requête POST.  
  
-   Lorsqu'une requête POST est reçue, le service de données appelle la méthode <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> pour créer la ressource multimédia avant d'appeler la méthode <xref:System.Data.Services.IUpdatable.SaveChanges%2A> pour créer l'entrée de lien média.  
  
-   Une implémentation de la méthode <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> ne doit pas retourner d'objet <xref:System.IO.MemoryStream>.  Si vous utilisez ce type de flux de données, des problèmes de ressource mémoire se produiront lorsque le service recevra des flux de données très volumineux.  
  
-   Voici des éléments à prendre en compte lors du stockage de ressources multimédias dans une base de données :  
  
    -   Une propriété binaire qui est une ressource multimédia ne doit pas être incluse dans le modèle de données.  Toutes les propriétés exposées dans un modèle de données sont retournées dans l'entrée dans un flux de réponse.  
  
    -   Pour améliorer les performances avec des flux binaires volumineux, nous vous conseillons de créer une classe de flux de données personnalisée pour stocker les données binaires dans la base de données.  Cette classe est retournée par votre implémentation de <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> et transmet les données binaires à la base de données par segments.  Pour une base de données [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], nous vous conseillons d'utiliser un FILESTREAM pour diffuser les données en continu dans la base de données lorsque la taille des données binaires est supérieure à 1 Mo.  
  
    -   Vérifiez que votre base de données est conçue pour stocker les flux de données binaires volumineux qui seront reçus par votre service de données.  
  
    -   Lorsqu'un client envoie une requête POST pour insérer une entrée de lien média avec une ressource multimédia dans une demande unique, la méthode <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> est appelée pour obtenir le flux de données avant que le service de données n'insère la nouvelle entité dans la base de données.  Une implémentation de fournisseur de diffusion en continu doit pouvoir gérer ce comportement de service de données.  Envisagez d'utiliser une table de données distincte pour stocker les données binaires ou stockez le flux de données dans un fichier jusqu'à ce que l'entité soit insérée dans la base de données.  
  
-   Lorsque vous implémentez les méthodes <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>, <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>ou <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>, vous devez utiliser les valeurs eTag et Content\-Type fournies comme paramètres de méthode.  Ne définissez pas d'en\-tête eTag ou Content\-Type dans votre implémentation de fournisseur <xref:System.Data.Services.Providers.IDataServiceStreamProvider>.  
  
-   Par défaut, le client transmet les flux binaires volumineux à l'aide d'un encodage de transfert HTTP segmenté.  Étant donné que le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ne prend pas en charge ce type d'encodage, vous ne pouvez pas utiliser ce serveur Web pour héberger un service de données en continu qui doit accepter des flux binaires volumineux. Pour plus d'informations sur le serveur de développement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez [Web Servers in Visual Studio for ASP.NET Web Projects](http://msdn.microsoft.com/fr-fr/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
<a name="versioning"></a>   
## Conditions requises pour le contrôle de version  
 Le fournisseur de diffusion en continu respecte les conditions requises pour le contrôle de version de protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] suivantes :  
  
-   Le fournisseur de diffusion en continu requiert que le client et le service de données prennent en charge les versions 2.0 et ultérieures du protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] .  
  
 Pour plus d'informations, consultez [Contrôle de version d'un service de données](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  
  
## Voir aussi  
 [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)   
 [Fournisseurs de services de données personnalisés](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)   
 [Utilisation de données binaires](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)